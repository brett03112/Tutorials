Okay, here's an in-depth Vanilla JavaScript tutorial for web development, designed to give you a strong foundation and equip you with the skills to build a portfolio-ready project.

**Table of Contents**

1. **Introduction to Web Development and JavaScript**
    *   What is JavaScript?
    *   Setting Up Your Development Environment
    *   Your First JavaScript Program
    *   Programming Exercises
2. **JavaScript Fundamentals**
    *   Variables and Data Types
    *   Operators
    *   Control Flow (Conditionals and Loops)
    *   Functions
    *   Scope
    *   Programming Exercises
3. **Working with the DOM**
    *   What is the DOM?
    *   Selecting Elements
    *   Modifying Elements
    *   Creating and Adding Elements
    *   Removing Elements
    *   Traversing the DOM
    *   Programming Exercises
4. **Events**
    *   Event Handlers
    *   Event Listeners
    *   Event Object
    *   Event Bubbling and Capturing
    *   Common Event Types
    *   Programming Exercises
5. **Asynchronous JavaScript**
    *   Callbacks
    *   Promises
    *   Async/Await
    *   Fetching Data from APIs
    *   Programming Exercises
6. **Intermediate JavaScript**
    *   Objects and Prototypes
    *   Classes
    *   Modules
    *   Error Handling
    *   Local Storage and Session Storage
    *   Programming Exercises
7. **HTML and CSS Integration with JavaScript**
    *   Inline Styles and JavaScript
    *   External Stylesheets and JavaScript
    *   Manipulating CSS Classes with JavaScript
    *   Creating Dynamic Styles with JavaScript
    *   Programming Exercises
8. **Final Project: Interactive Photo Gallery**
    *   Project Overview
    *   HTML Structure
    *   CSS Styling
    *   JavaScript Functionality
    *   Detailed Code Breakdown
    *   Enhancements and Further Development
9. **Conclusion and Next Steps**

**1. Introduction to Web Development and JavaScript**

**What is JavaScript?**

JavaScript is a versatile scripting language primarily used to add interactivity and dynamic behavior to websites. It runs in the user's web browser, making web pages more engaging and responsive.

**Setting Up Your Development Environment**

*   **Text Editor:** Choose a code editor like VS Code, Sublime Text, Atom, or any other you prefer.
*   **Web Browser:** You'll need a modern web browser (Chrome, Firefox, Edge, Safari) for testing and debugging your code.
*   **Browser Developer Tools:** Learn how to use your browser's developer tools (usually accessed by pressing F12). The "Console" tab is essential for JavaScript debugging.

**Your First JavaScript Program**

1. Create an HTML file named `index.html`:

```html
<!DOCTYPE html>
<html>
<head>
    <title>My First JavaScript Page</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <h1>Hello from HTML!</h1>
    <script src="script.js"></script>
</body>
</html>
```

1. Create a JavaScript file named `script.js` in the same folder:

```javascript
console.log("Hello from JavaScript!");
alert("Welcome to my website!");
```

1. Create a stylesheet named `styles.css` in the same folder:

```css
h1 {
  color: blue;
}
```

1. Open `index.html` in your browser. You should see the alert message and then the "Hello from HTML!" heading in blue. Open the browser's developer console (F12) to see the "Hello from JavaScript!" message.

**Programming Exercises**

1. Modify `script.js` to display your name in the console.
2. Change the alert message to something more creative.
3. Add a paragraph element to `index.html` and use JavaScript to change its text content.

**2. JavaScript Fundamentals**

**Variables and Data Types**

*   **Variables:** Used to store data. Declared using `var` (older, function-scoped), `let` (block-scoped), or `const` (block-scoped, for constants).

    ```javascript
    let name = "Alice";
    const age = 30;
    var city = "New York"; // Generally avoid using var in modern JavaScript
    ```

*   **Data Types:**
    *   **Number:** `let score = 100;`
    *   **String:** `let message = "Hello";`
    *   **Boolean:** `let isLoggedIn = true;`
    *   **Null:** `let data = null;` (Represents the intentional absence of a value)
    *   **Undefined:** `let address;` (Represents a variable that has been declared but not assigned a value)
    *   **Object:** `let person = { name: "Bob", age: 25 };`
    *   **Array:** `let colors = ["red", "green", "blue"];`

**Operators**

*   **Arithmetic:** `+`, `-`, `*`, `/`, `%` (modulo), `**` (exponentiation)
*   **Assignment:** `=`, `+=`, `-=`, `*=`, `/=`, `%=`
*   **Comparison:** `==` (loose equality), `===` (strict equality), `!=` (not loose equal), `!==` (not strict equal), `>`, `<`, `>=`, `<=`
*   **Logical:** `&&` (AND), `||` (OR), `!` (NOT)

**Control Flow**

*   **Conditionals:**

    ```javascript
    if (age >= 18) {
        console.log("You can vote.");
    } else if (age >= 16) {
        console.log("You can drive.");
    } else {
        console.log("You are a minor.");
    }

    //Ternary Operator
    let message = (age >= 18) ? "Adult" : "Minor";
    ```

