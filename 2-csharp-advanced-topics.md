# Advanced C# Topics: Deep Dive

## Reflection and Metadata Programming

Reflection is one of C#'s most powerful features, allowing programs to examine and modify their structure and behavior at runtime. Let's explore this concept step by step.

### Understanding Type Information

At its core, reflection starts with type information. Every object in C# carries metadata about its type, which we can examine:

```csharp
public class ReflectionExplorer
{
    public void ExploreType<T>(T instance) where T : class
    {
        // Get the Type object representing our instance
        Type type = instance.GetType();
        
        // We can also get type information without an instance
        Type staticType = typeof(T);

        Console.WriteLine($"Type name: {type.Name}");
        Console.WriteLine($"Full name: {type.FullName}");
        Console.WriteLine($"Assembly: {type.Assembly.GetName().Name}");
        
        // Is it a class, interface, or something else?
        Console.WriteLine($"Is class: {type.IsClass}");
        Console.WriteLine($"Is interface: {type.IsInterface}");
        
        // What does it inherit from?
        if (type.BaseType != null)
        {
            Console.WriteLine($"Base type: {type.BaseType.Name}");
        }
    }
}
```

Let's see how we might use this in practice:

```csharp
public class PersonAnalyzer
{
    public void AnalyzePersonProperties(Person person)
    {
        // Get all public properties
        var properties = person.GetType().GetProperties();
        
        foreach (var property in properties)
        {
            // Get the current value
            var value = property.GetValue(person);
            
            Console.WriteLine($"Property: {property.Name}");
            Console.WriteLine($"Type: {property.PropertyType.Name}");
            Console.WriteLine($"Current value: {value}");
            
            // Can we modify this property?
            if (property.CanWrite)
            {
                Console.WriteLine("This property can be modified");
            }
        }
    }
}
```

### Dynamic Object Creation and Method Invocation

One of the most powerful aspects of reflection is the ability to create objects and call methods dynamically:

```csharp
public class DynamicObjectCreator
{
    public object CreateInstance(string typeName, params object[] constructorArgs)
    {
        // First, find the type in the current assembly
        Type type = Type.GetType(typeName);
        if (type == null)
        {
            throw new ArgumentException($"Type {typeName} not found");
        }

        // Create an instance with the provided constructor arguments
        return Activator.CreateInstance(type, constructorArgs);
    }

    public object InvokeMethod(object instance, string methodName, params object[] parameters)
    {
        Type type = instance.GetType();
        
        // Find the method with the given name
        MethodInfo method = type.GetMethod(methodName);
        if (method == null)
        {
            throw new ArgumentException($"Method {methodName} not found");
        }

        // Invoke the method with the provided parameters
        return method.Invoke(instance, parameters);
    }
}
```

### Custom Attributes and Metadata

Custom attributes allow us to add metadata to our code. Here's a practical example using attributes for validation:

```csharp
[AttributeUsage(AttributeTargets.Property)]
public class ValidateAttribute : Attribute
{
    public string ErrorMessage { get; }
    
    public ValidateAttribute(string errorMessage)
    {
        ErrorMessage = errorMessage;
    }
}

public class RangeValidationAttribute : ValidateAttribute
{
    public double Minimum { get; }
    public double Maximum { get; }

    public RangeValidationAttribute(double min, double max, string errorMessage)
        : base(errorMessage)
    {
        Minimum = min;
        Maximum = max;
    }

    public bool IsValid(object value)
    {
        if (value == null) return false;
        
        double numValue = Convert.ToDouble(value);
        return numValue >= Minimum && numValue <= Maximum;
    }
}
```

Now let's create a validator that uses reflection to check these attributes:

```csharp
public class ObjectValidator
{
    public List<string> Validate(object instance)
    {
        var errors = new List<string>();
        var properties = instance.GetType().GetProperties();

        foreach (var property in properties)
        {
            // Get all validation attributes
            var validationAttributes = property
                .GetCustomAttributes<ValidateAttribute>();

            // Get the property's current value
            var value = property.GetValue(instance);

            foreach (var attribute in validationAttributes)
            {
                if (attribute is RangeValidationAttribute rangeAttr)
                {
                    if (!rangeAttr.IsValid(value))
                    {
                        errors.Add(rangeAttr.ErrorMessage);
                    }
                }
                // Add other validation types as needed
            }
        }

        return errors;
    }
}
```

## Strings and StringBuilder Operations

String manipulation is a fundamental part of programming, but it needs to be done efficiently. Let's explore the best practices and techniques.

### String Immutability and StringBuilder

First, let's understand why StringBuilder exists:

```csharp
public class StringPerformanceDemo
{
    public void DemonstrateStringConcatenation()
    {
        // This creates multiple string objects in memory
        string result = "";
        for (int i = 0; i < 1000; i++)
        {
            result += i.ToString(); // Creates a new string each time
        }

        // This is much more efficient
        var builder = new StringBuilder();
        for (int i = 0; i < 1000; i++)
        {
            builder.Append(i);
        }
        result = builder.ToString(); // Creates string only once
    }

    public void DemonstrateBuilderEfficiency(IEnumerable<string> items)
    {
        // Estimate the capacity to avoid resizing
        int estimatedLength = items.Sum(s => s.Length + 2);
        var builder = new StringBuilder(estimatedLength);

        foreach (var item in items)
        {
            builder.AppendLine(item);
        }

        string result = builder.ToString();
    }
}
```

