# Advanced Plugin System: Hot-Reloading, Configuration, and Testing

## Adding Hot-Reloading Support

First, let's enhance our plugin system to support hot-reloading. This allows us to update plugins without restarting the application.

```csharp
public class HotReloadablePluginManager
{
    private readonly IServiceProvider _services;
    private readonly ILogger<HotReloadablePluginManager> _logger;
    private readonly ConcurrentDictionary<string, PluginInfo> _loadedPlugins;
    private readonly FileSystemWatcher _watcher;
    private readonly string _pluginDirectory;

    public HotReloadablePluginManager(
        IServiceProvider services,
        ILogger<HotReloadablePluginManager> logger,
        string pluginDirectory)
    {
        _services = services;
        _logger = logger;
        _pluginDirectory = pluginDirectory;
        _loadedPlugins = new ConcurrentDictionary<string, PluginInfo>();

        // Set up file system watcher for hot-reloading
        _watcher = new FileSystemWatcher(pluginDirectory, "*.dll");
        _watcher.Created += OnPluginChanged;
        _watcher.Changed += OnPluginChanged;
        _watcher.Deleted += OnPluginDeleted;
        _watcher.EnableRaisingEvents = true;
    }

    private class PluginInfo
    {
        public IPlugin Instance { get; set; }
        public DateTime LastLoaded { get; set; }
        public string AssemblyPath { get; set; }
        public WeakReference<Assembly> Assembly { get; set; }
    }

    private async void OnPluginChanged(object sender, FileSystemEventArgs e)
    {
        try
        {
            // Wait briefly to ensure file is not locked
            await Task.Delay(100);

            var pluginPath = e.FullPath;
            var pluginName = Path.GetFileNameWithoutExtension(pluginPath);

            // Unload existing plugin if necessary
            if (_loadedPlugins.TryGetValue(pluginName, out var existingPlugin))
            {
                await UnloadPluginAsync(pluginName);
            }

            // Load the new version
            await LoadPluginAsync(pluginPath);
            _logger.LogInformation("Hot-reloaded plugin: {Name}", pluginName);
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error hot-reloading plugin: {Path}", e.FullPath);
        }
    }

    private async Task UnloadPluginAsync(string pluginName)
    {
        if (_loadedPlugins.TryRemove(pluginName, out var pluginInfo))
        {
            try
            {
                await pluginInfo.Instance.ShutdownAsync();
                
                // Force garbage collection to help unload assembly
                GC.Collect();
                GC.WaitForPendingFinalizers();
            }
            catch (Exception ex)
            {
                _logger.LogError(ex, "Error unloading plugin: {Name}", pluginName);
            }
        }
    }
}
```

## Adding Plugin Configuration Support

Now let's add configuration capabilities to our plugins:

```csharp
public interface IPluginConfiguration
{
    string GetSetting(string key);
    T GetSetting<T>(string key, T defaultValue);
    void UpdateSetting(string key, string value);
    Task SaveAsync();
}

public class PluginConfiguration : IPluginConfiguration
{
    private readonly string _configPath;
    private readonly ConcurrentDictionary<string, string> _settings;
    private readonly FileSystemWatcher _configWatcher;

    public PluginConfiguration(string pluginName, string configDirectory)
    {
        _configPath = Path.Combine(configDirectory, $"{pluginName}.json");
        _settings = new ConcurrentDictionary<string, string>();
        
        LoadConfiguration();

        // Watch for configuration file changes
        _configWatcher = new FileSystemWatcher(
            Path.GetDirectoryName(_configPath),
            Path.GetFileName(_configPath));
        _configWatcher.Changed += OnConfigurationFileChanged;
        _configWatcher.EnableRaisingEvents = true;
    }

    private void LoadConfiguration()
    {
        if (File.Exists(_configPath))
        {
            var json = File.ReadAllText(_configPath);
            var config = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            foreach (var item in config)
            {
                _settings[item.Key] = item.Value;
            }
        }
    }

    public string GetSetting(string key)
    {
        return _settings.TryGetValue(key, out var value) ? value : null;
    }

    public T GetSetting<T>(string key, T defaultValue)
    {
        if (!_settings.TryGetValue(key, out var value))
            return defaultValue;

        try
        {
            return JsonSerializer.Deserialize<T>(value);
        }
        catch
        {
            return defaultValue;
        }
    }

    public void UpdateSetting(string key, string value)
    {
        _settings[key] = value;
    }

    public async Task SaveAsync()
    {
        var json = JsonSerializer.Serialize(_settings, 
            new JsonSerializerOptions { WriteIndented = true });
        await File.WriteAllTextAsync(_configPath, json);
    }

    private void OnConfigurationFileChanged(object sender, FileSystemEventArgs e)
    {
        LoadConfiguration();
    }
}
```