*   **Loops:**

    ```javascript
    //For Loop
    for (let i = 0; i < 5; i++) {
        console.log(i);
    }

    //While Loop
    let count = 0;
    while (count < 3) {
        console.log(count);
        count++;
    }

    //Do-While Loop
    let j = 0;
    do {
      console.log(j);
      j++;
    } while (j < 5);

    //For-of Loop (iterating over iterable objects like arrays and strings)
    let colors = ["red", "green", "blue"];
    for (let color of colors) {
      console.log(color);
    }

    //For-in Loop (iterating over object keys)
    let person = { name: "Alice", age: 30, city: "New York" };
    for (let key in person) {
      console.log(key + ": " + person[key]);
    }
    ```

**Functions**

*   **Declaration:**

    ```javascript
    function greet(name) {
        console.log("Hello, " + name + "!");
    }
    ```

*   **Expression:**

    ```javascript
    const add = function(a, b) {
        return a + b;
    };
    ```

*   **Arrow Function:**

    ```javascript
    const multiply = (a, b) => a * b;
    ```

*   **Invocation:**

    ```javascript
    greet("Alice");
    let sum = add(5, 3);
    ```

**Scope**

*   **Global Scope:** Variables declared outside any function have global scope.
*   **Function Scope:** Variables declared with `var` inside a function have function scope.
*   **Block Scope:** Variables declared with `let` or `const` inside a block (`{}`) have block scope.

    ```javascript
    let globalVar = "I'm global";

    function myFunction() {
        let functionVar = "I'm function-scoped"; 
        if (true) {
            let blockVar = "I'm block-scoped";
            console.log(functionVar); // Accessible
            console.log(blockVar);   // Accessible
        }
        // console.log(blockVar); // Error: blockVar is not defined
    }

    myFunction();
    // console.log(functionVar); // Error: functionVar is not defined
    ```

**Programming Exercises**

1. Write a function that takes two numbers and returns the larger one.
2. Write a function that takes an array of numbers and returns the sum of all the numbers.
3. Create a function `isEven` that checks if a number is even.
4. Declare a variable in the global scope and try to access it inside a function.
5. Declare a variable inside a function and try to access it outside the function.

**Advanced JavaScript Concepts**

**Modern JavaScript Features (ES6+)**

* **Arrow Functions:** Concise syntax for writing functions
```javascript
const add = (a, b) => a + b;
```

* **Template Literals:** Easier string interpolation
```javascript
const name = "Alice";
console.log(`Hello, ${name}!`);
```

* **Destructuring:** Extract values from arrays/objects
```javascript
const [x, y] = [1, 2];
const {name, age} = {name: "Bob", age: 30};
```

* **Spread/Rest Operator:** 
```javascript
// Spread
const arr1 = [1, 2];
const arr2 = [...arr1, 3, 4];

// Rest
function sum(...numbers) {
  return numbers.reduce((a, b) => a + b);
}
```

* **Optional Chaining:** Safely access nested properties
```javascript
const user = {profile: {name: "Alice"}};
console.log(user?.profile?.name); // "Alice"
console.log(user?.address?.city); // undefined
```

* **Nullish Coalescing:** Provide default values
```javascript
const value = null;
const result = value ?? "default";
```

**JavaScript Performance Optimization**

* **Debouncing and Throttling:** Control function execution rate
* **Memoization:** Cache function results
* **Web Workers:** Offload heavy computations
* **Lazy Loading:** Load resources only when needed
* **Code Splitting:** Break code into smaller bundles
* **Tree Shaking:** Remove unused code
* **Minification:** Reduce file size
* **Caching:** Store frequently used data

**Real-World Patterns**

* **Singleton Pattern:** Ensure only one instance exists
* **Factory Pattern:** Create objects without specifying exact class
* **Observer Pattern:** Implement event-driven systems
* **Module Pattern:** Encapsulate private data
* **Revealing Module Pattern:** Expose public API
* **Prototype Pattern:** Clone existing objects
* **Mixin Pattern:** Add functionality to objects

**Closures**

A closure is a function that retains access to its lexical scope even when the function is executed outside that scope. This allows for powerful patterns like data encapsulation and function factories.

```javascript
function createCounter() {
    let count = 0;
    return function() {
        count++;
        return count;
    };
}

const counter = createCounter();
console.log(counter()); // 1
console.log(counter()); // 2
console.log(counter()); // 3
```

**Hoisting**

JavaScript hoists variable and function declarations to the top of their scope. This means you can use functions before they're declared, but be careful with variable hoisting.

```javascript
// Function hoisting
sayHello(); // Works because function declarations are hoisted

function sayHello() {
    console.log("Hello!");
}

// Variable hoisting
console.log(x); // undefined (declaration is hoisted, but not initialization)
var x = 5;
console.log(x); // 5

// let and const are hoisted but not initialized
console.log(y); // ReferenceError
let y = 10;
```

**The Event Loop**

JavaScript uses an event loop to handle asynchronous operations. Understanding this is crucial for working with async code.

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Timeout");
}, 0);

Promise.resolve().then(() => {
    console.log("Promise");
});

console.log("End");

