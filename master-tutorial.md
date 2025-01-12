I'll help create a comprehensive C# and .NET 8 tutorial. Due to length limitations, I'll provide the first major section, and you can request subsequent sections as needed.

<tutorial>

# C# and .NET 8 Comprehensive Tutorial

## Introduction
This comprehensive tutorial covers C# and .NET 8, designed to take you from basics to advanced concepts. We'll explore everything from fundamental programming concepts to advanced features, focusing on practical, hands-on learning.

### Prerequisites
- Basic understanding of programming concepts
- .NET 8 SDK installed
- Visual Studio 2022 or VS Code with C# extensions

### What You'll Learn
- C# fundamentals and advanced features
- .NET CLI and project management
- Object-Oriented Programming
- Asynchronous Programming
- File and Network Operations
- Database Integration with Entity Framework Core
- And much more...

## Section 1: Getting Started with .NET CLI and Project Basics

### Understanding the .NET CLI
The .NET Command Line Interface (CLI) is a powerful tool for creating, building, and managing .NET applications.

```bash
# Create a new console application
dotnet new console -n MyFirstProject

# Build the project
dotnet build

# Run the project
dotnet run
```

#### Common .NET CLI Commands
```bash
dotnet new         # Create new project/solution
dotnet restore     # Restore dependencies
dotnet build       # Build the project
dotnet run         # Run the application
dotnet test        # Run unit tests
dotnet add        # Add package/reference
dotnet list       # List project references
```

<exercise>
Exercise 1.1: CLI Basics
1. Create a new console application named "CLIPractice"
2. Add the Newtonsoft.Json package to your project
3. Build and run the application
4. List all package references
</exercise>

### Basic Project Structure
Let's create a simple program to understand the project structure:

```csharp
namespace MyFirstProject;

class Program
{
    static void Main(string[] args)
    {
        Console.WriteLine("Hello, .NET 8!");
        
        // Reading command line arguments
        foreach (var arg in args)
        {
            Console.WriteLine($"Argument: {arg}");
        }
    }
}
```

### Understanding Project Files
The .csproj file:
```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net8.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>
</Project>
```

<exercise>
Exercise 1.2: Project Structure
1. Create a new console application
2. Modify the Program.cs to accept command-line arguments
3. Add a new class file named "Calculator.cs"
4. Implement basic arithmetic operations in the Calculator class
5. Use the Calculator class in your Program.cs
</exercise>

<project>
Mini-Project 1: Command-Line Calculator
Create a command-line calculator that:
1. Accepts two numbers and an operation as arguments
2. Supports addition, subtraction, multiplication, and division
3. Handles invalid inputs gracefully
4. Displays results with proper formatting

Example usage:
dotnet run -- 10 + 5
dotnet run -- 20 * 3
dotnet run -- 15 / 3

Sample Solution:
```csharp
namespace CalculatorProject;

class Calculator
{
    public static double Calculate(double a, double b, string operation)
    {
        return operation switch
        {
            "+" => a + b,
            "-" => a - b,
            "*" => a * b,
            "/" => b != 0 ? a / b : throw new DivideByZeroException(),
            _ => throw new ArgumentException("Invalid operation")
        };
    }
}

class Program
{
    static void Main(string[] args)
    {
        try
        {
            if (args.Length != 3)
            {
                Console.WriteLine("Usage: dotnet run -- <number1> <operation> <number2>");
                return;
            }

            double num1 = double.Parse(args[0]);
            double num2 = double.Parse(args[2]);
            string operation = args[1];

            double result = Calculator.Calculate(num1, num2, operation);
            Console.WriteLine($"Result: {result:F2}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }
}
```
</project>

[Next sections will cover OOP, asynchronous programming, etc. Would you like me to continue with any specific section?]

</tutorial>

This is the first section of the tutorial. Would you like me to continue with the next section, such as Object-Oriented Programming or Asynchronous Programming?

<tutorial>

## Section 2: Object-Oriented Programming in C#

### Understanding Classes and Objects

Classes are the fundamental building blocks of OOP in C#. Let's explore key concepts:

