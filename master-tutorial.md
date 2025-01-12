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

<code>
# Create a new console application
dotnet new console -n MyFirstProject

# Build the project
dotnet build

# Run the project
dotnet run
</code>

#### Common .NET CLI Commands
<code>
dotnet new         # Create new project/solution
dotnet restore     # Restore dependencies
dotnet build       # Build the project
dotnet run         # Run the application
dotnet test        # Run unit tests
dotnet add        # Add package/reference
dotnet list       # List project references
</code>

<exercise>
Exercise 1.1: CLI Basics
1. Create a new console application named "CLIPractice"
2. Add the Newtonsoft.Json package to your project
3. Build and run the application
4. List all package references
</exercise>

### Basic Project Structure
Let's create a simple program to understand the project structure:

<code>
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
</code>

### Understanding Project Files
The .csproj file:
<code>
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net8.0</TargetFramework>
    <ImplicitUsings>enable</ImplicitUsings>
    <Nullable>enable</Nullable>
  </PropertyGroup>
</Project>
</code>

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
<code>
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
</code>
</project>

[Next sections will cover OOP, asynchronous programming, etc. Would you like me to continue with any specific section?]

</tutorial>

This is the first section of the tutorial. Would you like me to continue with the next section, such as Object-Oriented Programming or Asynchronous Programming?

<tutorial>

## Section 2: Object-Oriented Programming in C#

### Understanding Classes and Objects

Classes are the fundamental building blocks of OOP in C#. Let's explore key concepts:

<code>
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
</code>

### Inheritance and Polymorphism

<code>
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
</code>

### Interfaces and Implementation

<code>
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
</code>

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

<code>
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
</code>
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

<code>
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
</code>
</exercise>

[Would you like me to continue with the next section on Asynchronous Programming?]

</tutorial>

This section covered the core concepts of OOP in C#. The next section will focus on asynchronous programming, including Task-based operations, async/await, and parallel programming. Would you like me to proceed with that?

<tutorial>

## Section 3: Asynchronous Programming in C#

### Understanding Async/Await Fundamentals

Asynchronous programming is crucial for building responsive applications. Let's explore the key concepts:

<code>
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
</code>

### Task Parallel Library (TPL)

<code>
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
</code>

### Exception Handling in Async Code

<code>
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
</code>

### Progress Reporting and Cancellation

<code>
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
</code>

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

<code>
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
</code>
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

<code>
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
</code>
</exercise>

[Would you like me to continue with the next section on File and Network Programming?]

</tutorial>

This section covered asynchronous programming in C#. The next section will focus on file operations and network programming. Would you like me to proceed with that?

<tutorial>

## Section 4: File and Network Programming

### File Operations

First, let's explore file handling using modern C# features:

<code>
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
</code>

### File System Watcher

<code>
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
</code>

### Network Programming

#### HTTP Client Operations

<code>
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
</code>

#### TCP Client/Server Communication

<code>
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
</code>

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

<code>
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
</code>
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

<code>
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
</code>

### Entity Configuration and Relationships

<code>
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
    public int OrderId { get; set; }
    public int ProductId { get; set; }
    public int Quantity { get; set; }
    public Order Order { get; set; }
    public Product Product { get; set; }
}

// Entity Configurations
public class CustomerConfiguration : IEntityTypeConfiguration<Customer>
{
    public void Configure(EntityTypeBuilder<Customer> builder)
    {
        builder.HasKey(c => c.Id);
        
        builder.Property(c => c.Name)
               .IsRequired()
               .HasMaxLength(100);
               
        builder.Property(c => c.Email)
               .IsRequired()
               .HasMaxLength(150);
               
        builder.HasIndex(c => c.Email)
               .IsUnique();
               
        builder.HasMany(c => c.Orders)
               .WithOne(o => o.Customer)
               .HasForeignKey(o => o.CustomerId)
               .OnDelete(DeleteBehavior.Cascade);
    }
}
</code>

### Repository Pattern Implementation

<code>
public interface IRepository<T> where T : class
{
    Task<T> GetByIdAsync(int id);
    Task<IEnumerable<T>> GetAllAsync();
    Task<T> AddAsync(T entity);
    Task UpdateAsync(T entity);
    Task DeleteAsync(T entity);
}

public class Repository<T> : IRepository<T> where T : class
{
    protected readonly ApplicationDbContext _context;
    protected readonly DbSet<T> _dbSet;

    public Repository(ApplicationDbContext context)
    {
        _context = context;
        _dbSet = context.Set<T>();
    }

    public virtual async Task<T> GetByIdAsync(int id)
    {
        return await _dbSet.FindAsync(id);
    }

    public virtual async Task<IEnumerable<T>> GetAllAsync()
    {
        return await _dbSet.ToListAsync();
    }

    public virtual async Task<T> AddAsync(T entity)
    {
        await _dbSet.AddAsync(entity);
        await _context.SaveChangesAsync();
        return entity;
    }

    public virtual async Task UpdateAsync(T entity)
    {
        _dbSet.Update(entity);
        await _context.SaveChangesAsync();
    }

    public virtual async Task DeleteAsync(T entity)
    {
        _dbSet.Remove(entity);
        await _context.SaveChangesAsync();
    }
}

// Specific repository implementation
public interface ICustomerRepository : IRepository<Customer>
{
    Task<Customer> GetCustomerWithOrdersAsync(int id);
    Task<IEnumerable<Customer>> GetCustomersByOrderCountAsync(int minOrders);
}

public class CustomerRepository : Repository<Customer>, ICustomerRepository
{
    public CustomerRepository(ApplicationDbContext context) : base(context)
    {
    }

    public async Task<Customer> GetCustomerWithOrdersAsync(int id)
    {
        return await _dbSet
            .Include(c => c.Orders)
            .ThenInclude(o => o.Items)
            .FirstOrDefaultAsync(c => c.Id == id);
    }

    public async Task<IEnumerable<Customer>> GetCustomersByOrderCountAsync(int minOrders)
    {
        return await _dbSet
            .Include(c => c.Orders)
            .Where(c => c.Orders.Count >= minOrders)
            .ToListAsync();
    }
}
</code>

### Unit of Work Pattern

<code>
public interface IUnitOfWork : IDisposable
{
    ICustomerRepository Customers { get; }
    IRepository<Order> Orders { get; }
    IRepository<Product> Products { get; }
    Task<int> SaveChangesAsync();
}

public class UnitOfWork : IUnitOfWork
{
    private readonly ApplicationDbContext _context;
    private ICustomerRepository _customers;
    private IRepository<Order> _orders;
    private IRepository<Product> _products;

    public UnitOfWork(ApplicationDbContext context)
    {
        _context = context;
    }

    public ICustomerRepository Customers => 
        _customers ??= new CustomerRepository(_context);

    public IRepository<Order> Orders => 
        _orders ??= new Repository<Order>(_context);

    public IRepository<Product> Products => 
        _products ??= new Repository<Product>(_context);

    public async Task<int> SaveChangesAsync()
    {
        return await _context.SaveChangesAsync();
    }

    public void Dispose()
    {
        _context.Dispose();
    }
}
</code>

### Query Examples and Performance Optimization

<code>
public class QueryExamples
{
    private readonly IUnitOfWork _unitOfWork;

    public QueryExamples(IUnitOfWork unitOfWork)
    {
        _unitOfWork = unitOfWork;
    }

    // Efficient querying with pagination
    public async Task<(List<Customer> Customers, int TotalCount)> 
        GetCustomersPagedAsync(int pageNumber, int pageSize)
    {
        var query = _context.Customers
            .AsNoTracking()  // For read-only scenarios
            .OrderBy(c => c.Name);

        var totalCount = await query.CountAsync();
        
        var customers = await query
            .Skip((pageNumber - 1) * pageSize)
            .Take(pageSize)
            .ToListAsync();

        return (customers, totalCount);
    }

    // Complex query with multiple includes
    public async Task<List<Order>> GetDetailedOrdersAsync()
    {
        return await _context.Orders
            .Include(o => o.Customer)
            .Include(o => o.Items)
                .ThenInclude(i => i.Product)
            .Where(o => o.OrderDate >= DateTime.Today.AddDays(-30))
            .OrderByDescending(o => o.OrderDate)
            .ToListAsync();
    }

    // Using compiled queries for better performance
    private static readonly Func<ApplicationDbContext, int, Task<Customer>> 
        GetCustomerById = EF.CompileAsyncQuery(
            (ApplicationDbContext context, int id) =>
                context.Customers
                    .Include(c => c.Orders)
                    .FirstOrDefault(c => c.Id == id));
}
</code>

<exercise>
Exercise 5.1: Entity Framework Setup
1. Create a new database context with three related entities
2. Configure entity relationships using Fluent API
3. Generate and apply migrations
4. Implement seed data
</exercise>

<exercise>
Exercise 5.2: Repository Implementation
1. Create a generic repository interface and implementation
2. Implement a specific repository with custom queries
3. Add pagination and sorting capabilities
4. Implement proper error handling
</exercise>

<project>
Mini-Project 5: Blog Engine with EF Core

Create a simple blog engine with the following features:
- Posts, Categories, and Comments
- User authentication
- Tag system
- Full CRUD operations
- Search functionality

Sample Implementation:

<code>
// Entities
public class Post
{
    public int Id { get; set; }
    public string Title { get; set; }
    public string Content { get; set; }
    public DateTime PublishedDate { get; set; }
    public string AuthorId { get; set; }
    public List<Comment> Comments { get; set; } = new();
    public List<Category> Categories { get; set; } = new();
    public List<Tag> Tags { get; set; } = new();
}

public class BlogService
{
    private readonly IUnitOfWork _unitOfWork;

    public BlogService(IUnitOfWork unitOfWork)
    {
        _unitOfWork = unitOfWork;
    }

    public async Task<Post> CreatePostAsync(Post post)
    {
        // Validate post
        if (string.IsNullOrEmpty(post.Title))
            throw new ValidationException("Title is required");

        await _unitOfWork.Posts.AddAsync(post);
        await _unitOfWork.SaveChangesAsync();
        return post;
    }

    public async Task<IEnumerable<Post>> SearchPostsAsync(
        string searchTerm,
        int page = 1,
        int pageSize = 10)
    {
        var query = _context.Posts
            .AsNoTracking()
            .Where(p => p.Title.Contains(searchTerm) || 
                       p.Content.Contains(searchTerm))
            .Include(p => p.Categories)
            .Include(p => p.Tags)
            .OrderByDescending(p => p.PublishedDate);

        return await query
            .Skip((page - 1) * pageSize)
            .Take(pageSize)
            .ToListAsync();
    }
}
</code>
</project>