// Output order:
// Start
// End
// Promise
// Timeout
```

**Practical Examples and Exercises**

**Example 1: Shopping Cart with Closures**
```javascript
function createCart() {
  let items = [];
  
  return {
    addItem: function(item) {
      items.push(item);
      console.log(`${item} added to cart`);
    },
    removeItem: function(item) {
      const index = items.indexOf(item);
      if (index !== -1) {
        items.splice(index, 1);
        console.log(`${item} removed from cart`);
      }
    },
    getItems: function() {
      return [...items];
    },
    getTotal: function() {
      return items.length;
    }
  };
}

const cart = createCart();
cart.addItem('Shirt');
cart.addItem('Shoes');
console.log(cart.getItems()); // ['Shirt', 'Shoes']
cart.removeItem('Shirt');
console.log(cart.getTotal()); // 1
```

**Example 2: Event Loop Visualization**
```javascript
console.log('Start');

setTimeout(() => console.log('Timeout 1'), 0);
setTimeout(() => console.log('Timeout 2'), 1000);

Promise.resolve().then(() => console.log('Promise 1'));
Promise.resolve().then(() => console.log('Promise 2'));

console.log('End');

// Output order:
// Start
// End
// Promise 1
// Promise 2
// Timeout 1
// Timeout 2
```

**Example 3: Memoization with Closures**
```javascript
function memoize(fn) {
  const cache = new Map();
  
  return function(...args) {
    const key = JSON.stringify(args);
    if (cache.has(key)) {
      console.log('From cache');
      return cache.get(key);
    }
    
    const result = fn(...args);
    cache.set(key, result);
    console.log('Calculated');
    return result;
  };
}

const factorial = memoize(n => {
  if (n === 0) return 1;
  return n * factorial(n - 1);
});

console.log(factorial(5)); // Calculated
console.log(factorial(5)); // From cache
```

**Programming Exercises**

1. Create a function factory that generates functions to add a specific number.
2. Write a function that uses closures to create a private counter.
3. Experiment with hoisting by moving function calls before their declarations.
4. Create an example that demonstrates the event loop's behavior with multiple setTimeout and Promise calls.
5. Implement a memoized Fibonacci sequence generator.
6. Create a rate limiter using closures that limits function calls to N per second.
7. Build a simple state management system using closures.
8. Implement a debounce function that only executes after a certain period of inactivity.

**3. Working with the DOM**

**What is the DOM?**

The Document Object Model (DOM) is a tree-like representation of an HTML document. It's how JavaScript interacts with the structure, content, and style of a web page. Each HTML element, attribute, and piece of text becomes a node in the DOM tree.

**Selecting Elements**

*   `document.getElementById("id")`
*   `document.getElementsByClassName("class")`
*   `document.getElementsByTagName("tag")`
*   `document.querySelector("css-selector")` (selects the first match)
*   `document.querySelectorAll("css-selector")` (selects all matches)

**Example:**

```html
<!DOCTYPE html>
<html>
<head>
    <title>DOM Manipulation</title>
</head>
<body>
    <h1 id="main-heading">My Page</h1>
    <p class="intro">This is an introductory paragraph.</p>
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>
    <script>
        let heading = document.getElementById("main-heading");
        let introParagraphs = document.getElementsByClassName("intro");
        let listItems = document.getElementsByTagName("li");
        let firstListItem = document.querySelector("ul li:first-child");
        let allListItems = document.querySelectorAll("li");
    </script>
</body>
</html>
```

**Modifying Elements**

*   `element.textContent` (changes the text content)
*   `element.innerHTML` (changes the HTML content)
*   `element.setAttribute("attribute", "value")`
*   `element.style.property = "value"`

**Example:**

```javascript
heading.textContent = "New Heading";
introParagraphs[0].innerHTML = "<strong>Modified paragraph.</strong>";
firstListItem.setAttribute("class", "highlight");
allListItems[1].style.color = "blue";
```

**Creating and Adding Elements**

*   `document.createElement("tag")`
*   `element.appendChild(newChild)`
*   `element.insertBefore(newChild, referenceChild)`

**Example:**

```javascript
let newParagraph = document.createElement("p");
newParagraph.textContent = "This is a dynamically created paragraph.";
document.body.appendChild(newParagraph);

let newListItem = document.createElement("li");
newListItem.textContent = "Item 0";
let ul = document.querySelector("ul");
ul.insertBefore(newListItem, firstListItem);
```

**Removing Elements**

*   `element.removeChild(child)`
*   `element.remove()` (more modern)

**Example:**

```javascript
ul.removeChild(listItems[2]);
// or
// listItems[2].remove();
```

**Traversing the DOM**

*   `element.parentNode`
*   `element.childNodes`
*   `element.firstChild`
*   `element.lastChild`
*   `element.nextSibling`
*   `element.previousSibling`
*   `element.children` (HTMLCollection of child elements)
*   `element.firstElementChild`
*   `element.lastElementChild`
*   `element.nextElementSibling`
*   `element.previousElementSibling`

**Example:**

```javascript
let parent = firstListItem.parentNode; // ul
let children = ul.children; // listItems
```

**Advanced DOM Techniques**

**Event Delegation**

Event delegation is a pattern where you add a single event listener to a parent element to handle events for multiple child elements. This is more efficient than adding listeners to each child element.

```html
<ul id="todo-list">
    <li>Buy groceries</li>
    <li>Walk the dog</li>
    <li>Do laundry</li>
