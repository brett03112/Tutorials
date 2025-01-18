Okay, here is a comprehensive Python tutorial that addresses the concepts you've listed, adhering to Python 3.12 and 3.13 best practices, and incorporating examples from Project Euler, Pygame, and data analysis.

**I. Fundamental Data Types**

* **1. Numbers**

  * **Integers (int):** Whole numbers without decimal points.

        ```python
        age = 30
        population = 7800000000
        ```

  * **Floating-Point Numbers (float):** Numbers with decimal points.

        ```python
        pi = 3.14159
        temperature = 25.5
        ```

  * **Complex Numbers (complex):** Numbers with real and imaginary parts.

        ```python
        z = 2 + 3j
        w = complex(4, -1)  # Another way to create complex numbers
        ```

  * **Numeric Operations:**

        ```python
        # Basic arithmetic
        sum_result = 10 + 5
        difference = 20 - 8
        product = 7 * 6
        quotient = 25 / 5  # Always returns a float
        floor_division = 25 // 6  # Returns the integer part of the division
        remainder = 17 % 5  # Modulo operator
        power = 2 ** 3  # Exponentiation

        # Built-in functions
        absolute_value = abs(-10)
        rounded_number = round(3.14159, 2)  # Round to 2 decimal places
        ```

  * **Project Euler Example (Problem 1: Multiples of 3 or 5):**

        ```python
        def sum_multiples(limit):
            total = 0
            for i in range(limit):
                if i % 3 == 0 or i % 5 == 0:
                    total += i
            return total

        print(sum_multiples(1000))  # Output: 233168
        ```

* **2. Strings (str)**

  * **Creating Strings:**

        ```python
        name = "Alice"
        message = 'Hello, world!'
        paragraph = """This is a
        multi-line string."""
        ```

  * **String Operations:**

        ```python
        # Concatenation
        greeting = "Hello" + " " + "world!"

        # Repetition
        repeated_string = "abc" * 3  # Output: "abcabcabc"

        # Indexing (0-based)
        first_char = name[0]  # Output: "A"
        last_char = name[-1]  # Output: "e"

        # Slicing
        substring = name[1:4]  # Output: "lic" (from index 1 up to, but not including, 4)

        # Length
        length = len(name)  # Output: 5

        # String methods (a few examples)
        uppercase_name = name.upper()
        lowercase_name = name.lower()
        is_alpha = name.isalpha()  # Check if all characters are letters
        replaced_string = message.replace("world", "Python")
        split_string = message.split(",")  # Split into a list of strings
        ```

  * **String Formatting:**
    * **f-strings (formatted string literals - recommended in Python 3.12 and 3.13):**

            ```python
            name = "Bob"
            age = 30
            print(f"My name is {name} and I am {age} years old.")

            # f-strings with expressions:
            print(f"The sum of 2 and 3 is {2 + 3}.")

            # f-strings with formatting:
            pi = 3.14159
            print(f"Pi rounded to 2 decimal places: {pi:.2f}")
            ```

    * **`str.format()` method (older style):**

            ```python
            print("My name is {} and I am {} years old.".format(name, age))
            ```

    * **%-formatting (very old style - avoid):**

            ```python
            print("My name is %s and I am %d years old." % (name, age))
            ```

  * **Data Analysis Example (basic string cleaning):**

        ```python
        text = "   This is a sentence with extra whitespace and mixed Case.   "

        cleaned_text = text.strip().lower()  # Remove leading/trailing whitespace, convert to lowercase
        print(cleaned_text)  # Output: "this is a sentence with extra whitespace and mixed case."
        ```

* **3. Booleans (bool)**

  * **Values:** `True` and `False`
  * **Logical Operators:**
    * `and`: Returns `True` if both operands are `True`.
    * `or`: Returns `True` if at least one operand is `True`.
    * `not`: Negates the boolean value.
  * **Comparison Operators:**
    * `==`: Equal to
    * `!=`: Not equal to
    * `>`: Greater than
    * `<`: Less than
    * `>=`: Greater than or equal to
    * `<=`: Less than or equal to

    ```python
    is_active = True
    is_admin = False

    if is_active and not is_admin:
        print("User is active but not an admin.")

    result = 5 > 2  # result will be True
    is_equal = "hello" == "hello"  # is_equal will be True
    ```

**II. Collections**

* **1. Lists**

  * **Creating Lists:** Ordered, mutable (changeable) sequences of items.

        ```python
        numbers = [1, 2, 3, 4, 5]
        names = ["Alice", "Bob", "Charlie"]
        mixed_list = [1, "hello", True, 3.14]
        ```

  * **List Operations:**

        ```python
        # Accessing elements (0-based indexing)
        first_number = numbers[0]  # Output: 1
        last_number = numbers[-1]  # Output: 5

        # Slicing
        sublist = numbers[1:4]  # Output: [2, 3, 4]

        # Modifying lists
        numbers[0] = 10
        numbers.append(6)  # Add to the end
        numbers.insert(2, 20)  # Insert 20 at index 2
        numbers.remove(3)  # Remove the first occurrence of 3
        deleted_element = numbers.pop()  # Remove and return the last element
        deleted_element = numbers.pop(1)  # Remove and return element at index 1

        # List length
        length = len(numbers)

        # Concatenation
        new_list = numbers + [7, 8, 9]

        # Repetition
        repeated_list = [1, 2] * 3  # Output: [1, 2, 1, 2, 1, 2]

        # Checking membership
        is_present = 3 in numbers

        # Iterating through a list
        for number in numbers:
            print(number)
        ```

  * **List Comprehensions:** A concise way to create lists.

        ```python
        # Create a list of squares
        squares = [x**2 for x in range(1, 6)]  # Output: [1, 4, 9, 16, 25]

        # Create a list of even numbers from another list
        even_numbers = [x for x in numbers if x % 2 == 0]
        ```

  * **Project Euler Example (Problem 2: Even Fibonacci Numbers):**

        ```python
        def even_fibonacci_sum(limit):
            fib_sequence = [1, 2]
            while fib_sequence[-1] + fib_sequence[-2] <= limit:
                fib_sequence.append(fib_sequence[-1] + fib_sequence[-2])
            even_sum = sum([x for x in fib_sequence if x % 2 == 0])
            return even_sum

        print(even_fibonacci_sum(4000000))  # Output: 4613732
        ```

* **2. Tuples**

  * **Creating Tuples:** Ordered, immutable sequences of items.

        ```python
        coordinates = (10, 20)
        rgb_color = (255, 0, 0)  # Red
        ```

  * **Tuple Operations:**

        ```python
        # Accessing elements
        x_coordinate = coordinates[0]  # Output: 10

        # Slicing (similar to lists)
        sub_tuple = coordinates[0:2]

        # Tuple length
        length = len(coordinates)

        # Concatenation
        new_tuple = coordinates + (30, 40)

        # Repetition
        repeated_tuple = (1, 2) * 3  # Output: (1, 2, 1, 2, 1, 2)

        # Checking membership
        is_present = 10 in coordinates

        # Immutability - you cannot modify a tuple after creation:
        # coordinates[0] = 5  # This would raise a TypeError
        ```

  * **Use Cases:**
    * Representing fixed collections of data.
    * Returning multiple values from a function.
    * Dictionary keys (since they must be immutable).

