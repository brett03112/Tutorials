Okay, here's an in-depth HTML and CSS masterclass covering the fundamentals, best practices, and advanced techniques, all culminating in a comprehensive portfolio-ready project:

**HTML & CSS Masterclass: Building a Foundation for Web Development and Design**

**Target Audience:** Beginners with little to no prior experience in web development.

**Goal:** Equip you with the fundamental knowledge of HTML and CSS to create static websites and prepare you for more advanced front-end development concepts.

**Methodology:**

*   **Concept Explanation:** Each topic starts with a clear and concise explanation.
*   **Code Examples:** Numerous examples illustrate the concepts in action.
*   **Best Practices:** Emphasize writing clean, maintainable, and accessible code.
*   **Capstone Project:** A real-world project to solidify your skills and showcase in your portfolio.

**Module 1: Introduction to HTML**

**1.1 What is HTML?**

*   **HTML (HyperText Markup Language):** The standard markup language for creating web pages. It structures the content of a web page.
*   **Structure, Not Style:** HTML defines the meaning and hierarchy of content (headings, paragraphs, lists, images, etc.), but it doesn't dictate how it looks. That's where CSS comes in.
*   **Tags, Elements, and Attributes:**
    *   **Tags:** Keywords enclosed in angle brackets (e.g., `<p>`, `<h1>`, `<img>`).
    *   **Elements:** A complete piece of content, including the opening tag, content, and closing tag (e.g., `<p>This is a paragraph.</p>`).
    *   **Attributes:** Provide additional information about an element and are included within the opening tag (e.g., `<img src="image.jpg" alt="Description">`).

**1.2 Basic HTML Structure**

```html
<!DOCTYPE html> 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Web Page</title>
    <link rel="stylesheet" href="style.css"> </head>
<body>

    <h1>Welcome to My Website</h1>
    <p>This is a paragraph of text.</p>

    <script src="script.js"></script> </body>
</html>
```

*   **`<!DOCTYPE html>`:** Declares the document as HTML5.
*   **`<html>`:** The root element of the page.
    *   `lang="en"` attribute specifies the language as English.
*   **`<head>`:** Contains meta-information about the page (not displayed on the page itself).
    *   **`<meta charset="UTF-8">`:** Sets the character encoding to UTF-8, supporting a wide range of characters.
    *   **`<meta name="viewport"...>`:** Configures how the page scales on different devices (essential for responsive design).
    *   **`<title>`:** Sets the title that appears in the browser tab.
    *   **`<link rel="stylesheet" href="style.css">`:** Links an external CSS file to style the page.
*   **`<body>`:** Contains the visible content of the page.
    *   **`<h1>`:** A top-level heading.
    *   **`<p>`:** A paragraph of text.
*   **`<script src="script.js"></script>`:** Links to an external JavaScript file (for interactivity). It's often placed at the end of the `<body>` so the HTML loads first.

**1.3 Common HTML Elements**

*   **Headings:** `<h1>` to `<h6>` (<h1> is the most important, <h6> the least).
    ```html
    <h1>Main Title</h1>
    <h2>Section Title</h2>
    <h3>Subsection Title</h3>
    ```
    Best Practices:
    - Use only one `<h1>` per page
    - Maintain proper heading hierarchy
    - Don't skip heading levels (e.g., don't go from h2 to h4)

*   **Paragraphs:** `<p>`
    ```html
    <p>This is a paragraph of text. It can contain <strong>bold text</strong>, 
    <em>italic text</em>, and <a href="#">links</a>.</p>
    ```
    Common Pitfalls:
    - Avoid using `<br>` tags for spacing (use CSS margin/padding instead)
    - Don't use empty paragraphs for spacing

*   **Links:** `<a>` (anchor)
    ```html
    <!-- Basic link -->
    <a href="https://www.example.com">Visit Example</a>

    <!-- Link with target -->
    <a href="https://www.example.com" target="_blank" rel="noopener noreferrer">
      Visit Example in New Tab
    </a>

    <!-- Email link -->
    <a href="mailto:example@example.com">Email Us</a>

    <!-- Telephone link -->
    <a href="tel:+1234567890">Call Us</a>
    ```
    Key Attributes:
    - `href`: Specifies the URL or resource
    - `target`: Controls where link opens (_blank, _self, _parent, _top)
    - `rel`: Specifies relationship (important for security with target="_blank")
    - `download`: Forces download of linked resource

*   **Images:** `<img>`
    ```html
    <!-- Basic image -->
    <img src="images/logo.png" alt="Company Logo">

    <!-- Responsive image -->
    <img src="images/hero.jpg" 
         alt="Hero Image"
         srcset="images/hero-320.jpg 320w,
                 images/hero-640.jpg 640w,
                 images/hero-1280.jpg 1280w"
         sizes="(max-width: 600px) 100vw, 50vw">

    <!-- Lazy-loaded image -->
    <img src="placeholder.jpg" 
         data-src="image.jpg" 
         alt="Description"
         class="lazyload">
    ```
    Best Practices:
    - Always include meaningful alt text
    - Use srcset for responsive images
    - Implement lazy loading for better performance
    - Optimize image file sizes
*   **Lists:**
    *   **Unordered Lists (`<ul>`):** Bulleted lists.
    *   **Ordered Lists (`<ol>`):** Numbered lists.
    *   **List Items (`<li>`):** Items within a list.

    ```html
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>

    <ol>
        <li>First step</li>
        <li>Second step</li>
    </ol>
    ```
*   **Divisions (`<div>`):** Generic containers used to group other elements for styling or structural purposes.
*   **Spans (`<span>`):** Inline containers used to apply styles to a specific portion of text within a larger element.

**Module 2: Introduction to CSS**

**2.1 What is CSS?**

*   **CSS (Cascading Style Sheets):** The language used to style the appearance of web pages.
*   **Separation of Concerns:** CSS separates the styling from the HTML structure, making code cleaner and easier to maintain.
*   **Selectors, Properties, and Values:**
    *   **Selectors:** Target specific HTML elements to style.
    *   **Properties:** The aspects of an element you want to style (e.g., `color`, `font-size`, `background-color`).
    *   **Values:** The specific settings for a property (e.g., `red`, `16px`, `#f0f0f0`).

**2.2 Ways to Add CSS**

*   **Inline CSS:** Applied directly within an HTML tag using the `style` attribute (generally discouraged for maintainability).

    ```html
    <p style="color: blue; font-size: 18px;">This is a blue paragraph.</p>
    ```
*   **Internal CSS:** Placed within a `<style>` tag in the `<head>` of the HTML document (useful for styles specific to a single page).

    ```html
    <head>
        <style>
            p {
                color: green;
                font-size: 16px;
            }
        </style>
    </head>
    ```
*   **External CSS:** Stored in a separate `.css` file and linked to the HTML using the `<link>` tag (best practice for most cases).

    ```html
    <!-- In your HTML file (index.html) -->
    <head>
        <link rel="stylesheet" href="styles.css">
    </head>
    ```

    ```css
    /* In your CSS file (styles.css) */
    p {
        color: black;
        font-size: 14px;
    }
    ```

**2.3 CSS Selectors**

*   **Element Selector:** Targets elements by their tag name.
    ```css
    /* Style all paragraphs */
    p {
        color: navy;
        line-height: 1.5;
        margin-bottom: 1em;
    }

    /* Style all headings */
    h1, h2, h3 {
        font-family: 'Arial', sans-serif;
        color: #333;
    }
    ```

*   **ID Selector:** Targets a single element with a specific `id` attribute.
    ```css
    #main-header {
        background-color: #0077cc;
        color: white;
        padding: 20px;
        text-align: center;
    }

    #contact-form {
        max-width: 600px;
        margin: 0 auto;
        padding: 20px;
        border: 1px solid #ddd;
    }
    ```

*   **Class Selector:** Targets elements with a specific `class` attribute.
    ```css
    .btn {
        display: inline-block;
        padding: 10px 20px;
        background-color: #0077cc;
        color: white;
        text-decoration: none;
        border-radius: 4px;
        transition: background-color 0.3s;
    }

    .btn:hover {
        background-color: #005fa3;
    }

    .warning {
        color: #dc3545;
        background-color: #f8d7da;
        padding: 10px;
        border: 1px solid #f5c6cb;
        border-radius: 4px;
    }
    ```

*   **Attribute Selectors:** Target elements based on attributes.
    ```css
    /* Links with target="_blank" */
    a[target="_blank"] {
        color: #0077cc;
    }

    /* Images with alt text */
    img[alt] {
        border: 2px solid #0077cc;
    }

    /* Inputs of type text */
    input[type="text"] {
        width: 100%;
        padding: 8px;
        border: 1px solid #ddd;
    }
    ```

*   **Pseudo-classes:** Target elements in specific states.
    ```css
    /* Style visited links */
    a:visited {
        color: #551a8b;
    }

    /* Style first child */
    li:first-child {
        font-weight: bold;
    }

    /* Style odd table rows */
    tr:nth-child(odd) {
        background-color: #f8f9fa;
    }

    /* Style focused inputs */
    input:focus {
        outline: 2px solid #0077cc;
        border-color: #0077cc;
    }
    ```

*   **Combinators:** Combine selectors for more specific targeting.
    ```css
    /* Direct child selector */
    nav > ul {
        list-style: none;
        padding: 0;
    }

    /* Adjacent sibling selector */
    h2 + p {
        margin-top: 0;
    }

    /* General sibling selector */
    h2 ~ p {
        color: #666;
    }

    /* Descendant selector */
    .article p {
        line-height: 1.6;
    }
    ```

*   **Universal Selector:** Selects all elements.
    ```css
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }
    ```

Best Practices:
- Use classes for reusable styles
- Avoid overusing ID selectors
- Keep specificity low when possible
- Use meaningful class names (BEM methodology recommended)
- Avoid inline styles
- Use shorthand properties when appropriate

**2.4 Common CSS Properties**

*   **Text Styling:**
    *   `color`: Sets the text color.
      ```css
      h1 {
        color: #333; /* Dark gray */
      }
      ```
    *   `font-family`: Sets the font.
      ```css
      body {
        font-family: 'Arial', sans-serif;
      }
      ```
    *   `font-size`: Sets the text size.
      ```css
      p {
        font-size: 1rem; /* Responsive sizing */
      }
      ```
    *   `font-weight`: Sets text boldness (e.g., `normal`, `bold`).
      ```css
      strong {
        font-weight: bold;
      }
      ```
    *   `text-align`: Aligns text (e.g., `left`, `center`, `right`).
      ```css
      .center {
        text-align: center;
      }
      ```
    *   `text-decoration`: Adds decorations (e.g., `underline`, `line-through`).
      ```css
      a {
        text-decoration: none; /* Remove underline */
      }
      ```

*   **Box Model:** (We'll cover this in more detail later)
    *   `width`: Sets the width of an element.
      ```css
      .container {
        width: 80%;
        max-width: 1200px;
      }
      ```
    *   `height`: Sets the height of an element.
      ```css
      .hero {
        height: 100vh;
      }
      ```
    *   `margin`: Sets the space outside the element's border.
      ```css
      .section {
        margin: 2rem 0;
      }
      ```
    *   `padding`: Sets the space inside the element's border.
      ```css
      .card {
        padding: 1.5rem;
      }
      ```
    *   `border`: Sets a border around the element.
      ```css
      .button {
        border: 2px solid #0077cc;
        border-radius: 4px;
      }
      ```

*   **Background:**
    *   `background-color`: Sets the background color.
      ```css
      header {
        background-color: #f8f9fa;
      }
      ```
    *   `background-image`: Sets a background image.
      ```css
      .hero {
        background-image: url('hero.jpg');
      }
      ```
    *   `background-repeat`: Controls how a background image repeats.
      ```css
      .pattern {
        background-image: url('pattern.png');
        background-repeat: repeat;
      }
      ```
    *   `background-position`: Controls the position of a background image.
      ```css
      .hero {
        background-position: center top;
      }
      ```

**Module 3: Intermediate HTML**

**3.1 Forms**

Forms are used to collect user input. Here's a comprehensive example with styling and validation:

```html
<form class="contact-form" action="/submit-form" method="post" novalidate>
    <div class="form-group">
        <label for="name">Full Name:</label>
        <input type="text" id="name" name="name" required
               placeholder="Enter your full name"
               minlength="2" maxlength="50"
               pattern="[A-Za-z ]+">
        <span class="error-message">Please enter a valid name</span>
    </div>

    <div class="form-group">
        <label for="email">Email Address:</label>
        <input type="email" id="email" name="email" required
               placeholder="example@domain.com"
               pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}$">
        <span class="error-message">Please enter a valid email</span>
    </div>

    <div class="form-group">
        <label for="phone">Phone Number:</label>
        <input type="tel" id="phone" name="phone"
               placeholder="123-456-7890"
               pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}">
        <span class="error-message">Format: 123-456-7890</span>
    </div>

    <div class="form-group">
        <label for="message">Your Message:</label>
        <textarea id="message" name="message" required
                  placeholder="Type your message here..."
                  minlength="10" maxlength="500"></textarea>
        <span class="error-message">Message must be 10-500 characters</span>
    </div>

    <div class="form-group">
        <label>Preferred Contact Method:</label>
        <div class="radio-group">
            <label>
                <input type="radio" name="contact-method" value="email" checked>
                Email
            </label>
            <label>
                <input type="radio" name="contact-method" value="phone">
                Phone
            </label>
        </div>
    </div>

    <div class="form-group">
        <label>Interests:</label>
        <div class="checkbox-group">
            <label>
                <input type="checkbox" name="interests[]" value="web-dev">
                Web Development
            </label>
            <label>
                <input type="checkbox" name="interests[]" value="design">
                Design
            </label>
            <label>
                <input type="checkbox" name="interests[]" value="seo">
                SEO
            </label>
        </div>
    </div>

    <div class="form-group">
        <label for="country">Country:</label>
        <select id="country" name="country" required>
            <option value="">Select your country</option>
            <option value="US">United States</option>
            <option value="CA">Canada</option>
            <option value="UK">United Kingdom</option>
            <!-- Add more countries -->
        </select>
    </div>

    <div class="form-group">
        <button type="submit">Send Message</button>
        <button type="reset">Clear Form</button>
    </div>
</form>
```

```css
/* Form Styling */
.contact-form {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    background: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 8px;
}

.form-group {
    margin-bottom: 20px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input[type="text"],
input[type="email"],
input[type="tel"],
textarea,
select {
    width: 100%;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
}

input:focus,
textarea:focus,
select:focus {
    outline: none;
    border-color: #0077cc;
    box-shadow: 0 0 5px rgba(0, 119, 204, 0.3);
}

.radio-group,
.checkbox-group {
    display: flex;
    gap: 15px;
    margin-top: 5px;
}

button {
    padding: 10px 20px;
    background-color: #0077cc;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-right: 10px;
}

button:hover {
    background-color: #005fa3;
}

.error-message {
    display: none;
    color: #dc3545;
    font-size: 0.9em;
    margin-top: 5px;
}

input:invalid:not(:placeholder-shown),
textarea:invalid:not(:placeholder-shown) {
    border-color: #dc3545;
}

input:invalid:not(:placeholder-shown) + .error-message,
textarea:invalid:not(:placeholder-shown) + .error-message {
    display: block;
}
```

**Key Features:**
- **Accessibility:** Proper label associations, focus states, and ARIA attributes
- **Validation:** HTML5 validation with custom error messages
- **Responsive Design:** Flexbox layout for radio/checkbox groups
- **User Experience:** Clear error states and helpful placeholders
- **Security:** `novalidate` attribute for custom validation
- **Styling:** Consistent design with focus states and hover effects

**Best Practices:**
1. Always use `<label>` elements with `for` attributes
2. Use proper input types for better mobile experience
3. Implement client-side validation with HTML5 attributes
4. Provide clear error messages
5. Use semantic HTML elements
6. Ensure proper tab order
7. Make forms keyboard-navigable
8. Use ARIA attributes for accessibility
9. Implement server-side validation (not shown in this example)
10. Consider progressive enhancement for older browsers

**3.2 Tables**

Tables are used to display tabular data in a structured format. Here's a comprehensive example with styling and accessibility features:

```html
<div class="table-container">
  <table class="data-table">
    <caption class="sr-only">Employee Salary Information</caption>
    <thead>
      <tr>
        <th scope="col">Name</th>
        <th scope="col">Department</th>
        <th scope="col">Position</th>
        <th scope="col">Salary</th>
        <th scope="col">Start Date</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th scope="row">John Doe</th>
        <td>Sales</td>
        <td>Account Manager</td>
        <td>$75,000</td>
        <td>2021-03-15</td>
      </tr>
      <tr>
        <th scope="row">Jane Smith</th>
        <td>Marketing</td>
        <td>Content Strategist</td>
        <td>$65,000</td>
        <td>2020-08-01</td>
      </tr>
      <!-- Additional rows -->
    </tbody>
    <tfoot>
      <tr>
        <td colspan="4">Total Employees</td>
        <td>2</td>
      </tr>
    </tfoot>
  </table>
</div>
```

```css
/* Table Styling */
.table-container {
  overflow-x: auto;
  margin: 2rem 0;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.data-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.9rem;
}

.data-table th,
.data-table td {
  padding: 12px 15px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

.data-table th {
  background-color: #f8f9fa;
  font-weight: 600;
  position: sticky;
  top: 0;
}

.data-table tbody tr:hover {
  background-color: #f5f5f5;
}

.data-table tfoot {
  background-color: #f8f9fa;
  font-weight: bold;
}

/* Responsive Table */
@media (max-width: 768px) {
  .data-table {
    display: block;
    width: 100%;
  }
  
  .data-table thead,
  .data-table tbody,
  .data-table th,
  .data-table td,
  .data-table tr {
    display: block;
  }
  
  .data-table thead {
    position: absolute;
    top: -9999px;
    left: -9999px;
  }
  
  .data-table tr {
    border: 1px solid #ddd;
    margin-bottom: 1rem;
  }
  
  .data-table td {
    border: none;
    border-bottom: 1px solid #eee;
    position: relative;
    padding-left: 50%;
  }
  
  .data-table td::before {
    content: attr(data-label);
    position: absolute;
    left: 0;
    width: 45%;
    padding-left: 15px;
    font-weight: bold;
    white-space: nowrap;
  }
}

/* Accessibility */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
```

**Key Features:**
- **Accessibility:** Proper use of scope attributes, ARIA roles, and screen reader-only text
- **Responsive Design:** Mobile-friendly layout with horizontal scrolling
- **Styling:** Clean, modern design with hover effects
- **Structure:** Includes header, body, and footer sections
- **Semantic HTML:** Proper use of table elements and attributes

**Best Practices:**
1. Use `<th>` elements with `scope` attributes for accessibility
2. Include a `<caption>` for table context
3. Use `<thead>`, `<tbody>`, and `<tfoot>` for better structure
4. Implement responsive design for mobile devices
5. Add visual feedback for interactive elements
6. Use proper contrast and spacing
7. Consider using CSS Grid for complex table layouts
8. Implement sorting and filtering with JavaScript (not shown in this example)

**Advanced Table Features:**
1. **Sortable Columns:**
```javascript
// JavaScript for sortable columns
document.querySelectorAll('.data-table th').forEach(header => {
  header.addEventListener('click', () => {
    const table = header.closest('table');
    const columnIndex = Array.prototype.indexOf.call(header.parentElement.children, header);
    const rows = Array.from(table.querySelectorAll('tbody tr'));
    
    rows.sort((a, b) => {
      const aText = a.children[columnIndex].textContent.trim();
      const bText = b.children[columnIndex].textContent.trim();
      return aText.localeCompare(bText);
    });
    
    table.querySelector('tbody').append(...rows);
  });
});
```

2. **Pagination:**
```html
<div class="table-pagination">
  <button class="pagination-btn" disabled>Previous</button>
  <span class="page-info">Page 1 of 3</span>
  <button class="pagination-btn">Next</button>
</div>
```

3. **Filtering:**
```html
<div class="table-filters">
  <input type="text" class="filter-input" placeholder="Search...">
  <select class="filter-select">
    <option value="">All Departments</option>
    <option value="Sales">Sales</option>
    <option value="Marketing">Marketing</option>
  </select>
</div>
```

4. **Export Options:**
```html
<div class="table-export">
  <button class="export-btn">Export as CSV</button>
  <button class="export-btn">Export as PDF</button>
</div>
```

**Accessibility Considerations:**
- Use proper ARIA roles and attributes
- Ensure keyboard navigation works
- Provide text alternatives for visual elements
- Use sufficient color contrast
- Test with screen readers
- Implement proper focus management

**Performance Considerations:**
- Virtualize large tables
- Implement lazy loading for table data
- Use efficient sorting algorithms
- Optimize table rendering
- Consider server-side pagination for large datasets

**When to Use Tables:**
- Displaying tabular data
- Financial reports
- Data comparisons
- Statistical information
- Product catalogs
- Timetables and schedules

**When Not to Use Tables:**
- Page layout (use CSS Grid or Flexbox instead)
- Non-tabular content
- Visual design elements
- Navigation menus
- Image galleries

**Modern Table Alternatives:**
1. **CSS Grid Layout:**
```css
.grid-table {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1px;
}

.grid-table > div {
  padding: 12px;
  border: 1px solid #ddd;
}
```

2. **Flexbox Layout:**
```css
.flex-table {
  display: flex;
  flex-direction: column;
}

.flex-table .row {
  display: flex;
}

.flex-table .cell {
  flex: 1;
  padding: 12px;
  border: 1px solid #ddd;
}
```

3. **Component-Based Tables:**
```javascript
// React example
function DataTable({ data }) {
  return (
    <table>
      <thead>
        <tr>
          {Object.keys(data[0]).map(header => (
            <th key={header}>{header}</th>
          ))}
        </tr>
      </thead>
      <tbody>
        {data.map((row, i) => (
          <tr key={i}>
            {Object.values(row).map((cell, j) => (
              <td key={j}>{cell}</td>
            ))}
          </tr>
        ))}
      </tbody>
    </table>
  );
}
```

**Conclusion:**
Tables remain an essential tool for displaying structured data on the web. By following modern best practices and implementing accessibility features, you can create tables that are both functional and user-friendly. Remember to consider responsive design and performance optimization when working with large datasets, and explore modern alternatives like CSS Grid and component-based approaches for more complex layouts.

**3.3 Semantic HTML5 Elements**

Semantic HTML5 elements provide meaning and structure to web content, improving accessibility, SEO, and maintainability. Here's a comprehensive example with styling and best practices:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Semantic HTML Example</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Header Section -->
    <header class="main-header">
        <div class="container">
            <h1>Website Title</h1>
            <p class="tagline">Your tagline here</p>
            
            <!-- Navigation -->
            <nav class="main-nav">
                <ul>
                    <li><a href="#about">About</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Main Content -->
    <main class="main-content">
        <div class="container">
            <!-- Article Section -->
            <article class="featured-article">
                <header>
                    <h2>Article Title</h2>
                    <p class="meta">Published on <time datetime="2023-08-01">August 1, 2023</time></p>
                </header>
                
                <section class="article-content">
                    <p>Main article content...</p>
                    
                    <figure>
                        <img src="image.jpg" alt="Description of image">
                        <figcaption>Image caption</figcaption>
                    </figure>
                </section>
                
                <footer class="article-footer">
                    <p>Written by Author Name</p>
                </footer>
            </article>

            <!-- Aside Section -->
            <aside class="sidebar">
                <section class="widget">
                    <h3>Related Links</h3>
                    <ul>
                        <li><a href="#">Link 1</a></li>
                        <li><a href="#">Link 2</a></li>
                    </ul>
                </section>
            </aside>
        </div>
    </main>

    <!-- Footer Section -->
    <footer class="main-footer">
        <div class="container">
            <p>&copy; 2023 Company Name. All rights reserved.</p>
            <nav class="footer-nav">
                <ul>
                    <li><a href="#">Privacy Policy</a></li>
                    <li><a href="#">Terms of Service</a></li>
                </ul>
            </nav>
        </div>
    </footer>
</body>
</html>
```

```css
/* Basic Reset */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* General Styles */
body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    color: #333;
}

.container {
    width: 90%;
    max-width: 1200px;
    margin: 0 auto;
}

/* Header Styles */
.main-header {
    background-color: #f8f9fa;
    padding: 20px 0;
    border-bottom: 1px solid #ddd;
}

.main-header h1 {
    font-size: 2.5rem;
    margin-bottom: 0.5rem;
}

.tagline {
    font-size: 1.2rem;
    color: #666;
}

.main-nav ul {
    list-style: none;
    margin-top: 1rem;
}

.main-nav li {
    display: inline-block;
    margin-right: 1rem;
}

.main-nav a {
    text-decoration: none;
    color: #0077cc;
}

/* Main Content Styles */
.main-content {
    display: grid;
    grid-template-columns: 3fr 1fr;
    gap: 2rem;
    padding: 2rem 0;
}

.featured-article {
    background-color: #fff;
    padding: 2rem;
    border: 1px solid #ddd;
    border-radius: 4px;
}

.article-content {
    margin-top: 1.5rem;
}

.article-content figure {
    margin: 1.5rem 0;
}