### Efficient String Processing

Let's look at some efficient string processing techniques:

```csharp
public class StringProcessor
{
    public string ProcessLargeText(string text)
    {
        // Use spans for efficient string operations
        ReadOnlySpan<char> span = text.AsSpan();
        
        var builder = new StringBuilder(text.Length);
        int start = 0;

        for (int i = 0; i < span.Length; i++)
        {
            if (span[i] == ' ' || i == span.Length - 1)
            {
                // Process each word
                var word = span.Slice(start, i - start + 1);
                ProcessWord(word, builder);
                start = i + 1;
            }
        }

        return builder.ToString();
    }

    private void ProcessWord(ReadOnlySpan<char> word, StringBuilder builder)
    {
        // Capitalize first letter if it's a letter
        if (word.Length > 0 && char.IsLetter(word[0]))
        {
            builder.Append(char.ToUpper(word[0]));
            builder.Append(word.Slice(1).ToString().ToLower());
        }
        else
        {
            builder.Append(word.ToString());
        }
    }
}
```

### String Interning and Memory Management

Understanding string interning can help optimize memory usage:

```csharp
public class StringMemoryOptimizer
{
    private readonly HashSet<string> _stringPool = new();

    public string OptimizeString(string input)
    {
        // Check if we already have this string in our pool
        if (_stringPool.TryGetValue(input, out string existing))
        {
            return existing;
        }

        // If not, add it to the pool
        string internedString = string.Intern(input);
        _stringPool.Add(internedString);
        return internedString;
    }
}
```

## Dependency Injection and Service Lifecycle

Dependency Injection (DI) is a crucial concept in modern C# applications. Let's explore it thoroughly.

### Understanding Service Lifetimes

```csharp
public interface IDataService
{
    Task<string> GetDataAsync();
}

// Singleton service - one instance for the entire application
public class GlobalConfigService : IDataService
{
    private readonly string _configData;

    public GlobalConfigService()
    {
        _configData = LoadConfiguration();
    }

    public Task<string> GetDataAsync()
    {
        return Task.FromResult(_configData);
    }

    private string LoadConfiguration()
    {
        // Load configuration once
        return "Global Configuration";
    }
}

// Scoped service - new instance for each scope (e.g., request)
public class UserContextService : IDataService
{
    private readonly string _userData;

    public UserContextService()
    {
        _userData = GenerateUserContext();
    }

    public Task<string> GetDataAsync()
    {
        return Task.FromResult(_userData);
    }

    private string GenerateUserContext()
    {
        // Generate new context for each scope
        return $"User Context: {Guid.NewGuid()}";
    }
}

// Transient service - new instance each time requested
public class TimeService : IDataService
{
    public Task<string> GetDataAsync()
    {
        // New time for each request
        return Task.FromResult(DateTime.Now.ToString());
    }
}
```

### Setting Up Dependency Injection

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register services with different lifetimes
        services.AddSingleton<IDataService, GlobalConfigService>();
        services.AddScoped<IDataService, UserContextService>();
        services.AddTransient<IDataService, TimeService>();

        // Register with factory pattern
        services.AddSingleton<IDataService>(sp =>
        {
            var configuration = sp.GetRequiredService<IConfiguration>();
            return new ConfigurableDataService(configuration);
        });

        // Register multiple implementations
        services.AddKeyedTransient<IDataService, EmailService>("email");
        services.AddKeyedTransient<IDataService, SmsService>("sms");
    }
}
```

### Service Decoration and Middleware

```csharp
public class LoggingDataServiceDecorator : IDataService
{
    private readonly IDataService _inner;
    private readonly ILogger<LoggingDataServiceDecorator> _logger;

    public LoggingDataServiceDecorator(
        IDataService inner,
        ILogger<LoggingDataServiceDecorator> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<string> GetDataAsync()
    {
        _logger.LogInformation("Getting data...");
        try
        {
            var result = await _inner.GetDataAsync();
            _logger.LogInformation("Data retrieved successfully");
            return result;
        }
        catch (Exception ex)
        {
            _logger.LogError(ex, "Error getting data");
            throw;
        }
    }
}
```

### Service Resolution and Usage

```csharp
public class ServiceConsumer
{
    private readonly IEnumerable<IDataService> _services;
    private readonly IServiceProvider _serviceProvider;

    public ServiceConsumer(
        IEnumerable<IDataService> services,
        IServiceProvider serviceProvider)
    {
        _services = services;
        _serviceProvider = serviceProvider;
    }

    public async Task ProcessDataAsync()
    {
        // Use all registered services
        foreach (var service in _services)
        {
            var data = await service.GetDataAsync();
            Console.WriteLine($"Data from service {service.GetType().Name}: {data}");
        }

        // Resolve specific implementation
        using var scope = _serviceProvider.CreateScope();
        var emailService = scope.ServiceProvider
            .GetRequiredKeyedService<IDataService>("email");
        var emailData = await emailService.GetDataAsync();
    }
}
```

These implementations demonstrate key C# concepts including:
- Runtime type inspection and manipulation with Reflection
- Efficient string handling with StringBuilder and Span<T>
- Proper service lifetime management with Dependency Injection
- Clean architecture principles
- Error handling and logging
- Asynchronous programming
- Memory optimization

Would you like me to explain any of these concepts in more detail or show more practical examples of their use?