### Best Practices and Common Pitfalls

1. Best Practices:
   - Use async/await consistently
   - Implement proper unit of work pattern
   - Use migration for database changes
   - Implement proper validation
   - Use appropriate indexes
   - Handle concurrency properly

2. Common Pitfalls:
   - N+1 query problems
   - Loading too much data
   - Not using appropriate tracking behavior
   - Missing indexes
   - Poor query performance
   - Memory leaks in long-running applications

[Would you like me to continue with the next section on Delegates and Events?]

</tutorial>

This section covered Entity Framework Core and database operations. The next section will focus on delegates and events in C#. Would you like me to proceed with that?

<tutorial>

## Section 6: Delegates and Events

### Understanding Delegates

Delegates are type-safe function pointers in C#. Let's explore their implementation and usage:

<code>
// Basic delegate declaration
public delegate void MessageHandler(string message);
public delegate TResult Transformer<T, TResult>(T input);

public class DelegateBasics
{
    // Method that accepts a delegate
    public void ProcessWithDelegate(string input, MessageHandler handler)
    {
        handler($"Processing: {input}");
    }

    // Generic delegate usage
    public List<TResult> TransformList<T, TResult>(
        IEnumerable<T> items, 
        Transformer<T, TResult> transformer)
    {
        return items.Select(item => transformer(item)).ToList();
    }

    // Usage example
    public void DemoDelegate()
    {
        MessageHandler logger = Console.WriteLine;
        ProcessWithDelegate("Test", logger);

        // Using lambda expression
        ProcessWithDelegate("Test", msg => 
            Console.WriteLine($"Lambda: {msg}"));

        // Generic transformer example
        var numbers = new[] { 1, 2, 3, 4, 5 };
        var doubled = TransformList(numbers, x => x * 2);
    }
}
</code>

### Multicast Delegates

<code>
public class MulticastDelegateExample
{
    public delegate void ProcessOperation();

    private ProcessOperation _operations;

    public void AddOperation(ProcessOperation operation)
    {
        _operations += operation;
    }

    public void RemoveOperation(ProcessOperation operation)
    {
        _operations -= operation;
    }

    public void ExecuteOperations()
    {
        _operations?.Invoke();
    }

    // Usage example
    public void DemoMulticast()
    {
        AddOperation(() => Console.WriteLine("Operation 1"));
        AddOperation(() => Console.WriteLine("Operation 2"));
        AddOperation(() => Console.WriteLine("Operation 3"));

        ExecuteOperations();
    }
}
</code>

### Events and Event Handlers

<code>
public class EventArgs<T> : EventArgs
{
    public T Data { get; }
    public DateTime Timestamp { get; }

    public EventArgs(T data)
    {
        Data = data;
        Timestamp = DateTime.UtcNow;
    }
}

public class DataProcessor<T>
{
    // Event declaration
    public event EventHandler<EventArgs<T>> DataReceived;
    public event EventHandler<EventArgs<Exception>> ErrorOccurred;

    protected virtual void OnDataReceived(T data)
    {
        DataReceived?.Invoke(this, new EventArgs<T>(data));
    }

    protected virtual void OnErrorOccurred(Exception ex)
    {
        ErrorOccurred?.Invoke(this, new EventArgs<Exception>(ex));
    }

    public void ProcessData(T data)
    {
        try
        {
            // Process the data
            Console.WriteLine($"Processing data: {data}");
            OnDataReceived(data);
        }
        catch (Exception ex)
        {
            OnErrorOccurred(ex);
        }
    }
}

// Custom EventArgs example
public class OrderEventArgs : EventArgs
{
    public int OrderId { get; }
    public decimal Amount { get; }
    public DateTime OrderDate { get; }

    public OrderEventArgs(int orderId, decimal amount)
    {
        OrderId = orderId;
        Amount = amount;
        OrderDate = DateTime.UtcNow;
    }
}
</code>

### Action, Func, and Predicate Delegates

<code>
public class ModernDelegates
{
    // Action delegate (void return type)
    public void ProcessWithAction(string input, Action<string> action)
    {
        action(input);
    }

    // Func delegate (with return value)
    public TResult ProcessWithFunc<T, TResult>(T input, Func<T, TResult> func)
    {
        return func(input);
    }

    // Predicate delegate (returns bool)
    public List<T> FilterItems<T>(IEnumerable<T> items, Predicate<T> predicate)
    {
        return items.Where(item => predicate(item)).ToList();
    }

    // Usage example
    public void DemoDelegates()
    {
        // Action usage
        ProcessWithAction("Hello", message => 
            Console.WriteLine($"Action: {message}"));

        // Func usage
        var result = ProcessWithFunc(5, x => x * x);

        // Predicate usage
        var numbers = Enumerable.Range(1, 10);
        var evenNumbers = FilterItems(numbers, x => x % 2 == 0);
    }
}
</code>

### Event Pattern Implementation

<code>
public class OrderProcessor
{
    public event EventHandler<OrderEventArgs> OrderProcessed;
    public event EventHandler<OrderEventArgs> LargeOrderDetected;

    protected virtual void OnOrderProcessed(OrderEventArgs e)
    {
        OrderProcessed?.Invoke(this, e);
    }

    protected virtual void OnLargeOrderDetected(OrderEventArgs e)
    {
        LargeOrderDetected?.Invoke(this, e);
    }

    public void ProcessOrder(int orderId, decimal amount)
    {
        // Process the order
        Console.WriteLine($"Processing order {orderId}");

        // Raise OrderProcessed event
        var args = new OrderEventArgs(orderId, amount);
        OnOrderProcessed(args);

        // Check for large orders
        if (amount > 1000)
        {
            OnLargeOrderDetected(args);
        }
    }
}

// Usage example
public class OrderSystem
{
    private readonly OrderProcessor _processor;

    public OrderSystem()
    {
        _processor = new OrderProcessor();
        
        // Subscribe to events
        _processor.OrderProcessed += HandleOrderProcessed;
        _processor.LargeOrderDetected += HandleLargeOrder;
    }

    private void HandleOrderProcessed(object sender, OrderEventArgs e)
    {
        Console.WriteLine($"Order {e.OrderId} processed at {e.OrderDate}");
    }

    private void HandleLargeOrder(object sender, OrderEventArgs e)
    {
        Console.WriteLine($"Large order detected: {e.OrderId}, Amount: {e.Amount}");
    }
}
</code>

<exercise>
Exercise 6.1: Delegate Implementation
1. Create a calculator class that uses delegates for operations
2. Implement addition, subtraction, multiplication, and division
3. Add error handling for division by zero
4. Create a method that accepts an operation delegate and performs calculations
</exercise>

<exercise>
Exercise 6.2: Event System
1. Create a simple logging system using events
2. Implement different log levels (Info, Warning, Error)
3. Create multiple subscribers for the logging events
4. Add the ability to filter logs by level
</exercise>

<project>
Mini-Project 6: Task Scheduler System

Create a task scheduling system with events and delegates:

<code>
public class Task
{
    public int Id { get; }
    public string Name { get; }
    public DateTime ScheduledTime { get; }
    public Action Operation { get; }

    public Task(int id, string name, DateTime scheduledTime, Action operation)
    {
        Id = id;
        Name = name;
        ScheduledTime = scheduledTime;
        Operation = operation;
    }
}

public class TaskScheduler
{
    private readonly List<Task> _tasks = new();
    private readonly Timer _timer;

    public event EventHandler<TaskEventArgs> TaskStarted;
    public event EventHandler<TaskEventArgs> TaskCompleted;
    public event EventHandler<TaskEventArgs> TaskFailed;

    public TaskScheduler()
    {
        _timer = new Timer(CheckTasks, null, 0, 1000);
    }

    public void ScheduleTask(Task task)
    {
        _tasks.Add(task);
    }

    private void CheckTasks(object state)
    {
        var now = DateTime.Now;
        var tasksToRun = _tasks
            .Where(t => t.ScheduledTime <= now)
            .ToList();

        foreach (var task in tasksToRun)
        {
            ExecuteTask(task);
            _tasks.Remove(task);
        }
    }

    private void ExecuteTask(Task task)
    {
        var args = new TaskEventArgs(task);
        try
        {
            OnTaskStarted(args);
            task.Operation();
            OnTaskCompleted(args);
        }
        catch (Exception ex)
        {
            args.Error = ex;
            OnTaskFailed(args);
        }
    }

    protected virtual void OnTaskStarted(TaskEventArgs e)
    {
        TaskStarted?.Invoke(this, e);
    }

    protected virtual void OnTaskCompleted(TaskEventArgs e)
    {
        TaskCompleted?.Invoke(this, e);
    }

    protected virtual void OnTaskFailed(TaskEventArgs e)
    {
        TaskFailed?.Invoke(this, e);
    }
}

public class TaskEventArgs : EventArgs
{
    public Task Task { get; }
    public Exception Error { get; set; }
    public DateTime Timestamp { get; }

    public TaskEventArgs(Task task)
    {
        Task = task;
        Timestamp = DateTime.Now;
    }
}

// Usage example
public class TaskSchedulerDemo
{
    public void Demo()
    {
        var scheduler = new TaskScheduler();

        scheduler.TaskStarted += (s, e) => 
            Console.WriteLine($"Task {e.Task.Name} started at {e.Timestamp}");
        
        scheduler.TaskCompleted += (s, e) => 
            Console.WriteLine($"Task {e.Task.Name} completed at {e.Timestamp}");
        
        scheduler.TaskFailed += (s, e) => 
            Console.WriteLine($"Task {e.Task.Name} failed: {e.Error.Message}");

        scheduler.ScheduleTask(new Task(
            1, 
            "Sample Task", 
            DateTime.Now.AddSeconds(5), 
            () => Console.WriteLine("Executing task...")));
    }
}
</code>
</project>

### Best Practices and Common Pitfalls

1. Best Practices:
   - Always check for null before invoking events
   - Use EventHandler<T> for custom events
   - Implement proper exception handling
   - Follow the standard event pattern
   - Use weak event patterns when appropriate

2. Common Pitfalls:
   - Memory leaks from unsubscribed events
   - Thread safety issues with events
   - Expensive operations in event handlers
   - Not handling exceptions in event handlers
   - Circular event references

[Would you like me to continue with the next section on Generics and Collections?]

</tutorial>

This section covered delegates and events in C#. The next section will focus on generics and collections. Would you like me to proceed with that?

<tutorial>

## Section 7: Generics and Collections

### Generic Types and Methods

