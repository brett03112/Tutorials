Okay, here's a comprehensive set of C# coding exercises categorized by topic, incorporating LeetCode problems and common C# interview questions where applicable.

**I. Basic Calculations, Input and Output**

1. **Calculator:**
    * Write a program that takes two numbers and an operator (+, -, \*, /) as input and performs the corresponding calculation.
    * Handle potential errors like division by zero.

    ```csharp
    using System;

    public class Calculator
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Enter first number:");
            double num1 = Convert.ToDouble(Console.ReadLine());

            Console.WriteLine("Enter operator (+, -, *, /):");
            char op = Convert.ToChar(Console.ReadLine());

            Console.WriteLine("Enter second number:");
            double num2 = Convert.ToDouble(Console.ReadLine());

            double result = 0;

            switch (op)
            {
                case '+':
                    result = num1 + num2;
                    break;
                case '-':
                    result = num1 - num2;
                    break;
                case '*':
                    result = num1 * num2;
                    break;
                case '/':
                    if (num2 == 0)
                    {
                        Console.WriteLine("Error: Division by zero!");
                        return;
                    }
                    result = num1 / num2;
                    break;
                default:
                    Console.WriteLine("Invalid operator!");
                    return;
            }

            Console.WriteLine("Result: " + result);
        }
    }
    ```

2. **Area of a Circle:**
    * Prompt the user to enter the radius of a circle and calculate its area.
    * Use `Math.PI` for the value of pi.

    ```csharp
    using System;

    public class CircleArea
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Enter the radius of the circle:");
            double radius = Convert.ToDouble(Console.ReadLine());

            double area = Math.PI * radius * radius;

            Console.WriteLine("Area of the circle: " + area);
        }
    }
    ```

3. **Temperature Converter:**
    * Create a program that converts temperature from Celsius to Fahrenheit and vice-versa, based on user input.
    * Formula:
        * Fahrenheit = (Celsius \* 9/5) + 32
        * Celsius = (Fahrenheit - 32) \* 5/9

    ```csharp
    using System;

    public class TemperatureConverter
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Choose conversion type:");
            Console.WriteLine("1. Celsius to Fahrenheit");
            Console.WriteLine("2. Fahrenheit to Celsius");

            int choice = Convert.ToInt32(Console.ReadLine());

            if (choice == 1)
            {
                Console.WriteLine("Enter temperature in Celsius:");
                double celsius = Convert.ToDouble(Console.ReadLine());
                double fahrenheit = (celsius * 9 / 5) + 32;
                Console.WriteLine("Temperature in Fahrenheit: " + fahrenheit);
            }
            else if (choice == 2)
            {
                Console.WriteLine("Enter temperature in Fahrenheit:");
                double fahrenheit = Convert.ToDouble(Console.ReadLine());
                double celsius = (fahrenheit - 32) * 5 / 9;
                Console.WriteLine("Temperature in Celsius: " + celsius);
            }
            else
            {
                Console.WriteLine("Invalid choice!");
            }
        }
    }
    ```

**II. Control Flow and Loops**

1. **FizzBuzz:** (Classic interview question)
    * Print numbers from 1 to 100.
    * For multiples of 3, print "Fizz".
    * For multiples of 5, print "Buzz".
    * For multiples of both 3 and 5, print "FizzBuzz".

    ```csharp
    using System;

    public class FizzBuzz
    {
        public static void Main(string[] args)
        {
            for (int i = 1; i <= 100; i++)
            {
                if (i % 3 == 0 && i % 5 == 0)
                {
                    Console.WriteLine("FizzBuzz");
                }
                else if (i % 3 == 0)
                {
                    Console.WriteLine("Fizz");
                }
                else if (i % 5 == 0)
                {
                    Console.WriteLine("Buzz");
                }
                else
                {
                    Console.WriteLine(i);
                }
            }
        }
    }
    ```

2. **Factorial:**
    * Calculate the factorial of a number entered by the user.

    ```csharp
    using System;

    public class Factorial
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Enter a non-negative integer:");
            int num = Convert.ToInt32(Console.ReadLine());

            if (num < 0)
            {
                Console.WriteLine("Factorial is not defined for negative numbers.");
                return;
            }

            long factorial = 1;
            for (int i = 1; i <= num; i++)
            {
                factorial *= i;
            }

            Console.WriteLine("Factorial of " + num + " = " + factorial);
        }
    }
    ```

