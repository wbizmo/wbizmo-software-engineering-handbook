# Lesson 01: Introduction To CSS

## Learning Objectives

By the end of this lesson, you should be able to:

- Explain what CSS is.
- Understand why CSS exists.
- Connect CSS to HTML.
- Use inline, internal, and external CSS.
- Write basic CSS rules.
- Understand properties and values.

## What Is CSS?

CSS means Cascading Style Sheets.

HTML gives a webpage structure.

CSS controls how that structure looks.

CSS can control:

- Colors
- Fonts
- Spacing
- Sizes
- Layout
- Borders
- Backgrounds
- Responsiveness
- Animations

## HTML vs CSS

HTML:

    <h1>Hello World</h1>

CSS:

    h1 {
      color: blue;
      font-size: 40px;
    }

HTML says:

    This is a heading.

CSS says:

    Make the heading blue and large.

## CSS Rule Structure

A CSS rule has a selector and declarations.

Example:

    p {
      color: red;
      font-size: 18px;
    }

Selector:

    p

Declarations:

    color: red;
    font-size: 18px;

Property:

    color

Value:

    red

## Three Ways To Add CSS

### 1. Inline CSS

CSS directly inside an HTML element.

    <p style="color: red;">Hello</p>

Avoid using inline CSS for most real projects because it becomes hard to maintain.

### 2. Internal CSS

CSS inside a style tag in the HTML head.

    <style>
      p {
        color: red;
      }
    </style>

Useful for small demos.

### 3. External CSS

CSS in a separate file.

HTML:

    <link rel="stylesheet" href="styles.css">

CSS:

    p {
      color: red;
    }

External CSS is preferred for real projects.

## Creating A CSS File

Create:

    styles.css

Link it inside HTML head:

    <link rel="stylesheet" href="styles.css">

Example HTML:

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>CSS Practice</title>
        <link rel="stylesheet" href="styles.css">
      </head>
      <body>
        <h1>Hello CSS</h1>
        <p>I am learning how to style webpages.</p>
      </body>
    </html>

Example CSS:

    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
    }

    h1 {
      color: #222;
    }

    p {
      color: #555;
    }

## Common Beginner Mistakes

- Forgetting to link the CSS file.
- Misspelling the CSS file name.
- Placing link outside head.
- Forgetting semicolons.
- Using inline CSS everywhere.
- Expecting CSS to work when the selector does not match HTML.

## Exercises

1. Create an HTML file and a CSS file.
2. Link the CSS file to the HTML file.
3. Change the body background.
4. Change the h1 color.
5. Change paragraph font size.
6. Add a border to an image.
7. Use external CSS, not inline CSS.

## Summary

CSS controls how HTML looks.

A CSS rule uses selectors, properties, and values.

External CSS is the best approach for maintainable projects.

## References

- https://developer.mozilla.org/en-US/docs/Web/CSS
- https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps
