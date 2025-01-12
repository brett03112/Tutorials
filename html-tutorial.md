# HTML: The Foundation of the Web

## Introduction
HTML (HyperText Markup Language) is the standard markup language for creating web pages. Think of it as the skeleton of every website you visit. In this tutorial, we'll learn how to create well-structured HTML documents, understand the purpose of different elements, and build a complete project to showcase your skills.

## Section 1: Basic Structure and Syntax

### The HTML Document Structure
Every HTML document follows a standard structure:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First HTML Page</title>
</head>
<body>
    <!-- Content goes here -->
</body>
</html>
```

Let's break down what each part means:
- `<!DOCTYPE html>`: Declares this is an HTML5 document
- `<html>`: The root element of the page
- `<head>`: Contains metadata about the document
- `<body>`: Contains the visible content

### Exercise 1: Creating Your First HTML Page
Create a new file called `index.html` and replicate the structure above. Add a heading inside the body that says "Hello, World!". Remember to use the `<h1>` tag for main headings.

## Section 2: Text Elements and Semantic HTML

### Common Text Elements
HTML provides various elements for structuring text:

```html
<h1>Main Heading</h1>
<h2>Subheading</h2>
<p>This is a paragraph of text.</p>
<strong>Important text</strong>
<em>Emphasized text</em>
<blockquote>A quoted section of text</blockquote>
```

### Semantic Elements
Semantic elements give meaning to your content:

```html
<article>
    <header>
        <h1>Article Title</h1>
    </header>
    <section>
        <p>Article content...</p>
    </section>
    <footer>
        <p>Article footer...</p>
    </footer>
</article>
```

### Exercise 2: Blog Post Structure
Create a blog post using semantic HTML. Include:
1. A main heading
2. Two paragraphs
3. A blockquote
4. A subheading
5. Another paragraph

## Section 3: Lists and Links

### Types of Lists
HTML supports three types of lists:

```html
<!-- Unordered List -->
<ul>
    <li>Item 1</li>
    <li>Item 2</li>
</ul>

<!-- Ordered List -->
<ol>
    <li>First item</li>
    <li>Second item</li>
</ol>

<!-- Description List -->
<dl>
    <dt>Term</dt>
    <dd>Description</dd>
</dl>
```

### Creating Links
Links are created using the anchor tag:

```html
<a href="https://www.example.com">Click here</a>
<a href="about.html">About page</a>
<a href="#section-id">Jump to section</a>
```

### Exercise 3: Navigation Menu
Create a navigation menu with:
1. An unordered list
2. At least 4 links (Home, About, Services, Contact)
3. Make one link open in a new tab using `target="_blank"`

## Section 4: Images and Media

### Adding Images
Images require both source and alternative text:

```html
<img src="image.jpg" alt="Description of image">
```

### Figure Element
For images with captions:

```html
<figure>
    <img src="diagram.jpg" alt="Diagram showing HTML structure">
    <figcaption>Basic HTML document structure</figcaption>
</figure>
```

### Exercise 4: Image Gallery
Create a simple image gallery with:
1. Three images in a row
2. Each image wrapped in a figure element
3. Appropriate captions for each image

## Section 5: Forms and Input

### Basic Form Structure
Forms are used to collect user input:

```html
<form action="/submit" method="POST">
    <label for="username">Username:</label>
    <input type="text" id="username" name="username" required>
    
    <label for="password">Password:</label>
    <input type="password" id="password" name="password" required>
    
    <button type="submit">Submit</button>
</form>
```

### Common Input Types
```html
<input type="text">
<input type="email">
<input type="password">
<input type="number">
<input type="date">
<input type="checkbox">
<input type="radio">
<textarea></textarea>
<select>
    <option>Option 1</option>
    <option>Option 2</option>
</select>
```

### Exercise 5: Contact Form
Create a contact form with:
1. Name field (required)
2. Email field (required)
3. Subject dropdown (3 options)
4. Message textarea
5. Submit button

## Final Project: Personal Portfolio Website

Now it's time to put everything together! You'll create a personal portfolio website that showcases your understanding of HTML.

### Project Requirements:

1. Homepage (index.html)
   - Navigation menu
   - Hero section with your name and brief introduction
   - Featured projects section
   - Contact information

2. About Page (about.html)
   - Professional photo/avatar
   - Detailed biography
   - Skills list
   - Educational background

3. Projects Page (projects.html)
   - At least 3 project showcases
   - Each project should have:
     - Title
     - Description
     - Image
     - Link (can be placeholder)

4. Contact Page (contact.html)
   - Contact form
   - Social media links
   - Business hours
   - Location information

### Project Steps:

1. Create the file structure:
```
portfolio/
├── index.html
├── about.html
├── projects.html
├── contact.html
└── images/
```

2. Create the basic HTML structure for each page
3. Add the navigation menu to all pages
4. Build each page according to requirements
5. Test all links and forms
6. Validate your HTML using the W3C Validator

### Best Practices to Follow:

1. Use semantic HTML throughout
2. Include proper indentation
3. Add helpful comments
4. Ensure all images have alt text
5. Make sure all forms have labels
6. Use descriptive class names

### Testing Your Project:

After completing your portfolio:
1. Click through all navigation links
2. Fill out all forms
3. Check if images load properly
4. Validate your HTML
5. Test on different browsers

## Resources and Next Steps

### HTML Validation
- Use the W3C Validator: https://validator.w3.org/

### Further Learning
1. Learn CSS to style your HTML
2. Study JavaScript for interactivity
3. Explore responsive design principles
4. Learn about web accessibility

### Common Mistakes to Avoid:
1. Forgetting to close tags
2. Missing required attributes
3. Improper nesting
4. Using deprecated elements
5. Non-semantic markup

Remember: The key to mastering HTML is practice. Don't be afraid to experiment and make mistakes. Use the browser's developer tools to inspect and understand how other websites are built.