3. **Prime Number Check:**
    * Determine if a given number is prime or not.

    ```csharp
    using System;

    public class PrimeChecker
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Enter a positive integer:");
            int num = Convert.ToInt32(Console.ReadLine());

            if (num <= 1)
            {
                Console.WriteLine(num + " is not a prime number.");
                return;
            }

            bool isPrime = true;
            for (int i = 2; i <= Math.Sqrt(num); i++)
            {
                if (num % i == 0)
                {
                    isPrime = false;
                    break;
                }
            }

            if (isPrime)
            {
                Console.WriteLine(num + " is a prime number.");
            }
            else
            {
                Console.WriteLine(num + " is not a prime number.");
            }
        }
    }
    ```

4. **Fibonacci Sequence:**
    * Generate the first `n` numbers of the Fibonacci sequence.

    ```csharp
    using System;

    public class Fibonacci
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Enter the number of Fibonacci numbers to generate:");
            int n = Convert.ToInt32(Console.ReadLine());

            int first = 0, second = 1;

            Console.Write("Fibonacci Sequence: " + first + " " + second + " ");

            for (int i = 2; i < n; i++)
            {
                int next = first + second;
                Console.Write(next + " ");
                first = second;
                second = next;
            }
            Console.WriteLine();
        }
    }
    ```

**III. Arrays**

1. **Reverse Array:**
    * Write a program to reverse an array of integers.

    ```csharp
    using System;

    public class ReverseArray
    {
        public static void Main(string[] args)
        {
            int[] numbers = { 1, 2, 3, 4, 5 };

            Console.WriteLine("Original array:");
            PrintArray(numbers);

            Reverse(numbers);

            Console.WriteLine("Reversed array:");
            PrintArray(numbers);
        }

        static void Reverse(int[] arr)
        {
            int start = 0;
            int end = arr.Length - 1;

            while (start < end)
            {
                int temp = arr[start];
                arr[start] = arr[end];
                arr[end] = temp;
                start++;
                end--;
            }
        }

        static void PrintArray(int[] arr)
        {
            foreach (int num in arr)
            {
                Console.Write(num + " ");
            }
            Console.WriteLine();
        }
    }
    ```

2. **Find Maximum and Minimum:**
    * Find the maximum and minimum elements in an array.

    ```csharp
    using System;

    public class MaxMinArray
    {
        public static void Main(string[] args)
        {
            int[] numbers = { 5, 2, 9, 1, 5, 6 };

            int max = numbers[0];
            int min = numbers[0];

            for (int i = 1; i < numbers.Length; i++)
            {
                if (numbers[i] > max)
                {
                    max = numbers[i];
                }

                if (numbers[i] < min)
                {
                    min = numbers[i];
                }
            }

            Console.WriteLine("Maximum: " + max);
            Console.WriteLine("Minimum: " + min);
        }
    }
    ```