</ul>
```

```javascript
document.getElementById('todo-list').addEventListener('click', function(e) {
    if (e.target.tagName === 'LI') {
        e.target.classList.toggle('completed');
    }
});
```

**Form Validation**

JavaScript can validate form input before submission:

```html
<form id="signup-form">
    <input type="text" id="username" placeholder="Username" required>
    <input type="email" id="email" placeholder="Email" required>
    <input type="password" id="password" placeholder="Password" required>
    <button type="submit">Sign Up</button>
</form>
```

```javascript
document.getElementById('signup-form').addEventListener('submit', function(e) {
    const username = document.getElementById('username').value;
    const email = document.getElementById('email').value;
    const password = document.getElementById('password').value;
    
    if (username.length < 3) {
        alert('Username must be at least 3 characters');
        e.preventDefault();
    }
    
    if (!validateEmail(email)) {
        alert('Please enter a valid email address');
        e.preventDefault();
    }
    
    if (password.length < 8) {
        alert('Password must be at least 8 characters');
        e.preventDefault();
    }
});

function validateEmail(email) {
    const re = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
    return re.test(String(email).toLowerCase());
}
```

**Drag and Drop**

Implementing drag and drop functionality:

```html
<div id="drag-container">
    <div id="drag-item" draggable="true">Drag me!</div>
</div>
<div id="drop-zone">Drop here</div>
```

```javascript
const dragItem = document.getElementById('drag-item');
const dropZone = document.getElementById('drop-zone');

dragItem.addEventListener('dragstart', function(e) {
    e.dataTransfer.setData('text/plain', e.target.id);
});

dropZone.addEventListener('dragover', function(e) {
    e.preventDefault();
    dropZone.classList.add('drag-over');
});

dropZone.addEventListener('dragleave', function() {
    dropZone.classList.remove('drag-over');
});

dropZone.addEventListener('drop', function(e) {
    e.preventDefault();
    dropZone.classList.remove('drag-over');
    const id = e.dataTransfer.getData('text/plain');
    const draggedElement = document.getElementById(id);
    dropZone.appendChild(draggedElement);
});
```

**Intersection Observer API**

Lazy loading images with Intersection Observer:

```html
<img class="lazy" data-src="image1.jpg" alt="Image 1">
<img class="lazy" data-src="image2.jpg" alt="Image 2">
```

```javascript
const lazyImages = document.querySelectorAll('.lazy');

const observer = new IntersectionObserver((entries, observer) => {
    entries.forEach(entry => {
        if (entry.isIntersecting) {
            const img = entry.target;
            img.src = img.dataset.src;
            img.classList.remove('lazy');
            observer.unobserve(img);
        }
    });
});

lazyImages.forEach(img => {
    observer.observe(img);
});
```

**Advanced DOM Traversal**

More sophisticated DOM traversal techniques:

```javascript
// Get all siblings of an element
function getSiblings(element) {
    return Array.from(element.parentNode.children)
        .filter(child => child !== element);
}

// Get the next element sibling that matches a selector
function nextElementSibling(element, selector) {
    let next = element.nextElementSibling;
    while (next) {
        if (next.matches(selector)) return next;
        next = next.nextElementSibling;
    }
    return null;
}

// Get all ancestors of an element
function getAncestors(element) {
    const ancestors = [];
    let current = element.parentElement;
    while (current) {
        ancestors.push(current);
        current = current.parentElement;
    }
    return ancestors;
}
```

**Programming Exercises**

1. Implement a todo list using event delegation to handle item clicks.
2. Create a form with real-time validation that shows error messages as the user types.
3. Build a drag-and-drop file upload interface.
4. Implement lazy loading for a gallery of images.
5. Write a function that finds all elements with a specific class within a given container.
6. Create a function that highlights all ancestors of a clicked element.

**4. Events**

**Event Handlers**

*   **HTML Attribute:** `onclick="myFunction()"` (less flexible)
*   **DOM Property:** `element.onclick = function() { ... }`

**Example:**

```html
<button onclick="alert('Clicked!')">Click Me (Attribute)</button>

<button id="myButton">Click Me (Property)</button>
<script>
    document.getElementById("myButton").onclick = function() {
        alert("Clicked!");
    };
</script>
```

**Event Listeners**

*   `element.addEventListener("event", function)` (more flexible, allows multiple handlers)

**Example:**

```html
<button id="myButton">Click Me</button>
<script>
    document.getElementById("myButton").addEventListener("click", function() {
        alert("Clicked!");
    });

    document.getElementById("myButton").addEventListener("mouseover", function() {
        console.log("Mouse over!");
    });
</script>
```

**Event Object**

The event handler function automatically receives an `event` object with information about the event.

```javascript
document.getElementById("myButton").addEventListener("click", function(event) {
    console.log(event.type); // "click"
    console.log(event.target); // The button element
    console.log(event.clientX, event.clientY); // Mouse coordinates
});
```

**Event Bubbling and Capturing**

*   **Bubbling:** The event propagates up the DOM tree from the target element to its ancestors.
*   **Capturing:** The event propagates down the DOM tree from the root to the target element (less common).
*   `addEventListener` can take a third argument, `useCapture` (boolean), to specify the capturing phase.

**Example:**

```html
<div id="outer">
    Outer
    <div id="inner">Inner</div>