```csharp
public class Person
{
    // Properties
    public string Name { get; set; }
    public int Age { get; private set; }
    
    // Fields
    private readonly DateTime _birthDate;
    
    // Constructor
    public Person(string name, DateTime birthDate)
    {
        Name = name;
        _birthDate = birthDate;
        CalculateAge();
    }
    
    // Methods
    private void CalculateAge()
    {
        Age = DateTime.Now.Year - _birthDate.Year;
        if (DateTime.Now.DayOfYear < _birthDate.DayOfYear)
            Age--;
    }
    
    // Method overriding
    public override string ToString()
    {
        return $"{Name} ({Age} years old)";
    }
}
```

### Inheritance and Polymorphism

```csharp
public abstract class Animal
{
    public string Name { get; set; }
    
    public abstract void MakeSound();
    
    protected virtual string GetDescription()
    {
        return $"I am a {GetType().Name}";
    }
}

public class Dog : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Woof!");
    }
    
    protected override string GetDescription()
    {
        return base.GetDescription() + " and I'm loyal";
    }
}

public class Cat : Animal
{
    public override void MakeSound()
    {
        Console.WriteLine("Meow!");
    }
}
```

### Interfaces and Implementation

```csharp
public interface IMovable
{
    void Move(int x, int y);
    double Speed { get; set; }
}

public interface IDrawable
{
    void Draw();
}

public class Vehicle : IMovable, IDrawable
{
    public double Speed { get; set; }
    private int _positionX;
    private int _positionY;
    
    public void Move(int x, int y)
    {
        _positionX += x;
        _positionY += y;
        Console.WriteLine($"Moved to position: ({_positionX}, {_positionY})");
    }
    
    public void Draw()
    {
        Console.WriteLine("Drawing vehicle...");
    }
}
```

<exercise>
Exercise 2.1: Class Implementation
1. Create a `BankAccount` class with:
   - Properties for balance and account number
   - Methods for deposit and withdrawal
   - Proper validation for negative amounts
2. Implement exception handling for invalid operations
3. Create a method to transfer money between accounts
</exercise>

<exercise>
Exercise 2.2: Inheritance Practice
1. Create a `Shape` abstract class with:
   - Abstract method for calculating area
   - Abstract method for calculating perimeter
2. Implement `Circle`, `Rectangle`, and `Triangle` classes
3. Add proper validation for dimensions
</exercise>

<project>
Mini-Project 2: Library Management System

Create a simple library management system with the following features:

1. Book class:
   - Properties: Title, Author, ISBN, Available
   - Methods: CheckOut(), Return()

2. Library class:
   - Collection of books
   - Methods to add/remove books
   - Search functionality
   - Checkout/return handling

Sample Implementation:

```csharp
public class Book
{
    public string Title { get; set; }
    public string Author { get; set; }
    public string ISBN { get; set; }
    public bool Available { get; private set; } = true;
    
    public Book(string title, string author, string isbn)
    {
        Title = title;
        Author = author;
        ISBN = isbn;
    }
    
    public bool CheckOut()
    {
        if (!Available)
            return false;
            
        Available = false;
        return true;
    }
    
    public void Return()
    {
        Available = true;
    }
}

public class Library
{
    private List<Book> _books = new();
    
    public void AddBook(Book book)
    {
        _books.Add(book);
    }
    
    public bool RemoveBook(string isbn)
    {
        var book = _books.FirstOrDefault(b => b.ISBN == isbn);
        if (book != null)
        {
            return _books.Remove(book);
        }
        return false;
    }
    
    public Book? FindBook(string searchTerm)
    {
        return _books.FirstOrDefault(b => 
            b.Title.Contains(searchTerm, StringComparison.OrdinalIgnoreCase) ||
            b.Author.Contains(searchTerm, StringComparison.OrdinalIgnoreCase) ||
            b.ISBN == searchTerm);
    }
    
    public bool CheckOutBook(string isbn)
    {
        var book = FindBook(isbn);
        return book?.CheckOut() ?? false;
    }
    
    public bool ReturnBook(string isbn)
    {
        var book = FindBook(isbn);
        if (book != null)
        {
            book.Return();
            return true;
        }
        return false;
    }
}

// Usage Example
class Program
{
    static void Main()
    {
        var library = new Library();
        
        // Add some books
        library.AddBook(new Book("The Pragmatic Programmer", "Dave Thomas", "978-0135957059"));
        library.AddBook(new Book("Clean Code", "Robert C. Martin", "978-0132350884"));
        
        // Check out a book
        if (library.CheckOutBook("978-0135957059"))
        {
            Console.WriteLine("Book checked out successfully!");
        }
        
        // Try to find a book
        var book = library.FindBook("Clean Code");
        if (book != null)
        {
            Console.WriteLine($"Found: {book.Title} by {book.Author}");
        }
    }
}
```
</project>