* **3. Dictionaries**

  * **Creating Dictionaries:** Unordered collections of key-value pairs. Keys must be unique and immutable (e.g., strings, numbers, tuples).

        ```python
        person = {
            "name": "Alice",
            "age": 30,
            "city": "New York"
        }

        student_grades = {
            "Bob": [85, 90, 92],
            "Charlie": [78, 88, 80]
        }
        ```

  * **Dictionary Operations:**

        ```python
        # Accessing values by key
        name = person["name"]  # Output: "Alice"
        age = person.get("age")  # Output: 30 (safer than using [], returns None if key not found)

        # Adding or updating key-value pairs
        person["occupation"] = "Engineer"
        person["age"] = 31

        # Removing key-value pairs
        del person["city"]
        removed_value = person.pop("occupation")  # Remove and return the value

        # Dictionary length
        length = len(person)

        # Checking membership (for keys)
        is_name_present = "name" in person

        # Iterating through a dictionary
        for key in person:  # Iterates over keys
            print(key, person[key])

        for value in person.values():  # Iterates over values
            print(value)

        for key, value in person.items():  # Iterates over key-value pairs
            print(key, value)
        ```

  * **Dictionary Comprehensions:**

        ```python
        # Create a dictionary that maps numbers to their squares
        squares_dict = {x: x**2 for x in range(1, 6)}  # Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
        ```

  * **Data Analysis Example (counting word frequencies):**

        ```python
        text = "this is a sample text with some repeated words this is a sample"
        words = text.split()
        word_counts = {}
        for word in words:
            word_counts[word] = word_counts.get(word, 0) + 1

        print(word_counts)
        # Output: {'this': 2, 'is': 2, 'a': 2, 'sample': 2, 'text': 1, 'with': 1, 'some': 1, 'repeated': 1, 'words': 1}
        ```

* **4. Sets**

  * **Creating Sets:** Unordered collections of unique items.

        ```python
        fruits = {"apple", "banana", "orange", "apple"}  # Duplicates are automatically removed
        print(fruits)  # Output: {'apple', 'banana', 'orange'} (order may vary)
        ```

  * **Set Operations:**

        ```python
        # Adding elements
        fruits.add("grape")
        fruits.update(["kiwi", "mango"])  # Add multiple elements

        # Removing elements
        fruits.remove("banana")  # Raises KeyError if element not found
        fruits.discard("kiwi")  # Does not raise an error if element not found

        # Set length
        length = len(fruits)

        # Checking membership
        is_apple_present = "apple" in fruits

        # Set operations (union, intersection, difference, etc.)
        set1 = {1, 2, 3}
        set2 = {3, 4, 5}

        union_set = set1 | set2  # or set1.union(set2)
        intersection_set = set1 & set2  # or set1.intersection(set2)
        difference_set = set1 - set2  # or set1.difference(set2)
        symmetric_difference_set = set1 ^ set2  # or set1.symmetric_difference(set2)
        ```

  * **Use Cases:**
    * Removing duplicates from a list.
    * Checking for membership efficiently.
    * Performing mathematical set operations.

**III. Date and Time**

* **`datetime` module:** The primary module for working with dates and times in Python.

    ```python
    import datetime

    # Current date and time
    now = datetime.datetime.now()
    print(now)

    # Specific date and time
    specific_date = datetime.datetime(2023, 10, 27, 10, 30, 0)  # Year, month, day, hour, minute, second
    print(specific_date)

    # Date only
    today = datetime.date.today()
    print(today)

    # Time only
    current_time = datetime.time(14, 15, 30)  # Hour, minute, second
    print(current_time)

    # Formatting date and time
    formatted_date = now.strftime("%Y-%m-%d %H:%M:%S")  # Using strftime codes
    print(formatted_date)

    # Parsing date and time from a string
    date_string = "2023-10-27 10:30:00"
    parsed_date = datetime.datetime.strptime(date_string, "%Y-%m-%d %H:%M:%S")
    print(parsed_date)

    # Date/time arithmetic
    time_difference = now - specific_date
    print(time_difference)
    print(time_difference.days)
    print(time_difference.seconds)

    future_date = now + datetime.timedelta(days=7)  # Add 7 days
    print(future_date)
    ```

* **Pygame Example (displaying a timer):**

    ```python
    import pygame
    import datetime

    pygame.init()

    # ... (Pygame setup code) ...

    font = pygame.font.Font(None, 36)

    start_time = datetime.datetime.now()

    running = True
    while running:
        # ... (Pygame event handling) ...

        elapsed_time = datetime.datetime.now() - start_time
        elapsed_seconds = int(elapsed_time.total_seconds())

        timer_text = font.render(f"Time: {elapsed_seconds}", True, (255, 255, 255))
        screen.blit(timer_text, (10, 10))

        pygame.display.flip()

    pygame.quit()
    ```

**IV. Control Flow**

* **1. Conditional Statements (if-elif-else)**

    ```python
    age = 20

    if age >= 18:
        print("You are an adult.")
    elif age >= 13:
        print("You are a teenager.")
    else:
        print("You are a child.")

    # More complex conditions
    is_raining = True
    temperature = 25

    if is_raining and temperature < 15:
        print("Wear a raincoat.")
    elif is_raining:
        print("Bring an umbrella.")
    else:
        print("Enjoy the weather!")
    ```

* **2. Loops**

  * **`for` loops:** Iterate over sequences (lists, tuples, strings, dictionaries, etc.) or other iterable objects.

        ```python
        # Iterate over a list
        numbers = [1, 2, 3, 4, 5]
        for number in numbers:
            print(number)

        # Iterate over a string
        name = "Alice"
        for char in name:
            print(char)

        # Iterate over a dictionary
        person = {"name": "Bob", "age": 30}
        for key, value in person.items():
            print(key, value)

        # Use range() for a sequence of numbers
        for i in range(5):  # 0, 1, 2, 3, 4
            print(i)

        for i in range(2, 10, 2):  # Start at 2, end before 10, step by 2 (2, 4, 6, 8)
            print(i)
        ```

  * **`while` loops:** Repeat as long as a condition is `True`.

        ```python
        count = 0
        while count < 5:
            print(count)
            count += 1

        # Example: Keep asking for input until valid
        while True:
            user_input = input("Enter a positive number: ")
            if user_input.isdigit() and int(user_input) > 0:
                break  # Exit the loop if input is valid
            else:
                print("Invalid input. Please try again.")
        ```

* **3. `break` and `continue` Statements**

  * **`break`:** Exits the innermost loop immediately.
  * **`continue`:** Skips the rest of the current iteration and goes to the next iteration of the loop.

    ```python
    # Example with break
    numbers = [1, 2, 3, 4, 5]
    for number in numbers:
        if number == 3:
            break  # Stop the loop when 3 is encountered
        print(number)  # Output: 1 2

    # Example with continue
    numbers = [1, 2, 3, 4, 5]
    for number in numbers:
        if number % 2 == 0:
            continue  # Skip even numbers
        print(number)  # Output: 1 3 5
    ```

* **4. `else` Clause with Loops**

  * The `else` block after a `for` or `while` loop executes only if the loop finishes normally (i.e., without encountering a `break` statement).

    ```python
    # Example with for-else
    numbers = [1, 2, 4, 5]
    for number in numbers:
        if number == 3:
            print("Number 3 found!")
            break
    else:
        print("Number 3 not found in the list.")  # This will execute

    # Example with while-else
    count = 0
    while count < 5:
        if count == 6:
            break
        count += 1
    else:
        print("Loop finished normally.")  # This will execute
    ```

**V. Functions**

* **Defining Functions:**

    ```python
    def greet(name):
      """This function greets the person passed in as a parameter."""
      print(f"Hello, {name}!")

    def add_numbers(x, y):
      """This function adds two numbers and returns the sum."""
      sum_result = x + y
      return sum_result

    def is_even(number):
        """
        This function checks if a number is even.
        Returns True if even, False otherwise.
        """
        return number % 2 == 0  # Concise way to return a boolean
    ```