</div>
<script>
    document.getElementById("outer").addEventListener("click", function() {
        console.log("Outer clicked (bubbling)");
    });
    document.getElementById("inner").addEventListener("click", function() {
        console.log("Inner clicked (bubbling)");
    });

    document.getElementById("outer").addEventListener("click", function() {
        console.log("Outer clicked (capturing)");
    }, true); // Capturing phase
</script>
```

**Common Event Types**

*   **Mouse:** `click`, `mouseover`, `mouseout`, `mousedown`, `mouseup`, `mousemove`
*   **Keyboard:** `keydown`, `keyup`, `keypress`
*   **Form:** `submit`, `focus`, `blur`, `change`
*   **Window:** `load`, `resize`, `scroll`

**Advanced Event Handling**

**Custom Events**

JavaScript allows you to create and dispatch custom events, which can be useful for creating your own event-driven architecture.

```javascript
// Create a custom event
const myEvent = new CustomEvent('myCustomEvent', {
    detail: {
        message: 'This is a custom event!'
    }
});

// Listen for the custom event
document.addEventListener('myCustomEvent', function(e) {
    console.log('Custom event received:', e.detail.message);
});

// Dispatch the event
document.dispatchEvent(myEvent);
```

**Event Throttling and Debouncing**

When handling events that fire rapidly (like scroll or resize), it's important to optimize performance using throttling or debouncing.

```javascript
// Throttle: Execute at most once every 100ms
function throttle(func, limit) {
    let lastFunc;
    let lastRan;
    return function() {
        const context = this;
        const args = arguments;
        if (!lastRan) {
            func.apply(context, args);
            lastRan = Date.now();
        } else {
            clearTimeout(lastFunc);
            lastFunc = setTimeout(function() {
                if ((Date.now() - lastRan) >= limit) {
                    func.apply(context, args);
                    lastRan = Date.now();
                }
            }, limit - (Date.now() - lastRan));
        }
    }
}

window.addEventListener('resize', throttle(function() {
    console.log('Resize event throttled');
}, 100));

// Debounce: Execute only after 100ms of inactivity
function debounce(func, delay) {
    let timeout;
    return function() {
        const context = this;
        const args = arguments;
        clearTimeout(timeout);
        timeout = setTimeout(() => func.apply(context, args), delay);
    }
}

window.addEventListener('scroll', debounce(function() {
    console.log('Scroll event debounced');
}, 100));
```

**Touch Events**

For mobile devices, you can handle touch-specific events:

```javascript
const touchElement = document.getElementById('touch-area');

touchElement.addEventListener('touchstart', function(e) {
    console.log('Touch started');
});

touchElement.addEventListener('touchmove', function(e) {
    console.log('Touch moved');
});

touchElement.addEventListener('touchend', function(e) {
    console.log('Touch ended');
});

touchElement.addEventListener('touchcancel', function(e) {
    console.log('Touch canceled');
});
```

**Event Delegation Patterns**

Event delegation is a powerful pattern for handling events on multiple elements efficiently:

```html
<ul id="task-list">
    <li>Task 1 <button class="complete">Complete</button></li>
    <li>Task 2 <button class="complete">Complete</button></li>
    <li>Task 3 <button class="complete">Complete</button></li>
</ul>
```

```javascript
document.getElementById('task-list').addEventListener('click', function(e) {
    if (e.target.classList.contains('complete')) {
        const taskItem = e.target.closest('li');
        taskItem.classList.add('completed');
        console.log('Task completed:', taskItem.textContent);
    }
});
```

**Programming Exercises**

1. Create a custom event that fires when a specific condition is met (e.g., when a counter reaches 10).
2. Implement a scroll-to-top button that appears after scrolling down 500px, using throttled scroll events.
3. Create a touch-enabled image carousel that responds to swipe gestures.
4. Implement a complex form with real-time validation using event delegation.
5. Build a drag-and-drop interface that works with both mouse and touch events.

**5. Asynchronous JavaScript**

**Callbacks**

A callback function is passed as an argument to another function and is executed after the first function has completed. Used for handling asynchronous operations (e.g., network requests).

```javascript
function fetchData(callback) {
    setTimeout(function() { // Simulate an asynchronous operation
        const data = "Here's your data!";
        callback(data);
    }, 2000);
}

fetchData(function(data) {
    console.log(data); // This will be executed after 2 seconds
});
```

**Promises**

Promises represent the eventual result of an asynchronous operation. They can be in one of three states:

*   **Pending:** Initial state, neither fulfilled nor rejected.
*   **Fulfilled:** The operation completed successfully.
*   **Rejected:** The operation failed.

```javascript
function fetchData() {
    return new Promise(function(resolve, reject) {
        setTimeout(function() {
            const data = "Here's your data!";
            // resolve(data); // Resolve the promise if successful
            reject("Error fetching data!"); // Reject if there's an error
        }, 2000);
    });
}

fetchData()
    .then(function(data) {
        console.log(data);
    })
    .catch(function(error) {
        console.error(error);
    });