### Best Practices and Common Pitfalls

1. Always use proper access modifiers
2. Follow Single Responsibility Principle
3. Prefer composition over inheritance
4. Use interfaces for loose coupling
5. Implement IDisposable for resource cleanup
6. Avoid deep inheritance hierarchies
7. Use properties instead of public fields
8. Initialize collections in constructors

Common Pitfalls:
- Overusing inheritance
- Not implementing proper validation
- Exposing internal state
- Ignoring proper exception handling
- Not following C# naming conventions

<exercise>
Exercise 2.3: Refactoring Challenge
Take the following poorly written class and improve it using OOP best practices:

```csharp
class data
{
    public string firstname;
    public string lastname;
    public int age;
    
    public void print()
    {
        Console.WriteLine(firstname + " " + lastname + ", " + age);
    }
    
    public void birthday()
    {
        age = age + 1;
    }
}
```
</exercise>

[Would you like me to continue with the next section on Asynchronous Programming?]

</tutorial>

This section covered the core concepts of OOP in C#. The next section will focus on asynchronous programming, including Task-based operations, async/await, and parallel programming. Would you like me to proceed with that?

<tutorial>

## Section 3: Asynchronous Programming in C#

### Understanding Async/Await Fundamentals

Asynchronous programming is crucial for building responsive applications. Let's explore the key concepts:

```csharp
public class AsyncBasics
{
    // Basic async method
    public async Task<string> GetDataAsync()
    {
        await Task.Delay(1000); // Simulating network delay
        return "Data retrieved";
    }

    // Multiple async operations
    public async Task<(string Data1, string Data2)> GetMultipleDataAsync()
    {
        var task1 = GetDataAsync();
        var task2 = GetDataAsync();
        
        // Run tasks concurrently
        await Task.WhenAll(task1, task2);
        
        return (await task1, await task2);
    }
}
```

### Task Parallel Library (TPL)

```csharp
public class ParallelProcessing
{
    public async Task ProcessItemsAsync(IEnumerable<int> items)
    {
        // Parallel foreach
        await Parallel.ForEachAsync(items, 
            new ParallelOptions { MaxDegreeOfParallelism = 3 },
            async (item, token) =>
            {
                await ProcessItemAsync(item);
            });
    }

    private async Task ProcessItemAsync(int item)
    {
        await Task.Delay(100); // Simulate work
        Console.WriteLine($"Processed item {item}");
    }
    
    // Using PLINQ
    public void ProcessWithPLINQ(IEnumerable<int> items)
    {
        var results = items.AsParallel()
                          .WithDegreeOfParallelism(3)
                          .Select(x => x * 2)
                          .ToList();
    }
}
```

### Exception Handling in Async Code

```csharp
public class AsyncExceptionHandling
{
    public async Task HandleExceptionsAsync()
    {
        try
        {
            await ThrowExceptionAsync();
        }
        catch (Exception ex)
        {
            // Handle exception
            Console.WriteLine($"Caught exception: {ex.Message}");
        }
    }

    private async Task ThrowExceptionAsync()
    {
        await Task.Delay(100);
        throw new InvalidOperationException("Async operation failed");
    }
    
    // Handling multiple tasks
    public async Task HandleMultipleTasksAsync()
    {
        var tasks = new List<Task>();
        for (int i = 0; i < 5; i++)
        {
            tasks.Add(ProcessWithPotentialErrorAsync(i));
        }

        try
        {
            await Task.WhenAll(tasks);
        }
        catch (Exception)
        {
            var failedTasks = tasks.Where(t => t.Status == TaskStatus.Faulted);
            foreach (var task in failedTasks)
            {
                Console.WriteLine($"Task failed: {task.Exception?.InnerException?.Message}");
            }
        }
    }
}
```

### Progress Reporting and Cancellation