* **Calling Functions:**

    ```python
    greet("Alice")  # Output: Hello, Alice!
    result = add_numbers(5, 3)  # result will be 8
    print(result)
    
    if is_even(4):
        print("4 is even")
    ```

* **Function Arguments:**

  * **Positional Arguments:** Passed in the order they are defined.

        ```python
        def describe_person(name, age):
            print(f"{name} is {age} years old.")

        describe_person("Bob", 30)  # "Bob" is assigned to name, 30 to age
        ```

  * **Keyword Arguments:** Passed with the name of the parameter.

        ```python
        describe_person(age=25, name="Alice")  # Order doesn't matter
        ```

  * **Default Arguments:** Provide default values for parameters.

        ```python
        def greet(name, greeting="Hello"):
            print(f"{greeting}, {name}!")

        greet("Bob")  # Output: Hello, Bob!
        greet("Alice", "Hi")  # Output: Hi, Alice!
        ```

  * **Arbitrary Positional Arguments (`*args`)**: Allows a function to accept any number of positional arguments. `args` becomes a tuple inside the function.

        ```python
        def sum_all_numbers(*args):
            total = 0
            for number in args:
                total += number
            return total

        print(sum_all_numbers(1, 2, 3, 4, 5))  # Output: 15
        print(sum_all_numbers(10, 20))  # Output: 30
        ```

  * **Arbitrary Keyword Arguments (`**kwargs`)**: Allows a function to accept any number of keyword arguments. `kwargs` becomes a dictionary inside the function.

        ```python
        def describe_student(**kwargs):
            for key, value in kwargs.items():
                print(f"{key}: {value}")

        describe_student(name="Alice", age=20, major="Computer Science")
        # Output:
        # name: Alice
        # age: 20
        # major: Computer Science
        ```

* **Scope:**
  * **Local Scope:** Variables defined inside a function are local to that function.
  * **Global Scope:** Variables defined outside any function are global.
  * **`global` Keyword:** Used inside a function to modify a global variable.

    ```python
    x = 10  # Global variable

    def my_function():
        y = 5  # Local variable
        global x
        x = 20  # Modifies the global x
        print(f"Inside function: x = {x}, y = {y}")

    my_function()
    print(f"Outside function: x = {x}")  # x is now 20
    ```

* **Lambda Functions (Anonymous Functions):** Small, single-line functions defined using the `lambda` keyword.

    ```python
    # Regular function to square a number
    def square(x):
        return x * x

    # Equivalent lambda function
    square_lambda = lambda x: x * x

    print(square(5))  # Output: 25
    print(square_lambda(5))  # Output: 25

    # Lambda function with multiple arguments
    add = lambda x, y: x + y
    print(add(2, 3))  # Output: 5

    # Use cases:
    # - Short, simple operations that you don't want to define as separate functions.
    # - As arguments to higher-order functions (functions that take other functions as arguments) like map, filter, sorted.
    ```

**VI. Comprehensions (expanded)**

   Comprehensions provide a very concise and readable way to create lists, dictionaries, and sets. They are generally preferred over traditional `for` loops for creating these collections when the logic is relatively straightforward.

* **List Comprehensions:**

        ```python
        # Basic list comprehension (squares of numbers)
        numbers = [1, 2, 3, 4, 5]
        squares = [x**2 for x in numbers]  # Output: [1, 4, 9, 16, 25]

        # List comprehension with a conditional (even squares)
        even_squares = [x**2 for x in numbers if x % 2 == 0]  # Output: [4, 16]

        # List comprehension with if-else (ternary operator)
        results = ["Even" if x % 2 == 0 else "Odd" for x in numbers]  # Output: ['Odd', 'Even', 'Odd', 'Even', 'Odd']

        # Nested list comprehension (create a matrix)
        matrix = [[i * j for j in range(3)] for i in range(3)]
        # Output: [[0, 0, 0], [0, 1, 2], [0, 2, 4]]
        ```

* **Dictionary Comprehensions:**

        ```python
        # Basic dictionary comprehension (number to square mapping)
        squares_dict = {x: x**2 for x in range(1, 6)}  # Output: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}

        # Dictionary comprehension with conditional
        even_squares_dict = {x: x**2 for x in range(1, 6) if x % 2 == 0}  # Output: {2: 4, 4: 16}

        # Dictionary comprehension from two lists (zipping)
        keys = ["a", "b", "c"]
        values = [1, 2, 3]
        my_dict = {k: v for k, v in zip(keys, values)}  # Output: {'a': 1, 'b': 2, 'c': 3}
        ```

* **Set Comprehensions:**

        ```python
        # Basic set comprehension (unique squares)
        numbers = [1, 1, 2, 2, 3, 3, 4, 4, 5, 5]
        unique_squares = {x**2 for x in numbers}  # Output: {1, 4, 9, 16, 25}

        # Set comprehension with conditional
        even_unique_squares = {x**2 for x in numbers if x % 2 == 0}  # Output: {4, 16}
        ```

* **Generator Expressions:**

  * Similar to list comprehensions but create a generator object instead of a list in memory.
  * Generators produce values on demand, making them memory-efficient for large sequences.
  * Created using parentheses `()` instead of square brackets `[]`.

        ```python
        numbers = [1, 2, 3, 4, 5]

        # Generator expression for squares
        squares_gen = (x**2 for x in numbers)

        # Iterate through the generator
        for square in squares_gen:
            print(square)  # Output: 1 4 9 16 25 (one at a time)

        # You can convert a generator to a list if needed (but be mindful of memory usage)
        squares_list = list(squares_gen)
        ```

**VII. Modules and Packages**

* **Modules:** Files containing Python definitions (variables, functions, classes).
* **Packages:** Collections of modules organized in a directory hierarchy. A package must contain an `__init__.py` file (can be empty).
* **Importing Modules:**

    ```python
    import math  # Import the entire math module

    print(math.sqrt(16))  # Use the sqrt() function from the math module

    from math import sqrt, pi  # Import specific items

    print(sqrt(25))  # Now you can use sqrt() directly
    print(pi)

    from math import *  # Import everything (generally discouraged)

    import math as m  # Import with an alias

    print(m.sqrt(9))
    ```

* **Creating Your Own Modules:**
    1. Create a Python file (e.g., `my_module.py`) with your functions, classes, etc.

        ```python
        # my_module.py
        def my_function():
            print("Hello from my_module!")

        PI = 3.14159
        ```

    2. Import and use it in another file:

        ```python
        # main.py
        import my_module

        my_module.my_function()
        print(my_module.PI)
        ```

* **Creating Your Own Packages:**
    1. Create a directory for your package (e.g., `my_package`).
    2. Inside the directory, create an `__init__.py` file (can be empty).
    3. Create your module files inside the package directory (e.g., `module1.py`, `module2.py`).

        ```
        my_package/
        ├── __init__.py
        ├── module1.py
        └── module2.py
        ```

    4. Import and use it:

        ```python
        # main.py
        from my_package import module1

        module1.some_function()
        ```

**VIII. Error Handling**

* **Exceptions:** Errors that occur during program execution.
* **`try-except` Blocks:** Handle exceptions gracefully.
* **`else` and `finally` Clauses:**
  * `else`: Code that runs if no exception occurred in the `try` block.
  * `finally`: Code that always runs, whether an exception occurred or not (used for cleanup).
* **Raising Exceptions:** Use the `raise` keyword to signal errors.

```python
def divide(x, y):
    try:
        result = x / y
    except ZeroDivisionError:
        print("Error: Cannot divide by zero!")
        return None  # Or handle the error in some other way
    except TypeError:
        print("Error: Invalid data types for division.")
        return None
    else:
        print("Division successful.")
        return result
    finally:
        print("This always runs.")

# Example usage
print(divide(10, 2))
print(divide(10, 0))
print(divide("a", 2))

# Raising a custom exception
def validate_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative.")

try:
    validate_age(-5)
except ValueError as e:
    print(e)
```

* **Common Exception Types:**
  * `ZeroDivisionError`: Division by zero.
  * `TypeError`: Invalid operation for a data type.
  * `ValueError`: Invalid value for a function.
  * `IndexError`: List index out of range.
  * `KeyError`: Dictionary key not found.
  * `FileNotFoundError`: File not found.
  * `IOError`: Input/output error.
  * `ImportError`: Module import error.

**IX. Object-Oriented Programming (OOP)**

* **Classes:** Blueprints for creating objects. Define attributes (data) and methods (functions) that objects of the class will have.
* **Objects (Instances):** Specific instances of a class.
* **`__init__` method (Constructor):** Initializes the object's attributes when an object is created.
* **`self`:** Refers to the current instance of the class within methods.

```python
class Dog:
    species = "Canis familiaris"  # Class attribute (shared by all instances)

    def __init__(self, name, age):
        self.name = name  # Instance attribute (specific to each instance)
        self.age = age

    def description(self):  # Instance method
        return f"{self.name} is {self.age} years old"

    def speak(self, sound):
        return f"{self.name} says {sound}"

# Create objects (instances) of the Dog class
buddy = Dog("Buddy", 3)
miles = Dog("Miles", 5)

# Access attributes
print(buddy.name)  # Output: Buddy
print(miles.age)  # Output: 5
print(Dog.species)  # Output: Canis familiaris (accessing class attribute)

# Call methods
print(buddy.description())  # Output: Buddy is 3 years old
print(miles.speak("Woof!"))  # Output: Miles says Woof!
```

* **Inheritance:** Creating new classes (child classes/subclasses) based on existing classes (parent classes/superclasses). Child classes inherit attributes and methods from the parent class and can add their own or override existing ones.

```python
# Parent class (base class)
class Animal:
    def __init__(self, name):
        self.name = name

    def speak(self):
        print("Generic animal sound")

# Child class (derived class) inheriting from Animal
class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)  # Call the __init__ method of the parent class
        self.breed = breed

    def speak(self):  # Override the speak() method
        print("Woof!")

# Another child class
class Cat(Animal):
    def speak(self):
        print("Meow!")

# Create objects
buddy = Dog("Buddy", "Golden Retriever")
whiskers = Cat("Whiskers")

# Use inherited and overridden methods
buddy.speak()  # Output: Woof! (overridden method)
whiskers.speak()  # Output: Meow! (overridden method)
```

* **Polymorphism:** The ability of objects of different classes to respond to the same method call in their own way.

    ```python

   Okay, let's continue building out the Python tutorial, picking up where we left off with polymorphism in OOP:

```python
    # Using the Animal, Dog, and Cat classes from the previous example

    animals = [Dog("Buddy", "Golden Retriever"), Cat("Whiskers"), Animal("Generic")]

    for animal in animals:
        print(f"{animal.name}: ", end="")
        animal.speak()  # Each animal responds to speak() differently
        # Output:
        # Buddy: Woof!
        # Whiskers: Meow!
        # Generic: Generic animal sound
    ```

*   **Method Overriding:** In inheritance, when a child class defines a method with the same name as a method in the parent class, the child class's method overrides the parent's method.

*   **`super()` function:** Used in a child class to call methods or access attributes from the parent class.

```python
class Rectangle:
    def __init__(self, length, width):
        self.length = length
        self.width = width

    def area(self):
        return self.length * self.width

class Square(Rectangle):
    def __init__(self, side):
        super().__init__(side, side)  # Call the parent's __init__ to set length and width

# Example
square = Square(5)
print(square.area())  # Output: 25 (using the area() method inherited from Rectangle)
```

* **Multiple Inheritance:** A class can inherit from multiple parent classes. This can be powerful but can also lead to complexity (e.g., the "diamond problem").

```python
class A:
    def method(self):
        print("A method")

class B:
    def method(self):
        print("B method")

class C(A, B):  # Inherits from both A and B
    pass

class D(B, A):  # Inherits from both B and A, but in a different order
    pass

obj_c = C()
obj_c.method()  # Output: A method (Method Resolution Order - MRO - determines which method is called)