```

**Async/Await**

`async/await` is a more modern way to work with promises, making asynchronous code look more like synchronous code.

*   `async` keyword before a function makes it return a promise.
*   `await` keyword inside an `async` function pauses execution until the promise it's awaiting settles (fulfills or rejects).

```javascript
async function fetchData() {
  return new Promise((resolve) => {
    setTimeout(() => {
      const data = "Here's your data!";
      resolve(data);
    }, 2000);
  });
}

async function processData() {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
}

processData();
```

**Fetching Data from APIs**

The `fetch()` API is used to make network requests (e.g., to get data from a server).

```javascript
async function getTodos() {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/todos");

    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }

    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Error fetching data:", error);
  }
}

getTodos();
```

**Advanced Asynchronous Patterns**

**Error Handling with Async/Await**

Proper error handling is crucial for robust async code. Here's how to handle errors effectively:

```javascript
async function fetchWithRetry(url, retries = 3) {
    for (let i = 0; i < retries; i++) {
        try {
            const response = await fetch(url);
            if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
            return await response.json();
        } catch (error) {
            if (i === retries - 1) throw error;
            await new Promise(resolve => setTimeout(resolve, 1000 * (i + 1)));
        }
    }
}

async function main() {
    try {
        const data = await fetchWithRetry('https://api.example.com/data');
        console.log(data);
    } catch (error) {
        console.error('Failed after retries:', error);
    }
}
```

**Parallel Execution with Promise.all()**

When you need to execute multiple async operations in parallel:

```javascript
async function fetchMultipleUrls(urls) {
    try {
        const promises = urls.map(url => fetch(url).then(res => res.json()));
        const results = await Promise.all(promises);
        return results;
    } catch (error) {
        console.error('One of the requests failed:', error);
        throw error;
    }
}

// Usage
const urls = [
    'https://api.example.com/data1',
    'https://api.example.com/data2',
    'https://api.example.com/data3'
];

fetchMultipleUrls(urls)
    .then(results => console.log(results))
    .catch(error => console.error(error));
```

**Advanced Fetch API Usage**

The Fetch API has many powerful features:

```javascript
async function fetchWithTimeout(url, options = {}, timeout = 5000) {
    const controller = new AbortController();
    const timeoutId = setTimeout(() => controller.abort(), timeout);

    try {
        const response = await fetch(url, {
            ...options,
            signal: controller.signal
        });
        clearTimeout(timeoutId);
        if (!response.ok) throw new Error(`HTTP error! status: ${response.status}`);
        return await response.json();
    } catch (error) {
        if (error.name === 'AbortError') {
            throw new Error('Request timed out');
        }
        throw error;
    }
}
```

**Web Workers for CPU-Intensive Tasks**

Offload heavy computations to a web worker:

```javascript
// main.js
const worker = new Worker('worker.js');

worker.postMessage({ type: 'CALCULATE', data: 1000000 });

worker.onmessage = function(event) {
    console.log('Result from worker:', event.data);
};

// worker.js
self.onmessage = function(event) {
    if (event.data.type === 'CALCULATE') {
        const result = heavyComputation(event.data.data);
        self.postMessage(result);
    }
};

function heavyComputation(n) {
    let result = 0;
    for (let i = 0; i < n; i++) {
        result += Math.sqrt(i);
    }
    return result;
}
```

**Real-World Async Patterns**

1. **Rate Limiting:** Control the rate of API calls
2. **Queue System:** Process tasks sequentially
3. **Caching:** Store API responses
4. **Batching:** Combine multiple requests

Example of a simple rate limiter:

```javascript
class RateLimiter {
    constructor(limit, interval) {
        this.limit = limit;
        this.interval = interval;
        this.queue = [];
        this.processing = 0;
    }

    async execute(fn) {
        return new Promise((resolve, reject) => {
            const task = async () => {
                this.processing++;
                try {
                    const result = await fn();
                    resolve(result);
                } catch (error) {
                    reject(error);
                } finally {
                    this.processing--;
                    this.processQueue();
                }
            };

            this.queue.push(task);
            this.processQueue();
        });
    }

    processQueue() {
        while (this.queue.length > 0 && this.processing < this.limit) {
            const task = this.queue.shift();
            task();
            setTimeout(() => this.processQueue(), this.interval);
        }
    }
}

// Usage
const limiter = new RateLimiter(2, 1000); // 2 requests per second

for (let i = 0; i < 10; i++) {
    limiter.execute(() => fetch('https://api.example.com/data'))
        .then(response => console.log(response))
        .catch(error => console.error(error));
}
```

**Programming Exercises**

1. Implement a retry mechanism with exponential backoff for failed API requests.
2. Create a function that fetches data from multiple APIs in parallel and returns the fastest response.
3. Build a simple caching system for API responses that invalidates after a certain time.
4. Implement a task queue that processes tasks sequentially with a configurable concurrency limit.
5. Create a web worker that performs image processing operations.

**6. Intermediate JavaScript**

**Objects and Prototypes**

*   **Objects:** Collections of key-value pairs.

    ```javascript
    const person = {
        firstName: "John",
        lastName: "Doe",
        age: 30,
        greet: function() {
            console.log("Hello, my name is " + this.firstName);
        }
    };
    ```

*   **Prototypes:** Every JavaScript object has a prototype, which is another object that it inherits properties and methods from. This is how inheritance is implemented in JavaScript.

**Classes**

Classes provide a more structured way to create objects (syntactical sugar over prototypes).

```javascript
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(this.name + " makes a sound.");
    }
}