<code>
public class GenericContainer<T>
{
    private T _value;

    public T Value
    {
        get => _value;
        set => _value = value;
    }

    // Generic method with constraints
    public bool Compare<TCompare>(TCompare other) 
        where TCompare : IComparable<T>
    {
        return other.CompareTo(_value) == 0;
    }
}

// Generic constraints examples
public class DataProcessor<T> where T : class, IComparable<T>, new()
{
    public T Process(T input)
    {
        if (input.CompareTo(new T()) == 0)
        {
            return new T();
        }
        return input;
    }
}

// Multiple type parameters
public class KeyValuePair<TKey, TValue>
    where TKey : notnull
    where TValue : class
{
    public TKey Key { get; set; }
    public TValue Value { get; set; }

    public KeyValuePair(TKey key, TValue value)
    {
        Key = key;
        Value = value;
    }
}
</code>

### Generic Collections

<code>
public class CollectionExamples
{
    // List<T> examples
    public void ListOperations()
    {
        var numbers = new List<int> { 1, 2, 3, 4, 5 };
        
        numbers.Add(6);
        numbers.AddRange(new[] { 7, 8, 9 });
        
        numbers.RemoveAll(x => x % 2 == 0);
        
        var evenNumbers = numbers.Where(x => x % 2 == 0).ToList();
        
        numbers.Sort();
        numbers.Reverse();
    }

    // Dictionary<TKey, TValue> examples
    public void DictionaryOperations()
    {
        var userAges = new Dictionary<string, int>();
        
        userAges.Add("John", 25);
        userAges["Jane"] = 30;

        if (userAges.TryGetValue("John", out int age))
        {
            Console.WriteLine($"John's age: {age}");
        }

        foreach (var kvp in userAges)
        {
            Console.WriteLine($"{kvp.Key} is {kvp.Value} years old");
        }
    }

    // HashSet<T> examples
    public void HashSetOperations()
    {
        var set1 = new HashSet<int> { 1, 2, 3, 4, 5 };
        var set2 = new HashSet<int> { 4, 5, 6, 7, 8 };

        set1.UnionWith(set2);
        set1.IntersectWith(set2);
        set1.ExceptWith(set2);
        
        var isSubset = set1.IsSubsetOf(set2);
    }
}
</code>

### Custom Collections

<code>
public class CircularBuffer<T> : IEnumerable<T>
{
    private readonly T[] _buffer;
    private int _start;
    private int _end;
    private int _count;

    public CircularBuffer(int capacity)
    {
        _buffer = new T[capacity];
    }

    public void Add(T item)
    {
        _buffer[_end] = item;
        _end = (_end + 1) % _buffer.Length;
        
        if (_count == _buffer.Length)
        {
            _start = (_start + 1) % _buffer.Length;
        }
        else
        {
            _count++;
        }
    }

    public IEnumerator<T> GetEnumerator()
    {
        for (int i = 0; i < _count; i++)
        {
            yield return _buffer[(_start + i) % _buffer.Length];
        }
    }

    IEnumerator IEnumerable.GetEnumerator()
    {
        return GetEnumerator();
    }
}

// Custom collection with index validation
public class ValidatedList<T> : IList<T>
{
    private readonly List<T> _items = new();
    private readonly Predicate<T> _validator;

    public ValidatedList(Predicate<T> validator)
    {
        _validator = validator;
    }

    public void Add(T item)
    {
        if (!_validator(item))
        {
            throw new ArgumentException("Item failed validation");
        }
        _items.Add(item);
    }

    // Implement other IList<T> members...
}
</code>

### Thread-Safe Collections

<code>
public class ThreadSafeCollectionExamples
{
    // ConcurrentDictionary
    private readonly ConcurrentDictionary<string, int> _concurrentDict = 
        new ConcurrentDictionary<string, int>();

    public void ConcurrentDictionaryOperations()
    {
        _concurrentDict.AddOrUpdate(
            "counter", 
            1, 
            (key, oldValue) => oldValue + 1);

        _concurrentDict.GetOrAdd("counter", 0);
    }

    // ConcurrentQueue
    private readonly ConcurrentQueue<string> _messageQueue = 
        new ConcurrentQueue<string>();

    public void ConcurrentQueueOperations()
    {
        _messageQueue.Enqueue("Message 1");
        
        if (_messageQueue.TryDequeue(out string message))
        {
            Console.WriteLine(message);
        }

        if (_messageQueue.TryPeek(out string peekedMessage))
        {
            Console.WriteLine($"Next message: {peekedMessage}");
        }
    }

    // ConcurrentBag
    private readonly ConcurrentBag<int> _numbers = new ConcurrentBag<int>();

    public void ConcurrentBagOperations()
    {
        Parallel.For(0, 1000, i => _numbers.Add(i));

        while (_numbers.TryTake(out int number))
        {
            Console.WriteLine(number);
        }
    }
}
</code>

### LINQ with Generic Collections

<code>
public class LinqExamples
{
    private readonly List<Person> _people = new();

    public IEnumerable<Person> ComplexQuery()
    {
        return _people
            .Where(p => p.Age >= 18)
            .OrderBy(p => p.LastName)
            .ThenBy(p => p.FirstName)
            .Select(p => new Person
            {
                FirstName = p.FirstName,
                LastName = p.LastName,
                Age = p.Age
            });
    }

    public IEnumerable<IGrouping<string, Person>> GroupedQuery()
    {
        return _people
            .GroupBy(p => p.LastName)
            .Where(g => g.Count() > 1)
            .OrderByDescending(g => g.Count());
    }

    public void AggregateOperations()
    {
        var averageAge = _people.Average(p => p.Age);
        var totalAge = _people.Sum(p => p.Age);
        var oldestPerson = _people.MaxBy(p => p.Age);
        
        var statistics = _people
            .GroupBy(p => p.LastName)
            .Select(g => new
            {
                LastName = g.Key,
                Count = g.Count(),
                AverageAge = g.Average(p => p.Age)
            });
    }
}
</code>

<exercise>
Exercise 7.1: Generic Implementation
1. Create a generic Stack<T> implementation
2. Add Push, Pop, and Peek methods
3. Implement proper exception handling
4. Add a method to check if an item exists in the stack
</exercise>

<exercise>
Exercise 7.2: Collection Operations
1. Create a method that merges two sorted lists
2. Implement a custom comparer for complex objects
3. Create a method to remove duplicates from a collection
4. Implement a custom collection that maintains items in sorted order
</exercise>

<project>
Mini-Project 7: Cache System

Create a generic cache system with the following features:

<code>
public class CacheItem<T>
{
    public T Value { get; }
    public DateTime ExpirationTime { get; }
    public bool IsExpired => DateTime.UtcNow >= ExpirationTime;

    public CacheItem(T value, TimeSpan timeToLive)
    {
        Value = value;
        ExpirationTime = DateTime.UtcNow.Add(timeToLive);
    }
}

public class Cache<TKey, TValue> where TKey : notnull
{
    private readonly ConcurrentDictionary<TKey, CacheItem<TValue>> _cache = 
        new ConcurrentDictionary<TKey, CacheItem<TValue>>();
    private readonly Timer _cleanupTimer;

    public Cache(TimeSpan cleanupInterval)
    {
        _cleanupTimer = new Timer(CleanupExpiredItems, null, 
            cleanupInterval, cleanupInterval);
    }

    public void Add(TKey key, TValue value, TimeSpan timeToLive)
    {
        var cacheItem = new CacheItem<TValue>(value, timeToLive);
        _cache.AddOrUpdate(key, cacheItem, (_, _) => cacheItem);
    }

    public bool TryGet(TKey key, out TValue value)
    {
        value = default;

        if (_cache.TryGetValue(key, out var cacheItem) && !cacheItem.IsExpired)
        {
            value = cacheItem.Value;
            return true;
        }

        _cache.TryRemove(key, out _);
        return false;
    }

    private void CleanupExpiredItems(object state)
    {
        var expiredKeys = _cache
            .Where(kvp => kvp.Value.IsExpired)
            .Select(kvp => kvp.Key)
            .ToList();

        foreach (var key in expiredKeys)
        {
            _cache.TryRemove(key, out _);
        }
    }

    public void Clear()
    {
        _cache.Clear();
    }
}

// Usage example
public class CacheDemo
{
    public async Task DemoCacheOperations()
    {
        var cache = new Cache<string, object>(TimeSpan.FromMinutes(5));

        // Add items to cache
        cache.Add("key1", "value1", TimeSpan.FromMinutes(1));
        cache.Add("key2", new { id = 1, name = "test" }, 
            TimeSpan.FromMinutes(2));

        // Retrieve items
        if (cache.TryGet("key1", out var value1))
        {
            Console.WriteLine($"Found value: {value1}");
        }

        // Wait for expiration
        await Task.Delay(TimeSpan.FromMinutes(1));

        // Try to get expired item
        if (!cache.TryGet("key1", out _))
        {
            Console.WriteLine("Item expired");
        }
    }
}
</code>
</project>

### Best Practices and Common Pitfalls

1. Best Practices:
   - Use the most specific collection interface possible
   - Consider thread safety requirements
   - Use generic constraints appropriately
   - Implement custom collections when needed
   - Use LINQ for complex queries
   - Consider memory usage with large collections

2. Common Pitfalls:
   - Not considering thread safety
   - Inappropriate collection choice
   - Memory leaks in custom collections
   - Poor performance with large datasets
   - Incorrect generic constraints
   - Overusing LINQ for simple operations

[Would you like me to continue with the next section on Exception Handling and Reflection?]

</tutorial>

This section covered generics and collections in C#. The next section will focus on exception handling and reflection. Would you like me to proceed with that?

<tutorial>

## Section 8: Exception Handling and Reflection

### Advanced Exception Handling

<code>
public class ExceptionHandlingExamples
{
    // Custom Exception
    public class BusinessRuleException : Exception
    {
        public string RuleId { get; }

        public BusinessRuleException(string message, string ruleId) 
            : base(message)
        {
            RuleId = ruleId;
        }

        public BusinessRuleException(string message, string ruleId, Exception inner) 
            : base(message, inner)
        {
            RuleId = ruleId;
        }
    }

    // Exception filters and when clause
    public async Task ProcessDataAsync()
    {
        try
        {
            await LoadDataAsync();
        }
        catch (HttpRequestException ex) when (ex.StatusCode == HttpStatusCode.NotFound)
        {
            throw new BusinessRuleException("Data not found", "DATA_001", ex);
        }
        catch (Exception ex) when (IsTransientException(ex))
        {
            await RetryOperation();
        }
    }

    // Exception handling with logging
    public async Task<T> ExecuteWithRetryAsync<T>(
        Func<Task<T>> operation,
        int maxRetries = 3)
    {
        for (int i = 0; i <= maxRetries; i++)
        {
            try
            {
                return await operation();
            }
            catch (Exception ex) when (i < maxRetries && IsTransientException(ex))
            {
                await Task.Delay(TimeSpan.FromSeconds(Math.Pow(2, i)));
                Logger.LogWarning($"Retry attempt {i + 1} after error: {ex.Message}");
            }
        }
        throw new OperationCanceledException("Max retries exceeded");
    }
}
</code>

### Reflection Basics

<code>
public class ReflectionExamples
{
    // Type inspection
    public void InspectType<T>()
    {
        Type type = typeof(T);
        
        Console.WriteLine($"Type: {type.Name}");
        Console.WriteLine($"Assembly: {type.Assembly.FullName}");
        Console.WriteLine($"Is class: {type.IsClass}");
        Console.WriteLine($"Is interface: {type.IsInterface}");
        
        // Get properties
        foreach (var prop in type.GetProperties())
        {
            Console.WriteLine($"Property: {prop.Name} ({prop.PropertyType.Name})");
        }
        
        // Get methods
        foreach (var method in type.GetMethods())
        {
            Console.WriteLine($"Method: {method.Name}");
        }
    }

    // Dynamic object creation
    public T CreateInstance<T>(params object[] parameters)
    {
        Type type = typeof(T);
        return (T)Activator.CreateInstance(type, parameters);
    }

    // Method invocation using reflection
    public object InvokeMethod(object instance, string methodName, params object[] parameters)
    {
        Type type = instance.GetType();
        MethodInfo method = type.GetMethod(methodName);
        
        if (method == null)
            throw new ArgumentException($"Method {methodName} not found");
            
        return method.Invoke(instance, parameters);
    }
}
</code>

### Attribute-based Programming

<code>
// Custom attribute
[AttributeUsage(AttributeTargets.Property | AttributeTargets.Field)]
public class ValidateAttribute : Attribute
{
    public string RegexPattern { get; }
    public string ErrorMessage { get; }

    public ValidateAttribute(string regexPattern, string errorMessage)
    {
        RegexPattern = regexPattern;
        ErrorMessage = errorMessage;
    }
}

// Validator using reflection
public class Validator
{
    public IEnumerable<ValidationError> Validate(object obj)
    {
        var errors = new List<ValidationError>();
        var type = obj.GetType();

        foreach (var prop in type.GetProperties())
        {
            var validateAttr = prop.GetCustomAttribute<ValidateAttribute>();
            if (validateAttr != null)
            {
                var value = prop.GetValue(obj)?.ToString();
                if (value != null && !Regex.IsMatch(value, validateAttr.RegexPattern))
                {
                    errors.Add(new ValidationError
                    {
                        PropertyName = prop.Name,
                        ErrorMessage = validateAttr.ErrorMessage
                    });
                }
            }
        }

        return errors;
    }
}

// Example usage
public class User
{
    [Validate(@"^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$", 
        "Invalid email format")]
    public string Email { get; set; }

    [Validate(@"^(?=.*[A-Za-z])(?=.*\d)[A-Za-z\d]{8,}$", 
        "Password must be at least 8 characters and contain letters and numbers")]
    public string Password { get; set; }
}
</code>

### Dynamic Type Loading and Assembly Manipulation

<code>
public class AssemblyLoader
{
    public Assembly LoadAssembly(string path)
    {
        try
        {
            return Assembly.LoadFrom(path);
        }
        catch (BadImageFormatException ex)
        {
            throw new Exception("Invalid assembly format", ex);
        }
    }

    public IEnumerable<Type> GetTypesImplementingInterface<TInterface>(Assembly assembly)
    {
        return assembly.GetTypes()
            .Where(t => typeof(TInterface).IsAssignableFrom(t) && !t.IsInterface);
    }

    public object CreateInstanceFromType(Type type)
    {
        try
        {
            return Activator.CreateInstance(type);
        }
        catch (Exception ex)
        {
            throw new Exception($"Failed to create instance of {type.Name}", ex);
        }
    }
}
</code>

<exercise>
Exercise 8.1: Custom Exception Handler
1. Create a custom exception class for database operations
2. Implement exception filtering based on error codes
3. Add proper logging and retry logic
4. Create a global exception handler
</exercise>

<exercise>
Exercise 8.2: Reflection-based Mapper
1. Create a generic object mapper using reflection
2. Implement property mapping with type conversion
3. Add support for nested objects
4. Handle collection properties
</exercise>

<project>
Mini-Project 8: Plugin System

Create a plugin system that dynamically loads and manages plugins:

<code>
public interface IPlugin
{
    string Name { get; }
    string Version { get; }
    void Initialize();
    void Execute();
}

[AttributeUsage(AttributeTargets.Class)]
public class PluginAttribute : Attribute
{
    public string Name { get; }
    public string Description { get; }

    public PluginAttribute(string name, string description)
    {
        Name = name;
        Description = description;
    }
}

public class PluginManager
{
    private readonly Dictionary<string, IPlugin> _plugins = new();
    private readonly string _pluginDirectory;

    public PluginManager(string pluginDirectory)
    {
        _pluginDirectory = pluginDirectory;
    }

    public void LoadPlugins()
    {
        foreach (var file in Directory.GetFiles(_pluginDirectory, "*.dll"))
        {
            try
            {
                var assembly = Assembly.LoadFrom(file);
                var pluginTypes = assembly.GetTypes()
                    .Where(t => typeof(IPlugin).IsAssignableFrom(t) && !t.IsInterface);

                foreach (var type in pluginTypes)
                {
                    var plugin = (IPlugin)Activator.CreateInstance(type);
                    var attr = type.GetCustomAttribute<PluginAttribute>();
                    
                    if (attr != null)
                    {
                        _plugins[attr.Name] = plugin;
                        plugin.Initialize();
                    }
                }
            }
            catch (Exception ex)
            {
                Logger.LogError($"Failed to load plugin from {file}: {ex.Message}");
            }
        }
    }

    public void ExecutePlugin(string name)
    {
        if (_plugins.TryGetValue(name, out var plugin))
        {
            try
            {
                plugin.Execute();
            }
            catch (Exception ex)
            {
                Logger.LogError($"Plugin {name} execution failed: {ex.Message}");
                throw;
            }
        }
        else
        {
            throw new PluginNotFoundException(name);
        }
    }

    public IEnumerable<PluginInfo> GetLoadedPlugins()
    {
        return _plugins.Select(p => new PluginInfo
        {
            Name = p.Key,
            Version = p.Value.Version,
            Description = p.Value.GetType()
                .GetCustomAttribute<PluginAttribute>()?.Description
        });
    }
}

// Example Plugin Implementation
[Plugin("DataExporter", "Exports data to various formats")]
public class DataExporterPlugin : IPlugin
{
    public string Name => "DataExporter";
    public string Version => "1.0.0";

    public void Initialize()
    {
        // Initialize resources
    }

    public void Execute()
    {
        // Export data
    }
}

// Usage Example
public class PluginSystemDemo
{
    public async Task RunDemo()
    {
        var pluginManager = new PluginManager(@"C:\Plugins");
        
        try
        {
            pluginManager.LoadPlugins();
            
            foreach (var plugin in pluginManager.GetLoadedPlugins())
            {
                Console.WriteLine($"Loaded: {plugin.Name} v{plugin.Version}");
            }
            
            await Task.Run(() => pluginManager.ExecutePlugin("DataExporter"));
        }
        catch (PluginNotFoundException ex)
        {
            Console.WriteLine($"Plugin not found: {ex.Message}");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }
}
</code>
</project>

### Best Practices and Common Pitfalls

1. Exception Handling Best Practices:
   - Only catch exceptions you can handle
   - Use specific exception types
   - Include meaningful error messages
   - Implement proper logging
   - Consider retry policies for transient failures
   - Maintain the exception stack trace

2. Reflection Best Practices:
   - Cache reflection results
   - Use compiled expressions for performance
   - Implement proper error handling
   - Consider security implications
   - Use reflection only when necessary
   - Test thoroughly with different types

3. Common Pitfalls:
   - Catching all exceptions
   - Swallowing exceptions
   - Excessive use of reflection
   - Not handling security restrictions
   - Performance issues with reflection
   - Memory leaks in dynamic loading

[Would you like me to continue with the next section on Strings and StringBuilder?]

</tutorial>

This section covered exception handling and reflection in C#. The next section will focus on string manipulation and StringBuilder. Would you like me to proceed with that?

<tutorial>

## Section 9: Strings and StringBuilder

### String Manipulation and Operations

<code>
public class StringOperations
{
    // Basic string operations
    public void BasicStringOperations()
    {
        string text = "Hello, World!";
        
        // String methods
        string lower = text.ToLower();
        string upper = text.ToUpper();
        string trimmed = text.Trim();
        string[] split = text.Split(',');
        
        // Substring operations
        string sub = text.Substring(0, 5);
        int index = text.IndexOf("World");
        bool contains = text.Contains("Hello");
        
        // String comparison
        bool equals = text.Equals("hello, world!", 
            StringComparison.OrdinalIgnoreCase);
        
        // String replacement
        string replaced = text.Replace("Hello", "Hi");
    }

    // String formatting
    public void StringFormatting()
    {
        string name = "John";
        int age = 30;
        decimal salary = 50000.50m;

        // Composite formatting
        string format1 = string.Format("Name: {0}, Age: {1}", name, age);

        // String interpolation
        string format2 = $"Name: {name}, Age: {age:D2}";

        // Number formatting
        string format3 = $"Salary: {salary:C2}";
        string format4 = $"Age: {age:D3}";

        // Date formatting
        DateTime now = DateTime.Now;
        string format5 = $"Date: {now:yyyy-MM-dd}";
        string format6 = $"Time: {now:HH:mm:ss}";
    }
}
</code>

### StringBuilder Usage

<code>
public class StringBuilderExamples
{
    // Efficient string concatenation
    public string BuildLargeString(IEnumerable<string> items)
    {
        var sb = new StringBuilder();
        
        foreach (var item in items)
        {
            sb.AppendLine(item);
        }
        
        return sb.ToString();
    }

    // StringBuilder with formatting
    public string CreateFormattedReport(List<ReportItem> items)
    {
        var sb = new StringBuilder();
        
        sb.AppendLine("=== Report ===");
        sb.AppendLine($"Generated: {DateTime.Now:yyyy-MM-dd HH:mm:ss}");
        sb.AppendLine();

        foreach (var item in items)
        {
            sb.AppendFormat("Item: {0}, Value: {1:C2}", 
                item.Name, item.Value)
              .AppendLine();
        }

        sb.AppendLine("=== End Report ===");
        
        return sb.ToString();
    }