```csharp
public class AsyncOperationsWithProgress
{
    public async Task ProcessWithProgressAsync(
        IProgress<int> progress, 
        CancellationToken cancellationToken)
    {
        for (int i = 0; i <= 100; i += 10)
        {
            cancellationToken.ThrowIfCancellationRequested();
            
            await Task.Delay(500, cancellationToken);
            progress.Report(i);
        }
    }

    // Usage example
    public async Task RunProcessAsync()
    {
        using var cts = new CancellationTokenSource();
        var progress = new Progress<int>(percent => 
            Console.WriteLine($"Progress: {percent}%"));

        try
        {
            await ProcessWithProgressAsync(progress, cts.Token);
        }
        catch (OperationCanceledException)
        {
            Console.WriteLine("Operation was cancelled");
        }
    }
}
```

<exercise>
Exercise 3.1: Async File Processing
1. Create a method that asynchronously reads multiple text files
2. Process the contents concurrently using PLINQ
3. Implement progress reporting
4. Handle exceptions appropriately
</exercise>

<exercise>
Exercise 3.2: Async Web Client
1. Create an async method to download multiple URLs
2. Implement timeout handling
3. Add progress reporting
4. Handle cancellation
</exercise>

<project>
Mini-Project 3: Async File Search Engine

Create a file search engine that asynchronously searches through directories:

```csharp
public class FileSearchEngine
{
    private readonly string _rootPath;
    
    public FileSearchEngine(string rootPath)
    {
        _rootPath = rootPath;
    }
    
    public async Task<IEnumerable<string>> SearchAsync(
        string searchPattern,
        IProgress<int> progress = null,
        CancellationToken cancellationToken = default)
    {
        var results = new ConcurrentBag<string>();
        var filesProcessed = 0;
        var totalFiles = Directory.GetFiles(_rootPath, "*.*", 
            SearchOption.AllDirectories).Length;

        await Parallel.ForEachAsync(
            Directory.EnumerateFiles(_rootPath, "*.*", 
                SearchOption.AllDirectories),
            new ParallelOptions 
            { 
                MaxDegreeOfParallelism = Environment.ProcessorCount,
                CancellationToken = cancellationToken
            },
            async (file, token) =>
            {
                try
                {
                    var content = await File.ReadAllTextAsync(file, token);
                    if (content.Contains(searchPattern, 
                        StringComparison.OrdinalIgnoreCase))
                    {
                        results.Add(file);
                    }
                    
                    Interlocked.Increment(ref filesProcessed);
                    progress?.Report((int)((double)filesProcessed / totalFiles * 100));
                }
                catch (Exception ex) when (ex is not OperationCanceledException)
                {
                    Console.WriteLine($"Error processing {file}: {ex.Message}");
                }
            });

        return results;
    }
}

// Usage Example
public class Program
{
    public static async Task Main()
    {
        var searchEngine = new FileSearchEngine(@"C:\Documents");
        var progress = new Progress<int>(percent => 
            Console.WriteLine($"Search progress: {percent}%"));
        var cts = new CancellationTokenSource();

        try
        {
            var results = await searchEngine.SearchAsync(
                "searchterm",
                progress,
                cts.Token);

            foreach (var file in results)
            {
                Console.WriteLine($"Found in: {file}");
            }
        }
        catch (OperationCanceledException)
        {
            Console.WriteLine("Search was cancelled");
        }
    }
}
```
</project>

### Best Practices and Common Pitfalls

1. Best Practices:
   - Always use async/await together
   - Avoid mixing async and sync code
   - Use ConfigureAwait(false) when appropriate
   - Implement cancellation where possible
   - Handle exceptions properly
   - Use Task.WhenAll for concurrent operations

2. Common Pitfalls:
   - Blocking on async code (using .Result or .Wait())
   - Not handling exceptions properly
   - Creating deadlocks
   - Forgetting to use cancellation tokens
   - Not implementing proper resource cleanup

<exercise>
Exercise 3.3: Async Best Practices
Identify and fix the issues in this code:

```csharp
public class ProblematicAsync
{
    public async void DoWork()  // Issue 1: async void
    {
        var result = GetDataAsync().Result;  // Issue 2: blocking
        await ProcessDataAsync(result);
    }

    private async Task<string> GetDataAsync()
    {
        return await Task.FromResult("data");  // Issue 3: unnecessary await
    }

    private Task ProcessDataAsync(string data)
    {
        throw new Exception("Error");  // Issue 4: unhandled exception
    }
}
```
</exercise>