.article-content img {
    max-width: 100%;
    height: auto;
    border-radius: 4px;
}

figcaption {
    font-size: 0.9rem;
    color: #666;
    margin-top: 0.5rem;
}

/* Sidebar Styles */
.sidebar {
    background-color: #f8f9fa;
    padding: 1.5rem;
    border: 1px solid #ddd;
    border-radius: 4px;
}

.widget {
    margin-bottom: 1.5rem;
}

.widget h3 {
    margin-bottom: 1rem;
}

.widget ul {
    list-style: none;
}

.widget li {
    margin-bottom: 0.5rem;
}

/* Footer Styles */
.main-footer {
    background-color: #333;
    color: #fff;
    padding: 2rem 0;
    margin-top: 2rem;
}

.footer-nav ul {
    list-style: none;
    margin-top: 1rem;
}

.footer-nav li {
    display: inline-block;
    margin-right: 1rem;
}

.footer-nav a {
    color: #fff;
    text-decoration: none;
}

/* Responsive Design */
@media (max-width: 768px) {
    .main-content {
        grid-template-columns: 1fr;
    }
    
    .sidebar {
        order: -1;
        margin-bottom: 2rem;
    }
}
```

**Key Semantic Elements:**

1. **`<header>`**
   - Represents introductory content
   - Can be used at page level or within sections/articles
   - Typically contains headings, logos, navigation

2. **`<nav>`**
   - Defines navigation sections
   - Should contain major navigation links
   - Use aria-label for multiple nav elements

3. **`<main>`**
   - Contains the primary content
   - Should be unique per page
   - Helps screen readers identify main content

4. **`<article>`**
   - Represents self-contained content
   - Should make sense independently
   - Examples: blog posts, news articles, forum posts

5. **`<section>`**
   - Groups thematically related content
   - Should have a heading (h2-h6)
   - Use for distinct content areas

6. **`<aside>`**
   - Contains tangentially related content
   - Often used for sidebars, pull quotes
   - Can be nested within articles

7. **`<footer>`**
   - Represents footer content
   - Can contain copyright, contact info, links
   - Can be used at page or section level

**Additional Semantic Elements:**

1. **`<figure>` and `<figcaption>`**
   - For images, diagrams, code snippets
   - Figcaption provides caption/description

2. **`<time>`**
   - Represents dates/times
   - Use datetime attribute for machine-readable format

3. **`<mark>`**
   - Highlights text for reference
   - Useful for search results

4. **`<details>` and `<summary>`**
   - Creates expandable/collapsible content
   - Good for FAQs, additional info

**Best Practices:**

1. Use semantic elements appropriately
2. Maintain proper heading hierarchy
3. Use ARIA roles when needed
4. Ensure logical content flow
5. Use landmarks for accessibility
6. Validate HTML structure
7. Test with screen readers
8. Use microdata for rich snippets

**Accessibility Considerations:**

1. Use proper heading levels (h1-h6)
2. Add alt text for images
3. Use ARIA attributes when needed
4. Ensure keyboard navigation
5. Provide text alternatives
6. Use sufficient color contrast
7. Test with screen readers
8. Implement focus management

**SEO Benefits:**

1. Better content understanding by search engines
2. Improved document outline
3. Enhanced rich snippets
4. Better mobile optimization
5. Improved page speed
6. Enhanced user experience
7. Better content organization
8. Improved crawlability

**Common Mistakes:**

1. Using divs instead of semantic elements
2. Improper nesting of elements
3. Missing required attributes
4. Overusing section elements
5. Ignoring heading hierarchy
6. Not using landmarks
7. Forgetting alt text
8. Not testing accessibility

**Advanced Techniques:**

1. **Microdata:**
```html
<div itemscope itemtype="http://schema.org/Person">
  <span itemprop="name">John Doe</span>
  <span itemprop="jobTitle">Web Developer</span>
</div>
```

2. **ARIA Landmarks:**
```html
<nav role="navigation">
  <!-- Navigation content -->
</nav>

<main role="main">
  <!-- Main content -->
</main>
```

3. **Accessible Forms:**
```html
<form>
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  
  <fieldset>
    <legend>Contact Method</legend>
    <label>
      <input type="radio" name="contact" value="email"> Email
    </label>
    <label>
      <input type="radio" name="contact" value="phone"> Phone
    </label>
  </fieldset>
</form>
```

4. **Responsive Images:**
```html
<picture>
  <source media="(min-width: 1200px)" srcset="large.jpg">
  <source media="(min-width: 768px)" srcset="medium.jpg">
  <img src="small.jpg" alt="Description">
</picture>
```

**Conclusion:**

Semantic HTML5 elements provide a powerful way to structure web content in a meaningful way. By using these elements appropriately, you can create websites that are more accessible, maintainable, and SEO-friendly. Remember to combine semantic markup with proper CSS styling and JavaScript interactivity to create modern, user-friendly web experiences.

**Module 4: Intermediate CSS**

**4.1 The Box Model**

The box model is a fundamental concept that describes how elements are rendered on a page as rectangular boxes. Understanding it is crucial for proper layout and spacing.

```html
<div class="box">
  This is a box with padding, border, and margin
</div>
```

```css
.box {
  /* Content dimensions */
  width: 300px;
  height: 200px;
  
  /* Padding */
  padding: 20px;
  
  /* Border */
  border: 5px solid #0077cc;
  border-radius: 8px;
  
  /* Margin */
  margin: 30px;
  
  /* Background */
  background-color: #f0f8ff;
  
  /* Text styling */
  color: #333;
  font-size: 16px;
  line-height: 1.5;
}
```

* **Content Box**: The innermost area containing the actual content
  - Controlled by width/height properties
  - Default background color is transparent
  - Text and child elements are rendered here

* **Padding**: Space between content and border
  - Adds to element's total size
  - Inherits background color
  - Useful for internal spacing
  ```css
  /* Individual sides */
  padding-top: 10px;
  padding-right: 15px;
  padding-bottom: 20px;
  padding-left: 15px;
  
  /* Shorthand */
  padding: 10px 15px 20px 15px; /* top right bottom left */
  padding: 10px 15px; /* vertical horizontal */
  padding: 10px; /* all sides */
  ```

* **Border**: Line surrounding padding and content
  - Adds to element's total size
  - Can have different styles, widths, and colors
  ```css
  /* Individual properties */
  border-width: 2px;
  border-style: solid;
  border-color: #0077cc;
  
  /* Shorthand */
  border: 2px solid #0077cc;
  
  /* Rounded corners */
  border-radius: 8px;
  ```

* **Margin**: Space outside the border
  - Creates space between elements
  - Transparent (doesn't inherit background)
  - Can collapse with adjacent margins
  ```css
  /* Individual sides */
  margin-top: 20px;
  margin-right: 15px;
  margin-bottom: 20px;
  margin-left: 15px;
  
  /* Shorthand */
  margin: 20px 15px; /* vertical horizontal */
  margin: 20px; /* all sides */
  
  /* Centering elements */
  margin: 0 auto;
  ```

**Box Model Visualization:**

```
+---------------------------+
|         Margin            |
|  +---------------------+  |
|  |      Border         |  |
|  |  +---------------+  |  |
|  |  |    Padding    |  |  |
|  |  |  +---------+  |  |  |
|  |  |  | Content |  |  |  |
|  |  |  +---------+  |  |  |
|  |  +---------------+  |  |
|  +---------------------+  |
+---------------------------+
```

**Box-Sizing Property:**

By default, padding and border are added to the element's width/height. The `box-sizing` property changes this behavior:

```css
/* Default behavior */
.box-default {
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  /* Total width = 300 + 20*2 + 5*2 = 350px */
}

/* Border-box behavior */
.box-border {
  box-sizing: border-box;
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  /* Total width = 300px (includes padding and border) */
}
```

Best Practices:
- Use `box-sizing: border-box` for more predictable layouts
- Use margin for spacing between elements
- Use padding for internal spacing within elements
- Be consistent with spacing values (e.g., use multiples of 4px or 8px)
- Use CSS variables for consistent spacing values

**4.2 Display Property**

The `display` property is one of the most important CSS properties, controlling how an element is rendered and how it interacts with other elements.

```html
<div class="block-example">Block Element</div>
<span class="inline-example">Inline Element</span>
<div class="inline-block-example">Inline-Block Element</div>
<div class="hidden-example">Hidden Element</div>
```

```css
/* Block-level elements */
.block-example {
  display: block;
  width: 80%;
  padding: 20px;
  background-color: #f0f8ff;
  border: 1px solid #0077cc;
  margin-bottom: 10px;
}

/* Inline elements */
.inline-example {
  display: inline;
  padding: 5px;
  background-color: #fff3cd;
  border: 1px solid #ffc107;
  /* width and height have no effect on inline elements */
}

/* Inline-block elements */
.inline-block-example {
  display: inline-block;
  width: 200px;
  padding: 10px;
  background-color: #d4edda;
  border: 1px solid #28a745;
  margin: 5px;
}

/* Hidden elements */
.hidden-example {
  display: none;
}
```

**Display Property Values:**

* **`block`**
  - Takes full available width (unless width is specified)
  - Starts on a new line
  - Can set width, height, margin, padding
  - Examples: `<div>`, `<p>`, `<h1>`-`<h6>`, `<form>`, `<ul>`, `<ol>`, `<li>`
  - Common uses: Page sections, containers, structural elements

* **`inline`**
  - Takes only as much width as needed
  - Flows with text content
  - Cannot set width/height
  - Vertical padding/margin doesn't affect surrounding elements
  - Examples: `<span>`, `<a>`, `<img>`, `<strong>`, `<em>`
  - Common uses: Text formatting, inline elements

* **`inline-block`**
  - Combines features of block and inline
  - Flows like inline elements
  - Can set width/height like block elements
  - Respects vertical margin/padding
  - Examples: Custom buttons, navigation items
  - Common uses: Creating grid-like layouts without flex/grid

* **`none`**
  - Completely removes element from document flow
  - Takes up no space
  - Not accessible to screen readers
  - Alternative: Use `visibility: hidden` to hide while maintaining space

**Display Property Best Practices:**

1. Use semantic HTML elements with their default display values when possible
2. Prefer `inline-block` over `float` for simple layouts
3. Use `display: none` judiciously - consider accessibility implications
4. Combine with other properties for complex layouts:
   ```css
   .menu-item {
     display: inline-block;
     width: 120px;
     text-align: center;
     padding: 10px;
     margin: 0 5px;
     background-color: #f8f9fa;
     border-radius: 4px;
   }
   ```
5. Use CSS Grid or Flexbox for complex layouts instead of relying solely on display properties

**Common Display Patterns:**

1. Centering Elements:
```css
/* Horizontally center block element */
.block-center {
  display: block;
  width: 80%;
  margin: 0 auto;
}

/* Vertically and horizontally center */
.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

2. Responsive Navigation:
```css
/* Mobile first approach */
.nav-item {
  display: block;
  padding: 10px;
}

@media (min-width: 768px) {
  .nav-item {
    display: inline-block;
  }
}
```

3. Image Gallery:
```css
.gallery-item {
  display: inline-block;
  width: 23%;
  margin: 1%;
  vertical-align: top;
}

@media (max-width: 768px) {
  .gallery-item {
    width: 48%;
  }
}
```

4. Toggle Visibility:
```css
/* JavaScript toggle class */
.hidden {
  display: none;
}

.visible {
  display: block;
}
```

**Accessibility Considerations:**
- Use `display: none` carefully as it removes elements from accessibility tree
- Consider `visibility: hidden` or `opacity: 0` for hiding elements while maintaining accessibility
- Ensure proper focus management when toggling visibility

**4.3 Positioning**

The `position` property is crucial for controlling element placement and creating complex layouts. Let's explore each positioning type with practical examples.

```html
<div class="position-examples">
  <div class="static-box">Static</div>
  <div class="relative-box">Relative</div>
  <div class="absolute-box">Absolute</div>
  <div class="fixed-box">Fixed</div>
  <div class="sticky-box">Sticky</div>
</div>
```

```css
.position-examples {
  position: relative;
  height: 2000px;
  border: 2px solid #ccc;
  padding: 20px;
}

/* Static Positioning (Default) */
.static-box {
  position: static;
  background-color: #f0f8ff;
  padding: 10px;
  border: 1px solid #0077cc;
}

/* Relative Positioning */
.relative-box {
  position: relative;
  top: 20px;
  left: 50px;
  background-color: #fff3cd;
  padding: 10px;
  border: 1px solid #ffc107;
  z-index: 1;
}

/* Absolute Positioning */
.absolute-box {
  position: absolute;
  top: 100px;
  right: 20px;
  background-color: #d4edda;
  padding: 10px;
  border: 1px solid #28a745;
  width: 200px;
}

/* Fixed Positioning */
.fixed-box {
  position: fixed;
  bottom: 20px;
  right: 20px;
  background-color: #f8d7da;
  padding: 10px;
  border: 1px solid #dc3545;
  width: 150px;
  text-align: center;
}

/* Sticky Positioning */
.sticky-box {
  position: sticky;
  top: 20px;
  background-color: #e2e3e5;
  padding: 10px;
  border: 1px solid #6c757d;
}
```

**Position Property Values:**

* **`static` (Default)**
  - Elements follow normal document flow
  - Ignores top/right/bottom/left properties
  - Cannot use z-index
  - Use case: Default behavior for most elements

* **`relative`**
  - Positioned relative to its normal position
  - Can use top/right/bottom/left to offset
  - Creates new stacking context (z-index works)
  - Original space in document flow is preserved
  - Use cases:
    - Minor adjustments to element position
    - Creating reference point for absolutely positioned children
    - Overlapping elements with z-index

* **`absolute`**
  - Removed from normal document flow
  - Positioned relative to nearest positioned ancestor
  - If no positioned ancestor, uses initial containing block (usually viewport)
  - Can use top/right/bottom/left for precise positioning
  - Use cases:
    - Tooltips and dropdown menus
    - Modal dialogs
    - Custom form controls
    - Overlays and popups

* **`fixed`**
  - Removed from normal document flow
  - Positioned relative to viewport
  - Stays fixed during scrolling
  - Can use top/right/bottom/left for positioning
  - Use cases:
    - Fixed headers/footers
    - Persistent navigation
    - Chat widgets
    - Back-to-top buttons

* **`sticky`**
  - Hybrid of relative and fixed
  - Treated as relative until crossing specified threshold
  - Then becomes fixed within its container
  - Requires at least one positioning property (top/right/bottom/left)
  - Use cases:
    - Sticky table headers
    - Sticky sidebars
    - Sticky navigation
    - Section headers in long pages

**Positioning Best Practices:**

1. Use relative positioning for minor adjustments and as reference points
2. Use absolute positioning for UI elements that need precise placement
3. Use fixed positioning for elements that should remain visible during scrolling
4. Use sticky positioning for elements that should stick after scrolling past a point
5. Always consider accessibility when positioning elements
6. Use z-index judiciously to control stacking order
7. Test positioning across different screen sizes
8. Combine with transform for advanced positioning effects

**Common Positioning Patterns:**

1. Centering Elements:
```css
/* Absolute Centering */
.center-absolute {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

/* Fixed Centering */
.center-fixed {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

2. Sticky Header:
```css
.header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: white;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
```

3. Overlay Modal:
```css
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
}

.modal-content {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90%;
  max-width: 600px;
  background: white;
  padding: 20px;
  border-radius: 8px;
}
```

4. Tooltip:
```css
.tooltip-container {
  position: relative;
}

.tooltip {
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  background: #333;
  color: white;
  padding: 5px 10px;
  border-radius: 4px;
  white-space: nowrap;
  opacity: 0;
  transition: opacity 0.2s;
}

.tooltip-container:hover .tooltip {
  opacity: 1;
}
```

**Accessibility Considerations:**
- Ensure positioned elements maintain proper focus order
- Use ARIA attributes for modals and tooltips
- Consider screen reader users when using absolute/fixed positioning
- Test with keyboard navigation
- Provide alternative ways to access content that might be obscured by fixed elements

**Performance Considerations:**
- Fixed and sticky elements can cause repaints during scrolling
- Use transform instead of top/left for animations
- Avoid excessive use of z-index
- Use will-change property for elements that will be animated

**4.4 Floats**

The `float` property was traditionally used for page layouts and wrapping text around images. While modern layouts typically use Flexbox or Grid, floats are still useful for specific scenarios like text wrapping and legacy browser support.

```html
<div class="float-container">
  <img src="image.jpg" alt="Description" class="float-left">
  <p>Text wraps around the floated image...</p>
</div>

<div class="clearfix"></div>
```

```css
/* Basic float example */
.float-left {
  float: left;
  margin: 0 20px 20px 0;
  width: 200px;
  shape-outside: circle(50%);
}

.float-right {
  float: right;
  margin: 0 0 20px 20px;
  width: 200px;
  shape-outside: polygon(0 0, 100% 0, 100% 100%);
}

/* Clearfix technique */
.clearfix::after {
  content: "";
  display: table;
  clear: both;
}

/* Modern float container */
.float-container {
  display: flow-root; /* Better than clearfix */
  padding: 20px;
  border: 1px solid #ddd;
}

/* Text wrapping with shapes */
.wrap-shape {
  float: left;
  width: 200px;
  height: 200px;
  margin: 0 20px 20px 0;
  shape-outside: url('shape.png');
  clip-path: url('shape.png');
}
```

**Float Property Values:**

* **`left`**
  - Floats element to left of container
  - Content flows around right side
  - Common uses: Image/text wrapping, legacy layouts

* **`right`**
  - Floats element to right of container
  - Content flows around left side
  - Common uses: Pull quotes, sidebars

* **`none`** (default)
  - Element remains in normal flow
  - Useful for overriding float behavior

**Float Behavior Characteristics:**

1. Removes element from normal document flow
2. Other content flows around floated element
3. Parent container collapses unless cleared
4. Requires width for predictable behavior
5. Can cause layout issues if not managed properly

**Modern Float Techniques:**

1. Shape Wrapping:
```css
.image-wrap {
  float: left;
  width: 200px;
  margin: 0 20px 20px 0;
  shape-outside: circle(50%);
  clip-path: circle(50%);
}
```

2. Text Wrapping:
```css
.text-wrap {
  float: right;
  width: 40%;
  margin: 0 0 20px 20px;
  shape-outside: margin-box;
}
```

3. Drop Caps:
```css
.drop-cap::first-letter {
  float: left;
  font-size: 4em;
  line-height: 0.8;
  margin: 0 10px 0 0;
}
```

**Clearing Floats:**

1. Clearfix Technique:
```css
.clearfix::after {
  content: "";
  display: table;
  clear: both;
}
```

2. Modern Flow-Root:
```css
.container {
  display: flow-root; /* Better alternative to clearfix */
}
```

3. Clear Property:
```css
.clear {
  clear: both;
}
```

**Float Best Practices:**

1. Use floats primarily for text wrapping and legacy support
2. Prefer Flexbox or Grid for modern layouts
3. Always clear floats to prevent layout issues
4. Use `display: flow-root` instead of clearfix when possible
5. Set explicit widths on floated elements
6. Use shape-outside for advanced text wrapping
7. Test across browsers for consistent behavior
8. Consider accessibility when using floats

**Common Float Patterns:**

1. Image Gallery:
```css
.gallery-item {
  float: left;
  width: 23%;
  margin: 1%;
}

@media (max-width: 768px) {
  .gallery-item {
    width: 48%;
  }
}
```

2. Pull Quotes:
```css
.pull-quote {
  float: right;
  width: 40%;
  margin: 0 0 20px 20px;
  font-style: italic;
  border-left: 3px solid #0077cc;
  padding-left: 15px;
}
```

3. Sidebar Layout:
```css
.sidebar {
  float: left;
  width: 25%;
}

.main-content {
  float: right;
  width: 72%;
}

@media (max-width: 768px) {
  .sidebar, .main-content {
    float: none;
    width: 100%;
  }
}
```

**Accessibility Considerations:**

- Ensure content order makes sense when floated
- Use proper alt text for floated images
- Test with screen readers
- Consider how floated elements affect tab order
- Provide clear visual separation for floated content

**Performance Considerations:**

- Excessive floats can cause layout thrashing
- Use will-change property for animated floats
- Minimize reflows by batching float changes
- Consider using CSS containment for complex float layouts

**When to Use Floats vs. Modern Layout Methods:**

| Feature            | Floats          | Flexbox         | Grid            |
|--------------------|-----------------|-----------------|-----------------|
| Text Wrapping      | Excellent       | Not supported   | Not supported   |
| Layout Control     | Limited         | Excellent       | Excellent       |
| Responsiveness     | Difficult       | Easy            | Easy            |
| Browser Support    | Excellent       | Modern browsers | Modern browsers |
| Accessibility      | Challenging     | Good            | Good            |
| Complex Layouts    | Difficult       | Good            | Excellent       |
| Vertical Alignment | Not supported   | Excellent       | Excellent       |
| Order Control      | Not supported   | Excellent       | Excellent       |

**Legacy Float Layout Example:**

```css
/* Old-school 3-column layout */
.header {
  width: 100%;
  margin-bottom: 20px;
}

.column {
  float: left;
  width: 31%;
  margin: 0 1%;
}

.footer {
  clear: both;
  margin-top: 20px;
}

@media (max-width: 768px) {
  .column {
    float: none;
    width: 100%;
    margin: 10px 0;
  }
}
```

**Modern Alternatives:**

1. Flexbox:
```css
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.item {
  flex: 1 1 300px;
}
```

2. Grid:
```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
```

**Conclusion:**

While floats are no longer the primary tool for page layouts, they remain valuable for specific use cases like text wrapping and legacy browser support. Modern CSS layout methods like Flexbox and Grid should be your first choice for most layout needs, but understanding floats is still important for maintaining older codebases and implementing certain design patterns.

**4.5 Flexbox**

Flexbox is a powerful one-dimensional layout system that provides efficient ways to align, distribute, and space items within a container. It's particularly useful for creating responsive layouts and handling dynamic content.

```html
<div class="flex-container">
  <div class="flex-item">1</div>
  <div class="flex-item">2</div>
  <div class="flex-item">3</div>
</div>
```

```css
/* Basic Flexbox Container */
.flex-container {
  display: flex;
  flex-direction: row; /* Default */
  justify-content: space-between;
  align-items: center;
  gap: 20px;
  padding: 20px;
  border: 1px solid #ddd;
}

.flex-item {
  flex: 1 1 200px;
  padding: 20px;
  background-color: #f0f8ff;
  border: 1px solid #0077cc;
}
```

**Flexbox Container Properties:**

1. **display: flex**
   - Enables flexbox layout
   - Creates flex formatting context
   - Direct children become flex items

2. **flex-direction**
   - Defines main axis direction
   - Values: row (default), row-reverse, column, column-reverse
   ```css
   .container {
     flex-direction: column; /* Stack items vertically */
   }
   ```

3. **justify-content**
   - Aligns items along main axis
   - Values: flex-start, flex-end, center, space-between, space-around, space-evenly
   ```css
   .container {
     justify-content: space-between; /* Distribute items with equal space between */
   }
   ```

4. **align-items**
   - Aligns items along cross axis
   - Values: flex-start, flex-end, center, stretch, baseline
   ```css
   .container {
     align-items: stretch; /* Stretch items to fill container */
   }
   ```

5. **flex-wrap**
   - Controls wrapping behavior
   - Values: nowrap (default), wrap, wrap-reverse
   ```css
   .container {
     flex-wrap: wrap; /* Allow items to wrap to new line */
   }
   ```

6. **gap**
   - Sets spacing between items
   - Values: length or percentage
   ```css
   .container {
     gap: 20px; /* Space between items */
   }
   ```

**Flexbox Item Properties:**

1. **flex**
   - Shorthand for flex-grow, flex-shrink, and flex-basis
   - Default: 0 1 auto
   ```css
   .item {
     flex: 1 1 200px; /* Grow, shrink, basis */
   }
   ```

2. **align-self**
   - Overrides align-items for individual items
   - Values: auto, flex-start, flex-end, center, stretch, baseline
   ```css
   .special-item {
     align-self: flex-end; /* Align this item differently */
   }
   ```

3. **order**
   - Controls display order of items
   - Default: 0
   ```css
   .first-item {
     order: -1; /* Move to start */
   }
   ```

**Common Flexbox Patterns:**

1. **Responsive Navigation:**
```css
.nav {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.nav-item {
  flex: 1 1 150px;
  text-align: center;
}
```

2. **Card Layout:**
```css
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.card {
  flex: 1 1 300px;
  padding: 20px;
  border: 1px solid #ddd;
}
```

3. **Sticky Footer:**
```css
body {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex: 1;
}

footer {
  margin-top: auto;
}
```

4. **Centering Elements:**
```css
.center-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

5. **Equal Height Columns:**
```css
.columns {
  display: flex;
}

.column {
  flex: 1;
  padding: 20px;
}
```

**Flexbox Best Practices:**

1. Use semantic HTML with flexbox
2. Prefer flexbox over floats for modern layouts
3. Use gap instead of margins for spacing
4. Combine with media queries for responsive designs
5. Use flex-basis instead of width for flexible sizing
6. Avoid nesting too many flex containers
7. Use min-width/max-width with flex items
8. Test across browsers for consistent behavior

**Accessibility Considerations:**

- Ensure logical source order matches visual order
- Use proper heading hierarchy
- Maintain keyboard navigation
- Consider screen reader users
- Test with high contrast modes

**Performance Considerations:**

- Avoid excessive nesting of flex containers
- Use will-change for animated flex items
- Minimize layout thrashing
- Use contain: layout when appropriate
- Avoid unnecessary reflows

**Flexbox vs. Grid:**

| Feature            | Flexbox          | Grid             |
|--------------------|------------------|------------------|
| Dimension          | One-dimensional  | Two-dimensional  |
| Alignment          | Excellent        | Excellent        |
| Responsiveness     | Easy             | Easy             |
| Complex Layouts    | Good             | Excellent        |
| Item Ordering      | Easy             | Limited          |
| Browser Support    | Excellent        | Modern browsers  |
| Use Case           | Components       | Page Layouts     |

**Common Flexbox Mistakes:**

1. Forgetting to set flex-direction
2. Overusing flex-grow
3. Not using gap for spacing
4. Ignoring flex-wrap
5. Using fixed widths with flex items
6. Not testing in older browsers
7. Over-nesting flex containers
8. Forgetting to set min-width/max-width

**Advanced Flexbox Techniques:**

1. **Intrinsic Sizing:**
```css
.container {
  display: flex;
  width: min-content;
}
```

2. **Aspect Ratio Boxes:**
```css
.aspect-box {
  flex: 1;
  aspect-ratio: 1;
}
```

3. **Sticky Sidebar:**
```css
.layout {
  display: flex;
  height: 100vh;
}

.sidebar {
  flex: 0 0 250px;
  position: sticky;
  top: 0;
}
```

4. **Responsive Masonry:**
```css
.masonry {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.masonry-item {
  flex: 1 1 300px;
}
```

5. **Dynamic Grid:**
```css
.grid {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.grid-item {
  flex: 1 1 calc(33.33% - 40px);
}
```

**Conclusion:**

Flexbox is an essential tool for modern web layouts, offering powerful alignment and distribution capabilities. While it's primarily designed for one-dimensional layouts, it can handle many common layout patterns with ease. When combined with CSS Grid, you can create sophisticated, responsive designs that work across all devices and screen sizes.

**4.6 CSS Grid**

CSS Grid is a powerful two-dimensional layout system that allows for precise control over both rows and columns. It's particularly useful for creating complex, responsive layouts with ease.

```html
<div class="grid-container">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="main-content">Main Content</main>
  <footer class="footer">Footer</footer>
</div>
```

```css
/* Basic Grid Container */
.grid-container {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: 100px 1fr 100px;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  gap: 20px;
  height: 100vh;
  padding: 20px;
  border: 1px solid #ddd;
}

.header {
  grid-area: header;
  background-color: #f0f8ff;
  padding: 20px;
  border: 1px solid #0077cc;
}

.sidebar {
  grid-area: sidebar;
  background-color: #fff3cd;
  padding: 20px;
  border: 1px solid #ffc107;
}

.main-content {
  grid-area: main;
  background-color: #d4edda;
  padding: 20px;
  border: 1px solid #28a745;
}

.footer {
  grid-area: footer;
  background-color: #f8d7da;
  padding: 20px;
  border: 1px solid #dc3545;
}

/* Responsive Grid */
@media (max-width: 768px) {
  .grid-container {
    grid-template-columns: 1fr;
    grid-template-rows: 80px auto 1fr 80px;
    grid-template-areas:
      "header"
      "sidebar"
      "main"
      "footer";
  }
}
```

**Key Features:**
- **Grid Areas:** Named template areas for better readability
- **Responsive Design:** Media queries for mobile layout
- **Fraction Units:** Flexible sizing with `fr` units
- **Gap Property:** Consistent spacing between items
- **Viewport Units:** Full-height layout with `100vh`

**Best Practices:**
1. Use semantic HTML with grid layout
2. Name grid areas for better maintainability
3. Use `fr` units for flexible sizing
4. Implement responsive design with media queries
5. Use `gap` instead of margins for spacing
6. Combine with Flexbox for component layouts
7. Test across browsers for compatibility
8. Use CSS variables for consistent values

**Advanced Grid Techniques:**

1. **Nested Grids:**
```css
.main-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 15px;
}
```

2. **Grid Auto-Flow:**
```css
.grid-container {
  grid-auto-flow: dense;
}
```

3. **Minmax Function:**
```css
.grid-container {
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

4. **Grid Alignment:**
```css
.header {
  justify-self: center;
  align-self: start;
}
```

5. **Grid Spanning:**
```css
.featured-item {
  grid-column: span 2;
  grid-row: span 2;
}
```

**Accessibility Considerations:**
- Maintain logical source order
- Ensure proper heading hierarchy
- Use ARIA landmarks
- Test with screen readers
- Ensure keyboard navigation
- Provide sufficient color contrast
- Use semantic HTML elements
- Test with different zoom levels

**Performance Considerations:**
- Avoid excessive nesting of grids
- Use `will-change` for animated grid items
- Minimize layout thrashing
- Use CSS containment
- Optimize grid item rendering
- Consider using `content-visibility` for large grids
- Test performance with DevTools
- Implement lazy loading for grid content

**Common Grid Patterns:**

1. **Holy Grail Layout:**
```css
.grid-container {
  display: grid;
  grid-template:
    "header header header" 100px
    "sidebar main aside" 1fr
    "footer footer footer" 100px
    / 200px 1fr 200px;
}
```

2. **Masonry Layout:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-auto-rows: 150px;
  gap: 20px;
}

.grid-item {
  grid-row: span 2;
}
```

3. **Responsive Image Gallery:**
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px;
}
```

4. **Dashboard Layout:**
```css
.dashboard {
  display: grid;
  grid-template-columns: 250px 1fr;
  grid-template-rows: 80px 1fr;
  grid-template-areas:
    "sidebar header"
    "sidebar main";
}
```

5. **Card Layout:**
```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}
```

**Grid vs. Flexbox:**

| Feature            | Grid             | Flexbox          |
|--------------------|------------------|------------------|
| Dimension          | Two-dimensional  | One-dimensional  |
| Alignment          | Excellent        | Excellent        |
| Responsiveness     | Easy             | Easy             |
| Complex Layouts    | Excellent        | Good             |
| Item Ordering      | Limited          | Easy             |
| Browser Support    | Modern browsers  | Excellent        |
| Use Case           | Page Layouts     | Components       |

**Conclusion:**
CSS Grid is an essential tool for modern web layouts, offering powerful two-dimensional layout capabilities. When combined with Flexbox, you can create sophisticated, responsive designs that work across all devices and screen sizes. Grid is particularly well-suited for page layouts and complex grid-based designs, while Flexbox excels at one-dimensional layouts and component-level designs.

**Grid Container Properties:**

1. **display: grid**
   - Enables grid layout
   - Creates grid formatting context
   - Direct children become grid items

2. **grid-template-columns**
   - Defines column tracks
   - Values: length, percentage, fr (fraction), minmax(), repeat()
   ```css
   .container {
     grid-template-columns: 200px 1fr 30%;
   }
   ```

3. **grid-template-rows**
   - Defines row tracks
   - Values: same as grid-template-columns
   ```css
   .container {
     grid-template-rows: 100px auto 200px;
   }
   ```

4. **gap**
   - Sets spacing between grid items
   - Values: length or percentage
   ```css
   .container {
     gap: 20px;
   }
   ```

5. **grid-template-areas**
   - Defines named grid areas
   - Values: strings representing area names
   ```css
   .container {
     grid-template-areas:
       "header header"
       "sidebar main"
       "footer footer";
   }
   ```

6. **justify-content**
   - Aligns grid along the inline (row) axis
   - Values: start, end, center, stretch, space-between, space-around, space-evenly
   ```css
   .container {
     justify-content: center;
   }
   ```

7. **align-content**
   - Aligns grid along the block (column) axis
   - Values: same as justify-content
   ```css
   .container {
     align-content: start;
   }
   ```

**Grid Item Properties:**

1. **grid-column**
   - Controls item column placement
   - Values: line numbers, span
   ```css
   .item {
     grid-column: 1 / 3;
   }
   ```

2. **grid-row**
   - Controls item row placement
   - Values: same as grid-column
   ```css
   .item {
     grid-row: 2 / 4;
   }
   ```

3. **grid-area**
   - Shorthand for grid-row and grid-column
   - Can reference named areas
   ```css
   .item {
     grid-area: header;
   }
   ```

4. **justify-self**
   - Aligns item along inline axis
   - Values: start, end, center, stretch
   ```css
   .item {
     justify-self: center;
   }
   ```

5. **align-self**
   - Aligns item along block axis
   - Values: same as justify-self
   ```css
   .item {
     align-self: end;
   }
   ```

**Common Grid Patterns:**

1. **Responsive Grid:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}
```

2. **Masonry Layout:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 150px;
  gap: 20px;
}

.grid-item {
  grid-row: span 2;
}
```

3. **Holy Grail Layout:**
```css
.container {
  display: grid;
  grid-template:
    "header header header" 100px
    "sidebar main aside" 1fr
    "footer footer footer" 100px
    / 200px 1fr 200px;
  min-height: 100vh;
}
```

4. **Card Layout:**
```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}
```

5. **Image Gallery:**
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px;
}
```

**Grid Best Practices:**

1. Use semantic HTML with grid
2. Prefer grid over floats for complex layouts
3. Use fr units for flexible sizing
4. Combine with media queries for responsive designs
5. Use named grid areas for better readability
6. Avoid nesting too many grid containers
7. Use minmax() for flexible track sizing
8. Test across browsers for consistent behavior

**Accessibility Considerations:**

- Ensure logical source order matches visual order
- Use proper heading hierarchy
- Maintain keyboard navigation
- Consider screen reader users
- Test with high contrast modes

**Performance Considerations:**

- Avoid excessive nesting of grid containers
- Use will-change for animated grid items
- Minimize layout thrashing
- Use contain: layout when appropriate
- Avoid unnecessary reflows

**Grid vs. Flexbox:**

| Feature            | Grid             | Flexbox          |
|--------------------|------------------|------------------|
| Dimension          | Two-dimensional  | One-dimensional  |
| Alignment          | Excellent        | Excellent        |
| Responsiveness     | Easy             | Easy             |
| Complex Layouts    | Excellent        | Good             |
| Item Ordering      | Limited          | Easy             |
| Browser Support    | Modern browsers  | Excellent        |
| Use Case           | Page Layouts     | Components       |

**Common Grid Mistakes:**

1. Forgetting to set grid-template-columns
2. Overusing fixed track sizes
3. Not using gap for spacing
4. Ignoring grid-template-areas
5. Using fixed widths with grid items
6. Not testing in older browsers
7. Over-nesting grid containers
8. Forgetting to set min-width/max-width

**Advanced Grid Techniques:**

1. **Subgrid:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.grid-item {
  display: grid;
  grid-template-columns: subgrid;
}
```

2. **Aspect Ratio Boxes:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  aspect-ratio: 1;
}
```

3. **Sticky Sidebar:**
```css
.layout {
  display: grid;
  grid-template-columns: 250px 1fr;
  height: 100vh;
}

.sidebar {
  position: sticky;
  top: 0;
}
```

4. **Responsive Masonry:**
```css
.masonry {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-auto-rows: 150px;
  gap: 20px;
}

.masonry-item {
  grid-row: span 2;
}
```

5. **Dynamic Grid:**
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
```

**Conclusion:**

CSS Grid is an essential tool for modern web layouts, offering powerful two-dimensional layout capabilities. When combined with Flexbox, you can create sophisticated, responsive designs that work across all devices and screen sizes. Grid is particularly well-suited for page layouts and complex grid-based designs, while Flexbox excels at one-dimensional layouts and component-level designs.

**4.7 Media Queries and Responsive Design**

Media queries are a fundamental tool for creating responsive websites that adapt to different screen sizes and devices. They allow you to apply CSS rules based on various device characteristics.

```css
/* Basic Media Query Structure */
@media media-type and (media-feature) {
  /* CSS rules */
}
```

**Media Types:**
- `all` (default) - All devices
- `screen` - Computer screens, tablets, smartphones
- `print` - Printers and print preview
- `speech` - Screen readers

**Common Media Features:**
1. **Width and Height:**
   - `width`, `min-width`, `max-width`
   - `height`, `min-height`, `max-height`
   ```css
   @media (min-width: 768px) {
     .container {
       width: 750px;
     }
   }
   ```

2. **Orientation:**
   - `portrait` - Height > Width
   - `landscape` - Width > Height
   ```css
   @media (orientation: landscape) {
     .header {
       height: 100vh;
     }
   }
   ```

3. **Resolution:**
   - `resolution` - Device pixel density
   - `min-resolution`, `max-resolution`
   ```css
   @media (min-resolution: 2dppx) {
     .logo {
       background-image: url('logo@2x.png');
     }
   }
   ```

4. **Aspect Ratio:**
   - `aspect-ratio` - Width to height ratio
   ```css
   @media (aspect-ratio: 16/9) {
     .video-container {
       padding-top: 56.25%;
     }
   }
   ```

**Responsive Design Strategies:**

1. **Mobile-First Approach:**
```css
/* Base styles for mobile */
.container {
  padding: 10px;
}

/* Styles for larger screens */
@media (min-width: 768px) {
  .container {
    padding: 20px;
  }
}
```

2. **Breakpoint Selection:**
```css
/* Common breakpoints */
@media (min-width: 576px) { /* Small devices */ }
@media (min-width: 768px) { /* Tablets */ }
@media (min-width: 992px) { /* Desktops */ }
@media (min-width: 1200px) { /* Large desktops */ }
```

3. **Fluid Layouts:**
```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
```

4. **Responsive Typography:**
```css
html {
  font-size: 16px;
}

@media (min-width: 768px) {
  html {
    font-size: 18px;
  }
}
```

5. **Responsive Images:**
```html
<picture>
  <source media="(min-width: 1200px)" srcset="large.jpg">
  <source media="(min-width: 768px)" srcset="medium.jpg">
  <img src="small.jpg" alt="Description">
</picture>
```

**Advanced Media Query Techniques:**

1. **Combining Conditions:**
```css
@media (min-width: 768px) and (max-width: 1199px) {
  /* Styles for tablets */
}
```

2. **Dark Mode Support:**
```css
@media (prefers-color-scheme: dark) {
  body {
    background-color: #121212;
    color: #ffffff;
  }
}
```

3. **Reduced Motion:**
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

4. **High Contrast Mode:**
```css
@media (prefers-contrast: high) {
  .button {
    border: 2px solid black;
  }
}
```

5. **Print Styles:**
```css
@media print {
  .no-print {
    display: none;
  }
  
  body {
    font-size: 12pt;
    color: black;
  }
}
```

**Responsive Design Best Practices:**

1. Use relative units (em, rem, %) instead of fixed units (px)
2. Implement mobile-first design approach
3. Use CSS Grid and Flexbox for flexible layouts
4. Optimize images for different screen sizes
5. Test on real devices and emulators
6. Use progressive enhancement
7. Consider performance implications
8. Implement responsive navigation patterns
9. Use CSS variables for consistent styling
10. Test with different zoom levels

**Common Responsive Patterns:**

1. **Hamburger Menu:**
```css
.nav {
  display: none;
}

@media (min-width: 768px) {
  .nav {
    display: flex;
  }
  
  .hamburger {
    display: none;
  }
}
```

2. **Responsive Grid:**
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
```

3. **Card Layout:**
```css
.card {
  width: 100%;
}

@media (min-width: 768px) {
  .card {
    width: 48%;
  }
}

@media (min-width: 992px) {
  .card {
    width: 32%;
  }
}
```

4. **Responsive Tables:**
```css
@media (max-width: 768px) {
  table, thead, tbody, th, td, tr {
    display: block;
  }
  
  td {
    position: relative;
    padding-left: 50%;
  }
  
  td::before {
    content: attr(data-label);
    position: absolute;
    left: 0;
    width: 45%;
    padding-right: 10px;
  }
}
```

5. **Viewport Units:**
```css
.header {
  height: 100vh;
}

.section {
  min-height: 50vh;
}
```

**Accessibility Considerations:**

1. Ensure proper text scaling
2. Maintain logical content order
3. Use proper heading hierarchy
4. Test with screen readers
5. Ensure sufficient color contrast
6. Provide alternative text for images
7. Make interactive elements touch-friendly
8. Test with keyboard navigation

**Performance Considerations:**

1. Optimize images for different screen sizes
2. Use responsive image techniques (srcset, picture)
3. Implement lazy loading
4. Use CSS containment
5. Minimize layout shifts
6. Optimize critical rendering path
7. Use media queries to load appropriate resources
8. Implement code splitting

**Testing Responsive Designs:**

1. Use browser developer tools
2. Test on real devices
3. Use online testing tools (BrowserStack, LambdaTest)
4. Check different orientations
5. Test with different zoom levels
6. Verify accessibility
7. Check performance metrics
8. Test with different network conditions

**Common Responsive Design Mistakes:**

1. Using fixed widths
2. Not testing on real devices
3. Ignoring performance implications
4. Not considering accessibility
5. Using too many breakpoints
6. Not implementing touch-friendly interfaces
7. Forgetting to test landscape orientation
8. Not optimizing images for different screens

**Modern Responsive Design Tools:**

1. CSS Grid and Flexbox
2. Viewport units (vw, vh, vmin, vmax)
3. CSS variables
4. Container queries (experimental)
5. Aspect-ratio property
6. clamp() function
7. min(), max() functions
8. prefers-reduced-motion media feature

**Practical Example: Responsive Portfolio Layout**

```html
<div class="portfolio-container">
  <header class="portfolio-header">
    <h1>My Portfolio</h1>
    <nav class="main-nav">
      <button class="hamburger">☰</button>
      <ul class="nav-links">
        <li><a href="#about">About</a></li>
        <li><a href="#projects">Projects</a></li>
        <li><a href="#contact">Contact</a></li>
      </ul>
    </nav>
  </header>

  <main class="portfolio-content">
    <section id="about" class="about-section">
      <h2>About Me</h2>
      <div class="about-content">
        <img src
Okay, here's an in-depth HTML and CSS masterclass covering the fundamentals, best practices, and advanced techniques, all culminating in a comprehensive portfolio-ready project:

**HTML & CSS Masterclass: Building a Foundation for Web Development and Design**

**Target Audience:** Beginners with little to no prior experience in web development.

**Goal:** Equip you with the fundamental knowledge of HTML and CSS to create static websites and prepare you for more advanced front-end development concepts.

**Methodology:**

*   **Concept Explanation:** Each topic starts with a clear and concise explanation.
*   **Code Examples:** Numerous examples illustrate the concepts in action.
*   **Best Practices:** Emphasize writing clean, maintainable, and accessible code.
*   **Capstone Project:** A real-world project to solidify your skills and showcase in your portfolio.

**Module 1: Introduction to HTML**

**1.1 What is HTML?**

*   **HTML (HyperText Markup Language):** The standard markup language for creating web pages. It structures the content of a web page.
*   **Structure, Not Style:** HTML defines the meaning and hierarchy of content (headings, paragraphs, lists, images, etc.), but it doesn't dictate how it looks. That's where CSS comes in.
*   **Tags, Elements, and Attributes:**
    *   **Tags:** Keywords enclosed in angle brackets (e.g., `<p>`, `<h1>`, `<img>`).
    *   **Elements:** A complete piece of content, including the opening tag, content, and closing tag (e.g., `<p>This is a paragraph.</p>`).
    *   **Attributes:** Provide additional information about an element and are included within the opening tag (e.g., `<img src="image.jpg" alt="Description">`).

**1.2 Basic HTML Structure**

```html
<!DOCTYPE html> 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Web Page</title>
    <link rel="stylesheet" href="style.css"> </head>
<body>

    <h1>Welcome to My Website</h1>
    <p>This is a paragraph of text.</p>

    <script src="script.js"></script> </body>
</html>
```

*   **`<!DOCTYPE html>`:** Declares the document as HTML5.
*   **`<html>`:** The root element of the page.
    *   `lang="en"` attribute specifies the language as English.
*   **`<head>`:** Contains meta-information about the page (not displayed on the page itself).
    *   **`<meta charset="UTF-8">`:** Sets the character encoding to UTF-8, supporting a wide range of characters.
    *   **`<meta name="viewport"...>`:** Configures how the page scales on different devices (essential for responsive design).
    *   **`<title>`:** Sets the title that appears in the browser tab.
    *   **`<link rel="stylesheet" href="style.css">`:** Links an external CSS file to style the page.
*   **`<body>`:** Contains the visible content of the page.
    *   **`<h1>`:** A top-level heading.
    *   **`<p>`:** A paragraph of text.
*   **`<script src="script.js"></script>`:** Links to an external JavaScript file (for interactivity). It's often placed at the end of the `<body>` so the HTML loads first.

**1.3 Common HTML Elements**

*   **Headings:** `<h1>` to `<h6>` (<h1> is the most important, <h6> the least).
    ```html
    <h1>Main Title</h1>
    <h2>Section Title</h2>
    <h3>Subsection Title</h3>
    ```
    Best Practices:
    - Use only one `<h1>` per page
    - Maintain proper heading hierarchy
    - Don't skip heading levels (e.g., don't go from h2 to h4)

*   **Paragraphs:** `<p>`
    ```html
    <p>This is a paragraph of text. It can contain <strong>bold text</strong>, 
    <em>italic text</em>, and <a href="#">links</a>.</p>
    ```
    Common Pitfalls:
    - Avoid using `<br>` tags for spacing (use CSS margin/padding instead)
    - Don't use empty paragraphs for spacing

*   **Links:** `<a>` (anchor)
    ```html
    <!-- Basic link -->
    <a href="https://www.example.com">Visit Example</a>

    <!-- Link with target -->
    <a href="https://www.example.com" target="_blank" rel="noopener noreferrer">
      Visit Example in New Tab
    </a>

    <!-- Email link -->
    <a href="mailto:example@example.com">Email Us</a>

    <!-- Telephone link -->
    <a href="tel:+1234567890">Call Us</a>
    ```
    Key Attributes:
    - `href`: Specifies the URL or resource
    - `target`: Controls where link opens (_blank, _self, _parent, _top)
    - `rel`: Specifies relationship (important for security with target="_blank")
    - `download`: Forces download of linked resource

*   **Images:** `<img>`
    ```html
    <!-- Basic image -->
    <img src="images/logo.png" alt="Company Logo">

    <!-- Responsive image -->
    <img src="images/hero.jpg" 
         alt="Hero Image"
         srcset="images/hero-320.jpg 320w,
                 images/hero-640.jpg 640w,
                 images/hero-1280.jpg 1280w"
         sizes="(max-width: 600px) 100vw, 50vw">

    <!-- Lazy-loaded image -->
    <img src="placeholder.jpg" 
         data-src="image.jpg" 
         alt="Description"
         class="lazyload">
    ```
    Best Practices:
    - Always include meaningful alt text
    - Use srcset for responsive images
    - Implement lazy loading for better performance
    - Optimize image file sizes
*   **Lists:**
    *   **Unordered Lists (`<ul>`):** Bulleted lists.
    *   **Ordered Lists (`<ol>`):** Numbered lists.
    *   **List Items (`<li>`):** Items within a list.

    ```html
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>

    <ol>
        <li>First step</li>
        <li>Second step</li>
    </ol>
    ```
*   **Divisions (`<div>`):** Generic containers used to group other elements for styling or structural purposes.
*   **Spans (`<span>`):** Inline containers used to apply styles to a specific portion of text within a larger element.

**Module 2: Introduction to CSS**

**2.1 What is CSS?**

*   **CSS (Cascading Style Sheets):** The language used to style the appearance of web pages.
*   **Separation of Concerns:** CSS separates the styling from the HTML structure, making code cleaner and easier to maintain.
*   **Selectors, Properties, and Values:**
    *   **Selectors:** Target specific HTML elements to style.
    *   **Properties:** The aspects of an element you want to style (e.g., `color`, `font-size`, `background-color`).
    *   **Values:** The specific settings for a property (e.g., `red`, `16px`, `#f0f0f0`).

**2.2 Ways to Add CSS**

*   **Inline CSS:** Applied directly within an HTML tag using the `style` attribute (generally discouraged for maintainability).

    ```html
    <p style="color: blue; font-size: 18px;">This is a blue paragraph.</p>
    ```
*   **Internal CSS:** Placed within a `<style>` tag in the `<head>` of the HTML document (useful for styles specific to a single page).

    ```html
    <head>
        <style>
            p {
                color: green;
                font-size: 16px;
            }
        </style>
    </head>
    ```
*   **External CSS:** Stored in a separate `.css` file and linked to the HTML using the `<link>` tag (best practice for most cases).

    ```html
    <!-- In your HTML file (index.html) -->
    <head>
        <link rel="stylesheet" href="styles.css">
    </head>
    ```

    ```css
    /* In your CSS file (styles.css) */
    p {
        color: black;
        font-size: 14px;
    }
    ```

**2.3 CSS Selectors**

*   **Element Selector:** Targets elements by their tag name.
    ```css
    /* Style all paragraphs */
    p {
        color: navy;
        line-height: 1.5;
        margin-bottom: 1em;
    }

    /* Style all headings */
    h1, h2, h3 {
        font-family: 'Arial', sans-serif;
        color: #333;
    }
    ```

*   **ID Selector:** Targets a single element with a specific `id` attribute.
    ```css
    #main-header {
        background-color: #0077cc;
        color: white;
        padding: 20px;
        text-align: center;
    }

    #contact-form {
        max-width: 600px;
        margin: 0 auto;
        padding: 20px;
        border: 1px solid #ddd;
    }
    ```

*   **Class Selector:** Targets elements with a specific `class` attribute.
    ```css
    .btn {
        display: inline-block;
        padding: 10px 20px;
        background-color: #0077cc;
        color: white;
        text-decoration: none;
        border-radius: 4px;
        transition: background-color 0.3s;
    }

    .btn:hover {
        background-color: #005fa3;
    }

    .warning {
        color: #dc3545;
        background-color: #f8d7da;
        padding: 10px;
        border: 1px solid #f5c6cb;
        border-radius: 4px;
    }
    ```

*   **Attribute Selectors:** Target elements based on attributes.
    ```css
    /* Links with target="_blank" */
    a[target="_blank"] {
        color: #0077cc;
    }

    /* Images with alt text */
    img[alt] {
        border: 2px solid #0077cc;
    }

    /* Inputs of type text */
    input[type="text"] {
        width: 100%;
        padding: 8px;
        border: 1px solid #ddd;
    }
    ```

*   **Pseudo-classes:** Target elements in specific states.
    ```css
    /* Style visited links */
    a:visited {
        color: #551a8b;
    }

    /* Style first child */
    li:first-child {
        font-weight: bold;
    }

    /* Style odd table rows */
    tr:nth-child(odd) {
        background-color: #f8f9fa;
    }

    /* Style focused inputs */
    input:focus {
        outline: 2px solid #0077cc;
        border-color: #0077cc;
    }
    ```

*   **Combinators:** Combine selectors for more specific targeting.
    ```css
    /* Direct child selector */
    nav > ul {
        list-style: none;
        padding: 0;
    }

    /* Adjacent sibling selector */
    h2 + p {
        margin-top: 0;
    }

    /* General sibling selector */
    h2 ~ p {
        color: #666;
    }

    /* Descendant selector */
    .article p {
        line-height: 1.6;
    }
    ```

*   **Universal Selector:** Selects all elements.
    ```css
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }
    ```

Best Practices:
- Use classes for reusable styles
- Avoid overusing ID selectors
- Keep specificity low when possible
- Use meaningful class names (BEM methodology recommended)
- Avoid inline styles
- Use shorthand properties when appropriate

**2.4 Common CSS Properties**

*   **Text Styling:**
    *   `color`: Sets the text color.
      ```css
      h1 {
        color: #333; /* Dark gray */
      }
      ```
    *   `font-family`: Sets the font.
      ```css
      body {
        font-family: 'Arial', sans-serif;
      }
      ```
    *   `font-size`: Sets the text size.
      ```css
      p {
        font-size: 1rem; /* Responsive sizing */
      }
      ```
    *   `font-weight`: Sets text boldness (e.g., `normal`, `bold`).
      ```css
      strong {
        font-weight: bold;
      }
      ```
    *   `text-align`: Aligns text (e.g., `left`, `center`, `right`).
      ```css
      .center {
        text-align: center;
      }
      ```
    *   `text-decoration`: Adds decorations (e.g., `underline`, `line-through`).
      ```css
      a {
        text-decoration: none; /* Remove underline */
      }
      ```

*   **Box Model:** (We'll cover this in more detail later)
    *   `width`: Sets the width of an element.
      ```css
      .container {
        width: 80%;
        max-width: 1200px;
      }
      ```
    *   `height`: Sets the height of an element.
      ```css
      .hero {
        height: 100vh;
      }
      ```
    *   `margin`: Sets the space outside the element's border.
      ```css
      .section {
        margin: 2rem 0;
      }
      ```
    *   `padding`: Sets the space inside the element's border.
      ```css
      .card {
        padding: 1.5rem;
      }
      ```
    *   `border`: Sets a border around the element.
      ```css
      .button {
        border: 2px solid #0077cc;
        border-radius: 4px;
      }
      ```

*   **Background:**
    *   `background-color`: Sets the background color.
      ```css
      header {
        background-color: #f8f9fa;
      }
      ```
    *   `background-image`: Sets a background image.
      ```css
      .hero {
        background-image: url('hero.jpg');
      }
      ```
    *   `background-repeat`: Controls how a background image repeats.
      ```css
      .pattern {
        background-image: url('pattern.png');
        background-repeat: repeat;
      }
      ```
    *   `background-position`: Controls the position of a background image.
      ```css
      .hero {
        background-position: center top;
      }
      ```

**Module 3: Intermediate HTML**

**3.1 Forms**

Forms are used to collect user input. Here's a comprehensive example with styling and validation:

```html
<form class="contact-form" action="/submit-form" method="post" novalidate>
    <div class="form-group">
        <label for="name">Full Name:</label>
        <input type="text" id="name" name="name" required
               placeholder="Enter your full name"
               minlength="2" maxlength="50"
               pattern="[A-Za-z ]+">
        <span class="error-message">Please enter a valid name</span>
    </div>

    <div class="form-group">
        <label for="email">Email Address:</label>
        <input type="email" id="email" name="email" required
               placeholder="example@domain.com"
               pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}$">
        <span class="error-message">Please enter a valid email</span>
    </div>

    <div class="form-group">
        <label for="phone">Phone Number:</label>
        <input type="tel" id="phone" name="phone"
               placeholder="123-456-7890"
               pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}">
        <span class="error-message">Format: 123-456-7890</span>
    </div>

    <div class="form-group">
        <label for="message">Your Message:</label>
        <textarea id="message" name="message" required
                  placeholder="Type your message here..."
                  minlength="10" maxlength="500"></textarea>
        <span class="error-message">Message must be 10-500 characters</span>
    </div>

    <div class="form-group">
        <label>Preferred Contact Method:</label>
        <div class="radio-group">
            <label>
                <input type="radio" name="contact-method" value="email" checked>
                Email
            </label>
            <label>
                <input type="radio" name="contact-method" value="phone">
                Phone
            </label>
        </div>
    </div>

    <div class="form-group">
        <label>Interests:</label>
        <div class="checkbox-group">
            <label>
                <input type="checkbox" name="interests[]" value="web-dev">
                Web Development
            </label>
            <label>
                <input type="checkbox" name="interests[]" value="design">
                Design
            </label>
            <label>
                <input type="checkbox" name="interests[]" value="seo">
                SEO
            </label>
        </div>
    </div>

    <div class="form-group">
        <label for="country">Country:</label>
        <select id="country" name="country" required>
            <option value="">Select your country</option>
            <option value="US">United States</option>
            <option value="CA">Canada</option>
            <option value="UK">United Kingdom</option>
            <!-- Add more countries -->
        </select>
    </div>

    <div class="form-group">
        <button type="submit">Send Message</button>
        <button type="reset">Clear Form</button>
    </div>
</form>
```

```css
/* Form Styling */
.contact-form {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    background: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 8px;
}

.form-group {
    margin-bottom: 20px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input[type="text"],
input[type="email"],
input[type="tel"],
textarea,
select {
    width: 100%;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
}

input:focus,
textarea:focus,
select:focus {
    outline: none;
    border-color: #0077cc;
    box-shadow: 0 0 5px rgba(0, 119, 204, 0.3);
}

.radio-group,
.checkbox-group {
    display: flex;
    gap: 15px;
    margin-top: 5px;
}

button {
    padding: 10px 20px;
    background-color: #0077cc;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-right: 10px;
}

button:hover {
    background-color: #005fa3;
}

.error-message {
    display: none;
    color: #dc3545;
    font-size: 0.9em;
    margin-top: 5px;
}

input:invalid:not(:placeholder-shown),
textarea:invalid:not(:placeholder-shown) {
    border-color: #dc3545;
}

input:invalid:not(:placeholder-shown) + .error-message,
textarea:invalid:not(:placeholder-shown) + .error-message {
    display: block;
}
```

**Key Features:**
- **Accessibility:** Proper label associations, focus states, and ARIA attributes
- **Validation:** HTML5 validation with custom error messages
- **Responsive Design:** Flexbox layout for radio/checkbox groups
- **User Experience:** Clear error states and helpful placeholders
- **Security:** `novalidate` attribute for custom validation
- **Styling:** Consistent design with focus states and hover effects

**Best Practices:**
1. Always use `<label>` elements with `for` attributes
2. Use proper input types for better mobile experience
3. Implement client-side validation with HTML5 attributes
4. Provide clear error messages
5. Use semantic HTML elements
6. Ensure proper tab order
7. Make forms keyboard-navigable
8. Use ARIA attributes for accessibility
9. Implement server-side validation (not shown in this example)
10. Consider progressive enhancement for older browsers

**3.2 Tables**

Tables are used to display tabular data in a structured format. Here's a comprehensive example with styling and accessibility features:

```html
<div class="table-container">
  <table class="data-table">
    <caption class="sr-only">Employee Salary Information</caption>
    <thead>
      <tr>
        <th scope="col">Name</th>
        <th scope="col">Department</th>
        <th scope="col">Position</th>
        <th scope="col">Salary</th>
        <th scope="col">Start Date</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <th scope="row">John Doe</th>
        <td>Sales</td>
        <td>Account Manager</td>
        <td>$75,000</td>
        <td>2021-03-15</td>
      </tr>
      <tr>
        <th scope="row">Jane Smith</th>
        <td>Marketing</td>
        <td>Content Strategist</td>
        <td>$65,000</td>
        <td>2020-08-01</td>
      </tr>
      <!-- Additional rows -->
    </tbody>
    <tfoot>
      <tr>
        <td colspan="4">Total Employees</td>
        <td>2</td>
      </tr>
    </tfoot>
  </table>
</div>
```

```css
/* Table Styling */
.table-container {
  overflow-x: auto;
  margin: 2rem 0;
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.data-table {
  width: 100%;
  border-collapse: collapse;
  font-size: 0.9rem;
}

.data-table th,
.data-table td {
  padding: 12px 15px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

.data-table th {
  background-color: #f8f9fa;
  font-weight: 600;
  position: sticky;
  top: 0;
}

.data-table tbody tr:hover {
  background-color: #f5f5f5;
}

.data-table tfoot {
  background-color: #f8f9fa;
  font-weight: bold;
}

/* Responsive Table */
@media (max-width: 768px) {
  .data-table {
    display: block;
    width: 100%;
  }
  
  .data-table thead,
  .data-table tbody,
  .data-table th,
  .data-table td,
  .data-table tr {
    display: block;
  }
  
  .data-table thead {
    position: absolute;
    top: -9999px;
    left: -9999px;
  }
  
  .data-table tr {
    border: 1px solid #ddd;
    margin-bottom: 1rem;
  }
  
  .data-table td {
    border: none;
    border-bottom: 1px solid #eee;
    position: relative;
    padding-left: 50%;
  }
  
  .data-table td::before {
    content: attr(data-label);
    position: absolute;
    left: 0;
    width: 45%;
    padding-left: 15px;
    font-weight: bold;
    white-space: nowrap;
  }
}

/* Accessibility */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
```

**Key Features:**
- **Accessibility:** Proper use of scope attributes, ARIA roles, and screen reader-only text
- **Responsive Design:** Mobile-friendly layout with horizontal scrolling
- **Styling:** Clean, modern design with hover effects
- **Structure:** Includes header, body, and footer sections
- **Semantic HTML:** Proper use of table elements and attributes

**Best Practices:**
1. Use `<th>` elements with `scope` attributes for accessibility
2. Include a `<caption>` for table context
3. Use `<thead>`, `<tbody>`, and `<tfoot>` for better structure
4. Implement responsive design for mobile devices
5. Add visual feedback for interactive elements
6. Use proper contrast and spacing
7. Consider using CSS Grid for complex table layouts
8. Implement sorting and filtering with JavaScript (not shown in this example)

**Advanced Table Features:**
1. **Sortable Columns:**
```javascript
// JavaScript for sortable columns
document.querySelectorAll('.data-table th').forEach(header => {
  header.addEventListener('click', () => {
    const table = header.closest('table');
    const columnIndex = Array.prototype.indexOf.call(header.parentElement.children, header);
    const rows = Array.from(table.querySelectorAll('tbody tr'));
    
    rows.sort((a, b) => {
      const aText = a.children[columnIndex].textContent.trim();
      const bText = b.children[columnIndex].textContent.trim();
      return aText.localeCompare(bText);
    });
    
    table.querySelector('tbody').append(...rows);
  });
});
```

2. **Pagination:**
```html
<div class="table-pagination">
  <button class="pagination-btn" disabled>Previous</button>
  <span class="page-info">Page 1 of 3</span>
  <button class="pagination-btn">Next</button>
</div>
```

3. **Filtering:**
```html
<div class="table-filters">
  <input type="text" class="filter-input" placeholder="Search...">
  <select class="filter-select">
    <option value="">All Departments</option>
    <option value="Sales">Sales</option>
    <option value="Marketing">Marketing</option>
  </select>
</div>
```

4. **Export Options:**
```html
<div class="table-export">
  <button class="export-btn">Export as CSV</button>
  <button class="export-btn">Export as PDF</button>
</div>
```

**Accessibility Considerations:**
- Use proper ARIA roles and attributes
- Ensure keyboard navigation works
- Provide text alternatives for visual elements
- Use sufficient color contrast
- Test with screen readers
- Implement proper focus management

**Performance Considerations:**
- Virtualize large tables
- Implement lazy loading for table data
- Use efficient sorting algorithms
- Optimize table rendering
- Consider server-side pagination for large datasets

**When to Use Tables:**
- Displaying tabular data
- Financial reports
- Data comparisons
- Statistical information
- Product catalogs
- Timetables and schedules

**When Not to Use Tables:**
- Page layout (use CSS Grid or Flexbox instead)
- Non-tabular content
- Visual design elements
- Navigation menus
- Image galleries

**Modern Table Alternatives:**
1. **CSS Grid Layout:**
```css
.grid-table {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1px;
}

.grid-table > div {
  padding: 12px;
  border: 1px solid #ddd;
}
```

2. **Flexbox Layout:**
```css
.flex-table {
  display: flex;
  flex-direction: column;
}

.flex-table .row {
  display: flex;
}

.flex-table .cell {
  flex: 1;
  padding: 12px;
  border: 1px solid #ddd;
}
```

3. **Component-Based Tables:**
```javascript
// React example
function DataTable({ data }) {
  return (
    <table>
      <thead>
        <tr>
          {Object.keys(data[0]).map(header => (
            <th key={header}>{header}</th>
          ))}
        </tr>
      </thead>
      <tbody>
        {data.map((row, i) => (
          <tr key={i}>
            {Object.values(row).map((cell, j) => (
              <td key={j}>{cell}</td>
            ))}
          </tr>
        ))}
      </tbody>
    </table>
  );
}
```

**Conclusion:**
Tables remain an essential tool for displaying structured data on the web. By following modern best practices and implementing accessibility features, you can create tables that are both functional and user-friendly. Remember to consider responsive design and performance optimization when working with large datasets, and explore modern alternatives like CSS Grid and component-based approaches for more complex layouts.

**3.3 Semantic HTML5 Elements**

Semantic HTML5 elements provide meaning and structure to web content, improving accessibility, SEO, and maintainability. Here's a comprehensive example with styling and best practices:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Semantic HTML Example</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <!-- Header Section -->
    <header class="main-header">
        <div class="container">
            <h1>Website Title</h1>
            <p class="tagline">Your tagline here</p>
            
            <!-- Navigation -->
            <nav class="main-nav">
                <ul>
                    <li><a href="#about">About</a></li>
                    <li><a href="#services">Services</a></li>
                    <li><a href="#contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Main Content -->
    <main class="main-content">
        <div class="container">
            <!-- Article Section -->
            <article class="featured-article">
                <header>
                    <h2>Article Title</h2>
                    <p class="meta">Published on <time datetime="2023-08-01">August 1, 2023</time></p>
                </header>
                
                <section class="article-content">
                    <p>Main article content...</p>
                    
                    <figure>
                        <img src="image.jpg" alt="Description of image">
                        <figcaption>Image caption</figcaption>
                    </figure>
                </section>
                
                <footer class="article-footer">
                    <p>Written by Author Name</p>
                </footer>
            </article>

            <!-- Aside Section -->
            <aside class="sidebar">
                <section class="widget">
                    <h3>Related Links</h3>
                    <ul>
                        <li><a href="#">Link 1</a></li>
                        <li><a href="#">Link 2</a></li>
                    </ul>
                </section>
            </aside>
        </div>
    </main>

    <!-- Footer Section -->
    <footer class="main-footer">
        <div class="container">
            <p>&copy; 2023 Company Name. All rights reserved.</p>
            <nav class="footer-nav">
                <ul>
                    <li><a href="#">Privacy Policy</a></li>
                    <li><a href="#">Terms of Service</a></li>
                </ul>
            </nav>
        </div>
    </footer>
</body>
</html>
```

```css
/* Basic Reset */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

/* General Styles */
body {
    font-family: Arial, sans-serif;
    line-height: 1.6;
    color: #333;
}

.container {
    width: 90%;
    max-width: 1200px;
    margin: 0 auto;
}

/* Header Styles */
.main-header {
    background-color: #f8f9fa;
    padding: 20px 0;
    border-bottom: 1px solid #ddd;
}

.main-header h1 {
    font-size: 2.5rem;
    margin-bottom: 0.5rem;
}

.tagline {
    font-size: 1.2rem;
    color: #666;
}

.main-nav ul {
    list-style: none;
    margin-top: 1rem;
}

.main-nav li {
    display: inline-block;
    margin-right: 1rem;
}

.main-nav a {
    text-decoration: none;
    color: #0077cc;
}

/* Main Content Styles */
.main-content {
    display: grid;
    grid-template-columns: 3fr 1fr;
    gap: 2rem;
    padding: 2rem 0;
}

.featured-article {
    background-color: #fff;
    padding: 2rem;
    border: 1px solid #ddd;
    border-radius: 4px;
}

.article-content {
    margin-top: 1.5rem;
}

.article-content figure {
    margin: 1.5rem 0;
}

.article-content img {
    max-width: 100%;
    height: auto;
    border-radius: 4px;
}

figcaption {
    font-size: 0.9rem;
    color: #666;
    margin-top: 0.5rem;
}

/* Sidebar Styles */
.sidebar {
    background-color: #f8f9fa;
    padding: 1.5rem;
    border: 1px solid #ddd;
    border-radius: 4px;
}

.widget {
    margin-bottom: 1.5rem;
}

.widget h3 {
    margin-bottom: 1rem;
}

.widget ul {
    list-style: none;
}

.widget li {
    margin-bottom: 0.5rem;
}

/* Footer Styles */
.main-footer {
    background-color: #333;
    color: #fff;
    padding: 2rem 0;
    margin-top: 2rem;
}

.footer-nav ul {
    list-style: none;
    margin-top: 1rem;
}

.footer-nav li {
    display: inline-block;
    margin-right: 1rem;
}

.footer-nav a {
    color: #fff;
    text-decoration: none;
}

/* Responsive Design */
@media (max-width: 768px) {
    .main-content {
        grid-template-columns: 1fr;
    }
    
    .sidebar {
        order: -1;
        margin-bottom: 2rem;
    }
}
```

**Key Semantic Elements:**

1. **`<header>`**
   - Represents introductory content
   - Can be used at page level or within sections/articles
   - Typically contains headings, logos, navigation

2. **`<nav>`**
   - Defines navigation sections
   - Should contain major navigation links
   - Use aria-label for multiple nav elements

3. **`<main>`**
   - Contains the primary content
   - Should be unique per page
   - Helps screen readers identify main content

4. **`<article>`**
   - Represents self-contained content
   - Should make sense independently
   - Examples: blog posts, news articles, forum posts

5. **`<section>`**
   - Groups thematically related content
   - Should have a heading (h2-h6)
   - Use for distinct content areas

6. **`<aside>`**
   - Contains tangentially related content
   - Often used for sidebars, pull quotes
   - Can be nested within articles

7. **`<footer>`**
   - Represents footer content
   - Can contain copyright, contact info, links
   - Can be used at page or section level

**Additional Semantic Elements:**

1. **`<figure>` and `<figcaption>`**
   - For images, diagrams, code snippets
   - Figcaption provides caption/description

2. **`<time>`**
   - Represents dates/times
   - Use datetime attribute for machine-readable format

3. **`<mark>`**
   - Highlights text for reference
   - Useful for search results

4. **`<details>` and `<summary>`**
   - Creates expandable/collapsible content
   - Good for FAQs, additional info

**Best Practices:**

1. Use semantic elements appropriately
2. Maintain proper heading hierarchy
3. Use ARIA roles when needed
4. Ensure logical content flow
5. Use landmarks for accessibility
6. Validate HTML structure
7. Test with screen readers
8. Use microdata for rich snippets

**Accessibility Considerations:**

1. Use proper heading levels (h1-h6)
2. Add alt text for images
3. Use ARIA attributes when needed
4. Ensure keyboard navigation
5. Provide text alternatives
6. Use sufficient color contrast
7. Test with screen readers
8. Implement focus management

**SEO Benefits:**

1. Better content understanding by search engines
2. Improved document outline
3. Enhanced rich snippets
4. Better mobile optimization
5. Improved page speed
6. Enhanced user experience
7. Better content organization
8. Improved crawlability

**Common Mistakes:**

1. Using divs instead of semantic elements
2. Improper nesting of elements
3. Missing required attributes
4. Overusing section elements
5. Ignoring heading hierarchy
6. Not using landmarks
7. Forgetting alt text
8. Not testing accessibility

**Advanced Techniques:**

1. **Microdata:**
```html
<div itemscope itemtype="http://schema.org/Person">
  <span itemprop="name">John Doe</span>
  <span itemprop="jobTitle">Web Developer</span>
</div>
```

2. **ARIA Landmarks:**
```html
<nav role="navigation">
  <!-- Navigation content -->
</nav>

<main role="main">
  <!-- Main content -->
</main>
```

3. **Accessible Forms:**
```html
<form>
  <label for="name">Name:</label>
  <input type="text" id="name" name="name" required>
  
  <fieldset>
    <legend>Contact Method</legend>
    <label>
      <input type="radio" name="contact" value="email"> Email
    </label>
    <label>
      <input type="radio" name="contact" value="phone"> Phone
    </label>
  </fieldset>
</form>
```

4. **Responsive Images:**
```html
<picture>
  <source media="(min-width: 1200px)" srcset="large.jpg">
  <source media="(min-width: 768px)" srcset="medium.jpg">
  <img src="small.jpg" alt="Description">
</picture>
```

**Conclusion:**

Semantic HTML5 elements provide a powerful way to structure web content in a meaningful way. By using these elements appropriately, you can create websites that are more accessible, maintainable, and SEO-friendly. Remember to combine semantic markup with proper CSS styling and JavaScript interactivity to create modern, user-friendly web experiences.

**Module 4: Intermediate CSS**

**4.1 The Box Model**

The box model is a fundamental concept that describes how elements are rendered on a page as rectangular boxes. Understanding it is crucial for proper layout and spacing.

```html
<div class="box">
  This is a box with padding, border, and margin
</div>
```

```css
.box {
  /* Content dimensions */
  width: 300px;
  height: 200px;
  
  /* Padding */
  padding: 20px;
  
  /* Border */
  border: 5px solid #0077cc;
  border-radius: 8px;
  
  /* Margin */
  margin: 30px;
  
  /* Background */
  background-color: #f0f8ff;
  
  /* Text styling */
  color: #333;
  font-size: 16px;
  line-height: 1.5;
}
```

* **Content Box**: The innermost area containing the actual content
  - Controlled by width/height properties
  - Default background color is transparent
  - Text and child elements are rendered here

* **Padding**: Space between content and border
  - Adds to element's total size
  - Inherits background color
  - Useful for internal spacing
  ```css
  /* Individual sides */
  padding-top: 10px;
  padding-right: 15px;
  padding-bottom: 20px;
  padding-left: 15px;
  
  /* Shorthand */
  padding: 10px 15px 20px 15px; /* top right bottom left */
  padding: 10px 15px; /* vertical horizontal */
  padding: 10px; /* all sides */
  ```

* **Border**: Line surrounding padding and content
  - Adds to element's total size
  - Can have different styles, widths, and colors
  ```css
  /* Individual properties */
  border-width: 2px;
  border-style: solid;
  border-color: #0077cc;
  
  /* Shorthand */
  border: 2px solid #0077cc;
  
  /* Rounded corners */
  border-radius: 8px;
  ```

* **Margin**: Space outside the border
  - Creates space between elements
  - Transparent (doesn't inherit background)
  - Can collapse with adjacent margins
  ```css
  /* Individual sides */
  margin-top: 20px;
  margin-right: 15px;
  margin-bottom: 20px;
  margin-left: 15px;
  
  /* Shorthand */
  margin: 20px 15px; /* vertical horizontal */
  margin: 20px; /* all sides */
  
  /* Centering elements */
  margin: 0 auto;
  ```

**Box Model Visualization:**

```
+---------------------------+
|         Margin            |
|  +---------------------+  |
|  |      Border         |  |
|  |  +---------------+  |  |
|  |  |    Padding    |  |  |
|  |  |  +---------+  |  |  |
|  |  |  | Content |  |  |  |
|  |  |  +---------+  |  |  |
|  |  +---------------+  |  |
|  +---------------------+  |
+---------------------------+
```

**Box-Sizing Property:**

By default, padding and border are added to the element's width/height. The `box-sizing` property changes this behavior:

```css
/* Default behavior */
.box-default {
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  /* Total width = 300 + 20*2 + 5*2 = 350px */
}

/* Border-box behavior */
.box-border {
  box-sizing: border-box;
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  /* Total width = 300px (includes padding and border) */
}
```

Best Practices:
- Use `box-sizing: border-box` for more predictable layouts
- Use margin for spacing between elements
- Use padding for internal spacing within elements
- Be consistent with spacing values (e.g., use multiples of 4px or 8px)
- Use CSS variables for consistent spacing values

**4.2 Display Property**

The `display` property is one of the most important CSS properties, controlling how an element is rendered and how it interacts with other elements.

```html
<div class="block-example">Block Element</div>
<span class="inline-example">Inline Element</span>
<div class="inline-block-example">Inline-Block Element</div>
<div class="hidden-example">Hidden Element</div>
```

```css
/* Block-level elements */
.block-example {
  display: block;
  width: 80%;
  padding: 20px;
  background-color: #f0f8ff;
  border: 1px solid #0077cc;
  margin-bottom: 10px;
}

/* Inline elements */
.inline-example {
  display: inline;
  padding: 5px;
  background-color: #fff3cd;
  border: 1px solid #ffc107;
  /* width and height have no effect on inline elements */
}

/* Inline-block elements */
.inline-block-example {
  display: inline-block;
  width: 200px;
  padding: 10px;
  background-color: #d4edda;
  border: 1px solid #28a745;
  margin: 5px;
}

/* Hidden elements */
.hidden-example {
  display: none;
}
```

**Display Property Values:**

* **`block`**
  - Takes full available width (unless width is specified)
  - Starts on a new line
  - Can set width, height, margin, padding
  - Examples: `<div>`, `<p>`, `<h1>`-`<h6>`, `<form>`, `<ul>`, `<ol>`, `<li>`
  - Common uses: Page sections, containers, structural elements

* **`inline`**
  - Takes only as much width as needed
  - Flows with text content
  - Cannot set width/height
  - Vertical padding/margin doesn't affect surrounding elements
  - Examples: `<span>`, `<a>`, `<img>`, `<strong>`, `<em>`
  - Common uses: Text formatting, inline elements

* **`inline-block`**
  - Combines features of block and inline
  - Flows like inline elements
  - Can set width/height like block elements
  - Respects vertical margin/padding
  - Examples: Custom buttons, navigation items
  - Common uses: Creating grid-like layouts without flex/grid

* **`none`**
  - Completely removes element from document flow
  - Takes up no space
  - Not accessible to screen readers
  - Alternative: Use `visibility: hidden` to hide while maintaining space

**Display Property Best Practices:**

1. Use semantic HTML elements with their default display values when possible
2. Prefer `inline-block` over `float` for simple layouts
3. Use `display: none` judiciously - consider accessibility implications
4. Combine with other properties for complex layouts:
   ```css
   .menu-item {
     display: inline-block;
     width: 120px;
     text-align: center;
     padding: 10px;
     margin: 0 5px;
     background-color: #f8f9fa;
     border-radius: 4px;
   }
   ```
5. Use CSS Grid or Flexbox for complex layouts instead of relying solely on display properties

**Common Display Patterns:**

1. Centering Elements:
```css
/* Horizontally center block element */
.block-center {
  display: block;
  width: 80%;
  margin: 0 auto;
}

/* Vertically and horizontally center */
.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

2. Responsive Navigation:
```css
/* Mobile first approach */
.nav-item {
  display: block;
  padding: 10px;
}

@media (min-width: 768px) {
  .nav-item {
    display: inline-block;
  }
}
```

3. Image Gallery:
```css
.gallery-item {
  display: inline-block;
  width: 23%;
  margin: 1%;
  vertical-align: top;
}

@media (max-width: 768px) {
  .gallery-item {
    width: 48%;
  }
}
```

4. Toggle Visibility:
```css
/* JavaScript toggle class */
.hidden {
  display: none;
}

.visible {
  display: block;
}
```

**Accessibility Considerations:**
- Use `display: none` carefully as it removes elements from accessibility tree
- Consider `visibility: hidden` or `opacity: 0` for hiding elements while maintaining accessibility
- Ensure proper focus management when toggling visibility

**4.3 Positioning**

The `position` property is crucial for controlling element placement and creating complex layouts. Let's explore each positioning type with practical examples.

```html
<div class="position-examples">
  <div class="static-box">Static</div>
  <div class="relative-box">Relative</div>
  <div class="absolute-box">Absolute</div>
  <div class="fixed-box">Fixed</div>
  <div class="sticky-box">Sticky</div>
</div>
```

```css
.position-examples {
  position: relative;
  height: 2000px;
  border: 2px solid #ccc;
  padding: 20px;
}

/* Static Positioning (Default) */
.static-box {
  position: static;
  background-color: #f0f8ff;
  padding: 10px;
  border: 1px solid #0077cc;
}

/* Relative Positioning */
.relative-box {
  position: relative;
  top: 20px;
  left: 50px;
  background-color: #fff3cd;
  padding: 10px;
  border: 1px solid #ffc107;
  z-index: 1;
}

/* Absolute Positioning */
.absolute-box {
  position: absolute;
  top: 100px;
  right: 20px;
  background-color: #d4edda;
  padding: 10px;
  border: 1px solid #28a745;
  width: 200px;
}

/* Fixed Positioning */
.fixed-box {
  position: fixed;
  bottom: 20px;
  right: 20px;
  background-color: #f8d7da;
  padding: 10px;
  border: 1px solid #dc3545;
  width: 150px;
  text-align: center;
}

/* Sticky Positioning */
.sticky-box {
  position: sticky;
  top: 20px;
  background-color: #e2e3e5;
  padding: 10px;
  border: 1px solid #6c757d;
}
```

**Position Property Values:**

* **`static` (Default)**
  - Elements follow normal document flow
  - Ignores top/right/bottom/left properties
  - Cannot use z-index
  - Use case: Default behavior for most elements

* **`relative`**
  - Positioned relative to its normal position
  - Can use top/right/bottom/left to offset
  - Creates new stacking context (z-index works)
  - Original space in document flow is preserved
  - Use cases:
    - Minor adjustments to element position
    - Creating reference point for absolutely positioned children
    - Overlapping elements with z-index

* **`absolute`**
  - Removed from normal document flow
  - Positioned relative to nearest positioned ancestor
  - If no positioned ancestor, uses initial containing block (usually viewport)
  - Can use top/right/bottom/left for precise positioning
  - Use cases:
    - Tooltips and dropdown menus
    - Modal dialogs
    - Custom form controls
    - Overlays and popups

* **`fixed`**
  - Removed from normal document flow
  - Positioned relative to viewport
  - Stays fixed during scrolling
  - Can use top/right/bottom/left for positioning
  - Use cases:
    - Fixed headers/footers
    - Persistent navigation
    - Chat widgets
    - Back-to-top buttons

* **`sticky`**
  - Hybrid of relative and fixed
  - Treated as relative until crossing specified threshold
  - Then becomes fixed within its container
  - Requires at least one positioning property (top/right/bottom/left)
  - Use cases:
    - Sticky table headers
    - Sticky sidebars
    - Sticky navigation
    - Section headers in long pages

**Positioning Best Practices:**

1. Use relative positioning for minor adjustments and as reference points
2. Use absolute positioning for UI elements that need precise placement
3. Use fixed positioning for elements that should remain visible during scrolling
4. Use sticky positioning for elements that should stick after scrolling past a point
5. Always consider accessibility when positioning elements
6. Use z-index judiciously to control stacking order
7. Test positioning across different screen sizes
8. Combine with transform for advanced positioning effects

**Common Positioning Patterns:**

1. Centering Elements:
```css
/* Absolute Centering */
.center-absolute {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

/* Fixed Centering */
.center-fixed {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

2. Sticky Header:
```css
.header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: white;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
```

3. Overlay Modal:
```css
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
}

.modal-content {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90%;
  max-width: 600px;
  background: white;
  padding: 20px;
  border-radius: 8px;
}
```

4. Tooltip:
```css
.tooltip-container {
  position: relative;
}

.tooltip {
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  background: #333;
  color: white;
  padding: 5px 10px;
  border-radius: 4px;
  white-space: nowrap;
  opacity: 0;
  transition: opacity 0.2s;
}

.tooltip-container:hover .tooltip {
  opacity: 1;
}
```

**Accessibility Considerations:**
- Ensure positioned elements maintain proper focus order
- Use ARIA attributes for modals and tooltips
- Consider screen reader users when using absolute/fixed positioning
- Test with keyboard navigation
- Provide alternative ways to access content that might be obscured by fixed elements

**Performance Considerations:**
- Fixed and sticky elements can cause repaints during scrolling
- Use transform instead of top/left for animations
- Avoid excessive use of z-index
- Use will-change property for elements that will be animated

**4.4 Floats**

The `float` property was traditionally used for page layouts and wrapping text around images. While modern layouts typically use Flexbox or Grid, floats are still useful for specific scenarios like text wrapping and legacy browser support.

```html
<div class="float-container">
  <img src="image.jpg" alt="Description" class="float-left">
  <p>Text wraps around the floated image...</p>
</div>

<div class="clearfix"></div>
```

```css
/* Basic float example */
.float-left {
  float: left;
  margin: 0 20px 20px 0;
  width: 200px;
  shape-outside: circle(50%);
}

.float-right {
  float: right;
  margin: 0 0 20px 20px;
  width: 200px;
  shape-outside: polygon(0 0, 100% 0, 100% 100%);
}

/* Clearfix technique */
.clearfix::after {
  content: "";
  display: table;
  clear: both;
}

/* Modern float container */
.float-container {
  display: flow-root; /* Better than clearfix */
  padding: 20px;
  border: 1px solid #ddd;
}

/* Text wrapping with shapes */
.wrap-shape {
  float: left;
  width: 200px;
  height: 200px;
  margin: 0 20px 20px 0;
  shape-outside: url('shape.png');
  clip-path: url('shape.png');
}
```

**Float Property Values:**

* **`left`**
  - Floats element to left of container
  - Content flows around right side
  - Common uses: Image/text wrapping, legacy layouts

* **`right`**
  - Floats element to right of container
  - Content flows around left side
  - Common uses: Pull quotes, sidebars

* **`none`** (default)
  - Element remains in normal flow
  - Useful for overriding float behavior

**Float Behavior Characteristics:**

1. Removes element from normal document flow
2. Other content flows around floated element
3. Parent container collapses unless cleared
4. Requires width for predictable behavior
5. Can cause layout issues if not managed properly

**Modern Float Techniques:**

1. Shape Wrapping:
```css
.image-wrap {
  float: left;
  width: 200px;
  margin: 0 20px 20px 0;
  shape-outside: circle(50%);
  clip-path: circle(50%);
}
```

2. Text Wrapping:
```css
.text-wrap {
  float: right;
  width: 40%;
  margin: 0 0 20px 20px;
  shape-outside: margin-box;
}
```

3. Drop Caps:
```css
.drop-cap::first-letter {
  float: left;
  font-size: 4em;
  line-height: 0.8;
  margin: 0 10px 0 0;
}
```

**Clearing Floats:**

1. Clearfix Technique:
```css
.clearfix::after {
  content: "";
  display: table;
  clear: both;
}
```

2. Modern Flow-Root:
```css
.container {
  display: flow-root; /* Better alternative to clearfix */
}
```

3. Clear Property:
```css
.clear {
  clear: both;
}
```

**Float Best Practices:**

1. Use floats primarily for text wrapping and legacy support
2. Prefer Flexbox or Grid for modern layouts
3. Always clear floats to prevent layout issues
4. Use `display: flow-root` instead of clearfix when possible
5. Set explicit widths on floated elements
6. Use shape-outside for advanced text wrapping
7. Test across browsers for consistent behavior
8. Consider accessibility when using floats

**Common Float Patterns:**

1. Image Gallery:
```css
.gallery-item {
  float: left;
  width: 23%;
  margin: 1%;
}

@media (max-width: 768px) {
  .gallery-item {
    width: 48%;
  }
}
```

2. Pull Quotes:
```css
.pull-quote {
  float: right;
  width: 40%;
  margin: 0 0 20px 20px;
  font-style: italic;
  border-left: 3px solid #0077cc;
  padding-left: 15px;
}
```

3. Sidebar Layout:
```css
.sidebar {
  float: left;
  width: 25%;
}

.main-content {
  float: right;
  width: 72%;
}

@media (max-width: 768px) {
  .sidebar, .main-content {
    float: none;
    width: 100%;
  }
}
```

**Accessibility Considerations:**

- Ensure content order makes sense when floated
- Use proper alt text for floated images
- Test with screen readers
- Consider how floated elements affect tab order
- Provide clear visual separation for floated content

**Performance Considerations:**

- Excessive floats can cause layout thrashing
- Use will-change property for animated floats
- Minimize reflows by batching float changes
- Consider using CSS containment for complex float layouts

**When to Use Floats vs. Modern Layout Methods:**

| Feature            | Floats          | Flexbox         | Grid            |
|--------------------|-----------------|-----------------|-----------------|
| Text Wrapping      | Excellent       | Not supported   | Not supported   |
| Layout Control     | Limited         | Excellent       | Excellent       |
| Responsiveness     | Difficult       | Easy            | Easy            |
| Browser Support    | Excellent       | Modern browsers | Modern browsers |
| Accessibility      | Challenging     | Good            | Good            |
| Complex Layouts    | Difficult       | Good            | Excellent       |
| Vertical Alignment | Not supported   | Excellent       | Excellent       |
| Order Control      | Not supported   | Excellent       | Excellent       |

**Legacy Float Layout Example:**

```css
/* Old-school 3-column layout */
.header {
  width: 100%;
  margin-bottom: 20px;
}

.column {
  float: left;
  width: 31%;
  margin: 0 1%;
}

.footer {
  clear: both;
  margin-top: 20px;
}

@media (max-width: 768px) {
  .column {
    float: none;
    width: 100%;
    margin: 10px 0;
  }
}
```

**Modern Alternatives:**

1. Flexbox:
```css
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.item {
  flex: 1 1 300px;
}
```

2. Grid:
```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
```

**Conclusion:**

While floats are no longer the primary tool for page layouts, they remain valuable for specific use cases like text wrapping and legacy browser support. Modern CSS layout methods like Flexbox and Grid should be your first choice for most layout needs, but understanding floats is still important for maintaining older codebases and implementing certain design patterns.

**4.5 Flexbox**

Flexbox is a powerful one-dimensional layout system that provides efficient ways to align, distribute, and space items within a container. It's particularly useful for creating responsive layouts and handling dynamic content.

```html
<div class="flex-container">
  <div class="flex-item">1</div>
  <div class="flex-item">2</div>
  <div class="flex-item">3</div>
</div>
```

```css
/* Basic Flexbox Container */
.flex-container {
  display: flex;
  flex-direction: row; /* Default */
  justify-content: space-between;
  align-items: center;
  gap: 20px;
  padding: 20px;
  border: 1px solid #ddd;
}

.flex-item {
  flex: 1 1 200px;
  padding: 20px;
  background-color: #f0f8ff;
  border: 1px solid #0077cc;
}
```

**Flexbox Container Properties:**

1. **display: flex**
   - Enables flexbox layout
   - Creates flex formatting context
   - Direct children become flex items

2. **flex-direction**
   - Defines main axis direction
   - Values: row (default), row-reverse, column, column-reverse
   ```css
   .container {
     flex-direction: column; /* Stack items vertically */
   }
   ```

3. **justify-content**
   - Aligns items along main axis
   - Values: flex-start, flex-end, center, space-between, space-around, space-evenly
   ```css
   .container {
     justify-content: space-between; /* Distribute items with equal space between */
   }
   ```

4. **align-items**
   - Aligns items along cross axis
   - Values: flex-start, flex-end, center, stretch, baseline
   ```css
   .container {
     align-items: stretch; /* Stretch items to fill container */
   }
   ```

5. **flex-wrap**
   - Controls wrapping behavior
   - Values: nowrap (default), wrap, wrap-reverse
   ```css
   .container {
     flex-wrap: wrap; /* Allow items to wrap to new line */
   }
   ```

6. **gap**
   - Sets spacing between items
   - Values: length or percentage
   ```css
   .container {
     gap: 20px; /* Space between items */
   }
   ```

**Flexbox Item Properties:**

1. **flex**
   - Shorthand for flex-grow, flex-shrink, and flex-basis
   - Default: 0 1 auto
   ```css
   .item {
     flex: 1 1 200px; /* Grow, shrink, basis */
   }
   ```

2. **align-self**
   - Overrides align-items for individual items
   - Values: auto, flex-start, flex-end, center, stretch, baseline
   ```css
   .special-item {
     align-self: flex-end; /* Align this item differently */
   }
   ```

3. **order**
   - Controls display order of items
   - Default: 0
   ```css
   .first-item {
     order: -1; /* Move to start */
   }
   ```

**Common Flexbox Patterns:**

1. **Responsive Navigation:**
```css
.nav {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.nav-item {
  flex: 1 1 150px;
  text-align: center;
}
```

2. **Card Layout:**
```css
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.card {
  flex: 1 1 300px;
  padding: 20px;
  border: 1px solid #ddd;
}
```

3. **Sticky Footer:**
```css
body {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex: 1;
}

footer {
  margin-top: auto;
}
```

4. **Centering Elements:**
```css
.center-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

5. **Equal Height Columns:**
```css
.columns {
  display: flex;
}

.column {
  flex: 1;
  padding: 20px;
}
```

**Flexbox Best Practices:**

1. Use semantic HTML with flexbox
2. Prefer flexbox over floats for modern layouts
3. Use gap instead of margins for spacing
4. Combine with media queries for responsive designs
5. Use flex-basis instead of width for flexible sizing
6. Avoid nesting too many flex containers
7. Use min-width/max-width with flex items
8. Test across browsers for consistent behavior

**Accessibility Considerations:**

- Ensure logical source order matches visual order
- Use proper heading hierarchy
- Maintain keyboard navigation
- Consider screen reader users
- Test with high contrast modes

**Performance Considerations:**

- Avoid excessive nesting of flex containers
- Use will-change for animated flex items
- Minimize layout thrashing
- Use contain: layout when appropriate
- Avoid unnecessary reflows

**Flexbox vs. Grid:**

| Feature            | Flexbox          | Grid             |
|--------------------|------------------|------------------|
| Dimension          | One-dimensional  | Two-dimensional  |
| Alignment          | Excellent        | Excellent        |
| Responsiveness     | Easy             | Easy             |
| Complex Layouts    | Good             | Excellent        |
| Item Ordering      | Easy             | Limited          |
| Browser Support    | Excellent        | Modern browsers  |
| Use Case           | Components       | Page Layouts     |

**Common Flexbox Mistakes:**

1. Forgetting to set flex-direction
2. Overusing flex-grow
3. Not using gap for spacing
4. Ignoring flex-wrap
5. Using fixed widths with flex items
6. Not testing in older browsers
7. Over-nesting flex containers
8. Forgetting to set min-width/max-width

**Advanced Flexbox Techniques:**

1. **Intrinsic Sizing:**
```css
.container {
  display: flex;
  width: min-content;
}
```

2. **Aspect Ratio Boxes:**
```css
.aspect-box {
  flex: 1;
  aspect-ratio: 1;
}
```

3. **Sticky Sidebar:**
```css
.layout {
  display: flex;
  height: 100vh;
}

.sidebar {
  flex: 0 0 250px;
  position: sticky;
  top: 0;
}
```

4. **Responsive Masonry:**
```css
.masonry {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.masonry-item {
  flex: 1 1 300px;
}
```

5. **Dynamic Grid:**
```css
.grid {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.grid-item {
  flex: 1 1 calc(33.33% - 40px);
}
```

**Conclusion:**

Flexbox is an essential tool for modern web layouts, offering powerful alignment and distribution capabilities. While it's primarily designed for one-dimensional layouts, it can handle many common layout patterns with ease. When combined with CSS Grid, you can create sophisticated, responsive designs that work across all devices and screen sizes.

**4.6 CSS Grid**

CSS Grid is a powerful two-dimensional layout system that allows for precise control over both rows and columns. It's particularly useful for creating complex, responsive layouts with ease.

```html
<div class="grid-container">
  <header class="header">Header</header>
  <aside class="sidebar">Sidebar</aside>
  <main class="main-content">Main Content</main>
  <footer class="footer">Footer</footer>
</div>
```

```css
/* Basic Grid Container */
.grid-container {
  display: grid;
  grid-template-columns: 200px 1fr;
  grid-template-rows: 100px 1fr 100px;
  grid-template-areas:
    "header header"
    "sidebar main"
    "footer footer";
  gap: 20px;
  height: 100vh;
  padding: 20px;
  border: 1px solid #ddd;
}

.header {
  grid-area: header;
  background-color: #f0f8ff;
  padding: 20px;
  border: 1px solid #0077cc;
}

.sidebar {
  grid-area: sidebar;
  background-color: #fff3cd;
  padding: 20px;
  border: 1px solid #ffc107;
}

.main-content {
  grid-area: main;
  background-color: #d4edda;
  padding: 20px;
  border: 1px solid #28a745;
}

.footer {
  grid-area: footer;
  background-color: #f8d7da;
  padding: 20px;
  border: 1px solid #dc3545;
}

/* Responsive Grid */
@media (max-width: 768px) {
  .grid-container {
    grid-template-columns: 1fr;
    grid-template-rows: 80px auto 1fr 80px;
    grid-template-areas:
      "header"
      "sidebar"
      "main"
      "footer";
  }
}
```

**Key Features:**
- **Grid Areas:** Named template areas for better readability
- **Responsive Design:** Media queries for mobile layout
- **Fraction Units:** Flexible sizing with `fr` units
- **Gap Property:** Consistent spacing between items
- **Viewport Units:** Full-height layout with `100vh`

**Best Practices:**
1. Use semantic HTML with grid layout
2. Name grid areas for better maintainability
3. Use `fr` units for flexible sizing
4. Implement responsive design with media queries
5. Use `gap` instead of margins for spacing
6. Combine with Flexbox for component layouts
7. Test across browsers for compatibility
8. Use CSS variables for consistent values

**Advanced Grid Techniques:**

1. **Nested Grids:**
```css
.main-content {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 15px;
}
```

2. **Grid Auto-Flow:**
```css
.grid-container {
  grid-auto-flow: dense;
}
```

3. **Minmax Function:**
```css
.grid-container {
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}
```

4. **Grid Alignment:**
```css
.header {
  justify-self: center;
  align-self: start;
}
```

5. **Grid Spanning:**
```css
.featured-item {
  grid-column: span 2;
  grid-row: span 2;
}
```

**Accessibility Considerations:**
- Maintain logical source order
- Ensure proper heading hierarchy
- Use ARIA landmarks
- Test with screen readers
- Ensure keyboard navigation
- Provide sufficient color contrast
- Use semantic HTML elements
- Test with different zoom levels

**Performance Considerations:**
- Avoid excessive nesting of grids
- Use `will-change` for animated grid items
- Minimize layout thrashing
- Use CSS containment
- Optimize grid item rendering
- Consider using `content-visibility` for large grids
- Test performance with DevTools
- Implement lazy loading for grid content

**Common Grid Patterns:**

1. **Holy Grail Layout:**
```css
.grid-container {
  display: grid;
  grid-template:
    "header header header" 100px
    "sidebar main aside" 1fr
    "footer footer footer" 100px
    / 200px 1fr 200px;
}
```

2. **Masonry Layout:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-auto-rows: 150px;
  gap: 20px;
}

.grid-item {
  grid-row: span 2;
}
```

3. **Responsive Image Gallery:**
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px;
}
```

4. **Dashboard Layout:**
```css
.dashboard {
  display: grid;
  grid-template-columns: 250px 1fr;
  grid-template-rows: 80px 1fr;
  grid-template-areas:
    "sidebar header"
    "sidebar main";
}
```

5. **Card Layout:**
```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}
```

**Grid vs. Flexbox:**

| Feature            | Grid             | Flexbox          |
|--------------------|------------------|------------------|
| Dimension          | Two-dimensional  | One-dimensional  |
| Alignment          | Excellent        | Excellent        |
| Responsiveness     | Easy             | Easy             |
| Complex Layouts    | Excellent        | Good             |
| Item Ordering      | Limited          | Easy             |
| Browser Support    | Modern browsers  | Excellent        |
| Use Case           | Page Layouts     | Components       |

**Conclusion:**
CSS Grid is an essential tool for modern web layouts, offering powerful two-dimensional layout capabilities. When combined with Flexbox, you can create sophisticated, responsive designs that work across all devices and screen sizes. Grid is particularly well-suited for page layouts and complex grid-based designs, while Flexbox excels at one-dimensional layouts and component-level designs.

**Grid Container Properties:**

1. **display: grid**
   - Enables grid layout
   - Creates grid formatting context
   - Direct children become grid items

2. **grid-template-columns**
   - Defines column tracks
   - Values: length, percentage, fr (fraction), minmax(), repeat()
   ```css
   .container {
     grid-template-columns: 200px 1fr 30%;
   }
   ```

3. **grid-template-rows**
   - Defines row tracks
   - Values: same as grid-template-columns
   ```css
   .container {
     grid-template-rows: 100px auto 200px;
   }
   ```

4. **gap**
   - Sets spacing between grid items
   - Values: length or percentage
   ```css
   .container {
     gap: 20px;
   }
   ```

5. **grid-template-areas**
   - Defines named grid areas
   - Values: strings representing area names
   ```css
   .container {
     grid-template-areas:
       "header header"
       "sidebar main"
       "footer footer";
   }
   ```

6. **justify-content**
   - Aligns grid along the inline (row) axis
   - Values: start, end, center, stretch, space-between, space-around, space-evenly
   ```css
   .container {
     justify-content: center;
   }
   ```

7. **align-content**
   - Aligns grid along the block (column) axis
   - Values: same as justify-content
   ```css
   .container {
     align-content: start;
   }
   ```

**Grid Item Properties:**

1. **grid-column**
   - Controls item column placement
   - Values: line numbers, span
   ```css
   .item {
     grid-column: 1 / 3;
   }
   ```

2. **grid-row**
   - Controls item row placement
   - Values: same as grid-column
   ```css
   .item {
     grid-row: 2 / 4;
   }
   ```

3. **grid-area**
   - Shorthand for grid-row and grid-column
   - Can reference named areas
   ```css
   .item {
     grid-area: header;
   }
   ```

4. **justify-self**
   - Aligns item along inline axis
   - Values: start, end, center, stretch
   ```css
   .item {
     justify-self: center;
   }
   ```

5. **align-self**
   - Aligns item along block axis
   - Values: same as justify-self
   ```css
   .item {
     align-self: end;
   }
   ```

**Common Grid Patterns:**

1. **Responsive Grid:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}
```

2. **Masonry Layout:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 150px;
  gap: 20px;
}

.grid-item {
  grid-row: span 2;
}
```

3. **Holy Grail Layout:**
```css
.container {
  display: grid;
  grid-template:
    "header header header" 100px
    "sidebar main aside" 1fr
    "footer footer footer" 100px
    / 200px 1fr 200px;
  min-height: 100vh;
}
```

4. **Card Layout:**
```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}
```

5. **Image Gallery:**
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px;
}
```

**Grid Best Practices:**

1. Use semantic HTML with grid
2. Prefer grid over floats for complex layouts
3. Use fr units for flexible sizing
4. Combine with media queries for responsive designs
5. Use named grid areas for better readability
6. Avoid nesting too many grid containers
7. Use minmax() for flexible track sizing
8. Test across browsers for consistent behavior

**Accessibility Considerations:**

- Ensure logical source order matches visual order
- Use proper heading hierarchy
- Maintain keyboard navigation
- Consider screen reader users
- Test with high contrast modes

**Performance Considerations:**

- Avoid excessive nesting of grid containers
- Use will-change for animated grid items
- Minimize layout thrashing
- Use contain: layout when appropriate
- Avoid unnecessary reflows

**Grid vs. Flexbox:**

| Feature            | Grid             | Flexbox          |
|--------------------|------------------|------------------|
| Dimension          | Two-dimensional  | One-dimensional  |
| Alignment          | Excellent        | Excellent        |
| Responsiveness     | Easy             | Easy             |
| Complex Layouts    | Excellent        | Good             |
| Item Ordering      | Limited          | Easy             |
| Browser Support    | Modern browsers  | Excellent        |
| Use Case           | Page Layouts     | Components       |

**Common Grid Mistakes:**

1. Forgetting to set grid-template-columns
2. Overusing fixed track sizes
3. Not using gap for spacing
4. Ignoring grid-template-areas
5. Using fixed widths with grid items
6. Not testing in older browsers
7. Over-nesting grid containers
8. Forgetting to set min-width/max-width

**Advanced Grid Techniques:**

1. **Subgrid:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.grid-item {
  display: grid;
  grid-template-columns: subgrid;
}
```

2. **Aspect Ratio Boxes:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  aspect-ratio: 1;
}
```

3. **Sticky Sidebar:**
```css
.layout {
  display: grid;
  grid-template-columns: 250px 1fr;
  height: 100vh;
}

.sidebar {
  position: sticky;
  top: 0;
}
```

4. **Responsive Masonry:**
```css
.masonry {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-auto-rows: 150px;
  gap: 20px;
}

.masonry-item {
  grid-row: span 2;
}
```

5. **Dynamic Grid:**
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
```

**Conclusion:**

CSS Grid is an essential tool for modern web layouts, offering powerful two-dimensional layout capabilities. When combined with Flexbox, you can create sophisticated, responsive designs that work across all devices and screen sizes. Grid is particularly well-suited for page layouts and complex grid-based designs, while Flexbox excels at one-dimensional layouts and component-level designs.

**4.7 Media Queries and Responsive Design**

Media queries are a fundamental tool for creating responsive websites that adapt to different screen sizes and devices. They allow you to apply CSS rules based on various device characteristics.

```css
/* Basic Media Query Structure */
@media media-type and (media-feature) {
  /* CSS rules */
}
```

**Media Types:**
- `all` (default) - All devices
- `screen` - Computer screens, tablets, smartphones
- `print` - Printers and print preview
- `speech` - Screen readers

**Common Media Features:**
1. **Width and Height:**
   - `width`, `min-width`, `max-width`
   - `height`, `min-height`, `max-height`
   ```css
   @media (min-width: 768px) {
     .container {
       width: 750px;
     }
   }
   ```

2. **Orientation:**
   - `portrait` - Height > Width
   - `landscape` - Width > Height
   ```css
   @media (orientation: landscape) {
     .header {
       height: 100vh;
     }
   }
   ```

3. **Resolution:**
   - `resolution` - Device pixel density
   - `min-resolution`, `max-resolution`
   ```css
   @media (min-resolution: 2dppx) {
     .logo {
       background-image: url('logo@2x.png');
     }
   }
   ```

4. **Aspect Ratio:**
   - `aspect-ratio` - Width to height ratio
   ```css
   @media (aspect-ratio: 16/9) {
     .video-container {
       padding-top: 56.25%;
     }
   }
   ```

**Responsive Design Strategies:**

1. **Mobile-First Approach:**
```css
/* Base styles for mobile */
.container {
  padding: 10px;
}

/* Styles for larger screens */
@media (min-width: 768px) {
  .container {
    padding: 20px;
  }
}
```

2. **Breakpoint Selection:**
```css
/* Common breakpoints */
@media (min-width: 576px) { /* Small devices */ }
@media (min-width: 768px) { /* Tablets */ }
@media (min-width: 992px) { /* Desktops */ }
@media (min-width: 1200px) { /* Large desktops */ }
```

3. **Fluid Layouts:**
```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
```

4. **Responsive Typography:**
```css
html {
  font-size: 16px;
}

@media (min-width: 768px) {
  html {
    font-size: 18px;
  }
}
```

5. **Responsive Images:**
```html
<picture>
  <source media="(min-width: 1200px)" srcset="large.jpg">
  <source media="(min-width: 768px)" srcset="medium.jpg">
  <img src="small.jpg" alt="Description">
</picture>
```

**Advanced Media Query Techniques:**

1. **Combining Conditions:**
```css
@media (min-width: 768px) and (max-width: 1199px) {
  /* Styles for tablets */
}
```

2. **Dark Mode Support:**
```css
@media (prefers-color-scheme: dark) {
  body {
    background-color: #121212;
    color: #ffffff;
  }
}
```

3. **Reduced Motion:**
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

4. **High Contrast Mode:**
```css
@media (prefers-contrast: high) {
  .button {
    border: 2px solid black;
  }
}
```

5. **Print Styles:**
```css
@media print {
  .no-print {
    display: none;
  }
  
  body {
    font-size: 12pt;
    color: black;
  }
}
```

**Responsive Design Best Practices:**

1. Use relative units (em, rem, %) instead of fixed units (px)
2. Implement mobile-first design approach
3. Use CSS Grid and Flexbox for flexible layouts
4. Optimize images for different screen sizes
5. Test on real devices and emulators
6. Use progressive enhancement
7. Consider performance implications
8. Implement responsive navigation patterns
9. Use CSS variables for consistent styling
10. Test with different zoom levels

**Common Responsive Patterns:**

1. **Hamburger Menu:**
```css
.nav {
  display: none;
}

@media (min-width: 768px) {
  .nav {
    display: flex;
  }
  
  .hamburger {
    display: none;
  }
}
```

2. **Responsive Grid:**
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
```

3. **Card Layout:**
```css
.card {
  width: 100%;
}

@media (min-width: 768px) {
  .card {
    width: 48%;
  }
}

@media (min-width: 992px) {
  .card {
    width: 32%;
  }
}
```

4. **Responsive Tables:**
```css
@media (max-width: 768px) {
  table, thead, tbody, th, td, tr {
    display: block;
  }
  
  td {
    position: relative;
    padding-left: 50%;
  }
  
  td::before {
    content: attr(data-label);
    position: absolute;
    left: 0;
    width: 45%;
    padding-right: 10px;
  }
}
```

5. **Viewport Units:**
```css
.header {
  height: 100vh;
}

.section {
  min-height: 50vh;
}
```

**Accessibility Considerations:**

1. Ensure proper text scaling
2. Maintain logical content order
3. Use proper heading hierarchy
4. Test with screen readers
5. Ensure sufficient color contrast
6. Provide alternative text for images
7. Make interactive elements touch-friendly
8. Test with keyboard navigation

**Performance Considerations:**

1. Optimize images for different screen sizes
2. Use responsive image techniques (srcset, picture)
3. Implement lazy loading
4. Use CSS containment
5. Minimize layout shifts
6. Optimize critical rendering path
7. Use media queries to load appropriate resources
8. Implement code splitting

**Testing Responsive Designs:**

1. Use browser developer tools
2. Test on real devices
3. Use online testing tools (BrowserStack, LambdaTest)
4. Check different orientations
5. Test with different zoom levels
6. Verify accessibility
7. Check performance metrics
8. Test with different network conditions

**Common Responsive Design Mistakes:**

1. Using fixed widths
2. Not testing on real devices
3. Ignoring performance implications
4. Not considering accessibility
5. Using too many breakpoints
6. Not implementing touch-friendly interfaces
7. Forgetting to test landscape orientation
8. Not optimizing images for different screens

**Modern Responsive Design Tools:**

1. CSS Grid and Flexbox
2. Viewport units (vw, vh, vmin, vmax)
3. CSS variables
4. Container queries (experimental)
5. Aspect-ratio property
6. clamp() function
7. min(), max() functions
8. prefers-reduced-motion media feature

**Conclusion:**

Responsive design is essential in today's multi-device world. By using media queries effectively and following best practices, you can create websites that provide optimal viewing experiences across a wide range of devices. Remember to consider not just screen size, but also device capabilities, user preferences, and performance when implementing responsive designs.

**Module 5: Capstone Project - Personal Portfolio Website**

**Project Goal:** Create a responsive personal portfolio website to showcase your skills and projects.

**Project Requirements:**

*   **HTML Structure:**
    *   Use semantic HTML5 elements.
    *   Include sections for:
        *   **Header:** Name, tagline, navigation.
        *   **About Me:** Brief introduction, photo, skills.
        *   **Projects:** Showcase at least 3 projects with images, descriptions, and links.
        *   **Contact:** Contact form.
        *   **Footer:** Copyright, social media links.
*   **CSS Styling:**
    *   Use external CSS file.
    *   Implement a visually appealing design.
    *   Use Flexbox or Grid for layout.
    *   Make the website responsive using media queries.
*   **Responsiveness:** The website should look good and function well on different screen sizes (desktops, tablets, and mobile phones).
*   **Accessibility:**
    *   Use appropriate `alt` text for images.
    *   Use semantic HTML elements.
    *   Ensure good color contrast.

**Detailed Implementation Guide:**

1. **Planning:**
    *   **Content Strategy:**
        - Write compelling copy for each section
        - Prepare high-quality images
        - Gather project details and screenshots
    *   **Design Considerations:**
        - Choose a color palette (use tools like Coolors or Adobe Color)
        - Select appropriate fonts (Google Fonts recommended)
        - Create wireframes for desktop and mobile layouts
    *   **File Structure:**
        ```
        portfolio/
        ├── index.html
        ├── styles.css
        ├── scripts.js
        └── assets/
            ├── images/
            │   ├── profile.jpg
            │   ├── project1.jpg
            │   └── project2.jpg
            └── icons/
                ├── github.svg
                └── linkedin.svg
        ```

2. **HTML Structure (index.html):**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Professional portfolio of [Your Name]">
    <title>[Your Name] - Portfolio</title>
    <link rel="stylesheet" href="styles.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
</head>
<body>
    <!-- Header Section -->
    <header class="header">
        <div class="container">
            <div class="header-content">
                <h1>[Your Name]</h1>
                <p class="tagline">Web Developer & Designer</p>
                <nav class="main-nav">
                    <ul>
                        <li><a href="#about">About</a></li>
                        <li><a href="#projects">Projects</a></li>
                        <li><a href="#contact">Contact</a></li>
                    </ul>
                </nav>
            </div>
        </div>
    </header>

    <!-- About Section -->
    <section id="about" class="about-section">
        <div class="container">
            <h2 class="section-title">About Me</h2>
            <div class="about-content">
                <div class="profile-image">
                    <img src="assets/images/profile.jpg" alt="[Your Name] profile picture">
                </div>
                <div class="bio">
                    <p>I'm a passionate web developer with expertise in HTML, CSS, and JavaScript. I specialize in creating responsive, user-friendly websites that deliver exceptional user experiences.</p>
                    <div class="skills">
                        <h3>Technical Skills</h3>
                        <ul class="skills-list">
                            <li>HTML5 & CSS3</li>
                            <li>JavaScript (ES6+)</li>
                            <li>Responsive Design</li>
                            <li>Version Control (Git)</li>
                            <li>Web Accessibility</li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="projects-section">
        <div class="container">
            <h2 class="section-title">Featured Projects</h2>
            <div class="projects-grid">
                <article class="project-card">
                    <div class="project-image">
                        <img src="assets/images/project1.jpg" alt="Project 1 screenshot">
                    </div>
                    <div class="project-content">
                        <h3>Project Title 1</h3>
                        <p>Brief description of the project, technologies used, and your role in the project.</p>
                        <div class="project-links">
                            <a href="#" class="btn" target="_blank">Live Demo</a>
                            <a href="#" class="btn" target="_blank">View Code</a>
                        </div>
                    </div>
                </article>
                <!-- Repeat for other projects -->
            </div>
        </div>
    </section>

    <!-- Contact Section -->
    <section id="contact" class="contact-section">
        <div class="container">
            <h2 class="section-title">Get in Touch</h2>
            <form class="contact-form" action="#" method="post">
                <div class="form-group">
                    <label for="name">Name:</label>
                    <input type="text" id="name" name="name" required>
                </div>
                <div class="form-group">
                    <label for="email">Email:</label>
                    <input type="email" id="email" name="email" required>
                </div>
                <div class="form-group">
                    <label for="message">Message:</label>
                    <textarea id="message" name="message" rows="5" required></textarea>
                </div>
                <button type="submit" class="btn">Send Message</button>
            </form>
        </div>
    </section>

    <!-- Footer -->
    <footer class="footer">
        <div class="container">
            <div class="footer-content">
                <p>&copy; 2023 [Your Name]. All rights reserved.</p>
                <ul class="social-links">
                    <li><a href="#" aria-label="GitHub profile"><i class="fab fa-github"></i></a></li>
                    <li><a href="#" aria-label="LinkedIn profile"><i class="fab fa-linkedin"></i></a></li>
                    <li><a href="#" aria-label="Twitter profile"><i class="fab fa-twitter"></i></a></li>
                </ul>
            </div>
        </div>
    </footer>

    <script src="scripts.js"></script>
</body>
</html>
```

3. **CSS Styling (styles.css):**

```css
/* Global Styles */
:root {
    --primary-color: #0077cc;
    --secondary-color: #333;
    --background-color: #f8f9fa;
    --text-color: #333;
    --white: #ffffff;
    --spacing-unit: 1rem;
    --max-width: 1200px;
}

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', system-ui, sans-serif;
    line-height: 1.6;
    color: var(--text-color);
    background-color: var(--background-color);
}

.container {
    width: 90%;
Okay, here's an in-depth HTML and CSS masterclass covering the fundamentals, best practices, and advanced techniques, all culminating in a comprehensive portfolio-ready project:

**HTML & CSS Masterclass: Building a Foundation for Web Development and Design**

**Target Audience:** Beginners with little to no prior experience in web development.

**Goal:** Equip you with the fundamental knowledge of HTML and CSS to create static websites and prepare you for more advanced front-end development concepts.

**Methodology:**

*   **Concept Explanation:** Each topic starts with a clear and concise explanation.
*   **Code Examples:** Numerous examples illustrate the concepts in action.
*   **Best Practices:** Emphasize writing clean, maintainable, and accessible code.
*   **Capstone Project:** A real-world project to solidify your skills and showcase in your portfolio.

**Module 1: Introduction to HTML**

**1.1 What is HTML?**

*   **HTML (HyperText Markup Language):** The standard markup language for creating web pages. It structures the content of a web page.
*   **Structure, Not Style:** HTML defines the meaning and hierarchy of content (headings, paragraphs, lists, images, etc.), but it doesn't dictate how it looks. That's where CSS comes in.
*   **Tags, Elements, and Attributes:**
    *   **Tags:** Keywords enclosed in angle brackets (e.g., `<p>`, `<h1>`, `<img>`).
    *   **Elements:** A complete piece of content, including the opening tag, content, and closing tag (e.g., `<p>This is a paragraph.</p>`).
    *   **Attributes:** Provide additional information about an element and are included within the opening tag (e.g., `<img src="image.jpg" alt="Description">`).

**1.2 Basic HTML Structure**

```html
<!DOCTYPE html> 
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First Web Page</title>
    <link rel="stylesheet" href="style.css"> </head>
<body>

    <h1>Welcome to My Website</h1>
    <p>This is a paragraph of text.</p>

    <script src="script.js"></script> </body>
</html>
```

*   **`<!DOCTYPE html>`:** Declares the document as HTML5.
*   **`<html>`:** The root element of the page.
    *   `lang="en"` attribute specifies the language as English.
*   **`<head>`:** Contains meta-information about the page (not displayed on the page itself).
    *   **`<meta charset="UTF-8">`:** Sets the character encoding to UTF-8, supporting a wide range of characters.
    *   **`<meta name="viewport"...>`:** Configures how the page scales on different devices (essential for responsive design).
    *   **`<title>`:** Sets the title that appears in the browser tab.
    *   **`<link rel="stylesheet" href="style.css">`:** Links an external CSS file to style the page.
*   **`<body>`:** Contains the visible content of the page.
    *   **`<h1>`:** A top-level heading.
    *   **`<p>`:** A paragraph of text.
*   **`<script src="script.js"></script>`:** Links to an external JavaScript file (for interactivity). It's often placed at the end of the `<body>` so the HTML loads first.

**1.3 Common HTML Elements**

*   **Headings:** `<h1>` to `<h6>` (<h1> is the most important, <h6> the least).
    ```html
    <h1>Main Title</h1>
    <h2>Section Title</h2>
    <h3>Subsection Title</h3>
    ```
    Best Practices:
    - Use only one `<h1>` per page
    - Maintain proper heading hierarchy
    - Don't skip heading levels (e.g., don't go from h2 to h4)

*   **Paragraphs:** `<p>`
    ```html
    <p>This is a paragraph of text. It can contain <strong>bold text</strong>, 
    <em>italic text</em>, and <a href="#">links</a>.</p>
    ```
    Common Pitfalls:
    - Avoid using `<br>` tags for spacing (use CSS margin/padding instead)
    - Don't use empty paragraphs for spacing

*   **Links:** `<a>` (anchor)
    ```html
    <!-- Basic link -->
    <a href="https://www.example.com">Visit Example</a>

    <!-- Link with target -->
    <a href="https://www.example.com" target="_blank" rel="noopener noreferrer">
      Visit Example in New Tab
    </a>

    <!-- Email link -->
    <a href="mailto:example@example.com">Email Us</a>

    <!-- Telephone link -->
    <a href="tel:+1234567890">Call Us</a>
    ```
    Key Attributes:
    - `href`: Specifies the URL or resource
    - `target`: Controls where link opens (_blank, _self, _parent, _top)
    - `rel`: Specifies relationship (important for security with target="_blank")
    - `download`: Forces download of linked resource

*   **Images:** `<img>`
    ```html
    <!-- Basic image -->
    <img src="images/logo.png" alt="Company Logo">

    <!-- Responsive image -->
    <img src="images/hero.jpg" 
         alt="Hero Image"
         srcset="images/hero-320.jpg 320w,
                 images/hero-640.jpg 640w,
                 images/hero-1280.jpg 1280w"
         sizes="(max-width: 600px) 100vw, 50vw">

    <!-- Lazy-loaded image -->
    <img src="placeholder.jpg" 
         data-src="image.jpg" 
         alt="Description"
         class="lazyload">
    ```
    Best Practices:
    - Always include meaningful alt text
    - Use srcset for responsive images
    - Implement lazy loading for better performance
    - Optimize image file sizes
*   **Lists:**
    *   **Unordered Lists (`<ul>`):** Bulleted lists.
    *   **Ordered Lists (`<ol>`):** Numbered lists.
    *   **List Items (`<li>`):** Items within a list.

    ```html
    <ul>
        <li>Item 1</li>
        <li>Item 2</li>
    </ul>

    <ol>
        <li>First step</li>
        <li>Second step</li>
    </ol>
    ```
*   **Divisions (`<div>`):** Generic containers used to group other elements for styling or structural purposes.
*   **Spans (`<span>`):** Inline containers used to apply styles to a specific portion of text within a larger element.

**Module 2: Introduction to CSS**

**2.1 What is CSS?**

*   **CSS (Cascading Style Sheets):** The language used to style the appearance of web pages.
*   **Separation of Concerns:** CSS separates the styling from the HTML structure, making code cleaner and easier to maintain.
*   **Selectors, Properties, and Values:**
    *   **Selectors:** Target specific HTML elements to style.
    *   **Properties:** The aspects of an element you want to style (e.g., `color`, `font-size`, `background-color`).
    *   **Values:** The specific settings for a property (e.g., `red`, `16px`, `#f0f0f0`).

**2.2 Ways to Add CSS**

*   **Inline CSS:** Applied directly within an HTML tag using the `style` attribute (generally discouraged for maintainability).

    ```html
    <p style="color: blue; font-size: 18px;">This is a blue paragraph.</p>
    ```
*   **Internal CSS:** Placed within a `<style>` tag in the `<head>` of the HTML document (useful for styles specific to a single page).

    ```html
    <head>
        <style>
            p {
                color: green;
                font-size: 16px;
            }
        </style>
    </head>
    ```
*   **External CSS:** Stored in a separate `.css` file and linked to the HTML using the `<link>` tag (best practice for most cases).

    ```html
    <!-- In your HTML file (index.html) -->
    <head>
        <link rel="stylesheet" href="styles.css">
    </head>
    ```

    ```css
    /* In your CSS file (styles.css) */
    p {
        color: black;
        font-size: 14px;
    }
    ```

**2.3 CSS Selectors**

*   **Element Selector:** Targets elements by their tag name.
    ```css
    /* Style all paragraphs */
    p {
        color: navy;
        line-height: 1.5;
        margin-bottom: 1em;
    }

    /* Style all headings */
    h1, h2, h3 {
        font-family: 'Arial', sans-serif;
        color: #333;
    }
    ```

*   **ID Selector:** Targets a single element with a specific `id` attribute.
    ```css
    #main-header {
        background-color: #0077cc;
        color: white;
        padding: 20px;
        text-align: center;
    }

    #contact-form {
        max-width: 600px;
        margin: 0 auto;
        padding: 20px;
        border: 1px solid #ddd;
    }
    ```

*   **Class Selector:** Targets elements with a specific `class` attribute.
    ```css
    .btn {
        display: inline-block;
        padding: 10px 20px;
        background-color: #0077cc;
        color: white;
        text-decoration: none;
        border-radius: 4px;
        transition: background-color 0.3s;
    }

    .btn:hover {
        background-color: #005fa3;
    }

    .warning {
        color: #dc3545;
        background-color: #f8d7da;
        padding: 10px;
        border: 1px solid #f5c6cb;
        border-radius: 4px;
    }
    ```

*   **Attribute Selectors:** Target elements based on attributes.
    ```css
    /* Links with target="_blank" */
    a[target="_blank"] {
        color: #0077cc;
    }

    /* Images with alt text */
    img[alt] {
        border: 2px solid #0077cc;
    }

    /* Inputs of type text */
    input[type="text"] {
        width: 100%;
        padding: 8px;
        border: 1px solid #ddd;
    }
    ```