    // StringBuilder with conditional logic
    public string BuildConditionalString(Dictionary<string, bool> flags)
    {
        var sb = new StringBuilder();
        
        if (flags.TryGetValue("header", out bool includeHeader) && includeHeader)
        {
            sb.AppendLine("=== Header ===");
        }

        foreach (var flag in flags)
        {
            sb.AppendFormat("{0}: {1}", flag.Key, flag.Value)
              .AppendLine();
        }

        return sb.ToString().TrimEnd();
    }
}
</code>

### String Parsing and Regular Expressions

<code>
public class StringParsingExamples
{
    // Regular expression patterns
    private static readonly Regex EmailRegex = new(
        @"^[^@\s]+@[^@\s]+\.[^@\s]+$",
        RegexOptions.Compiled | RegexOptions.IgnoreCase);

    private static readonly Regex PhoneRegex = new(
        @"^\+?(\d{1,3})?[-. ]?\(?\d{3}\)?[-. ]?\d{3}[-. ]?\d{4}$",
        RegexOptions.Compiled);

    // String validation
    public bool IsValidEmail(string email)
    {
        return !string.IsNullOrWhiteSpace(email) && 
               EmailRegex.IsMatch(email);
    }

    public bool IsValidPhone(string phone)
    {
        return !string.IsNullOrWhiteSpace(phone) && 
               PhoneRegex.IsMatch(phone);
    }

    // String parsing with regex
    public IEnumerable<string> ExtractUrls(string text)
    {
        var urlRegex = new Regex(@"https?:\/\/[\w\-_]+(\.[\w\-_]+)+([\w\-\.,@?^=%&amp;:/~\+#]*[\w\-\@?^=%&amp;/~\+#])?",
            RegexOptions.IgnoreCase);

        return urlRegex.Matches(text)
                      .Select(m => m.Value);
    }

    // Advanced string parsing
    public class ParsedData
    {
        public string Name { get; set; }
        public decimal Amount { get; set; }
        public DateTime Date { get; set; }
    }

    public ParsedData ParseCustomFormat(string input)
    {
        // Example format: "Name: John Doe | Amount: $123.45 | Date: 2023-12-31"
        var pattern = @"Name: (.*?) \| Amount: \$(\d+\.\d{2}) \| Date: (\d{4}-\d{2}-\d{2})";
        var match = Regex.Match(input, pattern);

        if (!match.Success)
            throw new FormatException("Invalid input format");

        return new ParsedData
        {
            Name = match.Groups[1].Value,
            Amount = decimal.Parse(match.Groups[2].Value),
            Date = DateTime.Parse(match.Groups[3].Value)
        };
    }
}
</code>

### String Interning and Memory Management

<code>
public class StringMemoryManagement
{
    // String interning example
    public void DemonstrateStringInterning()
    {
        string str1 = "Hello";
        string str2 = "Hello";
        string str3 = new string(new char[] { 'H', 'e', 'l', 'l', 'o' });
        string str4 = string.Intern(str3);

        Console.WriteLine($"str1 == str2: {ReferenceEquals(str1, str2)}");
        Console.WriteLine($"str1 == str3: {ReferenceEquals(str1, str3)}");
        Console.WriteLine($"str1 == str4: {ReferenceEquals(str1, str4)}");
    }

    // Memory-efficient string handling
    public class StringPool
    {
        private readonly HashSet<string> _pool = new();

        public string GetString(string value)
        {
            if (_pool.TryGetValue(value, out string existing))
            {
                return existing;
            }

            _pool.Add(value);
            return value;
        }
    }
}
</code>

<exercise>
Exercise 9.1: String Parser
1. Create a parser for a custom log format
2. Extract timestamp, log level, and message
3. Handle multiple line entries
4. Implement error handling for malformed entries
</exercise>

<exercise>
Exercise 9.2: StringBuilder Performance
1. Compare string concatenation vs StringBuilder
2. Implement a CSV builder using StringBuilder
3. Create a method to build an HTML document
4. Handle large datasets efficiently
</exercise>

<project>
Mini-Project 9: Text Template Engine

Create a simple template engine that replaces placeholders with values:

<code>
public class TemplateEngine
{
    private readonly Dictionary<string, object> _globalVariables = new();
    private readonly Regex _placeholderRegex = new(
        @"\{\{([^}]+)\}\}", 
        RegexOptions.Compiled);

    public void SetGlobalVariable(string name, object value)
    {
        _globalVariables[name] = value;
    }

    public string Process(string template, 
        Dictionary<string, object> variables = null)
    {
        variables ??= new Dictionary<string, object>();
        var allVariables = new Dictionary<string, object>(_globalVariables);
        
        foreach (var (key, value) in variables)
        {
            allVariables[key] = value;
        }

        var sb = new StringBuilder(template);
        var matches = _placeholderRegex.Matches(template);

        foreach (Match match in matches.Reverse())
        {
            var placeholder = match.Groups[1].Value.Trim();
            var replacement = ProcessPlaceholder(placeholder, allVariables);
            sb.Remove(match.Index, match.Length);
            sb.Insert(match.Index, replacement);
        }

        return sb.ToString();
    }

    private string ProcessPlaceholder(string placeholder, 
        Dictionary<string, object> variables)
    {
        // Handle expressions like "value | uppercase"
        var parts = placeholder.Split('|').Select(p => p.Trim()).ToArray();
        var key = parts[0];

        if (!variables.TryGetValue(key, out var value))
            return string.Empty;

        var result = value?.ToString() ?? string.Empty;

        // Apply filters
        for (int i = 1; i < parts.Length; i++)
        {
            result = ApplyFilter(result, parts[i]);
        }

        return result;
    }

    private string ApplyFilter(string value, string filter)
    {
        return filter.ToLower() switch
        {
            "uppercase" => value.ToUpper(),
            "lowercase" => value.ToLower(),
            "capitalize" => CultureInfo.CurrentCulture
                .TextInfo.ToTitleCase(value.ToLower()),
            "trim" => value.Trim(),
            _ => value
        };
    }
}

// Usage Example
public class TemplateEngineDemo
{
    public void RunDemo()
    {
        var engine = new TemplateEngine();
        
        // Set global variables
        engine.SetGlobalVariable("company", "Acme Corp");
        
        // Template with variables and filters
        var template = @"
            Dear {{name | capitalize}},

            Welcome to {{company}}!
            Your account details:
            Email: {{email | lowercase}}
            Role: {{role | uppercase}}

            Best regards,
            {{company}} Team
        ";

        var variables = new Dictionary<string, object>
        {
            ["name"] = "john doe",
            ["email"] = "John.Doe@Example.com",
            ["role"] = "Administrator"
        };

        string result = engine.Process(template, variables);
        Console.WriteLine(result);
    }
}
</code>
</project>

### Best Practices and Common Pitfalls

1. String Best Practices:
   - Use string interpolation for readability
   - Use StringBuilder for multiple concatenations
   - Use appropriate string comparison methods
   - Cache regular expressions
   - Use string.Empty instead of ""
   - Consider culture-specific operations

2. StringBuilder Best Practices:
   - Set initial capacity when size is known
   - Reuse StringBuilder instances
   - Clear instead of creating new instances
   - Use AppendFormat for complex formatting
   - Consider thread safety when needed

3. Common Pitfalls:
   - String concatenation in loops
   - Unnecessary string allocations
   - Incorrect string comparisons
   - Regular expression performance issues
   - Memory leaks with large strings
   - Not considering culture-specific behavior

[Would you like me to continue with the next section on Dependency Injection and Services?]

</tutorial>

This section covered strings and StringBuilder in C#. The next section will focus on dependency injection and services. Would you like me to proceed with that?

<tutorial>

## Section 10: Dependency Injection and Services

### Understanding Dependency Injection

<code>
// Interface definitions
public interface ILogger
{
    void Log(string message, LogLevel level);
}

public interface IEmailService
{
    Task SendEmailAsync(string to, string subject, string body);
}

public interface IUserService
{
    Task<User> GetUserAsync(int id);
    Task<bool> ValidateUserAsync(string email, string password);
}

// Service implementations
public class FileLogger : ILogger
{
    private readonly string _logPath;

    public FileLogger(string logPath)
    {
        _logPath = logPath;
    }

    public void Log(string message, LogLevel level)
    {
        var logEntry = $"{DateTime.UtcNow:yyyy-MM-dd HH:mm:ss} [{level}] {message}";
        File.AppendAllLines(_logPath, new[] { logEntry });
    }
}

public class EmailService : IEmailService
{
    private readonly SmtpClient _smtpClient;
    private readonly ILogger _logger;

    public EmailService(SmtpClient smtpClient, ILogger logger)
    {
        _smtpClient = smtpClient;
        _logger = logger;
    }

    public async Task SendEmailAsync(string to, string subject, string body)
    {
        try
        {
            var message = new MailMessage
            {
                From = new MailAddress("noreply@example.com"),
                Subject = subject,
                Body = body,
                IsBodyHtml = true
            };
            message.To.Add(to);

            await _smtpClient.SendMailAsync(message);
            _logger.Log($"Email sent to {to}", LogLevel.Information);
        }
        catch (Exception ex)
        {
            _logger.Log($"Failed to send email: {ex.Message}", LogLevel.Error);
            throw;
        }
    }
}
</code>

### Configuring Services

<code>
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Singleton - one instance for the entire application
        services.AddSingleton<ILogger>(sp => 
            new FileLogger("app.log"));

        // Scoped - one instance per scope (e.g., per request)
        services.AddScoped<IUserService, UserService>();

        // Transient - new instance each time
        services.AddTransient<IEmailService, EmailService>();

        // Register configuration
        services.Configure<EmailSettings>(configuration.GetSection("EmailSettings"));

        // Register typed client
        services.AddHttpClient<IApiClient, ApiClient>(client =>
        {
            client.BaseAddress = new Uri("https://api.example.com");
            client.DefaultRequestHeaders.Add("Accept", "application/json");
        });
    }
}

// Configuration classes
public class EmailSettings
{
    public string SmtpServer { get; set; }
    public int Port { get; set; }
    public string Username { get; set; }
    public string Password { get; set; }
}
</code>

### Service Lifetime Management

<code>
public class ServiceLifetimeDemo
{
    private readonly IServiceProvider _serviceProvider;