class Dog extends Animal {
    constructor(name, breed) {
        super(name); // Call the parent class constructor
        this.breed = breed;
    }

    speak() {
        console.log(this.name + " barks.");
    }
}

const myDog = new Dog("Buddy", "Golden Retriever");
myDog.speak(); // Output: Buddy barks.
```

**Modules**

Modules help organize code into separate files.

*   **Exporting:**

    ```javascript
    // myModule.js
    export const myVar = 10;
    export function myFunction() { ... }
    ```

*   **Importing:**

    ```javascript
    // main.js
    import { myVar, myFunction } from './myModule.js';
    ```

**Error Handling**

*   `try...catch` blocks are used to handle errors gracefully.

    ```javascript
    try {
        // Code that might throw an error
        let result = someUndefinedVariable + 10;
    } catch (error) {
        console.error("An error occurred:", error);
    }
    ```

**Local Storage and Session Storage**

*   **Local Storage:** Stores data persistently in the user's browser (even after the browser is closed).
*   **Session Storage:** Stores data for the duration of the page session (data is cleared when the tab or window is closed).

```javascript
// Local Storage
localStorage.setItem("name", "Alice");
let name = localStorage.getItem("name");
localStorage.removeItem("name");

// Session Storage
sessionStorage.setItem("tempData", "Some value");
```

**Programming Exercises**

1. Create a `Rectangle` class with properties `width` and `height` and a method `getArea()`.
2. Create a `Circle` class that inherits from a `Shape` class.
3. Create a module with a function to validate email addresses and use it in your main script.
4. Add error handling to the API fetching example to display a user-friendly message if the request fails.
5. Use local storage to remember a user's preferences (e.g., theme color) on your website.

**7. HTML and CSS Integration with JavaScript**

**Inline Styles and JavaScript**

```html
<p id="myParagraph" style="color: blue;">This is a paragraph.</p>
<script>
    document.getElementById("myParagraph").style.fontSize = "20px";
</script>
```

**External Stylesheets and JavaScript**

```html
<!-- index.html -->
<link rel="stylesheet" href="styles.css">

/* styles.css */
#myParagraph {
    color: blue;
}
```

```javascript
// script.js
document.getElementById("myParagraph").style.backgroundColor = "lightgray";
```

**Manipulating CSS Classes with JavaScript**

*   `element.classList.add("className")`
*   `element.classList.remove("className")`
*   `element.classList.toggle("className")`
*   `element.classList.contains("className")`

```html
<p id="myParagraph" class="highlight">This is a paragraph.</p>
<script>
    let paragraph = document.getElementById("myParagraph");
    paragraph.classList.add("large-text");
    paragraph.classList.remove("highlight");
    paragraph.classList.toggle("hidden"); // Add if absent, remove if present
    if (paragraph.classList.contains("large-text")) {
        // ...
    }
</script>
```

**Creating Dynamic Styles with JavaScript**

```javascript
function changeTheme(theme) {
    if (theme === "dark") {
        document.body.style.backgroundColor = "black";
        document.body.style.color = "white";
    } else {
        document.body.style.backgroundColor = "white";
        document.body.style.color = "black";
    }
}
```

**Programming Exercises**

1. Create a button that changes the background color of a `div` element by adding or removing a CSS class.
2. Implement a simple "dark mode" toggle for your website using JavaScript to switch between different stylesheets or CSS classes.
3. Write JavaScript code to dynamically generate a CSS grid layout based on user input (e.g., number of rows and columns).

**8. Final Project: Interactive Photo Gallery**

**Project Overview**

You'll build an interactive photo gallery that fetches images from an API, displays them in a grid, and allows users to view larger versions of the images in a modal popup.

**Features:**

*   Fetch images from the Unsplash API (you'll need a free API key).
*   Display images in a responsive grid layout.
*   Clicking on an image opens a modal with a larger version and image details (photographer, description).
*   Modal can be closed by clicking outside the image or pressing the Esc key.
*   Loading indicator while fetching images.
*   Error handling for API request failures.

**HTML Structure (`index.html`)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Photo Gallery</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="container">
        <h1>Interactive Photo Gallery</h1>
        <div id="gallery" class="gallery">
            </div>
        <div id="modal" class="modal hidden">
            <div class="modal-content">
                <img id="modal-image" src="" alt="">
                <div id="modal-info">
                    <p id="modal-photographer"></p>
                    <p id="modal-description"></p>
                </div>
            </div>
        </div>
    </div>

    <script src="script.js"></script>
</body>
</html>
```

**CSS Styling (`styles.css`)**

