# Lesson 01: Introduction To HTML

## Learning Objectives

By the end of this lesson, you should be able to:

- Explain what HTML means.
- Understand the role of HTML in web development.
- Understand the difference between HTML, CSS, and JavaScript.
- Create basic HTML elements.
- Understand tags, elements, and attributes.
- Write your first simple webpage.

## What Is HTML?

HTML means HyperText Markup Language.

HTML is used to structure content on webpages.

It tells the browser what content exists and what each piece of content means.

Examples of content HTML can describe:

- Headings
- Paragraphs
- Links
- Images
- Lists
- Tables
- Forms
- Buttons
- Sections
- Articles

HTML is not used mainly for styling.

HTML is not used mainly for programming logic.

HTML is used for structure and meaning.

## HTML, CSS and JavaScript

A webpage usually uses three major technologies:

HTML:
    Structure and meaning.

CSS:
    Styling and layout.

JavaScript:
    Behavior and interactivity.

Example:

HTML creates a button.

CSS makes the button beautiful.

JavaScript makes the button do something when clicked.

## What Is A Tag?

A tag is a piece of HTML syntax.

Example:

    <p>

This is an opening paragraph tag.

A closing tag looks like this:

    </p>

## What Is An Element?

An element usually includes an opening tag, content, and a closing tag.

Example:

    <p>This is a paragraph.</p>

Opening tag:

    <p>

Content:

    This is a paragraph.

Closing tag:

    </p>

## Basic HTML Examples

Heading:

    <h1>Welcome To My Website</h1>

Paragraph:

    <p>This is my first webpage.</p>

Link:

    <a href="https://example.com">Visit Example</a>

Image:

    <img src="photo.jpg" alt="A sample photo">

## What Is An Attribute?

An attribute adds extra information to an HTML element.

Example:

    <a href="https://github.com">GitHub</a>

Here:

    href

is an attribute.

It tells the browser where the link should go.

Another example:

    <img src="logo.png" alt="Company logo">

Here:

    src

tells the browser where the image file is.

    alt

describes the image for accessibility and fallback text.

## Your First Webpage

A very small HTML document:

    <!DOCTYPE html>
    <html>
      <head>
        <title>My First Page</title>
      </head>
      <body>
        <h1>Hello World</h1>
        <p>This is my first webpage.</p>
      </body>
    </html>

## Why HTML Matters

HTML is the foundation of the web.

Browsers read HTML to understand the structure of a page.

Search engines use HTML to understand content.

Screen readers use HTML to help visually impaired users navigate webpages.

Poor HTML leads to poor accessibility, bad SEO, and confusing structure.

## Common Beginner Mistakes

### Mistake 1

Forgetting closing tags.

Wrong:

    <p>Hello

Better:

    <p>Hello</p>

### Mistake 2

Using headings only for size.

Headings should represent structure, not just visual size.

### Mistake 3

Forgetting alt text on images.

Wrong:

    <img src="cat.jpg">

Better:

    <img src="cat.jpg" alt="A sleeping cat">

### Mistake 4

Using HTML for styling.

Wrong:

    <center>Hello</center>

Better:

    Use CSS for styling.

## Exercises

### Exercise 1

Create a simple webpage with:

- One heading
- Two paragraphs
- One link
- One image

### Exercise 2

Write three HTML elements and identify their opening tag, content, and closing tag.

### Exercise 3

Explain the difference between HTML, CSS, and JavaScript.

### Exercise 4

Create an image element with src and alt attributes.

### Exercise 5

Create a link to GitHub.

## Did You Know?

HTML was created by Tim Berners-Lee, who also invented the World Wide Web.

## Fun Fact

HTML files usually end with the .html extension, but the browser reads the content, not just the file name.

## Summary

HTML structures webpage content.

Tags create elements.

Attributes add extra information.

HTML is the first major language every web developer should learn.

## References

- https://developer.mozilla.org/en-US/docs/Web/HTML
- https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML
- https://html.spec.whatwg.org