    public ServiceLifetimeDemo(IServiceProvider serviceProvider)
    {
        _serviceProvider = serviceProvider;
    }

    public async Task DemonstrateLifetimes()
    {
        // Singleton - same instance across all resolutions
        var logger1 = _serviceProvider.GetRequiredService<ILogger>();
        var logger2 = _serviceProvider.GetRequiredService<ILogger>();
        Console.WriteLine($"Singleton same instance: {ReferenceEquals(logger1, logger2)}");

        // Scoped - same instance within a scope
        using (var scope1 = _serviceProvider.CreateScope())
        using (var scope2 = _serviceProvider.CreateScope())
        {
            var service1 = scope1.ServiceProvider.GetRequiredService<IUserService>();
            var service2 = scope1.ServiceProvider.GetRequiredService<IUserService>();
            var service3 = scope2.ServiceProvider.GetRequiredService<IUserService>();

            Console.WriteLine($"Scoped same instance within scope: {ReferenceEquals(service1, service2)}");
            Console.WriteLine($"Scoped different instance across scopes: {!ReferenceEquals(service1, service3)}");
        }

        // Transient - new instance each time
        var email1 = _serviceProvider.GetRequiredService<IEmailService>();
        var email2 = _serviceProvider.GetRequiredService<IEmailService>();
        Console.WriteLine($"Transient different instances: {!ReferenceEquals(email1, email2)}");
    }
}
</code>

### Implementing Factory Pattern with DI

<code>
public interface IServiceFactory<T>
{
    T Create(string type);
}

public class NotificationServiceFactory : IServiceFactory<INotificationService>
{
    private readonly IServiceProvider _serviceProvider;

    public NotificationServiceFactory(IServiceProvider serviceProvider)
    {
        _serviceProvider = serviceProvider;
    }

    public INotificationService Create(string type)
    {
        return type.ToLower() switch
        {
            "email" => _serviceProvider.GetRequiredService<EmailNotificationService>(),
            "sms" => _serviceProvider.GetRequiredService<SmsNotificationService>(),
            "push" => _serviceProvider.GetRequiredService<PushNotificationService>(),
            _ => throw new ArgumentException($"Unknown notification type: {type}")
        };
    }
}

// Register factory
services.AddSingleton<IServiceFactory<INotificationService>, NotificationServiceFactory>();
</code>

### Decorators and Middleware with DI

<code>
// Decorator pattern
public class CachingUserService : IUserService
{
    private readonly IUserService _innerService;
    private readonly IMemoryCache _cache;

    public CachingUserService(IUserService innerService, IMemoryCache cache)
    {
        _innerService = innerService;
        _cache = cache;
    }

    public async Task<User> GetUserAsync(int id)
    {
        var cacheKey = $"user_{id}";
        
        if (_cache.TryGetValue(cacheKey, out User cachedUser))
            return cachedUser;

        var user = await _innerService.GetUserAsync(id);
        _cache.Set(cacheKey, user, TimeSpan.FromMinutes(10));
        
        return user;
    }
}

// Register decorator
services.AddScoped<IUserService>(sp =>
{
    var innerService = new UserService(/* dependencies */);
    var cache = sp.GetRequiredService<IMemoryCache>();
    return new CachingUserService(innerService, cache);
});
</code>

<exercise>
Exercise 10.1: Service Implementation
1. Create an interface for a caching service
2. Implement memory and file-based cache providers
3. Register services with appropriate lifetimes
4. Add logging and error handling
</exercise>

<exercise>
Exercise 10.2: Decorator Pattern
1. Create a service interface for data access
2. Implement the base service
3. Create decorators for caching and logging
4. Configure the decoration chain using DI
</exercise>

<project>
Mini-Project 10: Task Management System

Create a task management system using DI:

<code>
public interface ITaskRepository
{
    Task<List<TaskItem>> GetAllAsync();
    Task<TaskItem> GetByIdAsync(int id);
    Task<TaskItem> CreateAsync(TaskItem task);
    Task UpdateAsync(TaskItem task);
    Task DeleteAsync(int id);
}

public interface ITaskService
{
    Task<List<TaskItem>> GetUserTasksAsync(int userId);
    Task<TaskItem> AssignTaskAsync(int taskId, int userId);
    Task<TaskItem> CompleteTaskAsync(int taskId);
}

public class TaskService : ITaskService
{
    private readonly ITaskRepository _repository;
    private readonly ILogger _logger;
    private readonly IUserService _userService;
    private readonly INotificationService _notificationService;

    public TaskService(
        ITaskRepository repository,
        ILogger logger,
        IUserService userService,
        INotificationService notificationService)
    {
        _repository = repository;
        _logger = logger;
        _userService = userService;
        _notificationService = notificationService;
    }

    public async Task<List<TaskItem>> GetUserTasksAsync(int userId)
    {
        try
        {
            var user = await _userService.GetUserAsync(userId);
            if (user == null)
                throw new NotFoundException($"User {userId} not found");

            var tasks = await _repository.GetAllAsync();
            return tasks.Where(t => t.AssignedUserId == userId).ToList();
        }
        catch (Exception ex)
        {
            _logger.Log($"Error getting user tasks: {ex.Message}", LogLevel.Error);
            throw;
        }
    }

    public async Task<TaskItem> AssignTaskAsync(int taskId, int userId)
    {
        try
        {
            var task = await _repository.GetByIdAsync(taskId);
            if (task == null)
                throw new NotFoundException($"Task {taskId} not found");

            var user = await _userService.GetUserAsync(userId);
            if (user == null)
                throw new NotFoundException($"User {userId} not found");

            task.AssignedUserId = userId;
            task.Status = TaskStatus.Assigned;
            
            await _repository.UpdateAsync(task);
            
            await _notificationService.SendNotificationAsync(
                userId,
                $"New task assigned: {task.Title}");

            return task;
        }
        catch (Exception ex)
        {
            _logger.Log($"Error assigning task: {ex.Message}", LogLevel.Error);
            throw;
        }
    }

    public async Task<TaskItem> CompleteTaskAsync(int taskId)
    {
        try
        {
            var task = await _repository.GetByIdAsync(taskId);
            if (task == null)
                throw new NotFoundException($"Task {taskId} not found");

            task.Status = TaskStatus.Completed;
            task.CompletedDate = DateTime.UtcNow;
            
            await _repository.UpdateAsync(task);
            
            await _notificationService.SendNotificationAsync(
                task.CreatedByUserId,
                $"Task completed: {task.Title}");

            return task;
        }
        catch (Exception ex)
        {
            _logger.Log($"Error completing task: {ex.Message}", LogLevel.Error);
            throw;
        }
    }
}

// Service registration
public static class ServiceCollectionExtensions
{
    public static IServiceCollection AddTaskManagement(
        this IServiceCollection services,
        IConfiguration configuration)
    {
        services.AddScoped<ITaskRepository, TaskRepository>();
        services.AddScoped<ITaskService, TaskService>();
        
        services.Configure<TaskManagementOptions>(
            configuration.GetSection("TaskManagement"));

        return services;
    }
}
</code>
</project>

### Best Practices and Common Pitfalls

1. Best Practices:
   - Follow Interface Segregation Principle
   - Use appropriate service lifetimes
   - Avoid service locator pattern
   - Configure services at startup
   - Use options pattern for configuration
   - Implement proper disposal of services

2. Common Pitfalls:
   - Circular dependencies
   - Incorrect service lifetimes
   - Service locator anti-pattern
   - Overusing singleton scope
   - Not disposing of services properly
   - Mixing scoped and singleton services incorrectly

[Would you like me to continue with the final section on building the bash shell CLI terminal?]

</tutorial>

This section covered dependency injection and services in C#. The final section will focus on building a bash shell CLI terminal. Would you like me to proceed with that?

<tutorial>

## Section 11: Building a Bash Shell CLI Terminal in C#

### Basic Shell Structure

<code>
public class BashShell
{
    private readonly Dictionary<string, ICommand> _commands;
    private string _currentDirectory;
    private readonly Dictionary<string, string> _environment;

    public BashShell()
    {
        _currentDirectory = Environment.CurrentDirectory;
        _environment = new Dictionary<string, string>();
        _commands = InitializeCommands();
    }

    private Dictionary<string, ICommand> InitializeCommands()
    {
        return new Dictionary<string, ICommand>
        {
            ["pwd"] = new PwdCommand(),
            ["cd"] = new CdCommand(),
            ["ls"] = new LsCommand(),
            ["touch"] = new TouchCommand(),
            ["echo"] = new EchoCommand(),
            ["mkdir"] = new MkdirCommand(),
            ["grep"] = new GrepCommand(),
            ["mv"] = new MoveCommand(),
            ["rmdir"] = new RmdirCommand(),
            ["rm"] = new RemoveCommand(),
            ["locate"] = new LocateCommand(),
            ["less"] = new LessCommand(),
            ["cat"] = new CatCommand(),
            ["curl"] = new CurlCommand()
        };
    }

    public async Task RunAsync()
    {
        while (true)
        {
            Console.Write($"{_currentDirectory}$ ");
            var input = Console.ReadLine();

            if (string.IsNullOrEmpty(input))
                continue;

            if (input.ToLower() == "exit")
                break;

            await ExecuteCommandAsync(input);
        }
    }