[Would you like me to continue with the next section on File and Network Programming?]

</tutorial>

This section covered asynchronous programming in C#. The next section will focus on file operations and network programming. Would you like me to proceed with that?

<tutorial>

## Section 4: File and Network Programming

### File Operations

First, let's explore file handling using modern C# features:

```csharp
public class FileOperations
{
    public async Task<string> ReadFileAsync(string path)
    {
        try
        {
            return await File.ReadAllTextAsync(path);
        }
        catch (Exception ex) when (ex is FileNotFoundException || ex is DirectoryNotFoundException)
        {
            throw new FileOperationException($"File not found: {path}", ex);
        }
    }

    public async Task WriteFileAsync(string path, string content)
    {
        var directory = Path.GetDirectoryName(path);
        if (!Directory.Exists(directory))
        {
            Directory.CreateDirectory(directory!);
        }

        await using var fileStream = new FileStream(
            path, 
            FileMode.Create, 
            FileAccess.Write, 
            FileShare.None,
            bufferSize: 4096,
            useAsync: true);
        
        await using var writer = new StreamWriter(fileStream);
        await writer.WriteAsync(content);
    }

    // Working with file streams efficiently
    public async Task ProcessLargeFileAsync(string path, 
        Func<string, Task> lineProcessor)
    {
        await using var fileStream = new FileStream(
            path,
            FileMode.Open,
            FileAccess.Read,
            FileShare.Read,
            bufferSize: 4096,
            useAsync: true);
        
        using var reader = new StreamReader(fileStream);
        string? line;
        while ((line = await reader.ReadLineAsync()) != null)
        {
            await lineProcessor(line);
        }
    }
}
```

### File System Watcher

```csharp
public class FileSystemMonitor : IDisposable
{
    private readonly FileSystemWatcher _watcher;
    
    public FileSystemMonitor(string path)
    {
        _watcher = new FileSystemWatcher(path)
        {
            NotifyFilter = NotifyFilters.FileName 
                          | NotifyFilters.DirectoryName
                          | NotifyFilters.LastWrite,
            EnableRaisingEvents = true
        };

        _watcher.Created += OnFileCreated;
        _watcher.Changed += OnFileChanged;
        _watcher.Deleted += OnFileDeleted;
    }

    private void OnFileCreated(object sender, FileSystemEventArgs e)
    {
        Console.WriteLine($"File created: {e.FullPath}");
    }

    private void OnFileChanged(object sender, FileSystemEventArgs e)
    {
        Console.WriteLine($"File changed: {e.FullPath}");
    }

    private void OnFileDeleted(object sender, FileSystemEventArgs e)
    {
        Console.WriteLine($"File deleted: {e.FullPath}");
    }

    public void Dispose()
    {
        _watcher.Dispose();
    }
}
```

### Network Programming

#### HTTP Client Operations

```csharp
public class NetworkOperations
{
    private readonly HttpClient _httpClient;
    
    public NetworkOperations()
    {
        _httpClient = new HttpClient
        {
            Timeout = TimeSpan.FromSeconds(30)
        };
    }

    public async Task<string> FetchDataAsync(string url)
    {
        try
        {
            using var response = await _httpClient.GetAsync(url);
            response.EnsureSuccessStatusCode();
            return await response.Content.ReadAsStringAsync();
        }
        catch (HttpRequestException ex)
        {
            throw new NetworkException($"Failed to fetch data from {url}", ex);
        }
    }

    public async Task DownloadFileAsync(
        string url, 
        string destinationPath,
        IProgress<double> progress = null)
    {
        using var response = await _httpClient.GetAsync(
            url, 
            HttpCompletionOption.ResponseHeadersRead);
        
        response.EnsureSuccessStatusCode();
        var totalBytes = response.Content.Headers.ContentLength ?? -1L;

        await using var contentStream = await response.Content.ReadAsStreamAsync();
        await using var fileStream = new FileStream(
            destinationPath, 
            FileMode.Create, 
            FileAccess.Write, 
            FileShare.None, 
            bufferSize: 8192, 
            useAsync: true);

        var buffer = new byte[8192];
        var totalBytesRead = 0L;
        int bytesRead;

        while ((bytesRead = await contentStream.ReadAsync(buffer)) > 0)
        {
            await fileStream.WriteAsync(buffer.AsMemory(0, bytesRead));
            totalBytesRead += bytesRead;

            if (totalBytes > 0 && progress != null)
            {
                var progressPercentage = (double)totalBytesRead / totalBytes;
                progress.Report(progressPercentage);
            }
        }
    }
}
```