*   **Pseudo-classes:** Target elements in specific states.
    ```css
    /* Style visited links */
    a:visited {
        color: #551a8b;
    }

    /* Style first child */
    li:first-child {
        font-weight: bold;
    }

    /* Style odd table rows */
    tr:nth-child(odd) {
        background-color: #f8f9fa;
    }

    /* Style focused inputs */
    input:focus {
        outline: 2px solid #0077cc;
        border-color: #0077cc;
    }
    ```

*   **Combinators:** Combine selectors for more specific targeting.
    ```css
    /* Direct child selector */
    nav > ul {
        list-style: none;
        padding: 0;
    }

    /* Adjacent sibling selector */
    h2 + p {
        margin-top: 0;
    }

    /* General sibling selector */
    h2 ~ p {
        color: #666;
    }

    /* Descendant selector */
    .article p {
        line-height: 1.6;
    }
    ```

*   **Universal Selector:** Selects all elements.
    ```css
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }
    ```

Best Practices:
- Use classes for reusable styles
- Avoid overusing ID selectors
- Keep specificity low when possible
- Use meaningful class names (BEM methodology recommended)
- Avoid inline styles
- Use shorthand properties when appropriate

**2.4 Common CSS Properties**

*   **Text Styling:**
    *   `color`: Sets the text color.
    *   `font-family`: Sets the font.
    *   `font-size`: Sets the text size.
    *   `font-weight`: Sets text boldness (e.g., `normal`, `bold`).
    *   `text-align`: Aligns text (e.g., `left`, `center`, `right`).
    *   `text-decoration`: Adds decorations (e.g., `underline`, `line-through`).
*   **Box Model:** (We'll cover this in more detail later)
    *   `width`: Sets the width of an element.
    *   `height`: Sets the height of an element.
    *   `margin`: Sets the space outside the element's border.
    *   `padding`: Sets the space inside the element's border.
    *   `border`: Sets a border around the element.
*   **Background:**
    *   `background-color`: Sets the background color.
    *   `background-image`: Sets a background image.
    *   `background-repeat`: Controls how a background image repeats.
    *   `background-position`: Controls the position of a background image.

**Module 3: Intermediate HTML**

**3.1 Forms**

Forms are used to collect user input. Here's a comprehensive example with styling and validation:

```html
<form class="contact-form" action="/submit-form" method="post" novalidate>
    <div class="form-group">
        <label for="name">Full Name:</label>
        <input type="text" id="name" name="name" required
               placeholder="Enter your full name"
               minlength="2" maxlength="50"
               pattern="[A-Za-z ]+">
        <span class="error-message">Please enter a valid name</span>
    </div>

    <div class="form-group">
        <label for="email">Email Address:</label>
        <input type="email" id="email" name="email" required
               placeholder="example@domain.com"
               pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,4}$">
        <span class="error-message">Please enter a valid email</span>
    </div>

    <div class="form-group">
        <label for="phone">Phone Number:</label>
        <input type="tel" id="phone" name="phone"
               placeholder="123-456-7890"
               pattern="[0-9]{3}-[0-9]{3}-[0-9]{4}">
        <span class="error-message">Format: 123-456-7890</span>
    </div>

    <div class="form-group">
        <label for="message">Your Message:</label>
        <textarea id="message" name="message" required
                  placeholder="Type your message here..."
                  minlength="10" maxlength="500"></textarea>
        <span class="error-message">Message must be 10-500 characters</span>
    </div>

    <div class="form-group">
        <label>Preferred Contact Method:</label>
        <div class="radio-group">
            <label>
                <input type="radio" name="contact-method" value="email" checked>
                Email
            </label>
            <label>
                <input type="radio" name="contact-method" value="phone">
                Phone
            </label>
        </div>
    </div>

    <div class="form-group">
        <label>Interests:</label>
        <div class="checkbox-group">
            <label>
                <input type="checkbox" name="interests[]" value="web-dev">
                Web Development
            </label>
            <label>
                <input type="checkbox" name="interests[]" value="design">
                Design
            </label>
            <label>
                <input type="checkbox" name="interests[]" value="seo">
                SEO
            </label>
        </div>
    </div>

    <div class="form-group">
        <label for="country">Country:</label>
        <select id="country" name="country" required>
            <option value="">Select your country</option>
            <option value="US">United States</option>
            <option value="CA">Canada</option>
            <option value="UK">United Kingdom</option>
            <!-- Add more countries -->
        </select>
    </div>

    <div class="form-group">
        <button type="submit">Send Message</button>
        <button type="reset">Clear Form</button>
    </div>
</form>
```

```css
/* Form Styling */
.contact-form {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    background: #f9f9f9;
    border: 1px solid #ddd;
    border-radius: 8px;
}

.form-group {
    margin-bottom: 20px;
}

label {
    display: block;
    margin-bottom: 5px;
    font-weight: bold;
}

input[type="text"],
input[type="email"],
input[type="tel"],
textarea,
select {
    width: 100%;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    font-size: 16px;
}

input:focus,
textarea:focus,
select:focus {
    outline: none;
    border-color: #0077cc;
    box-shadow: 0 0 5px rgba(0, 119, 204, 0.3);
}

.radio-group,
.checkbox-group {
    display: flex;
    gap: 15px;
    margin-top: 5px;
}

button {
    padding: 10px 20px;
    background-color: #0077cc;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-right: 10px;
}

button:hover {
    background-color: #005fa3;
}

.error-message {
    display: none;
    color: #dc3545;
    font-size: 0.9em;
    margin-top: 5px;
}

input:invalid:not(:placeholder-shown),
textarea:invalid:not(:placeholder-shown) {
    border-color: #dc3545;
}

input:invalid:not(:placeholder-shown) + .error-message,
textarea:invalid:not(:placeholder-shown) + .error-message {
    display: block;
}
```

**Key Features:**
- **Accessibility:** Proper label associations, focus states, and ARIA attributes
- **Validation:** HTML5 validation with custom error messages
- **Responsive Design:** Flexbox layout for radio/checkbox groups
- **User Experience:** Clear error states and helpful placeholders
- **Security:** `novalidate` attribute for custom validation
- **Styling:** Consistent design with focus states and hover effects

**Best Practices:**
1. Always use `<label>` elements with `for` attributes
2. Use proper input types for better mobile experience
3. Implement client-side validation with HTML5 attributes
4. Provide clear error messages
5. Use semantic HTML elements
6. Ensure proper tab order
7. Make forms keyboard-navigable
8. Use ARIA attributes for accessibility
9. Implement server-side validation (not shown in this example)
10. Consider progressive enhancement for older browsers

*   **`<form>`:** The main form element.
    *   `action`: Specifies where to send the form data when submitted (usually a server-side script).
    *   `method`: Specifies the HTTP method to use (usually `post` for sending data securely).
*   **`<label>`:** Provides a label for an input field (important for accessibility).
    *   `for`: Associates the label with an input field using the input's `id`.
*   **`<input>`:** Creates various types of input fields.
    *   `type`: Specifies the input type (e.g., `text`, `email`, `password`, `checkbox`, `radio`, `submit`).
    *   `id`: Unique identifier for the input field.
    *   `name`: Name of the input field (used when submitting data).
    *   `required`: Makes the field mandatory.
*   **`<textarea>`:** Creates a multi-line text input area.
*   **`<select>`:** Creates a dropdown list.
    *   **`<option>`:** Defines an option within the dropdown list.

**3.2 Tables**

Tables are used to display data in rows and columns.

```html
<table>
    <caption>Employee Data</caption>
    <thead>
        <tr>
            <th>Name</th>
            <th>Department</th>
            <th>Salary</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>John Doe</td>
            <td>Sales</td>
            <td>$50,000</td>
        </tr>
        <tr>
            <td>Jane Smith</td>
            <td>Marketing</td>
            <td>$60,000</td>
        </tr>
    </tbody>
</table>
```

*   **`<table>`:** The main table element.
*   **`<caption>`:** Provides a caption for the table.
*   **`<thead>`:** Groups the table header rows.
*   **`<tbody>`:** Groups the table body rows.
*   **`<tr>`:** Defines a table row.
*   **`<th>`:** Defines a table header cell (usually bold and centered).
*   **`<td>`:** Defines a table data cell.

**3.3 Semantic HTML5 Elements**

Semantic elements provide meaning to the structure of a web page, making it more understandable for both browsers and developers.

```html
<header>
    </header>

<nav>
    </nav>

<main>
    <article>
        <section>
            </section>
    </article>
    <aside>
        </aside>
</main>

<footer>
    </footer>
```

*   **`<header>`:** Represents the introductory content of a page or section.
*   **`<nav>`:** Represents a section with navigation links.
*   **`<main>`:** Represents the main content of the page (there should be only one per page).
*   **`<article>`:** Represents a self-contained piece of content (e.g., a blog post).
*   **`<section>`:** Represents a thematic grouping of content within a page or article.
*   **`<aside>`:** Represents content that is tangentially related to the main content (e.g., a sidebar).
*   **`<footer>`:** Represents the footer of a page or section.

**Module 4: Intermediate CSS**

**4.1 The Box Model**

The box model is a fundamental concept that describes how elements are rendered on a page as rectangular boxes. Understanding it is crucial for proper layout and spacing.

```html
<div class="box">
  This is a box with padding, border, and margin
</div>
```

```css
.box {
  /* Content dimensions */
  width: 300px;
  height: 200px;
  
  /* Padding */
  padding: 20px;
  
  /* Border */
  border: 5px solid #0077cc;
  border-radius: 8px;
  
  /* Margin */
  margin: 30px;
  
  /* Background */
  background-color: #f0f8ff;
  
  /* Text styling */
  color: #333;
  font-size: 16px;
  line-height: 1.5;
}
```

* **Content Box**: The innermost area containing the actual content
  - Controlled by width/height properties
  - Default background color is transparent
  - Text and child elements are rendered here

* **Padding**: Space between content and border
  - Adds to element's total size
  - Inherits background color
  - Useful for internal spacing
  ```css
  /* Individual sides */
  padding-top: 10px;
  padding-right: 15px;
  padding-bottom: 20px;
  padding-left: 15px;
  
  /* Shorthand */
  padding: 10px 15px 20px 15px; /* top right bottom left */
  padding: 10px 15px; /* vertical horizontal */
  padding: 10px; /* all sides */
  ```

* **Border**: Line surrounding padding and content
  - Adds to element's total size
  - Can have different styles, widths, and colors
  ```css
  /* Individual properties */
  border-width: 2px;
  border-style: solid;
  border-color: #0077cc;
  
  /* Shorthand */
  border: 2px solid #0077cc;
  
  /* Rounded corners */
  border-radius: 8px;
  ```

* **Margin**: Space outside the border
  - Creates space between elements
  - Transparent (doesn't inherit background)
  - Can collapse with adjacent margins
  ```css
  /* Individual sides */
  margin-top: 20px;
  margin-right: 15px;
  margin-bottom: 20px;
  margin-left: 15px;
  
  /* Shorthand */
  margin: 20px 15px; /* vertical horizontal */
  margin: 20px; /* all sides */
  
  /* Centering elements */
  margin: 0 auto;
  ```

**Box Model Visualization:**

```
+---------------------------+
|         Margin            |
|  +---------------------+  |
|  |      Border         |  |
|  |  +---------------+  |  |
|  |  |    Padding    |  |  |
|  |  |  +---------+  |  |  |
|  |  |  | Content |  |  |  |
|  |  |  +---------+  |  |  |
|  |  +---------------+  |  |
|  +---------------------+  |
+---------------------------+
```

**Box-Sizing Property:**

By default, padding and border are added to the element's width/height. The `box-sizing` property changes this behavior:

```css
/* Default behavior */
.box-default {
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  /* Total width = 300 + 20*2 + 5*2 = 350px */
}

/* Border-box behavior */
.box-border {
  box-sizing: border-box;
  width: 300px;
  padding: 20px;
  border: 5px solid black;
  /* Total width = 300px (includes padding and border) */
}
```

Best Practices:
- Use `box-sizing: border-box` for more predictable layouts
- Use margin for spacing between elements
- Use padding for internal spacing within elements
- Be consistent with spacing values (e.g., use multiples of 4px or 8px)
- Use CSS variables for consistent spacing values

**4.2 Display Property**

The `display` property is one of the most important CSS properties, controlling how an element is rendered and how it interacts with other elements.

```html
<div class="block-example">Block Element</div>
<span class="inline-example">Inline Element</span>
<div class="inline-block-example">Inline-Block Element</div>
<div class="hidden-example">Hidden Element</div>
```

```css
/* Block-level elements */
.block-example {
  display: block;
  width: 80%;
  padding: 20px;
  background-color: #f0f8ff;
  border: 1px solid #0077cc;
  margin-bottom: 10px;
}

/* Inline elements */
.inline-example {
  display: inline;
  padding: 5px;
  background-color: #fff3cd;
  border: 1px solid #ffc107;
  /* width and height have no effect on inline elements */
}

/* Inline-block elements */
.inline-block-example {
  display: inline-block;
  width: 200px;
  padding: 10px;
  background-color: #d4edda;
  border: 1px solid #28a745;
  margin: 5px;
}

/* Hidden elements */
.hidden-example {
  display: none;
}
```

**Display Property Values:**

* **`block`**
  - Takes full available width (unless width is specified)
  - Starts on a new line
  - Can set width, height, margin, padding
  - Examples: `<div>`, `<p>`, `<h1>`-`<h6>`, `<form>`, `<ul>`, `<ol>`, `<li>`
  - Common uses: Page sections, containers, structural elements

* **`inline`**
  - Takes only as much width as needed
  - Flows with text content
  - Cannot set width/height
  - Vertical padding/margin doesn't affect surrounding elements
  - Examples: `<span>`, `<a>`, `<img>`, `<strong>`, `<em>`
  - Common uses: Text formatting, inline elements

* **`inline-block`**
  - Combines features of block and inline
  - Flows like inline elements
  - Can set width/height like block elements
  - Respects vertical margin/padding
  - Examples: Custom buttons, navigation items
  - Common uses: Creating grid-like layouts without flex/grid

* **`none`**
  - Completely removes element from document flow
  - Takes up no space
  - Not accessible to screen readers
  - Alternative: Use `visibility: hidden` to hide while maintaining space

**Display Property Best Practices:**

1. Use semantic HTML elements with their default display values when possible
2. Prefer `inline-block` over `float` for simple layouts
3. Use `display: none` judiciously - consider accessibility implications
4. Combine with other properties for complex layouts:
   ```css
   .menu-item {
     display: inline-block;
     width: 120px;
     text-align: center;
     padding: 10px;
     margin: 0 5px;
     background-color: #f8f9fa;
     border-radius: 4px;
   }
   ```
5. Use CSS Grid or Flexbox for complex layouts instead of relying solely on display properties

**Common Display Patterns:**

1. Centering Elements:
```css
/* Horizontally center block element */
.block-center {
  display: block;
  width: 80%;
  margin: 0 auto;
}

/* Vertically and horizontally center */
.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

2. Responsive Navigation:
```css
/* Mobile first approach */
.nav-item {
  display: block;
  padding: 10px;
}

@media (min-width: 768px) {
  .nav-item {
    display: inline-block;
  }
}
```

3. Image Gallery:
```css
.gallery-item {
  display: inline-block;
  width: 23%;
  margin: 1%;
  vertical-align: top;
}

@media (max-width: 768px) {
  .gallery-item {
    width: 48%;
  }
}
```

4. Toggle Visibility:
```css
/* JavaScript toggle class */
.hidden {
  display: none;
}

.visible {
  display: block;
}
```

**Accessibility Considerations:**
- Use `display: none` carefully as it removes elements from accessibility tree
- Consider `visibility: hidden` or `opacity: 0` for hiding elements while maintaining accessibility
- Ensure proper focus management when toggling visibility

**4.3 Positioning**

The `position` property is crucial for controlling element placement and creating complex layouts. Let's explore each positioning type with practical examples.

```html
<div class="position-examples">
  <div class="static-box">Static</div>
  <div class="relative-box">Relative</div>
  <div class="absolute-box">Absolute</div>
  <div class="fixed-box">Fixed</div>
  <div class="sticky-box">Sticky</div>
</div>
```

```css
.position-examples {
  position: relative;
  height: 2000px;
  border: 2px solid #ccc;
  padding: 20px;
}

/* Static Positioning (Default) */
.static-box {
  position: static;
  background-color: #f0f8ff;
  padding: 10px;
  border: 1px solid #0077cc;
}

/* Relative Positioning */
.relative-box {
  position: relative;
  top: 20px;
  left: 50px;
  background-color: #fff3cd;
  padding: 10px;
  border: 1px solid #ffc107;
  z-index: 1;
}

/* Absolute Positioning */
.absolute-box {
  position: absolute;
  top: 100px;
  right: 20px;
  background-color: #d4edda;
  padding: 10px;
  border: 1px solid #28a745;
  width: 200px;
}

/* Fixed Positioning */
.fixed-box {
  position: fixed;
  bottom: 20px;
  right: 20px;
  background-color: #f8d7da;
  padding: 10px;
  border: 1px solid #dc3545;
  width: 150px;
  text-align: center;
}

/* Sticky Positioning */
.sticky-box {
  position: sticky;
  top: 20px;
  background-color: #e2e3e5;
  padding: 10px;
  border: 1px solid #6c757d;
}
```

**Position Property Values:**

* **`static` (Default)**
  - Elements follow normal document flow
  - Ignores top/right/bottom/left properties
  - Cannot use z-index
  - Use case: Default behavior for most elements

* **`relative`**
  - Positioned relative to its normal position
  - Can use top/right/bottom/left to offset
  - Creates new stacking context (z-index works)
  - Original space in document flow is preserved
  - Use cases:
    - Minor adjustments to element position
    - Creating reference point for absolutely positioned children
    - Overlapping elements with z-index

* **`absolute`**
  - Removed from normal document flow
  - Positioned relative to nearest positioned ancestor
  - If no positioned ancestor, uses initial containing block (usually viewport)
  - Can use top/right/bottom/left for precise positioning
  - Use cases:
    - Tooltips and dropdown menus
    - Modal dialogs
    - Custom form controls
    - Overlays and popups

* **`fixed`**
  - Removed from normal document flow
  - Positioned relative to viewport
  - Stays fixed during scrolling
  - Can use top/right/bottom/left for positioning
  - Use cases:
    - Fixed headers/footers
    - Persistent navigation
    - Chat widgets
    - Back-to-top buttons

* **`sticky`**
  - Hybrid of relative and fixed
  - Treated as relative until crossing specified threshold
  - Then becomes fixed within its container
  - Requires at least one positioning property (top/right/bottom/left)
  - Use cases:
    - Sticky table headers
    - Sticky sidebars
    - Sticky navigation
    - Section headers in long pages

**Positioning Best Practices:**

1. Use relative positioning for minor adjustments and as reference points
2. Use absolute positioning for UI elements that need precise placement
3. Use fixed positioning for elements that should remain visible during scrolling
4. Use sticky positioning for elements that should stick after scrolling past a point
5. Always consider accessibility when positioning elements
6. Use z-index judiciously to control stacking order
7. Test positioning across different screen sizes
8. Combine with transform for advanced positioning effects

**Common Positioning Patterns:**

1. Centering Elements:
```css
/* Absolute Centering */
.center-absolute {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

/* Fixed Centering */
.center-fixed {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

2. Sticky Header:
```css
.header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: white;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}
```

3. Overlay Modal:
```css
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.5);
  z-index: 1000;
}

.modal-content {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 90%;
  max-width: 600px;
  background: white;
  padding: 20px;
  border-radius: 8px;
}
```

4. Tooltip:
```css
.tooltip-container {
  position: relative;
}

.tooltip {
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  background: #333;
  color: white;
  padding: 5px 10px;
  border-radius: 4px;
  white-space: nowrap;
  opacity: 0;
  transition: opacity 0.2s;
}

.tooltip-container:hover .tooltip {
  opacity: 1;
}
```

**Accessibility Considerations:**
- Ensure positioned elements maintain proper focus order
- Use ARIA attributes for modals and tooltips
- Consider screen reader users when using absolute/fixed positioning
- Test with keyboard navigation
- Provide alternative ways to access content that might be obscured by fixed elements

**Performance Considerations:**
- Fixed and sticky elements can cause repaints during scrolling
- Use transform instead of top/left for animations
- Avoid excessive use of z-index
- Use will-change property for elements that will be animated

**4.4 Floats**

The `float` property was traditionally used for page layouts and wrapping text around images. While modern layouts typically use Flexbox or Grid, floats are still useful for specific scenarios like text wrapping and legacy browser support.

```html
<div class="float-container">
  <img src="image.jpg" alt="Description" class="float-left">
  <p>Text wraps around the floated image...</p>
</div>

<div class="clearfix"></div>
```

```css
/* Basic float example */
.float-left {
  float: left;
  margin: 0 20px 20px 0;
  width: 200px;
  shape-outside: circle(50%);
}

.float-right {
  float: right;
  margin: 0 0 20px 20px;
  width: 200px;
  shape-outside: polygon(0 0, 100% 0, 100% 100%);
}

/* Clearfix technique */
.clearfix::after {
  content: "";
  display: table;
  clear: both;
}

/* Modern float container */
.float-container {
  display: flow-root; /* Better than clearfix */
  padding: 20px;
  border: 1px solid #ddd;
}

/* Text wrapping with shapes */
.wrap-shape {
  float: left;
  width: 200px;
  height: 200px;
  margin: 0 20px 20px 0;
  shape-outside: url('shape.png');
  clip-path: url('shape.png');
}
```

**Float Property Values:**

* **`left`**
  - Floats element to left of container
  - Content flows around right side
  - Common uses: Image/text wrapping, legacy layouts

* **`right`**
  - Floats element to right of container
  - Content flows around left side
  - Common uses: Pull quotes, sidebars

* **`none`** (default)
  - Element remains in normal flow
  - Useful for overriding float behavior

**Float Behavior Characteristics:**

1. Removes element from normal document flow
2. Other content flows around floated element
3. Parent container collapses unless cleared
4. Requires width for predictable behavior
5. Can cause layout issues if not managed properly

**Modern Float Techniques:**

1. Shape Wrapping:
```css
.image-wrap {
  float: left;
  width: 200px;
  margin: 0 20px 20px 0;
  shape-outside: circle(50%);
  clip-path: circle(50%);
}
```

2. Text Wrapping:
```css
.text-wrap {
  float: right;
  width: 40%;
  margin: 0 0 20px 20px;
  shape-outside: margin-box;
}
```

3. Drop Caps:
```css
.drop-cap::first-letter {
  float: left;
  font-size: 4em;
  line-height: 0.8;
  margin: 0 10px 0 0;
}
```

**Clearing Floats:**

1. Clearfix Technique:
```css
.clearfix::after {
  content: "";
  display: table;
  clear: both;
}
```

2. Modern Flow-Root:
```css
.container {
  display: flow-root; /* Better alternative to clearfix */
}
```

3. Clear Property:
```css
.clear {
  clear: both;
}
```

**Float Best Practices:**

1. Use floats primarily for text wrapping and legacy support
2. Prefer Flexbox or Grid for modern layouts
3. Always clear floats to prevent layout issues
4. Use `display: flow-root` instead of clearfix when possible
5. Set explicit widths on floated elements
6. Use shape-outside for advanced text wrapping
7. Test across browsers for consistent behavior
8. Consider accessibility when using floats

**Common Float Patterns:**

1. Image Gallery:
```css
.gallery-item {
  float: left;
  width: 23%;
  margin: 1%;
}

@media (max-width: 768px) {
  .gallery-item {
    width: 48%;
  }
}
```

2. Pull Quotes:
```css
.pull-quote {
  float: right;
  width: 40%;
  margin: 0 0 20px 20px;
  font-style: italic;
  border-left: 3px solid #0077cc;
  padding-left: 15px;
}
```

3. Sidebar Layout:
```css
.sidebar {
  float: left;
  width: 25%;
}

.main-content {
  float: right;
  width: 72%;
}

@media (max-width: 768px) {
  .sidebar, .main-content {
    float: none;
    width: 100%;
  }
}
```

**Accessibility Considerations:**

- Ensure content order makes sense when floated
- Use proper alt text for floated images
- Test with screen readers
- Consider how floated elements affect tab order
- Provide clear visual separation for floated content

**Performance Considerations:**

- Excessive floats can cause layout thrashing
- Use will-change property for animated floats
- Minimize reflows by batching float changes
- Consider using CSS containment for complex float layouts

**When to Use Floats vs. Modern Layout Methods:**

| Feature            | Floats          | Flexbox         | Grid            |
|--------------------|-----------------|-----------------|-----------------|
| Text Wrapping      | Excellent       | Not supported   | Not supported   |
| Layout Control     | Limited         | Excellent       | Excellent       |
| Responsiveness     | Difficult       | Easy            | Easy            |
| Browser Support    | Excellent       | Modern browsers | Modern browsers |
| Accessibility      | Challenging     | Good            | Good            |
| Complex Layouts    | Difficult       | Good            | Excellent       |
| Vertical Alignment | Not supported   | Excellent       | Excellent       |
| Order Control      | Not supported   | Excellent       | Excellent       |

**Legacy Float Layout Example:**

```css
/* Old-school 3-column layout */
.header {
  width: 100%;
  margin-bottom: 20px;
}

.column {
  float: left;
  width: 31%;
  margin: 0 1%;
}

.footer {
  clear: both;
  margin-top: 20px;
}

@media (max-width: 768px) {
  .column {
    float: none;
    width: 100%;
    margin: 10px 0;
  }
}
```

**Modern Alternatives:**

1. Flexbox:
```css
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.item {
  flex: 1 1 300px;
}
```

2. Grid:
```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
```

**Conclusion:**

While floats are no longer the primary tool for page layouts, they remain valuable for specific use cases like text wrapping and legacy browser support. Modern CSS layout methods like Flexbox and Grid should be your first choice for most layout needs, but understanding floats is still important for maintaining older codebases and implementing certain design patterns.

**4.5 Flexbox**

Flexbox is a powerful one-dimensional layout system that provides efficient ways to align, distribute, and space items within a container. It's particularly useful for creating responsive layouts and handling dynamic content.

```html
<div class="flex-container">
  <div class="flex-item">1</div>
  <div class="flex-item">2</div>
  <div class="flex-item">3</div>
</div>
```

```css
/* Basic Flexbox Container */
.flex-container {
  display: flex;
  flex-direction: row; /* Default */
  justify-content: space-between;
  align-items: center;
  gap: 20px;
  padding: 20px;
  border: 1px solid #ddd;
}

.flex-item {
  flex: 1 1 200px;
  padding: 20px;
  background-color: #f0f8ff;
  border: 1px solid #0077cc;
}
```

**Flexbox Container Properties:**

1. **display: flex**
   - Enables flexbox layout
   - Creates flex formatting context
   - Direct children become flex items

2. **flex-direction**
   - Defines main axis direction
   - Values: row (default), row-reverse, column, column-reverse
   ```css
   .container {
     flex-direction: column; /* Stack items vertically */
   }
   ```

3. **justify-content**
   - Aligns items along main axis
   - Values: flex-start, flex-end, center, space-between, space-around, space-evenly
   ```css
   .container {
     justify-content: space-between; /* Distribute items with equal space between */
   }
   ```

4. **align-items**
   - Aligns items along cross axis
   - Values: flex-start, flex-end, center, stretch, baseline
   ```css
   .container {
     align-items: stretch; /* Stretch items to fill container */
   }
   ```

5. **flex-wrap**
   - Controls wrapping behavior
   - Values: nowrap (default), wrap, wrap-reverse
   ```css
   .container {
     flex-wrap: wrap; /* Allow items to wrap to new line */
   }
   ```

6. **gap**
   - Sets spacing between items
   - Values: length or percentage
   ```css
   .container {
     gap: 20px; /* Space between items */
   }
   ```

**Flexbox Item Properties:**

1. **flex**
   - Shorthand for flex-grow, flex-shrink, and flex-basis
   - Default: 0 1 auto
   ```css
   .item {
     flex: 1 1 200px; /* Grow, shrink, basis */
   }
   ```

2. **align-self**
   - Overrides align-items for individual items
   - Values: auto, flex-start, flex-end, center, stretch, baseline
   ```css
   .special-item {
     align-self: flex-end; /* Align this item differently */
   }
   ```

3. **order**
   - Controls display order of items
   - Default: 0
   ```css
   .first-item {
     order: -1; /* Move to start */
   }
   ```

**Common Flexbox Patterns:**

1. **Responsive Navigation:**
```css
.nav {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.nav-item {
  flex: 1 1 150px;
  text-align: center;
}
```

2. **Card Layout:**
```css
.card-container {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.card {
  flex: 1 1 300px;
  padding: 20px;
  border: 1px solid #ddd;
}
```

3. **Sticky Footer:**
```css
body {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
}

main {
  flex: 1;
}

footer {
  margin-top: auto;
}
```

4. **Centering Elements:**
```css
.center-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

5. **Equal Height Columns:**
```css
.columns {
  display: flex;
}

.column {
  flex: 1;
  padding: 20px;
}
```

**Flexbox Best Practices:**

1. Use semantic HTML with flexbox
2. Prefer flexbox over floats for modern layouts
3. Use gap instead of margins for spacing
4. Combine with media queries for responsive designs
5. Use flex-basis instead of width for flexible sizing
6. Avoid nesting too many flex containers
7. Use min-width/max-width with flex items
8. Test across browsers for consistent behavior

**Accessibility Considerations:**

- Ensure logical source order matches visual order
- Use proper heading hierarchy
- Maintain keyboard navigation
- Consider screen reader users
- Test with high contrast modes

**Performance Considerations:**

- Avoid excessive nesting of flex containers
- Use will-change for animated flex items
- Minimize layout thrashing
- Use contain: layout when appropriate
- Avoid unnecessary reflows

**Flexbox vs. Grid:**

| Feature            | Flexbox          | Grid             |
|--------------------|------------------|------------------|
| Dimension          | One-dimensional  | Two-dimensional  |
| Alignment          | Excellent        | Excellent        |
| Responsiveness     | Easy             | Easy             |
| Complex Layouts    | Good             | Excellent        |
| Item Ordering      | Easy             | Limited          |
| Browser Support    | Excellent        | Modern browsers  |
| Use Case           | Components       | Page Layouts     |

**Common Flexbox Mistakes:**

1. Forgetting to set flex-direction
2. Overusing flex-grow
3. Not using gap for spacing
4. Ignoring flex-wrap
5. Using fixed widths with flex items
6. Not testing in older browsers
7. Over-nesting flex containers
8. Forgetting to set min-width/max-width

**Advanced Flexbox Techniques:**

1. **Intrinsic Sizing:**
```css
.container {
  display: flex;
  width: min-content;
}
```

2. **Aspect Ratio Boxes:**
```css
.aspect-box {
  flex: 1;
  aspect-ratio: 1;
}
```

3. **Sticky Sidebar:**
```css
.layout {
  display: flex;
  height: 100vh;
}

.sidebar {
  flex: 0 0 250px;
  position: sticky;
  top: 0;
}
```

4. **Responsive Masonry:**
```css
.masonry {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.masonry-item {
  flex: 1 1 300px;
}
```

5. **Dynamic Grid:**
```css
.grid {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.grid-item {
  flex: 1 1 calc(33.33% - 40px);
}
```

**Conclusion:**

Flexbox is an essential tool for modern web layouts, offering powerful alignment and distribution capabilities. While it's primarily designed for one-dimensional layouts, it can handle many common layout patterns with ease. When combined with CSS Grid, you can create sophisticated, responsive designs that work across all devices and screen sizes.

**4.6 CSS Grid**

CSS Grid is a powerful two-dimensional layout system that allows for precise control over both rows and columns. It's particularly useful for creating complex, responsive layouts with ease.

```html
<div class="grid-container">
  <div class="grid-item">1</div>
  <div class="grid-item">2</div>
  <div class="grid-item">3</div>
  <div class="grid-item">4</div>
  <div class="grid-item">5</div>
  <div class="grid-item">6</div>
</div>
```

```css
/* Basic Grid Container */
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: 100px 200px;
  gap: 20px;
  padding: 20px;
  border: 1px solid #ddd;
}

.grid-item {
  background-color: #f0f8ff;
  border: 1px solid #0077cc;
  padding: 20px;
}
```

**Grid Container Properties:**

1. **display: grid**
   - Enables grid layout
   - Creates grid formatting context
   - Direct children become grid items

2. **grid-template-columns**
   - Defines column tracks
   - Values: length, percentage, fr (fraction), minmax(), repeat()
   ```css
   .container {
     grid-template-columns: 200px 1fr 30%;
   }
   ```

3. **grid-template-rows**
   - Defines row tracks
   - Values: same as grid-template-columns
   ```css
   .container {
     grid-template-rows: 100px auto 200px;
   }
   ```

4. **gap**
   - Sets spacing between grid items
   - Values: length or percentage
   ```css
   .container {
     gap: 20px;
   }
   ```

5. **grid-template-areas**
   - Defines named grid areas
   - Values: strings representing area names
   ```css
   .container {
     grid-template-areas:
       "header header"
       "sidebar main"
       "footer footer";
   }
   ```

6. **justify-content**
   - Aligns grid along the inline (row) axis
   - Values: start, end, center, stretch, space-between, space-around, space-evenly
   ```css
   .container {
     justify-content: center;
   }
   ```

7. **align-content**
   - Aligns grid along the block (column) axis
   - Values: same as justify-content
   ```css
   .container {
     align-content: start;
   }
   ```

**Grid Item Properties:**

1. **grid-column**
   - Controls item column placement
   - Values: line numbers, span
   ```css
   .item {
     grid-column: 1 / 3;
   }
   ```

2. **grid-row**
   - Controls item row placement
   - Values: same as grid-column
   ```css
   .item {
     grid-row: 2 / 4;
   }
   ```

3. **grid-area**
   - Shorthand for grid-row and grid-column
   - Can reference named areas
   ```css
   .item {
     grid-area: header;
   }
   ```

4. **justify-self**
   - Aligns item along inline axis
   - Values: start, end, center, stretch
   ```css
   .item {
     justify-self: center;
   }
   ```

5. **align-self**
   - Aligns item along block axis
   - Values: same as justify-self
   ```css
   .item {
     align-self: end;
   }
   ```

**Common Grid Patterns:**

1. **Responsive Grid:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 20px;
}
```

2. **Masonry Layout:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-auto-rows: 150px;
  gap: 20px;
}

.grid-item {
  grid-row: span 2;
}
```

3. **Holy Grail Layout:**
```css
.container {
  display: grid;
  grid-template:
    "header header header" 100px
    "sidebar main aside" 1fr
    "footer footer footer" 100px
    / 200px 1fr 200px;
  min-height: 100vh;
}
```

4. **Card Layout:**
```css
.card-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 20px;
}
```

5. **Image Gallery:**
```css
.gallery {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  gap: 10px;
}
```

**Grid Best Practices:**

1. Use semantic HTML with grid
2. Prefer grid over floats for complex layouts
3. Use fr units for flexible sizing
4. Combine with media queries for responsive designs
5. Use named grid areas for better readability
6. Avoid nesting too many grid containers
7. Use minmax() for flexible track sizing
8. Test across browsers for consistent behavior

**Accessibility Considerations:**

- Ensure logical source order matches visual order
- Use proper heading hierarchy
- Maintain keyboard navigation
- Consider screen reader users
- Test with high contrast modes

**Performance Considerations:**

- Avoid excessive nesting of grid containers
- Use will-change for animated grid items
- Minimize layout thrashing
- Use contain: layout when appropriate
- Avoid unnecessary reflows

**Grid vs. Flexbox:**

| Feature            | Grid             | Flexbox          |
|--------------------|------------------|------------------|
| Dimension          | Two-dimensional  | One-dimensional  |
| Alignment          | Excellent        | Excellent        |
| Responsiveness     | Easy             | Easy             |
| Complex Layouts    | Excellent        | Good             |
| Item Ordering      | Limited          | Easy             |
| Browser Support    | Modern browsers  | Excellent        |
| Use Case           | Page Layouts     | Components       |

**Common Grid Mistakes:**

1. Forgetting to set grid-template-columns
2. Overusing fixed track sizes
3. Not using gap for spacing
4. Ignoring grid-template-areas
5. Using fixed widths with grid items
6. Not testing in older browsers
7. Over-nesting grid containers
8. Forgetting to set min-width/max-width

**Advanced Grid Techniques:**

1. **Subgrid:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 20px;
}

.grid-item {
  display: grid;
  grid-template-columns: subgrid;
}
```

2. **Aspect Ratio Boxes:**
```css
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  aspect-ratio: 1;
}
```

3. **Sticky Sidebar:**
```css
.layout {
  display: grid;
  grid-template-columns: 250px 1fr;
  height: 100vh;
}

.sidebar {
  position: sticky;
  top: 0;
}
```

4. **Responsive Masonry:**
```css
.masonry {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
  grid-auto-rows: 150px;
  gap: 20px;
}

.masonry-item {
  grid-row: span 2;
}
```

5. **Dynamic Grid:**
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}
```

**Conclusion:**

CSS Grid is an essential tool for modern web layouts, offering powerful two-dimensional layout capabilities. When combined with Flexbox, you can create sophisticated, responsive designs that work across all devices and screen sizes. Grid is particularly well-suited for page layouts and complex grid-based designs, while Flexbox excels at one-dimensional layouts and component-level designs.

**4.7 Media Queries and Responsive Design**

Media queries are a fundamental tool for creating responsive websites that adapt to different screen sizes and devices. They allow you to apply CSS rules based on various device characteristics.

```css
/* Basic Media Query Structure */
@media media-type and (media-feature) {
  /* CSS rules */
}
```

**Media Types:**
- `all` (default) - All devices
- `screen` - Computer screens, tablets, smartphones
- `print` - Printers and print preview
- `speech` - Screen readers

**Common Media Features:**
1. **Width and Height:**
   - `width`, `min-width`, `max-width`
   - `height`, `min-height`, `max-height`
   ```css
   @media (min-width: 768px) {
     .container {
       width: 750px;
     }
   }
   ```

2. **Orientation:**
   - `portrait` - Height > Width
   - `landscape` - Width > Height
   ```css
   @media (orientation: landscape) {
     .header {
       height: 100vh;
     }
   }
   ```

3. **Resolution:**
   - `resolution` - Device pixel density
   - `min-resolution`, `max-resolution`
   ```css
   @media (min-resolution: 2dppx) {
     .logo {
       background-image: url('logo@2x.png');
     }
   }
   ```

4. **Aspect Ratio:**
   - `aspect-ratio` - Width to height ratio
   ```css
   @media (aspect-ratio: 16/9) {
     .video-container {
       padding-top: 56.25%;
     }
   }
   ```

**Responsive Design Strategies:**

1. **Mobile-First Approach:**
```css
/* Base styles for mobile */
.container {
  padding: 10px;
}

/* Styles for larger screens */
@media (min-width: 768px) {
  .container {
    padding: 20px;
  }
}
```

2. **Breakpoint Selection:**
```css
/* Common breakpoints */
@media (min-width: 576px) { /* Small devices */ }
@media (min-width: 768px) { /* Tablets */ }
@media (min-width: 992px) { /* Desktops */ }
@media (min-width: 1200px) { /* Large desktops */ }
```

3. **Fluid Layouts:**
```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
}
```

4. **Responsive Typography:**
```css
html {
  font-size: 16px;
}

@media (min-width: 768px) {
  html {
    font-size: 18px;
  }
}
```

5. **Responsive Images:**
```html
<picture>
  <source media="(min-width: 1200px)" srcset="large.jpg">
  <source media="(min-width: 768px)" srcset="medium.jpg">
  <img src="small.jpg" alt="Description">
</picture>
```

**Advanced Media Query Techniques:**

1. **Combining Conditions:**
```css
@media (min-width: 768px) and (max-width: 1199px) {
  /* Styles for tablets */
}
```

2. **Dark Mode Support:**
```css
@media (prefers-color-scheme: dark) {
  body {
    background-color: #121212;
    color: #ffffff;
  }
}
```

3. **Reduced Motion:**
```css
@media (prefers-reduced-motion: reduce) {
  * {
    animation: none !important;
    transition: none !important;
  }
}
```

4. **High Contrast Mode:**
```css
@media (prefers-contrast: high) {
  .button {
    border: 2px solid black;
  }
}
```

5. **Print Styles:**
```css
@media print {
  .no-print {
    display: none;
  }
  
  body {
    font-size: 12pt;
    color: black;
  }
}
```

**Responsive Design Best Practices:**

1. Use relative units (em, rem, %) instead of fixed units (px)
2. Implement mobile-first design approach
3. Use CSS Grid and Flexbox for flexible layouts
4. Optimize images for different screen sizes
5. Test on real devices and emulators
6. Use progressive enhancement
7. Consider performance implications
8. Implement responsive navigation patterns
9. Use CSS variables for consistent styling
10. Test with different zoom levels

**Common Responsive Patterns:**

1. **Hamburger Menu:**
```css
.nav {
  display: none;
}

@media (min-width: 768px) {
  .nav {
    display: flex;
  }
  
  .hamburger {
    display: none;
  }
}
```

2. **Responsive Grid:**
```css
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}
```

3. **Card Layout:**
```css
.card {
  width: 100%;
}

