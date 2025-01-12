# C# and .NET 8 Mastery: From Fundamentals to Advanced Programming

## Course Overview

This comprehensive course will guide you through C# and .NET 8, starting with basic concepts and progressing to advanced programming techniques. Each section includes detailed explanations, practical examples, exercises, and a section project to reinforce your learning.

## Section 1: Getting Started with .NET CLI and C# Basics

### Understanding the .NET CLI

The .NET Command Line Interface (CLI) is your primary tool for creating and managing .NET projects. Let's explore essential commands:

```bash
# Create a new console application
dotnet new console -n MyFirstApp

# Create a new class library
dotnet new classlib -n MyLibrary

# Build your application
dotnet build

# Run your application
dotnet run

# Add package reference
dotnet add package PackageName

# Create a solution and add projects
dotnet new sln -n MySolution
dotnet sln add MyFirstApp/MyFirstApp.csproj
```

### Exercise 1: CLI Mastery
Create a solution with multiple projects:
1. Create a new solution named "BookLibrary"
2. Add a console application project
3. Add a class library project
4. Add a reference from the console app to the class library
5. Build and run the solution

### C# Basic Syntax and Data Types

```csharp
using System;

namespace BasicSyntaxDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Value types
            int number = 42;
            double price = 19.99;
            bool isActive = true;
            char grade = 'A';

            // Reference types
            string name = "John Doe";
            object obj = new object();

            // Arrays
            int[] numbers = new int[5] { 1, 2, 3, 4, 5 };
            string[] names = { "Alice", "Bob", "Charlie" };

            // Constants and readonly
            const double PI = 3.14159;
            
            // Type inference
            var inferredNumber = 42; // int
            var inferredText = "Hello"; // string
            
            // Nullable types
            int? nullableNumber = null;
        }
    }
}
```

### Exercise 2: Data Types and Variables
Create a program that:
1. Declares variables of each basic data type
2. Performs arithmetic operations
3. Demonstrates type conversion
4. Uses nullable types
5. Works with arrays

### Control Flow and Decision Making

```csharp
// If statements
if (condition)
{
    // code
}
else if (anotherCondition)
{
    // code
}
else
{
    // code
}

// Switch statement
switch (value)
{
    case 1:
        // code
        break;
    case 2:
        // code
        break;
    default:
        // code
        break;
}

// Switch expression (C# 8.0+)
string result = value switch
{
    1 => "One",
    2 => "Two",
    _ => "Other"
};

// Loops
for (int i = 0; i < 10; i++)
{
    // code
}

foreach (var item in collection)
{
    // code
}

while (condition)
{
    // code
}

do
{
    // code
} while (condition);
```

### Exercise 3: Control Flow
Create a number guessing game that:
1. Generates a random number
2. Takes user input
3. Provides hints (higher/lower)
4. Counts attempts
5. Allows multiple games

### Section Project: Grade Calculator
Build a console application that:
1. Takes student grades as input
2. Calculates average, highest, and lowest grades
3. Assigns letter grades based on ranges
4. Handles invalid input
5. Provides summary statistics

## Section 2: Object-Oriented Programming in C#

### Classes and Objects

```csharp
public class Person
{
    // Fields
    private string _name;
    private int _age;

    // Properties
    public string Name
    {
        get { return _name; }
        set { _name = value; }
    }

    // Auto-implemented property
    public int Age { get; set; }

    // Constructors
    public Person()
    {
        // Default constructor
    }

    public Person(string name, int age)
    {
        _name = name;
        _age = age;
    }

    // Methods
    public virtual string GetInfo()
    {
        return $"{Name} is {Age} years old";
    }
}
```

### Exercise 4: Class Design
Create a banking system with:
1. Account class with properties and methods
2. Different account types (Checking, Savings)
3. Transaction handling
4. Balance calculations
5. Account history

### Inheritance and Polymorphism

```csharp
public abstract class Shape
{
    public abstract double CalculateArea();
    public abstract double CalculatePerimeter();
}

public class Circle : Shape
{
    public double Radius { get; set; }

    public override double CalculateArea()
    {
        return Math.PI * Radius * Radius;
    }

    public override double CalculatePerimeter()
    {
        return 2 * Math.PI * Radius;
    }
}

public class Rectangle : Shape
{
    public double Width { get; set; }
    public double Height { get; set; }

    public override double CalculateArea()
    {
        return Width * Height;
    }

    public override double CalculatePerimeter()
    {
        return 2 * (Width + Height);
    }
}
```

### Exercise 5: Inheritance
Create a vehicle management system:
1. Abstract Vehicle base class
2. Different vehicle types (Car, Motorcycle, Truck)
3. Common and specific behaviors
4. Vehicle registration system
5. Polymorphic method calls

### Section Project: Library Management System
Build a console application that:
1. Manages books, magazines, and digital content
2. Handles member borrowing and returns
3. Tracks due dates and fines
4. Generates reports
5. Implements search functionality

## Section 3: Asynchronous Programming

### Understanding Async/Await

```csharp
public class FileProcessor
{
    public async Task ProcessFileAsync(string filePath)
    {
        try
        {
            string content = await File.ReadAllTextAsync(filePath);
            await Task.Delay(1000); // Simulate processing
            await File.WriteAllTextAsync("processed.txt", content.ToUpper());
        }
        catch (Exception ex)
        {
            throw new ProcessingException("File processing failed", ex);
        }
    }
}

// Using async/await with multiple tasks
public async Task ProcessMultipleFilesAsync(string[] filePaths)
{
    var tasks = filePaths.Select(path => ProcessFileAsync(path));
    await Task.WhenAll(tasks);
}
```

### Exercise 6: Async Operations
Create an application that:
1. Downloads multiple files simultaneously
2. Shows progress indicators
3. Handles timeouts
4. Implements cancellation
5. Processes results as they complete

### Section Project: Batch Image Processor
Build an application that:
1. Processes multiple images asynchronously
2. Applies various transformations
3. Handles progress reporting
4. Implements cancellation
5. Saves processed images

[Content continues with detailed sections on File Handling, Network Programming, Entity Framework Core, 
Delegates and Events, Generics, Collections, Exception Handling, Reflection, Strings, Dependency Injection, 
and the final CLI project... Would you like me to continue with the next sections?]