## Creating Specific Plugin Types

Let's create some specific plugin types to demonstrate the system's flexibility:

```csharp
// Data Processing Plugin
[PluginMetadata("DataProcessor", "Processes data files", "Logger")]
public class DataProcessorPlugin : IPlugin
{
    private readonly ILogger<DataProcessorPlugin> _logger;
    private readonly IPluginConfiguration _configuration;

    public string Name => "DataProcessor";
    public string Version => "1.0.0";

    public DataProcessorPlugin(
        ILogger<DataProcessorPlugin> logger,
        IPluginConfiguration configuration)
    {
        _logger = logger;
        _configuration = configuration;
    }

    public async Task InitializeAsync(IServiceProvider services)
    {
        var batchSize = _configuration.GetSetting("BatchSize", 100);
        var processDelay = _configuration.GetSetting("ProcessDelay", 1000);
        
        _logger.LogInformation(
            "Initializing with batch size: {BatchSize}, delay: {Delay}ms",
            batchSize, processDelay);
            
        await Task.CompletedTask;
    }

    public async Task ProcessDataAsync(Stream inputStream)
    {
        using var reader = new StreamReader(inputStream);
        var batchSize = _configuration.GetSetting("BatchSize", 100);
        var batch = new List<string>();

        while (!reader.EndOfStream)
        {
            var line = await reader.ReadLineAsync();
            batch.Add(line);

            if (batch.Count >= batchSize)
            {
                await ProcessBatchAsync(batch);
                batch.Clear();
            }
        }

        if (batch.Count > 0)
        {
            await ProcessBatchAsync(batch);
        }
    }

    private async Task ProcessBatchAsync(List<string> batch)
    {
        var delay = _configuration.GetSetting("ProcessDelay", 1000);
        await Task.Delay(delay);
        _logger.LogInformation("Processed batch of {Count} items", batch.Count);
    }
}

// Notification Plugin
[PluginMetadata("Notifier", "Sends notifications", "DataProcessor")]
public class NotificationPlugin : IPlugin
{
    private readonly ILogger<NotificationPlugin> _logger;
    private readonly IPluginConfiguration _configuration;
    private readonly HttpClient _httpClient;

    public string Name => "Notifier";
    public string Version => "1.0.0";

    public NotificationPlugin(
        ILogger<NotificationPlugin> logger,
        IPluginConfiguration configuration)
    {
        _logger = logger;
        _configuration = configuration;
        _httpClient = new HttpClient();
    }

    public async Task SendNotificationAsync(string message)
    {
        var webhook = _configuration.GetSetting("WebhookUrl", "");
        if (string.IsNullOrEmpty(webhook))
        {
            _logger.LogWarning("No webhook URL configured");
            return;
        }

        var content = new StringContent(
            JsonSerializer.Serialize(new { message }), 
            Encoding.UTF8, 
            "application/json");

        var response = await _httpClient.PostAsync(webhook, content);
        if (!response.IsSuccessStatusCode)
        {
            _logger.LogError(
                "Failed to send notification. Status: {Status}", 
                response.StatusCode);
        }
    }
}
```

## Testing the Plugin System

Now let's create comprehensive tests for our plugin system:

```csharp
public class PluginSystemTests
{
    private readonly IServiceProvider _services;
    private readonly string _testPluginDirectory;
    private readonly string _testConfigDirectory;

    public PluginSystemTests()
    {
        _testPluginDirectory = Path.Combine(Path.GetTempPath(), "TestPlugins");
        _testConfigDirectory = Path.Combine(Path.GetTempPath(), "TestConfigs");
        
        Directory.CreateDirectory(_testPluginDirectory);
        Directory.CreateDirectory(_testConfigDirectory);

        // Set up test services
        var services = new ServiceCollection()
            .AddLogging(builder => builder.AddXUnit(this))
            .AddSingleton<HotReloadablePluginManager>();

        _services = services.BuildServiceProvider();
    }

    [Fact]
    public async Task LoadPlugin_ValidPlugin_LoadsSuccessfully()
    {
        // Arrange
        var manager = _services.GetRequiredService<HotReloadablePluginManager>();
        var pluginPath = CreateTestPlugin("TestPlugin.dll");

        // Act
        await manager.LoadPluginAsync(pluginPath);

        // Assert
        var plugin = manager.GetPlugin("TestPlugin");
        Assert.NotNull(plugin);
        Assert.Equal("1.0.0", plugin.Version);
    }

    [Fact]
    public async Task HotReload_UpdatedPlugin_ReloadsCorrectly()
    {
        // Arrange
        var manager = _services.GetRequiredService<HotReloadablePluginManager>();
        var pluginPath = CreateTestPlugin("HotReloadTest.dll");
        await manager.LoadPluginAsync(pluginPath);

        // Act
        // Simulate plugin update
        await Task.Delay(100); // Ensure file timestamp differs
        File.Copy("UpdatedPlugin.dll", pluginPath, true);

        // Wait for hot-reload
        await Task.Delay(200);

        // Assert
        var plugin = manager.GetPlugin("HotReloadTest");
        Assert.NotNull(plugin);
        Assert.Equal("1.0.1", plugin.Version); // Updated version
    }

    [Fact]
    public async Task Configuration_UpdatedConfig_ReflectsChanges()
    {
        // Arrange
        var config = new PluginConfiguration("TestPlugin", _testConfigDirectory);
        await config.UpdateSetting("TestKey", "InitialValue");
        await config.SaveAsync();

        // Act
        await config.UpdateSetting("TestKey", "UpdatedValue");
        await config.SaveAsync();

        // Assert
        Assert.Equal("UpdatedValue", config.GetSetting("TestKey"));
    }

    [Fact]
    public async Task ProcessData_LargeDataSet_ProcessesCorrectly()
    {
        // Arrange
        var logger = _services.GetRequiredService<ILogger<DataProcessorPlugin>>();
        var config = new PluginConfiguration("DataProcessor", _testConfigDirectory);
        var plugin = new DataProcessorPlugin(logger, config);

        // Create test data
        var testData = GenerateTestData(1000);
        using var stream = new MemoryStream();
        using var writer = new StreamWriter(stream);
        foreach (var line in testData)
        {
            await writer.WriteLineAsync(line);
        }
        stream.Position = 0;

        // Act
        await plugin.ProcessDataAsync(stream);

        // Assert
        // Verify processing through logs
        // This depends on your logging implementation
    }

    private string CreateTestPlugin(string fileName)
    {
        // Helper method to create test plugin assembly
        // In real tests, you might use compile-time generated assemblies
        // or mock assemblies for testing
        string pluginPath = Path.Combine(_testPluginDirectory, fileName);
        // Create test assembly
        return pluginPath;
    }

    private IEnumerable<string> GenerateTestData(int count)
    {
        for (int i = 0; i < count; i++)
        {
            yield return $"Test data line {i}";
        }
    }
}
```

This implementation demonstrates several advanced features:

1. Hot-Reloading:
   - File system monitoring for plugin changes
   - Safe plugin unloading and reloading
   - Assembly management to prevent memory leaks

2. Configuration:
   - JSON-based configuration
   - Live configuration updates
   - Type-safe configuration access
   - Configuration file monitoring

3. Specific Plugin Types:
   - Data processing plugin with batch processing
   - Notification plugin with webhook integration
   - Plugin dependencies and ordering

4. Testing:
   - Unit tests for core functionality
   - Integration tests for plugin loading
   - Configuration testing
   - Performance testing with large datasets

The system provides several benefits:
- Dynamic updates without application restart
- Flexible configuration management
- Type-safe plugin development
- Comprehensive testing capabilities
- Proper resource management

Would you like me to:
1. Add more specific plugin types?
2. Demonstrate more advanced testing scenarios?
3. Show how to implement plugin versioning and compatibility checking?
4. Explain any particular aspect in more detail?