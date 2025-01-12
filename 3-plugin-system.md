# Building a Comprehensive Plugin System

Let's create a plugin system that allows for dynamic loading of functionality at runtime. We'll build this step by step, starting with the core interfaces and working our way up to the full implementation.

## Core Plugin Infrastructure

First, let's define our plugin contract and metadata:

```csharp
using System.Reflection;

public interface IPlugin
{
    string Name { get; }
    string Version { get; }
    Task InitializeAsync(IServiceProvider services);
    Task ShutdownAsync();
}

[AttributeUsage(AttributeTargets.Class)]
public class PluginMetadataAttribute : Attribute
{
    public string Name { get; }
    public string Description { get; }
    public string[] Dependencies { get; }

    public PluginMetadataAttribute(
        string name, 
        string description, 
        params string[] dependencies)
    {
        Name = name;
        Description = description;
        Dependencies = dependencies;
    }
}
```

## Plugin Discovery and Loading

Now, let's create the system that discovers and loads plugins:

```csharp
public class PluginLoader
{
    private readonly ILogger<PluginLoader> _logger;
    private readonly Dictionary<string, Assembly> _loadedAssemblies;
    private readonly Dictionary<string, IPlugin> _plugins;
    private readonly StringBuilder _loadingLog;

    public PluginLoader(ILogger<PluginLoader> logger)
    {
        _logger = logger;
        _loadedAssemblies = new Dictionary<string, Assembly>();
        _plugins = new Dictionary<string, IPlugin>();
        _loadingLog = new StringBuilder();
    }

    public async Task LoadPluginsAsync(string pluginDirectory, 
        IServiceProvider services)
    {
        _loadingLog.AppendLine($"Starting plugin discovery in: {pluginDirectory}");
        
        // Find all DLL files in the plugin directory
        var dllFiles = Directory.GetFiles(pluginDirectory, "*.dll", 
            SearchOption.AllDirectories);

        foreach (var dllPath in dllFiles)
        {
            try
            {
                await LoadPluginAssemblyAsync(dllPath, services);
            }
            catch (Exception ex)
            {
                _loadingLog.AppendLine(
                    $"Error loading assembly {dllPath}: {ex.Message}");
                _logger.LogError(ex, "Failed to load plugin assembly: {Path}", 
                    dllPath);
            }
        }

        // After loading all assemblies, resolve dependencies
        await ResolveDependenciesAsync(services);
    }

    private async Task LoadPluginAssemblyAsync(string assemblyPath, 
        IServiceProvider services)
    {
        // Load the assembly
        var assembly = Assembly.LoadFrom(assemblyPath);
        _loadedAssemblies[assembly.FullName] = assembly;

        // Find all types implementing IPlugin
        var pluginTypes = assembly.GetTypes()
            .Where(t => typeof(IPlugin).IsAssignableFrom(t) && 
                       !t.IsInterface && !t.IsAbstract);

        foreach (var pluginType in pluginTypes)
        {
            var metadata = pluginType.GetCustomAttribute<PluginMetadataAttribute>();
            if (metadata == null)
            {
                _loadingLog.AppendLine(
                    $"Warning: Plugin {pluginType.Name} lacks metadata attribute");
                continue;
            }

            try
            {
                // Create plugin instance
                var plugin = (IPlugin)ActivatePluginInstance(pluginType, services);
                _plugins[metadata.Name] = plugin;

                _loadingLog.AppendLine(
                    $"Successfully loaded plugin: {metadata.Name} v{plugin.Version}");
            }
            catch (Exception ex)
            {
                _loadingLog.AppendLine(
                    $"Error instantiating plugin {metadata.Name}: {ex.Message}");
                _logger.LogError(ex, "Failed to instantiate plugin: {Name}", 
                    metadata.Name);
            }
        }
    }

    private object ActivatePluginInstance(Type pluginType, 
        IServiceProvider services)
    {
        // Find the most suitable constructor
        var constructors = pluginType.GetConstructors()
            .OrderByDescending(c => c.GetParameters().Length);

        foreach (var constructor in constructors)
        {
            try
            {
                var parameters = constructor.GetParameters();
                var parameterInstances = new object[parameters.Length];

                // Resolve constructor parameters from DI container
                for (int i = 0; i < parameters.Length; i++)
                {
                    parameterInstances[i] = services.GetService(
                        parameters[i].ParameterType);
                    if (parameterInstances[i] == null)
                    {
                        throw new InvalidOperationException(
                            $"Cannot resolve parameter {parameters[i].Name} " + 
                            $"of type {parameters[i].ParameterType}");
                    }
                }

                return constructor.Invoke(parameterInstances);
            }
            catch (Exception)
            {
                continue; // Try next constructor
            }
        }

        // If no constructor worked with DI, try parameterless constructor
        return Activator.CreateInstance(pluginType);
    }

    private async Task ResolveDependenciesAsync(IServiceProvider services)
    {
        var resolved = new HashSet<string>();
        var failed = new HashSet<string>();

        foreach (var plugin in _plugins.Values)
        {
            await ResolveDependencyTreeAsync(plugin, resolved, failed, services);
        }
    }

    private async Task ResolveDependencyTreeAsync(
        IPlugin plugin,
        HashSet<string> resolved,
        HashSet<string> failed,
        IServiceProvider services)
    {
        var metadata = plugin.GetType()
            .GetCustomAttribute<PluginMetadataAttribute>();
        
        if (metadata == null || resolved.Contains(metadata.Name))
            return;

        if (failed.Contains(metadata.Name))
        {
            throw new InvalidOperationException(
                $"Circular dependency detected for plugin: {metadata.Name}");
        }

        failed.Add(metadata.Name);

        foreach (var dependency in metadata.Dependencies)
        {
            if (!_plugins.TryGetValue(dependency, out var dependencyPlugin))
            {
                throw new InvalidOperationException(
                    $"Missing dependency {dependency} for plugin {metadata.Name}");
            }

            await ResolveDependencyTreeAsync(
                dependencyPlugin, resolved, failed, services);
        }

        failed.Remove(metadata.Name);
        
        // Initialize the plugin
        await plugin.InitializeAsync(services);
        resolved.Add(metadata.Name);

        _loadingLog.AppendLine($"Initialized plugin: {metadata.Name}");
    }

    public string GetLoadingLog()
    {
        return _loadingLog.ToString();
    }
}
```