    private async Task ExecuteCommandAsync(string input)
    {
        try
        {
            var (command, args) = ParseCommand(input);
            
            if (_commands.TryGetValue(command, out var cmd))
            {
                await cmd.ExecuteAsync(args, new ShellContext
                {
                    CurrentDirectory = _currentDirectory,
                    Environment = _environment
                });
            }
            else
            {
                Console.WriteLine($"Command not found: {command}");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error: {ex.Message}");
        }
    }

    private (string Command, string[] Args) ParseCommand(string input)
    {
        var parts = input.Split(' ', StringSplitOptions.RemoveEmptyEntries);
        return (parts[0].ToLower(), parts.Skip(1).ToArray());
    }
}
</code>

### Command Interface and Context

<code>
public interface ICommand
{
    Task ExecuteAsync(string[] args, ShellContext context);
}

public class ShellContext
{
    public string CurrentDirectory { get; set; }
    public Dictionary<string, string> Environment { get; set; }
}
</code>

### Implementing Basic Commands

<code>
public class PwdCommand : ICommand
{
    public Task ExecuteAsync(string[] args, ShellContext context)
    {
        Console.WriteLine(context.CurrentDirectory);
        return Task.CompletedTask;
    }
}

public class CdCommand : ICommand
{
    public Task ExecuteAsync(string[] args, ShellContext context)
    {
        if (args.Length == 0)
        {
            context.CurrentDirectory = Environment.GetFolderPath(
                Environment.SpecialFolder.UserProfile);
            return Task.CompletedTask;
        }

        string path = args[0];
        if (path == "..")
        {
            var parent = Directory.GetParent(context.CurrentDirectory);
            if (parent != null)
                context.CurrentDirectory = parent.FullName;
        }
        else
        {
            string newPath = Path.GetFullPath(
                Path.Combine(context.CurrentDirectory, path));
                
            if (Directory.Exists(newPath))
                context.CurrentDirectory = newPath;
            else
                throw new DirectoryNotFoundException($"Directory not found: {path}");
        }

        return Task.CompletedTask;
    }
}

public class LsCommand : ICommand
{
    public Task ExecuteAsync(string[] args, ShellContext context)
    {
        var path = args.Length > 0 ? args[0] : context.CurrentDirectory;
        var directory = new DirectoryInfo(path);

        Console.WriteLine("Directories:");
        foreach (var dir in directory.GetDirectories())
        {
            Console.WriteLine($"d {dir.LastWriteTime:yyyy-MM-dd HH:mm} {dir.Name}/");
        }

        Console.WriteLine("\nFiles:");
        foreach (var file in directory.GetFiles())
        {
            Console.WriteLine($"- {file.LastWriteTime:yyyy-MM-dd HH:mm} {file.Name}");
        }

        return Task.CompletedTask;
    }
}
</code>

### File Operation Commands

<code>
public class TouchCommand : ICommand
{
    public Task ExecuteAsync(string[] args, ShellContext context)
    {
        if (args.Length == 0)
            throw new ArgumentException("File name required");

        string filePath = Path.Combine(context.CurrentDirectory, args[0]);
        File.Create(filePath).Dispose();
        
        return Task.CompletedTask;
    }
}

public class MkdirCommand : ICommand
{
    public Task ExecuteAsync(string[] args, ShellContext context)
    {
        if (args.Length == 0)
            throw new ArgumentException("Directory name required");

        string dirPath = Path.Combine(context.CurrentDirectory, args[0]);
        Directory.CreateDirectory(dirPath);
        
        return Task.CompletedTask;
    }
}

public class RemoveCommand : ICommand
{
    public Task ExecuteAsync(string[] args, ShellContext context)
    {
        if (args.Length == 0)
            throw new ArgumentException("Path required");

        string path = Path.Combine(context.CurrentDirectory, args[0]);
        
        if (File.Exists(path))
            File.Delete(path);
        else
            throw new FileNotFoundException($"File not found: {args[0]}");

        return Task.CompletedTask;
    }
}
</code>

### Text Processing Commands

<code>
public class GrepCommand : ICommand
{
    public Task ExecuteAsync(string[] args, ShellContext context)
    {
        if (args.Length < 2)
            throw new ArgumentException("Usage: grep <pattern> <file>");

        string pattern = args[0];
        string filePath = Path.Combine(context.CurrentDirectory, args[1]);

        if (!File.Exists(filePath))
            throw new FileNotFoundException($"File not found: {args[1]}");

        var matches = File.ReadLines(filePath)
            .Select((line, index) => new { Line = line, LineNumber = index + 1 })
            .Where(x => x.Line.Contains(pattern, StringComparison.OrdinalIgnoreCase));

        foreach (var match in matches)
        {
            Console.WriteLine($"{match.LineNumber}: {match.Line}");
        }

        return Task.CompletedTask;
    }
}

public class CatCommand : ICommand
{
    public async Task ExecuteAsync(string[] args, ShellContext context)
    {
        if (args.Length == 0)
            throw new ArgumentException("File name required");

        string filePath = Path.Combine(context.CurrentDirectory, args[0]);
        
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"File not found: {args[0]}");

        await foreach (var line in File.ReadLinesAsync(filePath))
        {
            Console.WriteLine(line);
        }
    }
}
</code>

### Network Commands

<code>
public class CurlCommand : ICommand
{
    private readonly HttpClient _httpClient = new();

    public async Task ExecuteAsync(string[] args, ShellContext context)
    {
        if (args.Length == 0)
            throw new ArgumentException("URL required");

        string url = args[0];
        try
        {
            var response = await _httpClient.GetStringAsync(url);
            Console.WriteLine(response);
        }
        catch (HttpRequestException ex)
        {
            Console.WriteLine($"Error fetching URL: {ex.Message}");
        }
    }
}
</code>

### Implementing Pipes and Redirection

<code>
public class PipelineExecutor
{
    private readonly Dictionary<string, ICommand> _commands;

    public PipelineExecutor(Dictionary<string, ICommand> commands)
    {
        _commands = commands;
    }

    public async Task ExecutePipelineAsync(string input, ShellContext context)
    {
        var commands = input.Split('|')
            .Select(cmd => cmd.Trim())
            .ToList();

        string output = null;

        foreach (var command in commands)
        {
            var (cmd, args) = ParseCommand(command);
            
            if (_commands.TryGetValue(cmd, out var executor))
            {
                using var stdout = new StringWriter();
                var originalOut = Console.Out;
                Console.SetOut(stdout);

                await executor.ExecuteAsync(args, context);
                output = stdout.ToString();

                Console.SetOut(originalOut);
            }
        }

        if (output != null)
            Console.Write(output);
    }

    private (string Command, string[] Args) ParseCommand(string input)
    {
        var parts = input.Split(' ', StringSplitOptions.RemoveEmptyEntries);
        return (parts[0].ToLower(), parts.Skip(1).ToArray());
    }
}

public class RedirectionHandler
{
    public async Task HandleRedirectionAsync(string input, ShellContext context)
    {
        var parts = input.Split('>');
        if (parts.Length != 2)
            throw new ArgumentException("Invalid redirection syntax");

        var command = parts[0].Trim();
        var fileName = parts[1].Trim();

        using var writer = new StreamWriter(
            Path.Combine(context.CurrentDirectory, fileName));
        var originalOut = Console.Out;
        Console.SetOut(writer);

        await new PipelineExecutor(context.Commands)
            .ExecutePipelineAsync(command, context);

        Console.SetOut(originalOut);
    }
}
</code>

### Main Program Integration

<code>
class Program
{
    static async Task Main(string[] args)
    {
        Console.WriteLine("Custom Bash Shell (Type 'exit' to quit)");
        Console.WriteLine("----------------------------------------");

        var shell = new BashShell();
        await shell.RunAsync();
    }
}
</code>

### Best Practices and Error Handling

1. Command Pattern Best Practices:
   - Keep commands single-responsibility
   - Implement proper argument validation
   - Use async/await consistently
   - Handle paths correctly
   - Implement proper error messages

2. Error Handling:
   - Validate input parameters
   - Handle file system exceptions
   - Provide meaningful error messages
   - Clean up resources properly
   - Handle cancellation

3. Security Considerations:
   - Validate file paths
   - Handle permissions
   - Sanitize input
   - Limit command access
   - Protect against directory traversal

This completes our comprehensive C# and .NET 8 tutorial. The bash shell implementation demonstrates many of the concepts we've covered throughout the tutorial, including:

- Object-oriented programming
- Interface-based design
- File system operations
- Asynchronous programming
- Error handling
- String manipulation
- Command pattern
- Resource management

Would you like me to elaborate on any particular aspect or provide additional examples?

</tutorial>

I'll break down the bash shell CLI terminal project in more detail with additional explanations and implementations.

<tutorial>

## Detailed Bash Shell CLI Terminal Implementation

### 1. Core Shell Structure

First, let's create the basic shell infrastructure with detailed explanations:

<code>
public class BashShell
{
    private readonly Dictionary<string, ICommand> _commands;
    private string _currentDirectory;
    private readonly Dictionary<string, string> _environment;
    private readonly IOutputWriter _outputWriter;
    private readonly CommandParser _commandParser;

    public BashShell(IOutputWriter outputWriter = null)
    {
        _currentDirectory = Environment.CurrentDirectory;
        _environment = InitializeEnvironment();
        _commands = InitializeCommands();
        _outputWriter = outputWriter ?? new ConsoleOutputWriter();
        _commandParser = new CommandParser();
    }

    // Initialize environment variables
    private Dictionary<string, string> InitializeEnvironment()
    {
        return new Dictionary<string, string>
        {
            ["HOME"] = Environment.GetFolderPath(Environment.SpecialFolder.UserProfile),
            ["PATH"] = Environment.GetEnvironmentVariable("PATH"),
            ["USER"] = Environment.UserName,
            ["PWD"] = Environment.CurrentDirectory
        };
    }

    // Main shell loop
    public async Task RunAsync()
    {
        while (true)
        {
            try
            {
                await DisplayPromptAsync();
                var input = await _outputWriter.ReadLineAsync();

                if (string.IsNullOrEmpty(input))
                    continue;

                if (input.ToLower() == "exit")
                    break;

                await ExecuteCommandLineAsync(input);
            }
            catch (Exception ex)
            {
                await _outputWriter.WriteLineAsync($"Error: {ex.Message}");
            }
        }
    }

    private async Task DisplayPromptAsync()
    {
        var username = _environment["USER"];
        var hostname = Environment.MachineName;
        var directory = Path.GetFileName(_currentDirectory) ?? _currentDirectory;
        await _outputWriter.WriteAsync($"{username}@{hostname}:{directory}$ ");
    }
}
</code>

### 2. Command Infrastructure

Let's create a robust command infrastructure:

<code>
public interface ICommand
{
    string Description { get; }
    string Usage { get; }
    Task<CommandResult> ExecuteAsync(CommandContext context);
}

public class CommandContext
{
    public string[] Arguments { get; set; }
    public string CurrentDirectory { get; set; }
    public Dictionary<string, string> Environment { get; set; }
    public IOutputWriter OutputWriter { get; set; }
    public TextReader InputReader { get; set; }
    public CancellationToken CancellationToken { get; set; }
}

public class CommandResult
{
    public bool Success { get; set; }
    public string Output { get; set; }
    public string Error { get; set; }
    public int ExitCode { get; set; }

    public static CommandResult Ok(string output = "") => new()
    {
        Success = true,
        Output = output,
        ExitCode = 0
    };

    public static CommandResult Fail(string error) => new()
    {
        Success = false,
        Error = error,
        ExitCode = 1
    };
}
</code>

### 3. Command Parser Implementation