#### TCP Client/Server Communication

```csharp
public class TcpServer
{
    private readonly TcpListener _listener;
    private readonly CancellationTokenSource _cts;
    
    public TcpServer(int port)
    {
        _listener = new TcpListener(IPAddress.Any, port);
        _cts = new CancellationTokenSource();
    }

    public async Task StartAsync()
    {
        _listener.Start();
        
        try
        {
            while (!_cts.Token.IsCancellationRequested)
            {
                var client = await _listener.AcceptTcpClientAsync(_cts.Token);
                _ = HandleClientAsync(client);
            }
        }
        finally
        {
            _listener.Stop();
        }
    }

    private async Task HandleClientAsync(TcpClient client)
    {
        try
        {
            using (client)
            {
                var stream = client.GetStream();
                var buffer = new byte[1024];
                
                while (!_cts.Token.IsCancellationRequested)
                {
                    var bytesRead = await stream.ReadAsync(
                        buffer, 
                        0, 
                        buffer.Length, 
                        _cts.Token);
                        
                    if (bytesRead == 0) break;

                    await stream.WriteAsync(
                        buffer, 
                        0, 
                        bytesRead, 
                        _cts.Token);
                }
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Client error: {ex.Message}");
        }
    }

    public void Stop()
    {
        _cts.Cancel();
    }
}

public class TcpClient
{
    public async Task ConnectAndSendAsync(
        string server, 
        int port, 
        string message)
    {
        using var client = new System.Net.Sockets.TcpClient();
        await client.ConnectAsync(server, port);
        
        var stream = client.GetStream();
        var data = Encoding.UTF8.GetBytes(message);
        
        await stream.WriteAsync(data);
        
        var buffer = new byte[1024];
        var bytesRead = await stream.ReadAsync(buffer);
        var response = Encoding.UTF8.GetString(buffer, 0, bytesRead);
        
        Console.WriteLine($"Server response: {response}");
    }
}
```

<exercise>
Exercise 4.1: File Processing
1. Create a program that:
   - Watches a directory for new CSV files
   - Processes each new file asynchronously
   - Generates a summary report
   - Moves processed files to an archive folder
</exercise>

<exercise>
Exercise 4.2: Network Client
1. Create an HTTP client that:
   - Downloads files from multiple URLs concurrently
   - Reports progress for each download
   - Implements retry logic with exponential backoff
   - Handles timeouts and errors appropriately
</exercise>

<project>
Mini-Project 4: File Sync Service

Create a service that synchronizes files between two directories:

```csharp
public class FileSyncService
{
    private readonly string _sourceDir;
    private readonly string _targetDir;
    private readonly FileSystemWatcher _watcher;
    private readonly ConcurrentQueue<FileSystemEventArgs> _changes;
    private readonly CancellationTokenSource _cts;

    public FileSyncService(string sourceDir, string targetDir)
    {
        _sourceDir = sourceDir;
        _targetDir = targetDir;
        _changes = new ConcurrentQueue<FileSystemEventArgs>();
        _cts = new CancellationTokenSource();

        _watcher = new FileSystemWatcher(sourceDir)
        {
            NotifyFilter = NotifyFilters.FileName 
                          | NotifyFilters.LastWrite
                          | NotifyFilters.DirectoryName,
            EnableRaisingEvents = true,
            IncludeSubdirectories = true
        };

        _watcher.Created += OnChanged;
        _watcher.Changed += OnChanged;
        _watcher.Deleted += OnChanged;
        _watcher.Renamed += OnRenamed;
    }

    private void OnChanged(object sender, FileSystemEventArgs e)
    {
        _changes.Enqueue(e);
    }

    private void OnRenamed(object sender, RenamedEventArgs e)
    {
        _changes.Enqueue(e);
    }

    public async Task StartAsync()
    {
        while (!_cts.Token.IsCancellationRequested)
        {
            if (_changes.TryDequeue(out var change))
            {
                await ProcessChangeAsync(change);
            }
            else
            {
                await Task.Delay(100, _cts.Token);
            }
        }
    }

    private async Task ProcessChangeAsync(FileSystemEventArgs e)
    {
        try
        {
            var relativePath = Path.GetRelativePath(_sourceDir, e.FullPath);
            var targetPath = Path.Combine(_targetDir, relativePath);

            switch (e.ChangeType)
            {
                case WatcherChangeTypes.Created:
                case WatcherChangeTypes.Changed:
                    await SyncFileAsync(e.FullPath, targetPath);
                    break;

                case WatcherChangeTypes.Deleted:
                    File.Delete(targetPath);
                    break;

                case WatcherChangeTypes.Renamed:
                    var renameEvent = (RenamedEventArgs)e;
                    var oldTargetPath = Path.Combine(
                        _targetDir, 
                        Path.GetRelativePath(_sourceDir, renameEvent.OldFullPath));
                    File.Move(oldTargetPath, targetPath);
                    break;
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error processing change: {ex.Message}");
        }
    }

    private async Task SyncFileAsync(string sourcePath, string targetPath)
    {
        var targetDir = Path.GetDirectoryName(targetPath);
        if (!Directory.Exists(targetDir))
        {
            Directory.CreateDirectory(targetDir!);
        }

        await using var sourceStream = new FileStream(
            sourcePath, 
            FileMode.Open, 
            FileAccess.Read, 
            FileShare.Read,
            bufferSize: 4096,
            useAsync: true);

        await using var targetStream = new FileStream(
            targetPath, 
            FileMode.Create, 
            FileAccess.Write, 
            FileShare.None,
            bufferSize: 4096,
            useAsync: true);

        await sourceStream.CopyToAsync(targetStream);
    }

    public void Stop()
    {
        _cts.Cancel();
    }
}
```
</project>

### Best Practices and Common Pitfalls

1. File Operations Best Practices:
   - Always use async I/O operations
   - Properly dispose of resources using 'using' statements
   - Handle file locks and sharing violations
   - Implement proper error handling
   - Use appropriate buffer sizes

2. Network Programming Best Practices:
   - Implement timeout handling
   - Use HttpClientFactory in production
   - Handle network errors gracefully
   - Implement retry logic
   - Use cancellation tokens

Common Pitfalls:
- Not disposing of network resources
- Blocking I/O operations
- Improper error handling
- Memory leaks in file operations
- Not implementing timeout handling

[Would you like me to continue with the next section on Entity Framework Core and Database Operations?]

</tutorial>

This section covered file and network programming in C#. The next section will focus on database operations with Entity Framework Core. Would you like me to proceed with that?

<tutorial>

## Section 5: Entity Framework Core and Database Operations

### Setting Up Entity Framework Core

First, let's set up the required packages and basic configuration:

```csharp
// Required NuGet packages
// Microsoft.EntityFrameworkCore
// Microsoft.EntityFrameworkCore.SqlServer
// Microsoft.EntityFrameworkCore.Design
// Microsoft.EntityFrameworkCore.Tools

public class ApplicationDbContext : DbContext
{
    public ApplicationDbContext(DbContextOptions<ApplicationDbContext> options)
        : base(options)
    {
    }

    // DbSet properties for entities
    public DbSet<Customer> Customers { get; set; }
    public DbSet<Order> Orders { get; set; }
    public DbSet<Product> Products { get; set; }

    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
        base.OnModelCreating(modelBuilder);
        
        // Apply configurations
        modelBuilder.ApplyConfigurationsFromAssembly(typeof(ApplicationDbContext).Assembly);
    }
}
```

### Entity Configuration and Relationships

```csharp
// Domain Entities
public class Customer
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
    public List<Order> Orders { get; set; } = new();
}

public class Order
{
    public int Id { get; set; }
    public DateTime OrderDate { get; set; }
    public int CustomerId { get; set; }
    public Customer Customer { get; set; }
    public List<OrderItem> Items { get; set; } = new();
}

public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}

public class OrderItem
{
    public int OrderId { get; set