```css
body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
    background-color: #f4f4f4;
}

.container {
    max-width: 1200px;
    margin: 20px auto;
    padding: 0 20px;
}

h1 {
    text-align: center;
    margin-bottom: 20px;
}

.gallery {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    grid-gap: 20px;
}

.gallery img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    cursor: pointer;
    border-radius: 5px;
}

.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.7);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 100;
}

.modal-content {
    background-color: #fff;
    padding: 20px;
    border-radius: 5px;
    max-width: 80%;
    max-height: 80%;
    position: relative;
}

.modal-content img {
    width: auto;
    max-width: 100%;
    height: auto;
    max-height: 60vh;
    display: block;
    margin: 0 auto;
    border-radius: 5px;
}

.modal-info {
    margin-top: 10px;
}

.hidden {
    display: none;
}
```

**JavaScript Functionality (`script.js`)**

```javascript
const gallery = document.getElementById("gallery");
const modal = document.getElementById("modal");
const modalImage = document.getElementById("modal-image");
const modalPhotographer = document.getElementById("modal-photographer");
const modalDescription = document.getElementById("modal-description");
const apiKey = "YOUR_UNSPLASH_API_KEY"; // Replace with your actual API key
const apiUrl = `https://api.unsplash.com/photos/random?client_id=${apiKey}&count=12`;

async function fetchImages() {
  try {
    // Add a loading indicator to the gallery while fetching images
    gallery.innerHTML = '<div class="loading">Loading...</div>';

    const response = await fetch(apiUrl);
    if (!response.ok) {
      throw new Error(`HTTP error! status: ${response.status}`);
    }
    const images = await response.json();

    // Clear the loading indicator
    gallery.innerHTML = "";

    images.forEach((image) => {
      const imgElement = document.createElement("img");
      imgElement.src = image.urls.regular;
      imgElement.alt = image.alt_description || "Photo";
      imgElement.addEventListener("click", () => {
        openModal(image);
      });
      gallery.appendChild(imgElement);
    });
  } catch (error) {
    gallery.innerHTML = `<div class="error">Error: ${error.message}</div>`;
  }
}

function openModal(image) {
  modalImage.src = image.urls.full;
  modalImage.alt = image.alt_description || "Photo";
  modalPhotographer.textContent = `Photographer: ${image.user.name}`;
  modalDescription.textContent = image.description || "No description available.";
  modal.classList.remove("hidden");
}

function closeModal() {
  modal.classList.add("hidden");
}

modal.addEventListener("click", (event) => {
  if (event.target === modal) {
    closeModal();
  }
});

window.addEventListener("keydown", (event) => {
  if (event.key === "Escape" && !modal.classList.contains("hidden")) {
    closeModal();
  }
});

fetchImages();
```

**Detailed Code Breakdown:**

1. **HTML:** Sets up the basic page structure with a container for the gallery, a `div` for the gallery grid, and a `div` for the modal popup.
2. **CSS:** Styles the gallery grid with responsive columns, styles the images, and creates the modal popup styles (hidden by default).
3. **JavaScript:**
    *   `fetchImages()`:
        *   Fetches images from the Unsplash API using `fetch` and `async/await`.
        *   Handles errors using `try...catch`.
        *   Adds a loading indicator while images are being fetched.
        *   Clears the loading indicator after images are loaded or if an error occurs.
        *   Dynamically creates `img` elements and appends them to the gallery `div`.
        *   Adds an event listener to each image to open the modal when clicked.
    *   `openModal(image)`:
        *   Sets the `src`, `alt`, photographer, and description of the modal image elements.
        *   Displays the modal by removing the `hidden` class.
    *   `closeModal()`:
        *   Hides the modal by adding the `hidden` class.
    *   Event listeners are added to the modal and window to close the modal when clicking outside the image or pressing the Esc key.

**Enhancements and Further Development:**

*   **Pagination:** Implement pagination to load more images as the user scrolls down.
*   **Search:** Add a search bar to filter images by keywords.
*   **User Collections:** Allow users to create and manage their own collections of images (requires user accounts and a backend).
*   **Image Upload:** Allow users to upload their own images (requires backend storage and image processing).
*   **Performance Optimization:**
    *   Use smaller image sizes for thumbnails.
    *   Lazy load images (load images only when they are about to come into view).
    *   Cache API responses.

**9. Conclusion and Next Steps**

Congratulations! You've completed this in-depth JavaScript tutorial and built a portfolio-ready project. Here are some next steps to continue your learning:

*   **Practice:** The key to mastering JavaScript is practice. Work on more projects, contribute to open source, and keep building.
*   **Learn a Framework/Library:** Consider learning a popular JavaScript framework or library like React, Angular, or Vue.js. These tools can help you build more complex and scalable web applications.
*   **Explore the Backend:** Learn about server-side development with Node.js and databases like MongoDB or PostgreSQL. This will allow you to build full-stack applications.
*   **Dive Deeper into Advanced Concepts:** Continue to learn about topics like functional programming, design patterns, and testing.
*   **Stay Up-to-Date:** The web development landscape is constantly evolving. Follow blogs, attend conferences, and keep up with the latest trends and technologies.
*   **Build and refine your portfolio:** Add more projects to your portfolio and continue to improve the photo gallery project or others to showcase your skills to potential employers.

    **Important:** Remember to replace `"YOUR_UNSPLASH_API_KEY"` in the JavaScript code with your actual Unsplash API key.

    This comprehensive guide should provide you with a solid foundation in web development using JavaScript. Good luck, and happy coding!