obj_d = D()
obj_d.method()  # Output: B method
```

* **Abstract Base Classes (ABCs):**
  * Used to define a common interface for a set of subclasses.
  * Cannot be instantiated directly.
  * May contain abstract methods (methods without implementation) that subclasses *must* implement.
  * Use the `abc` module to define ABCs.

    ```python
    import abc

    class Shape(abc.ABC):  # Inherit from abc.ABC to create an abstract base class
        @abc.abstractmethod
        def area(self):
            pass  # No implementation in the abstract method

        @abc.abstractmethod
        def perimeter(self):
            pass

    class Rectangle(Shape):
        def __init__(self, length, width):
            self.length = length
            self.width = width

        def area(self):
            return self.length * self.width

        def perimeter(self):
            return 2 * (self.length + self.width)

    class Circle(Shape):
        def __init__(self, radius):
            self.radius = radius

        def area(self):
            return 3.14159 * self.radius * self.radius

        def perimeter(self):
            return 2 * 3.14159 * self.radius

    # shape = Shape()  # This would raise a TypeError because Shape is an ABC

    rect = Rectangle(5, 10)
    circle = Circle(7)

    print(rect.area())
    print(circle.perimeter())
    ```

**X. Input and Output**

* **1. Console Input (`input`)**

    ```python
    name = input("Enter your name: ")
    print(f"Hello, {name}!")

    age_str = input("Enter your age: ")
    age = int(age_str)  # Convert the input string to an integer
    print(f"You are {age} years old.")
    ```

* **2. Console Output (`print`)**

    ```python
    print("Hello, world!")  # Basic output

    x = 10
    y = 20
    print("The sum of", x, "and", y, "is", x + y)  # Printing multiple values

    # Using f-strings (formatted string literals)
    print(f"The sum of {x} and {y} is {x + y}")

    # Specifying a separator (default is a space)
    print("apple", "banana", "orange", sep=", ")  # Output: apple, banana, orange

    # Specifying an end character (default is a newline)
    print("Loading", end="...")
    print("Done!")  # Output: Loading...Done!
    ```

* **3. File Input/Output**

  * **Opening Files:** Use the `open()` function. Modes:
    * `"r"`: Read (default).
    * `"w"`: Write (creates a new file or overwrites an existing one).
    * `"a"`: Append (adds to the end of an existing file or creates a new one).
    * `"x"`: Create (creates a new file, returns an error if it already exists).
    * `"b"`: Binary mode (for non-text files like images).
    * `"t"`: Text mode (default).
    * `"+"`: Update (reading and writing).

  * **Reading from Files:**

        ```python
        # Method 1: Read the entire file as a single string
        with open("my_file.txt", "r") as file:
            contents = file.read()
            print(contents)

        # Method 2: Read line by line
        with open("my_file.txt", "r") as file:
            for line in file:
                print(line, end="")  # Print each line (line already includes newline)

        # Method 3: Read all lines into a list
        with open("my_file.txt", "r") as file:
            lines = file.readlines()
            for line in lines:
                print(line, end="")

        # Method 4: Read a specific number of characters
        with open("my_file.txt", "r") as file:
            chunk = file.read(10)  # Read the first 10 characters
            print(chunk)
        ```

  * **Writing to Files:**

        ```python
        # Write a single string
        with open("output.txt", "w") as file:
            file.write("Hello, file!\n")
            file.write("This is another line.\n")

        # Write a list of strings
        lines_to_write = ["Line 1", "Line 2", "Line 3"]
        with open("output.txt", "w") as file:
            file.writelines(line + "\n" for line in lines_to_write)  # Add newline to each line
        ```

  * **`with` statement:** Ensures that the file is automatically closed even if errors occur (recommended way to work with files).

* **4. Working with CSV Files**

  * Use the `csv` module to easily read and write CSV (Comma Separated Values) files.

        ```python
        import csv

        # Reading from a CSV file
        with open("data.csv", "r") as file:
            reader = csv.reader(file)
            for row in reader:
                print(row)  # Each row is a list of strings

        # Reading into a list of dictionaries
        with open("data.csv", "r") as file:
            reader = csv.DictReader(file)
            for row in reader:
                print(row)  # Each row is a dictionary

        # Writing to a CSV file
        data_to_write = [
            ["Name", "Age", "City"],
            ["Alice", "30", "New York"],
            ["Bob", "25", "Los Angeles"],
        ]

        with open("output.csv", "w", newline="") as file:  # newline="" is important on Windows
            writer = csv.writer(file)
            writer.writerows(data_to_write)

        # Writing from a list of dictionaries
        fieldnames = ["Name", "Age", "City"]
        data_to_write = [
            {"Name": "Alice", "Age": "30", "City": "New York"},
            {"Name": "Bob", "Age": "25", "City": "Los Angeles"},
        ]

        with open("output.csv", "w", newline="") as file:
            writer = csv.DictWriter(file, fieldnames=fieldnames)
            writer.writeheader()  # Write the header row
            writer.writerows(data_to_write)
        ```

* **5. Working with JSON Files**

  * Use the `json` module to read and write JSON (JavaScript Object Notation) data.

        ```python
        import json

        # Reading from a JSON file
        with open("data.json", "r") as file:
            data = json.load(file)
            print(data)

        # Writing to a JSON file
        data_to_write = {
            "name": "Alice",
            "age": 30,
            "city": "New York",
        }

        with open("output.json", "w") as file:
            json.dump(data_to_write, file, indent=4)  # Use indent for pretty printing
        ```

**XI. Formatting Input and Output (more details)**

* **1. f-strings (Formatted String Literals)**

  * Most versatile and readable way to format strings in modern Python.
  * Embed expressions, variables, and formatting specifications directly within the string.

    ```python
    name = "Alice"
    age = 30
    pi = 3.141592653589793

    # Basic f-string
    print(f"My name is {name} and I am {age} years old.")

    # Expressions inside f-strings
    print(f"The sum of 2 and 3 is {2 + 3}.")

    # Formatting numbers:
    print(f"Pi rounded to 2 decimal places: {pi:.2f}")  # Floating-point, 2 decimal places
    print(f"Age in hexadecimal: {age:#x}")  # Hexadecimal with 0x prefix
    print(f"A large number with commas: {1234567890:,}")  # Comma as thousands separator

    # Formatting strings:
    print(f"Name left-aligned: {name:<10}")  # Left-align within 10 spaces
    print(f"Name right-aligned: {name:>10}")  # Right-align within 10 spaces
    print(f"Name centered: {name:^10}")  # Center within 10 spaces

    # Padding with a specific character:
    print(f"Number padded with zeros: {age:05}")  # Pad with zeros to a width of 5

    # Dates and times:
    import datetime
    now = datetime.datetime.now()
    print(f"Current date and time: {now:%Y-%m-%d %H:%M:%S}")

    # Using f-strings with dictionaries:
    person = {"name": "Bob", "age": 25}
    print(f"Name: {person['name']}, Age: {person['age']}")
    ```

* **2. `str.format()` Method**

  * Older way of formatting strings, still useful in some cases.

    ```python
    name = "Alice"
    age = 30

    # Positional arguments
    print("My name is {} and I am {} years old.".format(name, age))

    # Named arguments
    print("My name is {name} and I am {age} years old.".format(name=name, age=age))

    # Formatting specifications
    print("Pi rounded to 2 decimal places: {:.2f}".format(pi))
    ```

* **3. %-formatting (Old Style)**
  * Very old style of string formatting, generally **avoid** in favor of f-strings or `str.format()`.

    ```python
    name = "Alice"
    age = 30
    print("My name is %s and I am %d years old." % (name, age))
    ```

**XII. Iterators and Generators**

* **1. Iterators**
  * Objects that allow you to traverse a container (like a list, string, etc.) and access its elements one at a time.
  * Implement the **iterator protocol**:
    * `__iter__()` method: Returns the iterator object itself.
    * `__next__()` method: Returns the next item in the sequence. Raises `StopIteration` when there are no more items.

    ```python
    my_list = [1, 2, 3]
    my_iter = iter(my_list)  # Get an iterator object from the list

    print(next(my_iter))  # Output: 1
    print(next(my_iter))  # Output: 2
    print(next(my_iter))  # Output: 3
    # print(next(my_iter))  # Raises StopIteration error
    ```

  * Many built-in functions and language constructs work with iterators behind the scenes (e.g., `for` loops, `in` operator, `sum()`, `min()`, `max()`, etc.).

* **2. Generators**
  * Special type of iterator that is defined using a function with the `yield` keyword.
  * Generate values on demand, making them memory-efficient, especially for large sequences.
  * When a generator function is called, it returns a generator object.
  * The generator object's `__next__()` method executes the function's code up to the next `yield` statement, returns the yielded value, and pauses execution. The next time `__next__()` is called, execution resumes from where it left off.

    ```python
    def my_generator(n):
        for i in range(n):
            yield i * 2

    gen = my_generator(3)  # Create a generator object
    print(next(gen))  # Output: 0
    print(next(gen))  # Output: 2
    print(next(gen))  # Output: 4
    # print(next(gen))  # Raises StopIteration

    # Using a generator in a for loop
    for x in my_generator(5):
        print(x)
    ```

  * **Generator Expressions:** Similar to list comprehensions, but create a generator object using parentheses `()` instead of square brackets `[]`.

        ```python
        squares = (x**2 for x in range(10))  # Generator expression

        for square in squares:
            print(square)
        ```

  * **Use Cases for Generators:**
    * Working with very large datasets that don't fit in memory.
    * Creating infinite sequences.
    * Pipelining data processing operations (chaining generators together).

**XIII. Python Standard Library (Selected Modules)**

The Python Standard Library is a vast collection of modules that provide a wide range of functionality. Here are some of the most commonly used ones:

* **1. `math`:** Mathematical functions.

    ```python
    import math

    print(math.sqrt(25))  # Square root
    print(math.sin(math.pi / 2))  # Sine
    print(math.cos(0))  # Cosine
    print(math.log(10))  # Natural logarithm
    print(math.log10(100))  # Base-10 logarithm
    print(math.factorial(5))  # Factorial
    print(math.gcd(12, 18))  # Greatest common divisor
    ```

* **2. `random`:** Pseudo-random number generation.

    ```python
    import random

    print(random.random())  # Random float between 0.0 and 1.0
    print(random.randint(1, 10))  # Random integer between 1 and 10 (inclusive)
    print(random.choice(["apple", "banana", "orange"]))  # Random element from a sequence
    my_list = [1, 2, 3, 4, 5]
    random.shuffle(my_list)  # Shuffle a list in place
    print(my_list)
    print(random.sample(my_list, 2))  # Get 2 random elements from the list
    ```

* **3. `datetime`:** (Covered earlier) Date and time manipulation.

* **4. `os`:** Operating system interface.

    ```python
    import os

    print(os.getcwd())  # Get current working directory
    # os.mkdir("new_directory")  # Create a new directory
    # os.rename("old_name.txt", "new_name.txt")  # Rename a file
    # os.remove("file.txt")  # Delete a file
    # os.rmdir("directory")  # Delete an empty directory
    print(os.path.exists("my_file.txt"))  # Check if a file or directory exists
    print(os.path.isfile("my_file.txt"))  # Check if it's a file
    print(os.path.isdir("my_directory"))  # Check if it's a directory
    print(os.path.join("folder", "subfolder", "file.txt"))  # Join path components
    ```

* **5. `sys`:** System-specific parameters and functions.

    ```python
    import sys

    print(sys.argv)  # List of command-line arguments
    # sys.exit()  # Exit the program
    print(sys.version)  # Python version information
    print(sys.platform)  # Operating system platform
    ```

* **6. `re`:** Regular expressions.

    ```python
    import re

    text = "My phone number is 123-456-7890 and my email is test@example.com."

    # Find all numbers
    numbers = re.findall(r"\d+", text)  # \d+ matches one or more digits
    print(numbers)  # Output: ['123', '456', '7890']

    # Find a phone number pattern
    phone_number = re.search(r"\d{3}-\d{3}-\d{4}", text)
    if phone_number:
        print(phone_number.group(0))  # Output: 123-456-7890

    # Replace email with a masked version
    masked_email = re.sub(r"[\w.-]+@[\w.-]+", "[email protected]", text)
    print(masked_email)
    ```

* **7. `json`:** (Covered earlier) JSON encoding and decoding.

* **8. `csv`:** (Covered earlier) CSV file reading and writing.

* **9. `collections`:** Specialized container datatypes.
  * `namedtuple`: Creates tuple-like objects with named fields.
  * `deque`: Double-ended queue (efficient for adding/removing from both ends).
  * `Counter`: Dictionary for counting the frequency of items.
  * `OrderedDict`: Dictionary that remembers the order of insertion.
  * `defaultdict`: Dictionary that provides default values for missing keys.

    ```python
    from collections import namedtuple, deque, Counter, OrderedDict, defaultdict

    # namedtuple
    Point = namedtuple("Point", ["x", "y"])
    p = Point(1, 2)
    print(p.x, p.y)

    # deque
    d = deque([1, 2, 3])
    d.appendleft(0)
    d.append(4)
    print(d)

    # Counter
    c = Counter("abracadabra")
    print(c)
    print(c.most_common(2))

    # OrderedDict
    od = OrderedDict()
    od["a"] = 1
    od["b"] = 2
    od["c"] = 3
    print(od)

    # defaultdict
    dd = defaultdict(int)  # Default value is 0
    dd["a"] += 1
    dd["b"] += 5
    print(dd)
    ```

* **10. `itertools`:** Functions for creating and working with iterators.

    ```python
    import itertools

    # Infinite iterator (count from 10 with a step of 2)
    for i in itertools.count(10, 2):
        if i > 20:
            break
        print(i)

    # Cycle through a sequence repeatedly
    for item in itertools.cycle(["a", "b", "c"]):
        if item == "c":
            break
        print(item)

    # Repeat an item
    for item in itertools.repeat("hello", 3):
        print(item)

    # Chain iterables together
    list1 = [1, 2]
    list2 = [3, 4]
    for item in itertools.chain(list1, list2):
        print(item)

    # Combinations
    for item in itertools.combinations([1, 2, 3], 2):
        print(item)

    # Permutations
    for item in itertools.permutations([1, 2, 3], 2):
        print(item)
    ```

* **11. `functools`:** Higher-order functions and operations on callable objects.
  * `partial`: Create a new function with some arguments pre-filled.
  * `reduce`: Apply a function cumulatively to the items of an iterable.
  * `lru_cache`: Cache the results of a function (memoization).

    ```python
    from functools import partial, reduce, lru_cache

    # partial
    def power(base, exponent):
        return base ** exponent

    square = partial(power, exponent=2)  # Create a new function that calculates squares
    cube = partial(power, exponent=3)  # Create a new function that calculates cubes

    print(square(5))  # Output: 25
    print(cube(5))  # Output: 125

    # reduce
    numbers = [1, 2, 3, 4, 5]
    sum_of_numbers = reduce(lambda x, y: x + y, numbers)  # Calculate the sum
    print(sum_of_numbers)  # Output: 15

    # lru_cache
    @lru_cache(maxsize=None)  # Cache all results
    def fibonacci(n):
        if n <= 1:
            return n
        return fibonacci(n - 1) + fibonacci(n - 2)

    print(fibonacci(10))  # Calculates and caches the result
    print(fibonacci(10))  # Retrieves the result from the cache (much faster)
    ```

* **12. `urllib`:** (For working with URLs - making requests, handling data, etc.)

* **13. `sqlite3`:** (For interacting with SQLite databases)

* **14. `pickle` and `shelve`:** (For serializing and persisting Python objects)

* **15. `time`:** (For time-related functions, pausing execution, etc.)

**XIV. Examples**

* **1. Project Euler**
  * **Problem 1: Multiples of 3 or 5 (revisited with iterators/generators)**

        ```python
        def multiples_of_3_or_5(limit):
            for i in range(limit):
                if i % 3 == 0 or i % 5 == 0:
                    yield i

        print(sum(multiples_of_3_or_5(1000)))
        ```

  * **Problem 7: 10001st Prime**

        ```python
        def is_prime(num):
            if num <= 1:
                return False
            if num <= 3:
                return True
            if num % 2 == 0 or num % 3 == 0:
                return False
            i = 5
            while i * i <= num:
                if num % i == 0 or num % (i + 2) == 0:
                    return False
                i += 6
            return True

        def nth_prime(n):
            count = 0
            num = 2
            while True:
                if is_prime(num):
                    count += 1
                    if count == n:
                        return num
                num += 1

        print(nth_prime(10001))
        ```

* **2. Pygame**
  * **Simple Pygame Window:**

        ```python
        import pygame

        # Initialize Pygame
        pygame.init()

        # Set window dimensions
        width = 800
        height = 600

        # Create the window
        screen = pygame.display.set_mode((width, height))

        # Set title
        pygame.display.set_caption("My Pygame Window")

        # Fill the background with white
        background_color = (255, 255, 255)  # RGB for white
        screen.fill(background_color)

        # Update the display
        pygame.display.flip()

        # Game loop
        running = True
        while running:
            # Handle events
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    running = False

        # Quit Pygame
        pygame.quit()
        ```

  * **Drawing Shapes:**

        ```python
        import pygame

        pygame.init()

        width = 800
        height = 600
        screen = pygame.display.set_mode((width, height))
        pygame.display.set_caption("Drawing Shapes")

        # Colors
        black = (0, 0, 0)
        white = (255, 255, 255)
        red = (255, 0, 0)
        green = (0, 255, 0)
        blue = (0, 0, 255)

        screen.fill(white)

        # Rectangle
        pygame.draw.rect(screen, red, (50, 50, 100, 50))  # Surface, color, (x, y, width, height)

        # Circle
        pygame.draw.circle(screen, green, (200, 200), 30)  # Surface, color, (center_x, center_y), radius

        # Line
        pygame.draw.line(screen, blue, (300, 50), (300, 200), 5)  # Surface, color, (start_x, start_y), (end_x, end_y), width

        # Polygon
        pygame.draw.polygon(screen, black, [(400, 100), (500, 50), (600, 150)])

        pygame.display.flip()

        running = True
        while running:
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    running = False

        pygame.quit()
        ```

  * **Displaying Text:**

        ```python
        import pygame

        pygame.init()

        width = 800
        height = 600
        screen = pygame.display.set_mode((width, height))
        pygame.display.set_caption("Displaying Text")

        white = (255, 255, 255)
        black = (0, 0, 0)

        screen.fill(white)

        # Font object
        font = pygame.font.Font(None, 36)  # Default font, size 36

        # Render text
        text_surface = font.render("Hello, Pygame!", True, black)  # Text, antialiasing, color

        # Get text rectangle
        text_rect = text_surface.get_rect()

        # Center the text
        text_rect.center = (width // 2, height // 2)

        # Blit (draw) the text onto the screen
        screen.blit(text_surface, text_rect)

        pygame.display.flip()

        running = True
        while running:
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    running = False

        pygame.quit()
        ```

  * **Handling Keyboard and Mouse Input:**

        ```python
        import pygame

        pygame.init()

        width = 800
        height = 600
        screen = pygame.display.set_mode((width, height))
        pygame.display.set_caption("Input Handling")

        white = (255, 255, 255)
        black = (0, 0, 0)

        x = width // 2
        y = height // 2

        screen.fill(white)

        running = True
        while running:
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    running = False
                elif event.type == pygame.KEYDOWN:  # Key pressed
                    if event.key == pygame.K_LEFT:
                        x -= 10
                    elif event.key == pygame.K_RIGHT:
                        x += 10
                    elif event.key == pygame.K_UP:
                        y -= 10
                    elif event.key == pygame.K_DOWN:
                        y += 10
                elif event.type == pygame.MOUSEBUTTONDOWN:  # Mouse button clicked
                    if event.button == 1:  # Left mouse button
                        x, y = pygame.mouse.get_pos()  # Get mouse coordinates

            screen.fill(white)
            pygame.draw.circle(screen, black, (x, y), 20)
            pygame.display.flip()

        pygame.quit()
        ```

  * **Simple Animation:**

        ```python
        import pygame

        pygame.init()

        width = 800
        height = 600
        screen = pygame.display.set_mode((width, height))
        pygame.display.set_caption("Simple Animation")

        white = (255, 255, 255)
        black = (0, 0, 0)

        x = 50
        y = 50
        x_speed = 5

        clock = pygame.time.Clock()  # Create a clock object

        running = True
        while running:
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    running = False

            # Move the circle
            x += x_speed
            if x > width - 20 or x < 20:
                x_speed = -x_speed  # Reverse direction

            screen.fill(white)
            pygame.draw.circle(screen, black, (x, y), 20)
            pygame.display.flip()

            clock.tick(60)  # Limit to 60 frames per second

        pygame.quit()
        ```

* **3. Data Analysis**
  * **Basic Data Analysis with `csv` and `statistics`:**

        ```python
        import csv
        import statistics

        data = []
        with open("data.csv", "r") as file:
            reader = csv.DictReader(file)
            for row in reader:
                data.append(row)

        # Convert numerical columns to the appropriate data type
        ages = [int(row["Age"]) for row in data]
        salaries = [float(row["Salary"]) for row in data]

        # Calculate basic statistics
        print(f"Average age: {statistics.mean(ages):.2f}")
        print(f"Median age: {statistics.median(ages)}")
        print(f"Standard deviation of ages: {statistics.stdev(ages):.2f}")
        print(f"Highest salary: {max(salaries):,.2f}")
        print(f"Lowest salary: {min(salaries):,.2f}")

        # Simple analysis - filter data
        high_earners = [row for row in data if float(row["Salary"]) > 60000]
        print("\nHigh earners:")
        for row in high_earners:
            print(f"  Name: {row['Name']}, Salary: {float(row['Salary']):,.2f}")
        ```

  * **Using `pandas` for Data Analysis:**

        ```python
        import pandas as pd

        # Load data from a CSV file into a DataFrame
        df = pd.read_csv("data.csv")

        # Basic information about the DataFrame
        print(df.info())
        print(df.head())  # Display the first few rows
        print(df.describe())  # Summary statistics

        # Accessing columns
        print(df["Name"])
        print(df[["Name", "Age"]])  # Select multiple columns

        # Filtering data
        high_earners = df[df["Salary"] > 60000]
        print(high_earners)

        # Sorting data
        df_sorted = df.sort_values("Salary", ascending=False)
        print(df_sorted)

        # Grouping and aggregation
        average_salary_by_city = df.groupby("City")["Salary"].mean()
        print(average_salary_by_city)

        # Adding a new column
        df["Age Group"] = pd.cut(df["Age"], bins=[0, 25, 40, 60], labels=["Young", "Adult", "Senior"])
        print(df)

        # Saving the modified DataFrame to a new CSV file
        df.to_csv("modified_data.csv", index=False)
        ```

  * **Data Visualization with `matplotlib`:**

        ```python
        ```python

import matplotlib.pyplot as plt
import pandas as pd

# Load data

df = pd.read_csv("data.csv")

# Histogram of ages

plt.hist(df["Age"], bins=10, edgecolor="black")
plt.xlabel("Age")
plt.ylabel("Frequency")
plt.title("Distribution of Ages")
plt.show()

# Scatter plot of age vs. salary

plt.scatter(df["Age"], df["Salary"])
plt.xlabel("Age")
plt.ylabel("Salary")
plt.title("Age vs. Salary")
plt.show()

# Bar chart of average salary by city

average_salary_by_city = df.groupby["City"]("Salary").mean()
average_salary_by_city.plot(kind="bar")
plt.xlabel("City")
plt.ylabel("Average Salary")
plt.title("Average Salary by City")
plt.xticks(rotation=45)  # Rotate x-axis labels for better readability
plt.tight_layout()  # Adjust layout to prevent labels from overlapping
plt.show()

# Box plot of salaries

plt.boxplot(df["Salary"], vert=False, patch_artist=True)  # vert=False makes it horizontal
plt.xlabel("Salary")
plt.title("Distribution of Salaries")
plt.show()

# Pie chart of the number of people in each age group

age_group_counts = df["Age Group"].value_counts()
plt.pie(age_group_counts, labels=age_group_counts.index, autopct="%1.1f%%", startangle=90)
plt.title("Proportion of People in Each Age Group")
plt.show()

# Line plot (time-series example)
# Create sample time-series data
dates = pd.date_range('20230101', periods=100)
values = np.random.randn(100).cumsum()

# Create DataFrame
df = pd.DataFrame({'Date': dates, 'Value': values})

# Plot the data
df.plot(x='Date', y='Value', 
        title='Time Series Example',
        xlabel='Date',
        ylabel='Value',
        grid=True,
        figsize=(10, 6))

# Customize the plot
plt.xticks(rotation=45)  # Rotate x-axis labels
plt.tight_layout()  # Adjust layout
plt.show()

```

**Explanation of the `matplotlib` examples:**

1. **Histogram:**
    *   `plt.hist(df["Age"], bins=10, edgecolor="black")` creates a histogram of the "Age" column.
    *   `bins=10` divides the data into 10 bins.
    *   `edgecolor="black"` adds black outlines to the bars.

2. **Scatter Plot:**
    *   `plt.scatter(df["Age"], df["Salary"])` creates a scatter plot with "Age" on the x-axis and "Salary" on the y-axis.

3. **Bar Chart:**
    *   `average_salary_by_city = df.groupby("City")["Salary"].mean()` calculates the average salary for each city.
    *   `average_salary_by_city.plot(kind="bar")` creates a bar chart from the grouped data.
    *   `plt.xticks(rotation=45)` rotates the x-axis labels 45 degrees.
    *   `plt.tight_layout()` automatically adjusts subplot parameters for a tight layout.

4. **Box Plot:**
    *   `plt.boxplot(df["Salary"], vert=False, patch_artist=True)` creates a horizontal box plot of the "Salary" column.
    *   `vert=False` makes the plot horizontal.
    *   `patch_artist=True` fills the boxes with color.

5. **Pie Chart:**
    *   `age_group_counts = df["Age Group"].value_counts()` counts the number of people in each age group.
    *   `plt.pie(age_group_counts, labels=age_group_counts.index, autopct="%1.1f%%", startangle=90)` creates a pie chart.
    *   `labels=age_group_counts.index` sets the labels for each slice.
    *   `autopct="%1.1f%%"` formats the percentage labels.
    *   `startangle=90` rotates the starting angle of the first slice.

6. **Line Plot (for time-series data):**
    *   This part is commented out because it assumes you have a "Date" column.
    *   `df["Date"] = pd.to_datetime(df["Date"])` would convert the "Date" column to datetime objects.
    *   `df.plot(x="Date", y="Value")` creates a line plot with "Date" on the x-axis and "Value" on the y-axis.

---

## **Conclusion**

This comprehensive Python tutorial has covered a wide range of topics, from fundamental programming concepts to advanced techniques. Here's a quick recap of what we've learned:

1. **Core Python Concepts:**
   - Data types, variables, and operators
   - Control flow and loops
   - Functions and modules
   - Error handling and debugging

2. **Data Structures:**
   - Lists, tuples, dictionaries, and sets
   - Comprehensions and generators
   - Working with files and data formats

3. **Object-Oriented Programming:**
   - Classes and objects
   - Inheritance and polymorphism
   - Special methods and properties

4. **Advanced Topics:**
   - Decorators and context managers
   - Concurrency and parallelism
   - Testing and type hints
   - Popular Python libraries and frameworks

5. **Practical Applications:**
   - Data analysis with pandas and matplotlib
   - Web development with Flask/Django
   - GUI development with Tkinter/PyQt
   - Scientific computing with NumPy/SciPy

### **Next Steps**

To continue your Python journey:

1. **Practice:** Work on coding challenges and personal projects
2. **Explore:** Dive deeper into specific areas of interest (e.g., web development, data science)
3. **Contribute:** Participate in open-source projects
4. **Stay Updated:** Follow Python news and updates through official channels

Remember, mastering Python is an ongoing process. Keep coding, keep learning, and most importantly, have fun!

---

## **Additional Resources**

- [Official Python Documentation](https://docs.python.org/3/)
- [Python Package Index (PyPI)](https://pypi.org/)
- [Real Python Tutorials](https://realpython.com/)
- [Python Weekly Newsletter](https://www.pythonweekly.com/)
- [Awesome Python](https://awesome-python.com/) - Curated list of Python frameworks and libraries

**XV. Advanced Topics (Brief Overview)**

*   **1. Decorators:**
    *   A way to modify the behavior of functions or classes without changing their code directly.
    *   Use the `@` symbol followed by the decorator function name.
    *   Common use cases:
        *   Logging
        *   Timing function execution
        *   Caching results (memoization)
        *   Access control (e.g., checking if a user is logged in)

    ```python
    import time
    from functools import wraps

    def timing_decorator(func):
        @wraps(func)  # Preserve function metadata (name, docstring)
        def wrapper(*args, **kwargs):
            start_time = time.time()
            result = func(*args, **kwargs)
            end_time = time.time()
            print(f"{func.__name__} took {end_time - start_time:.4f} seconds to run.")
            return result
        return wrapper

    @timing_decorator
    def slow_function():
        time.sleep(2)
        print("Slow function finished.")

    slow_function()
    ```

*   **2. Context Managers:**
    *   A way to manage resources (files, network connections, locks, etc.) efficiently.
    *   Use the `with` statement.
    *   Ensure that resources are properly acquired and released, even if errors occur.
    *   Implement the **context manager protocol**:
        *   `__enter__()` method: Sets up the resource (e.g., opens a file).
        *   `__exit__()` method: Cleans up the resource (e.g., closes the file).

    ```python
    # The 'open()' function is a built-in context manager
    with open("my_file.txt", "r") as file:
        contents = file.read()
        print(contents)
    # File is automatically closed when exiting the 'with' block

    # Creating a custom context manager
    class MyContextManager:
        def __enter__(self):
            print("Entering the context")
            # Acquire resources here

        def __exit__(self, exc_type, exc_value, traceback):
            print("Exiting the context")
            # Release resources here
            # Handle exceptions if needed

    with MyContextManager():
        print("Inside the context")
    ```

*   **3. Metaclasses:**
    *   Classes that create other classes.
    *   Allow you to customize class creation behavior.
    *   Used for advanced object-oriented programming techniques.

*   **4. Concurrency and Parallelism:**
    *   **Multithreading (`threading` module):** Running multiple threads within a single process. Useful for I/O-bound tasks (waiting for network requests, file operations).
    *   **Multiprocessing (`multiprocessing` module):** Running multiple processes. Useful for CPU-bound tasks (heavy computations).
    *   **`asyncio`:** Asynchronous programming using coroutines and event loops. Efficient for handling many concurrent I/O operations.

*   **5. Testing (`unittest`, `pytest`):**
    *   Writing automated tests to ensure the correctness of your code.
    *   **`unittest`:** Python's built-in testing framework.
    *   **`pytest`:** A popular third-party testing framework that is more flexible and feature-rich.

*   **6. Type Hinting:**
    *   Adding type annotations to your code to improve readability and help catch type errors.
    *   Use the `typing` module for more complex type hints.

    ```python
    def greet(name: str) -> str:
        return f"Hello, {name}!"

    from typing import List

    def sum_list(numbers: List[int]) -> int:
        return sum(numbers)
    ```

*   **7. Cython and C Extensions:**
    *   **Cython:** A superset of Python that allows you to write C extensions more easily. Can significantly improve performance for computationally intensive code.
    *   **C Extensions:** Writing parts of your code in C and calling them from Python. Used for performance optimization or interfacing with C libraries.

*   **8. Web Development (Flask, Django):**
    *   **Flask:** A micro web framework for building web applications.
    *   **Django:** A full-featured web framework for building complex web applications.

*   **9. Data Science Libraries (NumPy, SciPy, scikit-learn):**
    *   **NumPy:** Fundamental library for numerical computing. Provides powerful array objects and mathematical functions.
    *   **SciPy:** Library for scientific computing, built on top of NumPy. Includes modules for optimization, interpolation, signal processing, linear algebra, statistics, and more.
    *   **scikit-learn:** Machine learning library. Provides tools for classification, regression, clustering, dimensionality reduction, model selection, and preprocessing.

*   **10. GUI Development (Tkinter, PyQt, Kivy):**
    *   **Tkinter:** Python's standard GUI toolkit. Simple but somewhat limited.
    *   **PyQt:** Cross-platform GUI toolkit based on the Qt framework. More powerful and feature-rich than Tkinter.
    *   **Kivy:** Open-source Python framework for developing multi-touch applications.

This extended outline covers the major parts of the Python language and ecosystem. Remember to practice regularly, work on projects, and consult the official Python documentation for the most up-to-date and in-depth information.