## Plugin Management and Service Integration

Now let's create a plugin manager that handles the lifecycle of plugins:

```csharp
public class PluginManager
{
    private readonly PluginLoader _loader;
    private readonly IServiceProvider _services;
    private readonly ILogger<PluginManager> _logger;
    private readonly ConcurrentDictionary<string, IPlugin> _activePlugins;

    public PluginManager(
        IServiceProvider services,
        ILogger<PluginManager> logger)
    {
        _services = services;
        _logger = logger;
        _loader = new PluginLoader(
            services.GetRequiredService<ILogger<PluginLoader>>());
        _activePlugins = new ConcurrentDictionary<string, IPlugin>();
    }

    public async Task InitializePluginsAsync(string pluginDirectory)
    {
        try
        {
            await _loader.LoadPluginsAsync(pluginDirectory, _services);
            var loadingLog = _loader.GetLoadingLog();
            _logger.LogInformation("Plugin loading completed:\n{Log}", loadingLog);
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Failed to initialize plugins");
            throw;
        }
    }

    public async Task ShutdownAsync()
    {
        foreach (var plugin in _activePlugins.Values)
        {
            try
            {
                await plugin.ShutdownAsync();
            }
            catch (Exception ex)
            {
                _logger.LogError(ex, 
                    "Error shutting down plugin: {Name}", plugin.Name);
            }
        }
    }
}
```

## Example Plugin Implementation

Here's how we might implement a plugin using this system:

```csharp
[PluginMetadata("DataProcessor", "Processes data files", "Logger")]
public class DataProcessorPlugin : IPlugin
{
    private readonly ILogger<DataProcessorPlugin> _logger;
    private readonly StringBuilder _processingLog;

    public string Name => "DataProcessor";
    public string Version => "1.0.0";

    public DataProcessorPlugin(ILogger<DataProcessorPlugin> logger)
    {
        _logger = logger;
        _processingLog = new StringBuilder();
    }

    public async Task InitializeAsync(IServiceProvider services)
    {
        _processingLog.AppendLine($"Initializing {Name} v{Version}");
        await Task.CompletedTask;
    }

    public async Task ShutdownAsync()
    {
        _processingLog.AppendLine($"Shutting down {Name}");
        _logger.LogInformation("Processing log:\n{Log}", 
            _processingLog.ToString());
        await Task.CompletedTask;
    }

    public async Task ProcessDataAsync(string data)
    {
        _processingLog.AppendLine($"Processing data: {data}");
        await Task.Delay(100); // Simulate processing
    }
}
```

## Using the Plugin System

Here's how to set up and use the plugin system:

```csharp
public class Program
{
    public static async Task Main(string[] args)
    {
        // Set up dependency injection
        var services = new ServiceCollection()
            .AddLogging(builder =>
            {
                builder.AddConsole();
                builder.AddFile("plugin-system.log");
            })
            .AddSingleton<PluginManager>()
            .BuildServiceProvider();

        // Get plugin manager instance
        var pluginManager = services.GetRequiredService<PluginManager>();

        try
        {
            // Initialize plugins from a directory
            await pluginManager.InitializePluginsAsync("./plugins");

            // Your application logic here

            // Shutdown plugins when done
            await pluginManager.ShutdownAsync();
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

This plugin system demonstrates several advanced C# concepts:

1. Reflection Usage
   - Dynamic assembly loading
   - Type discovery
   - Attribute inspection
   - Dynamic instance creation

2. Dependency Injection
   - Service provider integration
   - Constructor parameter resolution
   - Scoped service management

3. StringBuilder Application
   - Efficient log building
   - Performance optimization for string operations

4. Asynchronous Programming
   - Proper async/await usage
   - Task management
   - Exception handling

5. Clean Architecture Principles
   - Separation of concerns
   - Interface-based design
   - Dependency inversion

The system provides several benefits:
- Dynamic loading of functionality at runtime
- Dependency management between plugins
- Efficient logging and diagnostics
- Clean separation of concerns
- Extensible architecture

Would you like me to explain any particular aspect in more detail or show how to implement specific plugin features?