@media (min-width: 768px) {
  .card {
    width: 48%;
  }
}

@media (min-width: 992px) {
  .card {
    width: 32%;
  }
}
```

4. **Responsive Tables:**
```css
@media (max-width: 768px) {
  table, thead, tbody, th, td, tr {
    display: block;
  }
  
  td {
    position: relative;
    padding-left: 50%;
  }
  
  td::before {
    content: attr(data-label);
    position: absolute;
    left: 0;
    width: 45%;
    padding-right: 10px;
  }
}
```

5. **Viewport Units:**
```css
.header {
  height: 100vh;
}

.section {
  min-height: 50vh;
}
```

**Accessibility Considerations:**

1. Ensure proper text scaling
2. Maintain logical content order
3. Use proper heading hierarchy
4. Test with screen readers
5. Ensure sufficient color contrast
6. Provide alternative text for images
7. Make interactive elements touch-friendly
8. Test with keyboard navigation

**Performance Considerations:**

1. Optimize images for different screen sizes
2. Use responsive image techniques (srcset, picture)
3. Implement lazy loading
4. Use CSS containment
5. Minimize layout shifts
6. Optimize critical rendering path
7. Use media queries to load appropriate resources
8. Implement code splitting

**Testing Responsive Designs:**

1. Use browser developer tools
2. Test on real devices
3. Use online testing tools (BrowserStack, LambdaTest)
4. Check different orientations
5. Test with different zoom levels
6. Verify accessibility
7. Check performance metrics
8. Test with different network conditions

**Common Responsive Design Mistakes:**

1. Using fixed widths
2. Not testing on real devices
3. Ignoring performance implications
4. Not considering accessibility
5. Using too many breakpoints
6. Not implementing touch-friendly interfaces
7. Forgetting to test landscape orientation
8. Not optimizing images for different screens

**Modern Responsive Design Tools:**

1. CSS Grid and Flexbox
2. Viewport units (vw, vh, vmin, vmax)
3. CSS variables
4. Container queries (experimental)
5. Aspect-ratio property
6. clamp() function
7. min(), max() functions
8. prefers-reduced-motion media feature

**Conclusion:**

Responsive design is essential in today's multi-device world. By using media queries effectively and following best practices, you can create websites that provide optimal viewing experiences across a wide range of devices. Remember to consider not just screen size, but also device capabilities, user preferences, and performance when implementing responsive designs.

**Module 5: Capstone Project - Personal Portfolio Website**

**Project Goal:** Create a responsive personal portfolio website to showcase your skills and projects.

**Project Requirements:**

*   **HTML Structure:**
    *   Use semantic HTML5 elements.
    *   Include sections for:
        *   **Header:** Name, tagline, navigation.
        *   **About Me:** Brief introduction, photo, skills.
        *   **Projects:** Showcase at least 3 projects with images, descriptions, and links.
        *   **Contact:** Contact form.
        *   **Footer:** Copyright, social media links.
*   **CSS Styling:**
    *   Use external CSS file.
    *   Implement a visually appealing design.
    *   Use Flexbox or Grid for layout.
    *   Make the website responsive using media queries.
*   **Responsiveness:** The website should look good and function well on different screen sizes (desktops, tablets, and mobile phones).
*   **Accessibility:**
    *   Use appropriate `alt` text for images.
    *   Use semantic HTML elements.
    *   Ensure good color contrast.

**Project Steps:**

1. **Planning:**
    *   **Content:** Decide on the content you want to include in each section.
    *   **Design:** Sketch a basic layout (wireframe) for different screen sizes. Choose a color scheme and fonts.
    *   **File Structure:** Create a project folder and organize files (HTML, CSS, images).

    ```
    portfolio/
    ├── index.html
    ├── styles.css
    └── images/
        ├── project1.jpg
        ├── project2.jpg
        └── project3.jpg
    ```

2. **HTML Structure (index.html):**

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Your Name - Portfolio</title>
        <link rel="stylesheet" href="styles.css">
    </head>
    <body>
        <header>
            <div class="container">
                <h1>Your Name</h1>
                <p>Web Developer & Designer</p>
                <nav>
                    <ul>
                        <li><a href="#about">About</a></li>
                        <li><a href="#projects">Projects</a></li>
                        <li><a href="#contact">Contact</a></li>
                    </ul>
                </nav>
            </div>
        </header>

        <main>
            <section id="about">
                <div class="container">
                    <h2>About Me</h2>
                    <div class="about-content">
                        <img src="images/your-photo.jpg" alt="Your Photo">
                        <p>Write a brief introduction about yourself, your skills, and your experience.</p>
                    </div>
                    <div class="skills">
                        <h3>Skills</h3>
                        <ul>
                            <li>HTML</li>
                            <li>CSS</li>
                            <li>JavaScript</li>
                            </ul>
                    </div>
                </div>
            </section>

            <section id="projects">
                <div class="container">
                    <h2>Projects</h2>
                    <div class="projects-grid">
                        <div class="project">
                            <img src="images/project1.jpg" alt="Project 1 Screenshot">
                            <h3>Project 1 Title</h3>
                            <p>Brief description of the project.</p>
                            <a href="#" target="_blank">View Project</a>
                        </div>
                        </div>
                </div>
            </section>

            <section id="contact">
                <div class="container">
                    <h2>Contact Me</h2>
                    <form action="submit-form" method="post">
                        </form>
                </div>
            </section>
        </main>

        <footer>
            <div class="container">
                <p>&copy; 2023 Your Name</p>
                <ul class="social-links">
                    <li><a href="#" target="_blank"><i class="fab fa-linkedin"></i></a></li> 
                    </ul>
            </div>
        </footer>
    </body>
    </html>
    ```

3. **CSS Styling (styles.css):**

```css
    /* Basic Reset */
    * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
    }

    /* General Styles */
    body {
        font-family: Arial, sans-serif;
        line-height: 1.6;
        color: #333;
    }

    .container {
        width: 80%;
        margin: 0 auto;
        overflow: hidden; /* Clearfix for floats (if used) */
    }

    a {
        text-decoration: none;
        color: #0077cc;
    }

    /* Header */
    header {
        background-color: #f4f4f4;
        padding: 20px 0;
        text-align: center;
    }

    header h1 {
        font-size: 2.5rem;
        margin-bottom: 5px;
    }

    header p {
        font-size: 1.2rem;
    }

    /* Navigation */
    nav ul {
        list-style: none;
        padding-top: 10px;
    }

    nav li {
        display: inline;
        margin: 0 15px;
    }

    /* About Section */
    #about {
        padding: 40px 0;
    }

    .about-content {
        display: flex;
        align-items: center;
        gap: 30px;
    }

    .about-content img {
        width: 200px;
        border-radius: 50%;
    }
    /*Project Section*/

    .projects-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
        gap: 20px;
    }

    .project {
        border: 1px solid #ddd;
        padding: 20px;
    }

    .project img {
        max-width: 100%;
        height: auto;
    }
    /* ... More styles for other sections ... */

    /* Media Queries for Responsiveness */
    @media (max-width: 768px) {
        .container {
            width: 90%;
        }

        .about-content {
            flex-direction: column;
        }
        .projects-grid{
          grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        }
    }
```

1. **Further Development:**
    *   Add more styles and refine the design.
    *   Fill in the content for all sections.
    *   Add more projects.
    *   Consider adding JavaScript for interactivity (e.g., a responsive menu toggle, form validation).
    *   Test thoroughly on different browsers and devices.

**Project Enhancements:**

*   **Image Gallery:** Use a JavaScript library (like Lightbox or PhotoSwipe) to create an interactive image gallery for your project screenshots.
*   **Testimonials:** If you have client feedback, add a testimonials section.
*   **Blog:** If you write, add a blog section where you can post articles related to web development. You can create a simple static blog using HTML and CSS or use a static site generator like Jekyll or Hugo.
*   **Custom 404 Page:** Create a custom 404 error page to provide a better user experience if someone tries to access a non-existent page on your website.

**Deployment:**

1. **Choose a Web Host:** Select a web hosting provider (e.g., Netlify, Vercel, GitHub Pages - these offer free hosting for static sites).
2. **Get a Domain Name (Optional):** Register a domain name (e.g., yourname.com) through a domain registrar (e.g., Namecheap, GoDaddy).
3. **Upload Your Files:** Upload your HTML, CSS, and image files to your web host using FTP or their web interface.
4. **Configure DNS (if using a custom domain):** Point your domain name to your web host's servers by updating your DNS settings.

**Conclusion:**

This masterclass has provided you with a strong foundation in HTML and CSS, covering everything from basic syntax to advanced layout techniques and responsive design. By completing the capstone project, you now have a portfolio-ready website that demonstrates your skills and knowledge.

Remember that web development is an ongoing learning process. Keep practicing, exploring new technologies, and building projects to further enhance your skills. The world of front-end development is constantly evolving, so stay curious and never stop learning!