3. **Two Sum (LeetCode #1):**
    * Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to `target`.

    ```csharp
    using System;
    using System.Collections.Generic;

    public class TwoSumSolution
    {
        public static int[] TwoSum(int[] nums, int target)
        {
            Dictionary<int, int> numMap = new Dictionary<int, int>();

            for (int i = 0; i < nums.Length; i++)
            {
                int complement = target - nums[i];
                if (numMap.ContainsKey(complement))
                {
                    return new int[] { numMap[complement], i };
                }
                if (!numMap.ContainsKey(nums[i]))
                {
                    numMap.Add(nums[i], i);
                }
            }

            return new int[] { }; // No solution found
        }

        public static void Main(string[] args)
        {
            int[] nums = { 2, 7, 11, 15 };
            int target = 9;
            int[] result = TwoSum(nums, target);

            Console.WriteLine("Indices: [" + result[0] + ", " + result[1] + "]");
        }
    }
    ```

**IV. Strings**

1. **Palindrome Check:**
    * Check if a given string is a palindrome (reads the same backward as forward).

    ```csharp
    using System;

    public class PalindromeChecker
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Enter a string:");
            string str = Console.ReadLine().ToLower();

            bool isPalindrome = IsPalindrome(str);

            if (isPalindrome)
            {
                Console.WriteLine(str + " is a palindrome.");
            }
            else
            {
                Console.WriteLine(str + " is not a palindrome.");
            }
        }

        static bool IsPalindrome(string str)
        {
            int left = 0;
            int right = str.Length - 1;

            while (left < right)
            {
                if (str[left] != str[right])
                {
                    return false;
                }
                left++;
                right--;
            }

            return true;
        }
    }
    ```

2. **String Reversal:**
    * Reverse a given string.

    ```csharp
    using System;

    public class StringReverser
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Enter a string:");
            string str = Console.ReadLine();

            string reversedStr = ReverseString(str);

            Console.WriteLine("Reversed string: " + reversedStr);
        }

        static string ReverseString(string str)
        {
            char[] charArray = str.ToCharArray();
            Array.Reverse(charArray);
            return new string(charArray);
        }
    }
    ```

3. **Anagram Check:**
    * Determine if two strings are anagrams of each other (contain the same characters in a different order).

    ```csharp
    using System;
    using System.Linq;

    public class AnagramChecker
    {
        public static void Main(string[] args)
        {
            Console.WriteLine("Enter first string:");
            string str1 = Console.ReadLine().ToLower();

            Console.WriteLine("Enter second string:");
            string str2 = Console.ReadLine().ToLower();

            bool areAnagrams = AreAnagrams(str1, str2);

            if (areAnagrams)
            {
                Console.WriteLine(str1 + " and " + str2 + " are anagrams.");
            }
            else
            {
                Console.WriteLine(str1 + " and " + str2 + " are not anagrams.");
            }
        }

        static bool AreAnagrams(string str1, string str2)
        {
            if (str1.Length != str2.Length)
            {
                return false;
            }

            return str1.OrderBy(c => c).SequenceEqual(str2.OrderBy(c => c));
        }
    }
    ```

4. **Valid Parentheses (LeetCode #20):**
    * Given a string `s` containing just the characters '(', ')', '{', '}', '\[' and '\]', determine if the input string is valid.

    ```csharp
    using System;
    using System.Collections.Generic;

    public class ValidParenthesesSolution
    {
        public static bool IsValid(string s)
        {
            Stack<char> stack = new Stack<char>();

            foreach (char c in s)
            {
                if (c == '(' || c == '{' || c == '[')
                {
                    stack.Push(c);
                }
                else if (c == ')' && (stack.Count == 0 || stack.Pop() != '('))
                {
                    return false;
                }
                else if (c == '}' && (stack.Count == 0 || stack.Pop() != '{'))
                {
                    return false;
                }
                else if (c == ']' && (stack.Count == 0 || stack.Pop() != '['))
                {
                    return false;
                }
            }

            return stack.Count == 0;
        }

        public static void Main(string[] args)
        {
            string s = "()[]{}";
            bool isValid = IsValid(s);
            Console.WriteLine(s + " is valid: " + isValid);

            s = "([)]";
            isValid = IsValid(s);
            Console.WriteLine(s + " is valid: " + isValid);
        }
    }
    ```

**V. Object-Oriented Programming (OOP)**

1. **Basic Class - `BankAccount`:**
    * Create a `BankAccount` class with properties like `AccountNumber`, `AccountHolderName`, `Balance`.
    * Implement methods for `Deposit`, `Withdraw`, and `GetBalance`.

    ```csharp
    using System;

    public class BankAccount
    {
        public string AccountNumber { get; set; }
        public string AccountHolderName { get; set; }
        public decimal Balance { get; private set; }

        public BankAccount(string accountNumber, string accountHolderName, decimal initialBalance)
        {
            AccountNumber = accountNumber;
            AccountHolderName = accountHolderName;
            Balance = initialBalance;
        }

        public void Deposit(decimal amount)
        {
            if (amount > 0)
            {
                Balance += amount;
                Console.WriteLine("Deposited: " + amount);
            }
            else
            {
                Console.WriteLine("Invalid deposit amount.");
            }
        }

        public void Withdraw(decimal amount)
        {
            if (amount > 0 && amount <= Balance)
            {
                Balance -= amount;
                Console.WriteLine("Withdrawn: " + amount);
            }
            else
            {
                Console.WriteLine("Invalid withdrawal amount or insufficient balance.");
            }
        }

        public decimal GetBalance()
        {
            return Balance;
        }
    }
    ```

2. **Inheritance - `SavingsAccount`:**
    * Create a `SavingsAccount` class that inherits from `BankAccount`.
    * Add an `InterestRate` property.
    * Implement a method to `CalculateInterest` and add it to the balance.

    ```csharp
    using System;

    public class SavingsAccount : BankAccount
    {
        public decimal InterestRate { get; set; }

        public SavingsAccount(string accountNumber, string accountHolderName, decimal initialBalance, decimal interestRate)
            : base(accountNumber, accountHolderName, initialBalance)
        {
            InterestRate = interestRate;
        }

        public void CalculateInterest()
        {
            decimal interest = Balance * InterestRate;
            Deposit(interest);
            Console.WriteLine("Interest added: " + interest);
        }
    }
    ```

3. **Polymorphism - `Animal` class:**
    * Create a base class `Animal` with a virtual method `MakeSound`.
    * Create derived classes like `Dog`, `Cat`, and `Cow` that override `MakeSound` to produce their respective sounds.
    * Demonstrate polymorphism by creating a list of `Animal` objects and calling `MakeSound` on each.

    ```csharp
    using System;
    using System.Collections.Generic;

    public class Animal
    {
        public virtual void MakeSound()
        {
            Console.WriteLine("Generic animal sound");
        }
    }

    public class Dog : Animal
    {
        public override void MakeSound()
        {
            Console.WriteLine("Woof!");
        }
    }

    public class Cat : Animal
    {
        public override void MakeSound()
        {
            Console.WriteLine("Meow!");
        }
    }

    public class Cow : Animal
    {
        public override void MakeSound()
        {
            Console.WriteLine("Moo!");
        }
    }

    public class AnimalDemo
    {
        public static void Main(string[] args)
        {
            List<Animal> animals = new List<Animal>
            {
                new Dog(),
                new Cat(),
                new Cow()
            };

            foreach (Animal animal in animals)
            {
                animal.MakeSound();
            }
        }
    }
    ```

**VI. LINQ (Language Integrated Query)**

1. **Filtering with LINQ:**
    * Given a list of numbers, use LINQ to filter out all even numbers.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;

    public class LinqFiltering
    {
        public static void Main(string[] args)
        {
            List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

            var evenNumbers = numbers.Where(n => n % 2 == 0);

            Console.WriteLine("Even numbers:");
            foreach (int num in evenNumbers)
            {
                Console.Write(num + " ");
            }
            Console.WriteLine();
        }
    }
    ```

2. **Sorting with LINQ:**
    * Given a list of strings, use LINQ to sort them in alphabetical order.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;

    public class LinqSorting
    {
        public static void Main(string[] args)
        {
            List<string> names = new List<string> { "Alice", "Bob", "Charlie", "David", "Eve" };

            var sortedNames = names.OrderBy(name => name);

            Console.WriteLine("Sorted names:");
            foreach (string name in sortedNames)
            {
                Console.Write(name + " ");
            }
            Console.WriteLine();
        }
    }
    ```

3. **Projection with LINQ:**
    * Given a list of `Person` objects (with `Name` and `Age` properties), use LINQ to create a new list containing only the names of people older than 25.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;

    public class Person
    {
        public string Name { get; set; }
        public int Age { get; set; }
    }

    public class LinqProjection
    {
        public static void Main(string[] args)
        {
            List<Person> people = new List<Person>
            {
                new Person { Name = "Alice", Age = 30 },
                new Person { Name = "Bob", Age = 22 },
                new Person { Name = "Charlie", Age = 28 },
                new Person { Name = "David", Age = 20 }
            };

            var namesOver25 = people
                .Where(p => p.Age > 25)
                .Select(p => p.Name);

            Console.WriteLine("Names of people over 25:");
            foreach (string name in namesOver25)
            {
                Console.Write(name + " ");
            }
            Console.WriteLine();
        }
    }
    ```

4. **Grouping with LINQ:**
    * Given a list of `Product` objects (with `Name` and `Category` properties), use LINQ to group them by category.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;

    public class Product
    {
        public string Name { get; set; }
        public string Category { get; set; }
    }

    public class LinqGrouping
    {
        public static void Main(string[] args)
        {
            List<Product> products = new List<Product>
            {
                new Product { Name = "Laptop", Category = "Electronics" },
                new Product { Name = "Mouse", Category = "Electronics" },
                new Product { Name = "T-Shirt", Category = "Clothing" },
                new Product { Name = "Jeans", Category = "Clothing" },
                new Product { Name = "Monitor", Category = "Electronics" }
            };

            var groupedProducts = products.GroupBy(p => p.Category);

            foreach (var group in groupedProducts)
            {
                Console.WriteLine("Category: " + group.Key);
                foreach (Product product in group)
                {
                    Console.WriteLine("- " + product.Name);
                }
            }
        }
    }
    ```

**VII. Data Structures**

1. **Linked List Implementation:**
    * Implement a basic singly linked list with `Add`, `Remove`, and `Print` operations.

    ```csharp
    using System;

    public class Node
    {
        public int Data;
        public Node Next;

        public Node(int data)
        {
            Data = data;
            Next = null;
        }
    }

    public class LinkedList
    {
        private Node head;

        public void Add(int data)
        {
            Node newNode = new Node(data);
            if (head == null)
            {
                head = newNode;
            }
            else
            {
                Node current = head;
                while (current.Next != null)
                {
                    current = current.Next;
                }
                current.Next = newNode;
            }
        }

        public void Remove(int data)
        {
            if (head == null) return;

            if (head.Data == data)
            {
                head = head.Next;
                return;
            }

            Node current = head;
            while (current.Next != null && current.Next.Data != data)
            {
                current = current.Next;
            }

            if (current.Next != null)
            {
                current.Next = current.Next.Next;
            }
        }

        public void Print()
        {
            Node current = head;
            while (current != null)
            {
                Console.Write(current.Data + " -> ");
                current = current.Next;
            }
            Console.WriteLine("null");
        }
    }
    ```

2. **Stack Implementation:**
    * Implement a stack using an array or `List<T>`. Include `Push`, `Pop`, and `Peek` methods.

    ```csharp
    using System;
    using System.Collections.Generic;

    public class MyStack<T>
    {
        private List<T> data = new List<T>();

        public void Push(T item)
        {
            data.Add(item);
        }

        public T Pop()
        {
            if (data.Count == 0)
            {
                throw new InvalidOperationException("Stack is empty");
            }
            T item = data[data.Count - 1];
            data.RemoveAt(data.Count - 1);
            return item;
        }

        public T Peek()
        {
            if (data.Count == 0)
            {
                throw new InvalidOperationException("Stack is empty");
            }
            return data[data.Count - 1];
        }

        public int Count
        {
            get { return data.Count; }
        }
    }
    ```

3. **Queue Implementation:**
    * Implement a queue using an array or `List<T>`. Include `Enqueue`, `Dequeue`, and `Peek` methods.

    ```csharp
    using System;
    using System.Collections.Generic;

    public class MyQueue<T>
    {
        private List<T> data = new List<T>();

        public void Enqueue(T item)
        {
            data.Add(item);
        }

        public T Dequeue()
        {
            if (data.Count == 0)
            {
                throw new InvalidOperationException("Queue is empty");
            }
            T item = data[0];
            data.RemoveAt(0);
            return item;
        }

        public T Peek()
        {
            if (data.Count == 0)
            {
                throw new InvalidOperationException("Queue is empty");
            }
            return data[0];
        }

        public int Count
        {
            get { return data.Count; }
        }
    }
    ```

4. **Merge Two Sorted Arrays (LeetCode #88):**
    * You are given two integer arrays `nums1` and `nums2`, sorted in non-decreasing order, and two integers `m` and `n`, representing the number of elements in `nums1` and `nums2` respectively. Merge `nums2` into `nums1` as one sorted array.

    ```csharp
    using System;

    public class MergeSortedArraySolution
    {
        public static void Merge(int[] nums1, int m, int[] nums2, int n)
        {
            int p1 = m - 1;
            int p2 = n - 1;
            int p = m + n - 1;

            while (p1 >= 0 && p2 >= 0)
            {
                if (nums1[p1] > nums2[p2])
                {
                    nums1[p] = nums1[p1];
                    p1--;
                }
                else
                {
                    nums1[p] = nums2[p2];
                    p2--;
                }
                p--;
            }

            // Copy remaining elements of nums2 (if any)
            while (p2 >= 0)
            {
                nums1[p] = nums2[p2];
                p2--;
                p--;
            }
        }

        public static void Main(string[] args)
        {
            int[] nums1 = { 1, 2, 3, 0, 0, 0 };
            int m = 3;
            int[] nums2 = { 2, 5, 6 };
            int n = 3;

            Merge(nums1, m, nums2, n);

            Console.WriteLine("Merged array:");
            foreach (int num in nums1)
            {
                Console.Write(num + " ");
            }
            Console.WriteLine();
        }
    }
    ```

**VIII. File Input and Output**

1. **Read from a File:**
    * Read the contents of a text file and print them to the console.

    ```csharp
    using System;
    using System.IO;

    public class FileReader
    {
        public static void Main(string[] args)
        {
            string filePath = "myFile.txt"; // Replace with your file path

            try
            {
                using (StreamReader reader = new StreamReader(filePath))
                {
                    string line;
                    while ((line = reader.ReadLine()) != null)
                    {
                        Console.WriteLine(line);
                    }
                }
            }
            catch (FileNotFoundException)
            {
                Console.WriteLine("File not found: " + filePath);
            }
            catch (IOException ex)
            {
                Console.WriteLine("Error reading file: " + ex.Message);
            }
        }
    }
    ```

2. **Write to a File:**
    * Write a list of strings to a text file, each string on a new line.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.IO;

    public class FileWriter
    {
        public static void Main(string[] args)
        {
            string filePath = "output.txt"; // Replace with your desired file path
            List<string> lines = new List<string>
            {
                "Hello",
                "World",
                "This is a test file."
            };

            try
            {
                using (StreamWriter writer = new StreamWriter(filePath))
                {
                    foreach (string line in lines)
                    {
                        writer.WriteLine(line);
                    }
                }
                Console.WriteLine("Successfully wrote to file: " + filePath);
            }
            catch (IOException ex)
            {
                Console.WriteLine("Error writing to file: " + ex.Message);
            }
        }
    }
    ```

3. **Copy a File:**
    * Copy the contents of one file to another.

    ```csharp
    using System;
    using System.IO;

    public class FileCopier
    {
        public static void Main(string[] args)
        {
            string sourceFilePath = "source.txt"; // Replace with your source file path
            string destinationFilePath = "destination.txt"; // Replace with your destination file path

            try
            {
                File.Copy(sourceFilePath, destinationFilePath, true); // true to overwrite if destination exists
                Console.WriteLine("File copied successfully.");
            }
            catch (FileNotFoundException)
            {
                Console.WriteLine("Source file not found: " + sourceFilePath);
            }
            catch (IOException ex)
            {
                Console.WriteLine("Error copying file: " + ex.Message);
            }
        }
    }
    ```

**IX. Asynchronous Programming**

1. **Basic Asynchronous Method:**
    * Create an asynchronous method that simulates a long-running operation (e.g., using `Task.Delay`) and returns a result.

    ```csharp
    using System;
    using System.Threading.Tasks;

    public class AsyncDemo
    {
        public static async Task Main(string[] args)
        {
            Console.WriteLine("Starting asynchronous operation...");
            string result = await LongRunningOperationAsync();
            Console.WriteLine("Asynchronous operation completed.");
            Console.WriteLine("Result: " + result);
        }

        static async Task<string> LongRunningOperationAsync()
        {
            Console.WriteLine("LongRunningOperationAsync started...");
            await Task.Delay(3000); // Simulate a 3-second delay
            Console.WriteLine("LongRunningOperationAsync finished.");
            return "Operation completed successfully!";
        }
    }
    ```

2. **Handling Multiple Asynchronous Tasks:**
    * Use `Task.WhenAll` to run multiple asynchronous operations concurrently and wait for all of them to complete.

    ```csharp
    using System;
    using System.Threading.Tasks;

    public class AsyncMultipleTasks
    {
        public static async Task Main(string[] args)
        {
            Console.WriteLine("Starting multiple asynchronous operations...");

            Task<string> task1 = Task1Async();
            Task<string> task2 = Task2Async();
            Task<string> task3 = Task3Async();

            await Task.WhenAll(task1, task2, task3);

            Console.WriteLine("All asynchronous operations completed.");
            Console.WriteLine("Task 1 result: " + task1.Result);
            Console.WriteLine("Task 2 result: " + task2.Result);
            Console.WriteLine("Task 3 result: " + task3.Result);
        }

        static async Task<string> Task1Async()
        {
            await Task.Delay(2000);
            return "Task 1 completed";
        }

        static async Task<string> Task2Async()
        {
            await Task.Delay(3000);
            return "Task 2 completed";
        }

        static async Task<string> Task3Async()
        {
            await Task.Delay(1500);
            return "Task 3 completed";
        }
    }
    ```

Okay, let's continue with the Asynchronous File I/O example and then cover Events and Delegates in Part X.

**IX. Asynchronous Programming (Continued)**

**3. Asynchronous File I/O:**

* Read the contents of a file asynchronously.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;

public class AsyncFileIO
{
    public static async Task Main(string[] args)
    {
        string filePath = "myFile.txt"; // Replace with your file path

        try
        {
            string content = await ReadFileAsync(filePath);
            Console.WriteLine("File content:\n" + content);
        }
        catch (FileNotFoundException)
        {
            Console.WriteLine("File not found: " + filePath);
        }
        catch (IOException ex)
        {
            Console.WriteLine("Error reading file: " + ex.Message);
        }
    }

    static async Task<string> ReadFileAsync(string filePath)
    {
        using (StreamReader reader = new StreamReader(filePath))
        {
            return await reader.ReadToEndAsync();
        }
    }
}
```

**Explanation:**

* **`async` and `await`:** The `ReadFileAsync` method is marked as `async`, allowing it to use the `await` keyword. The `await` keyword pauses execution until the asynchronous operation (reading the file) is complete.
* **`StreamReader.ReadToEndAsync()`:** This method reads the entire content of the file asynchronously and returns a `Task<string>` representing the result.
* **`using` statement:** Ensures that the `StreamReader` (which implements `IDisposable`) is properly disposed of even if exceptions occur.
* **Error Handling:** The `try-catch` block handles potential `FileNotFoundException` and `IOException`.

**4. Asynchronous File I/O (Write):**

* Write to a file asynchronously

```csharp
using System;
using System.IO;
using System.Threading.Tasks;

public class AsyncFileIOWrite
{
    public static async Task Main(string[] args)
    {
        string filePath = "output_async.txt"; // Replace with your desired file path
        string content = "This is some text written asynchronously.";

        try
        {
            await WriteFileAsync(filePath, content);
            Console.WriteLine("Successfully wrote to file asynchronously: " + filePath);
        }
        catch (IOException ex)
        {
            Console.WriteLine("Error writing to file: " + ex.Message);
        }
    }

    static async Task WriteFileAsync(string filePath, string content)
    {
        using (StreamWriter writer = new StreamWriter(filePath))
        {
            await writer.WriteAsync(content);
        }
    }
}
```

**Explanation:**

* **`StreamWriter.WriteAsync()`:** This method writes the provided string to the file asynchronously.

**X. Events and Delegates**

**1. Delegate Basics:**

* Define a simple delegate that takes two integers and returns their sum.
* Create an instance of the delegate and invoke it.

```csharp
using System;

public delegate int BinaryOperation(int x, int y);

public class DelegateExample
{
    public static int Add(int a, int b)
    {
        return a + b;
    }

    public static void Main(string[] args)
    {
        BinaryOperation addOperation = Add; // Create a delegate instance

        int result = addOperation(5, 3); // Invoke the delegate
        Console.WriteLine("Result: " + result); // Output: 8
    }
}
```

**2. Event Basics:**

* Create a `Counter` class that has an event `ThresholdReached`.
* The event should be raised when the counter reaches a certain threshold.

```csharp
using System;

// Define the delegate for the event handler
public delegate void ThresholdReachedEventHandler(object sender, ThresholdReachedEventArgs e);

// Define the event arguments class
public class ThresholdReachedEventArgs : EventArgs
{
    public int Threshold { get; set; }
    public DateTime TimeReached { get; set; }
}

public class Counter
{
    // Declare the event
    public event ThresholdReachedEventHandler ThresholdReached;

    public int Threshold { get; set; }
    private int count;

    public Counter(int threshold)
    {
        Threshold = threshold;
        count = 0;
    }

    public void Add(int x)
    {
        count += x;
        if (count >= Threshold)
        {
            // Create event arguments
            ThresholdReachedEventArgs args = new ThresholdReachedEventArgs
            {
                Threshold = Threshold,
                TimeReached = DateTime.Now
            };

            // Raise the event (check if there are any subscribers)
            OnThresholdReached(args);
        }
    }

    protected virtual void OnThresholdReached(ThresholdReachedEventArgs e)
    {
        ThresholdReached?.Invoke(this, e);
    }
}

public class EventExample
{
    public static void Main(string[] args)
    {
        Counter counter = new Counter(5);

        // Subscribe to the event
        counter.ThresholdReached += Counter_ThresholdReached;

        counter.Add(2);
        counter.Add(1);
        counter.Add(3); // This will trigger the event
    }

    // Event handler method
    static void Counter_ThresholdReached(object sender, ThresholdReachedEventArgs e)
    {
        Console.WriteLine("The threshold of " + e.Threshold + " was reached at " + e.TimeReached);
    }
}
```

**Explanation:**

* **Delegate for Event Handler:** The `ThresholdReachedEventHandler` delegate defines the signature of the method that will handle the `ThresholdReached` event.
* **Event Arguments:** The `ThresholdReachedEventArgs` class (inheriting from `EventArgs`) is used to pass data with the event.
* **`event` Keyword:** The `ThresholdReached` event is declared using the `event` keyword along with the delegate type.
* **`OnThresholdReached` Method:** This method is responsible for raising the event. The `?.` (null-conditional operator) checks if there are any subscribers before invoking the event to avoid a `NullReferenceException`.
* **Event Subscription:** In `Main`, `Counter_ThresholdReached` is subscribed to the `ThresholdReached` event using the `+=` operator.
* **Event Handler:** The `Counter_ThresholdReached` method is the event handler that will be executed when the event is raised.

**3. Multicast Delegate:**

* Demonstrate how a delegate can point to multiple methods (multicast).

```csharp
using System;

public delegate void StringDelegate(string message);

public class MulticastDelegateExample
{
    public static void Method1(string message)
    {
        Console.WriteLine("Method1 called with message: " + message);
    }

    public static void Method2(string message)
    {
        Console.WriteLine("Method2 called with message: " + message);
    }

    public static void Main(string[] args)
    {
        StringDelegate del1 = Method1;
        StringDelegate del2 = Method2;

        // Combine delegates
        StringDelegate multiDel = del1 + del2;

        // Invoke the multicast delegate
        multiDel("Hello from multicast delegate!");

        // Remove a delegate
        multiDel -= del1;
        multiDel("Hello again after removing del1!");
    }
}
```

**Explanation:**

* **`del1 + del2`:** Combines `del1` and `del2` into a single multicast delegate `multiDel`. When `multiDel` is invoked, it will call both `Method1` and `Method2`.
* **`multiDel -= del1`:** Removes `del1` from the invocation list of `multiDel`.

**4. Anonymous Methods:**

* Use an anonymous method with a delegate.

```csharp
using System;

public delegate void PrintDelegate(string message);

public class AnonymousMethodExample
{
    public static void Main(string[] args)
    {
        // Anonymous method
        PrintDelegate printDel = delegate (string message)
        {
            Console.WriteLine("Anonymous method: " + message);
        };

        printDel("Hello from anonymous method!");
    }
}
```

**5. Lambda Expressions:**

* Use a lambda expression with a delegate.

```csharp
using System;

public delegate int CalculateDelegate(int a, int b);

public class LambdaExpressionExample
{
    public static void Main(string[] args)
    {
        // Lambda expression
        CalculateDelegate add = (a, b) => a + b;

        int result = add(10, 5);
        Console.WriteLine("Result from lambda expression: " + result); // Output: 15
    }
}
```

**6. Delegates with LINQ:**

* Show how delegates (via lambda expressions) are used with LINQ methods like `Where`, `Select`, etc.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;

public class LinqWithDelegates
{
    public static void Main(string[] args)
    {
        List<int> numbers = new List<int> { 1, 2, 3, 4, 5, 6 };

        // Where (filters elements based on a condition - a Func delegate)
        var evenNumbers = numbers.Where(n => n % 2 == 0);

        // Select (projects each element to a new form - a Func delegate)
        var squaredNumbers = numbers.Select(n => n * n);

        Console.WriteLine("Even numbers:");
        foreach (int num in evenNumbers)
        {
            Console.Write(num + " ");
        }
        Console.WriteLine("\nSquared numbers:");
        foreach (int num in squaredNumbers)
        {
            Console.Write(num + " ");
        }
        Console.WriteLine();
    }
}
```

**Explanation:**

* **`Where` and `Select`:** These LINQ methods take delegates (often expressed as lambda expressions) to define the filtering or projection logic.
* **`Func` Delegate:**  LINQ often uses the `Func` delegate, which represents a method that takes a certain number of input parameters and returns a value of a specific type.

This concludes the C# coding exercises, covering a broad range of topics from basic to more advanced concepts. If you have any further questions, feel free to ask!