<code>
public class CommandParser
{
    public CommandLineInstruction Parse(string input)
    {
        var instruction = new CommandLineInstruction();
        
        // Handle pipes
        var pipeCommands = input.Split('|', StringSplitOptions.TrimEntries);
        foreach (var command in pipeCommands)
        {
            instruction.Commands.Add(ParseSingleCommand(command));
        }

        // Handle redirection
        var lastCommand = instruction.Commands.Last();
        if (lastCommand.Raw.Contains('>'))
        {
            var parts = lastCommand.Raw.Split('>', StringSplitOptions.TrimEntries);
            lastCommand.Raw = parts[0];
            instruction.RedirectTo = parts[1];
        }

        return instruction;
    }

    private ParsedCommand ParseSingleCommand(string command)
    {
        var parts = SplitCommandLine(command);
        return new ParsedCommand
        {
            Raw = command,
            Name = parts[0],
            Arguments = parts.Skip(1).ToArray()
        };
    }

    private string[] SplitCommandLine(string commandLine)
    {
        var parts = new List<string>();
        var currentPart = new StringBuilder();
        var inQuotes = false;

        for (int i = 0; i < commandLine.Length; i++)
        {
            char c = commandLine[i];
            if (c == '"')
            {
                inQuotes = !inQuotes;
            }
            else if (c == ' ' && !inQuotes)
            {
                if (currentPart.Length > 0)
                {
                    parts.Add(currentPart.ToString());
                    currentPart.Clear();
                }
            }
            else
            {
                currentPart.Append(c);
            }
        }

        if (currentPart.Length > 0)
        {
            parts.Add(currentPart.ToString());
        }

        return parts.ToArray();
    }
}
</code>

### 4. Detailed Command Implementations

Let's implement some of the more complex commands in detail:

<code>
public class GrepCommand : ICommand
{
    public string Description => "Search for patterns in files";
    public string Usage => "grep [options] pattern file";

    public async Task<CommandResult> ExecuteAsync(CommandContext context)
    {
        try
        {
            var options = ParseOptions(context.Arguments);
            if (options.Pattern == null || options.FilePath == null)
            {
                return CommandResult.Fail("Usage: " + Usage);
            }

            var filePath = Path.Combine(context.CurrentDirectory, options.FilePath);
            if (!File.Exists(filePath))
            {
                return CommandResult.Fail($"File not found: {options.FilePath}");
            }

            var output = new StringBuilder();
            var lineNumber = 0;
            var regex = new Regex(options.Pattern, 
                options.IgnoreCase ? RegexOptions.IgnoreCase : RegexOptions.None);

            await foreach (var line in File.ReadLinesAsync(filePath))
            {
                lineNumber++;
                if (regex.IsMatch(line))
                {
                    if (options.ShowLineNumbers)
                    {
                        output.AppendLine($"{lineNumber}:{line}");
                    }
                    else
                    {
                        output.AppendLine(line);
                    }
                }
            }

            return CommandResult.Ok(output.ToString());
        }
        catch (RegexParseException ex)
        {
            return CommandResult.Fail($"Invalid regular expression: {ex.Message}");
        }
        catch (Exception ex)
        {
            return CommandResult.Fail(ex.Message);
        }
    }

    private class GrepOptions
    {
        public string Pattern { get; set; }
        public string FilePath { get; set; }
        public bool IgnoreCase { get; set; }
        public bool ShowLineNumbers { get; set; }
    }

    private GrepOptions ParseOptions(string[] args)
    {
        var options = new GrepOptions();
        var argList = new List<string>(args);

        while (argList.Count > 0 && argList[0].StartsWith("-"))
        {
            var flag = argList[0];
            argList.RemoveAt(0);

            switch (flag)
            {
                case "-i":
                    options.IgnoreCase = true;
                    break;
                case "-n":
                    options.ShowLineNumbers = true;
                    break;
            }
        }

        if (argList.Count >= 2)
        {
            options.Pattern = argList[0];
            options.FilePath = argList[1];
        }

        return options;
    }
}

public class LessCommand : ICommand
{
    public string Description => "View file contents with pagination";
    public string Usage => "less [file]";

    public async Task<CommandResult> ExecuteAsync(CommandContext context)
    {
        if (context.Arguments.Length == 0)
        {
            return CommandResult.Fail("File name required");
        }

        var filePath = Path.Combine(context.CurrentDirectory, context.Arguments[0]);
        if (!File.Exists(filePath))
        {
            return CommandResult.Fail($"File not found: {context.Arguments[0]}");
        }

        try
        {
            var lines = await File.ReadAllLinesAsync(filePath);
            var currentLine = 0;
            var pageSize = Console.WindowHeight - 1;

            while (currentLine < lines.Length)
            {
                Console.Clear();
                
                // Display current page
                for (int i = 0; i < pageSize && currentLine + i < lines.Length; i++)
                {
                    await context.OutputWriter.WriteLineAsync(lines[currentLine + i]);
                }

                // Display status line
                var percentage = (currentLine + pageSize >= lines.Length) ? 100 
                    : (currentLine + pageSize) * 100 / lines.Length;
                await context.OutputWriter.WriteLineAsync(
                    $":{percentage}% (Press 'q' to quit, Space for next page)");

                // Handle input
                var key = Console.ReadKey(true);
                switch (key.Key)
                {
                    case ConsoleKey.Q:
                        return CommandResult.Ok();
                    case ConsoleKey.Spacebar:
                        currentLine += pageSize;
                        break;
                    case ConsoleKey.UpArrow:
                        currentLine = Math.Max(0, currentLine - 1);
                        break;
                    case ConsoleKey.DownArrow:
                        currentLine = Math.Min(lines.Length - 1, currentLine + 1);
                        break;
                }
            }

            return CommandResult.Ok();
        }
        catch (Exception ex)
        {
            return CommandResult.Fail(ex.Message);
        }
    }
}
</code>

### 5. Pipeline Implementation

Here's a detailed implementation of the pipeline mechanism:

<code>
public class Pipeline
{
    private readonly List<ICommand> _commands;
    private readonly CommandContext _context;

    public Pipeline(IEnumerable<ICommand> commands, CommandContext context)
    {
        _commands = commands.ToList();
        _context = context;
    }

    public async Task<CommandResult> ExecuteAsync()
    {
        if (!_commands.Any())
            return CommandResult.Ok();

        if (_commands.Count == 1)
            return await _commands[0].ExecuteAsync(_context);

        var output = new StringBuilder();
        var currentInput = string.Empty;

        for (int i = 0; i < _commands.Count; i++)
        {
            var command = _commands[i];
            var pipeContext = new CommandContext
            {
                Arguments = _context.Arguments,
                CurrentDirectory = _context.CurrentDirectory,
                Environment = _context.Environment,
                InputReader = new StringReader(currentInput),
                OutputWriter = new StringWriter(output),
                CancellationToken = _context.CancellationToken
            };

            var result = await command.ExecuteAsync(pipeContext);
            if (!result.Success)
                return result;

            currentInput = output.ToString();
            output.Clear();
        }

        return CommandResult.Ok(currentInput);
    }
}
</code>

### 6. File System Operations

Let's implement a robust file system operation handler:

<code>
public class FileSystemOperations
{
    public static async Task<bool> CopyFileAsync(
        string source, 
        string destination, 
        bool overwrite = false,
        IProgress<double> progress = null)
    {
        try
        {
            var sourceFile = new FileInfo(source);
            if (!sourceFile.Exists)
                return false;

            using var sourceStream = sourceFile.OpenRead();
            using var destinationStream = new FileStream(
                destination, 
                overwrite ? FileMode.Create : FileMode.CreateNew);

            var buffer = new byte[81920];
            long totalBytes = sourceFile.Length;
            long bytesRead = 0;
            int currentRead;

            while ((currentRead = await sourceStream.ReadAsync(buffer)) > 0)
            {
                await destinationStream.WriteAsync(buffer.AsMemory(0, currentRead));
                bytesRead += currentRead;
                progress?.Report((double)bytesRead / totalBytes);
            }

            return true;
        }
        catch (Exception)
        {
            return false;
        }
    }

    public static bool IsValidPath(string path)
    {
        try
        {
            _ = Path.GetFullPath(path);
            return true;
        }
        catch
        {
            return false;
        }
    }

    public static string NormalizePath(string path)
    {
        if (string.IsNullOrWhiteSpace(path))
            return path;

        return Path.GetFullPath(new Uri(path).LocalPath)
            .TrimEnd(Path.DirectorySeparatorChar, Path.AltDirectorySeparatorChar)
            .ToUpperInvariant();
    }
}
</code>

### 7. Command History Implementation

<code>
public class CommandHistory
{
    private readonly List<string> _history = new();
    private int _currentIndex = -1;
    private readonly int _maxHistory;

    public CommandHistory(int maxHistory = 1000)
    {
        _maxHistory = maxHistory;
    }

    public void Add(string command)
    {
        if (string.IsNullOrWhiteSpace(command))
            return;

        _history.Add(command);
        if (_history.Count > _maxHistory)
            _history.RemoveAt(0);
        
        _currentIndex = _history.Count;
    }

    public string GetPrevious()
    {
        if (_currentIndex <= 0)
            return null;

        _currentIndex--;
        return _history[_currentIndex];
    }

    public string GetNext()
    {
        if (_currentIndex >= _history.Count - 1)
            return null;

        _currentIndex++;
        return _history[_currentIndex];
    }

    public void Save(string filePath)
    {
        File.WriteAllLines(filePath, _history);
    }

    public void Load(string filePath)
    {
        if (File.Exists(filePath))
        {
            _history.AddRange(File.ReadAllLines(filePath));
            _currentIndex = _history.Count;
        }
    }
}
</code>

### 8. Integration and Usage

Here's how to put it all together:

<code>
class Program
{
    static async Task Main(string[] args)
    {
        var shell = new BashShell();
        var history = new CommandHistory();
        
        // Load command history
        var historyPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.UserProfile),
            ".shell_history");
        history.Load(historyPath);

        Console.CancelKeyPress += (s, e) =>
        {
            e.Cancel = true;
            history.Save(historyPath);
        };

        try
        {
            await shell.RunAsync();
        }
        finally
        {
            history.Save(historyPath);
        }
    }
}
</code>

### Key Features to Implement:

1. Command Auto-completion
2. Environment Variable Expansion
3. Input/Output Redirection
4. Background Process Handling
5. Signal Handling
6. Path Resolution
7. Wildcard Expansion
8. Alias Support

This implementation provides a robust foundation for a bash-like shell with modern C# features. The code includes:

- Proper error handling
- Async/await patterns
- Resource management
- Command history
- File system operations
- Pipeline support
- Redirection handling
- Progress reporting

Would you like me to elaborate on any specific aspect or provide additional implementations for other features?

</tutorial>