# Lesson 02: HTML Document Structure

## Learning Objectives

By the end of this lesson, you should be able to:

- Create a valid HTML document.
- Understand doctype, html, head, title, meta, and body.
- Explain what belongs in the head.
- Explain what belongs in the body.
- Understand indentation and nesting.
- Build a complete starter HTML page.

## The Basic HTML Document

A standard HTML page usually begins like this:

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>My Page</title>
      </head>
      <body>
        <h1>Hello World</h1>
      </body>
    </html>

## DOCTYPE

The doctype tells the browser which version of HTML is being used.

Modern HTML uses:

    <!DOCTYPE html>

This tells the browser to use modern standards mode.

## html Element

The html element wraps the entire page.

Example:

    <html lang="en">
    </html>

The lang attribute tells browsers and assistive technologies the language of the page.

## head Element

The head contains information about the document.

It is not the visible page content.

Common items inside head:

- title
- meta tags
- links to CSS files
- SEO metadata
- favicon links

## title Element

The title appears in the browser tab.

Example:

    <title>My Portfolio</title>

It also helps search engines understand the page.

## meta charset

This tells the browser how to interpret characters.

Use:

    <meta charset="UTF-8">

UTF-8 supports many characters and symbols.

## viewport Meta Tag

This helps pages display properly on mobile devices.

Use:

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

Without this, mobile layouts may behave poorly.

## body Element

The body contains visible page content.

Examples:

- Headings
- Paragraphs
- Images
- Links
- Forms
- Buttons
- Sections

## Nesting

Nesting means placing elements inside other elements.

Example:

    <body>
      <main>
        <h1>Welcome</h1>
      </main>
    </body>

Correct nesting matters.

Wrong:

    <p>Hello <strong>World</p></strong>

Better:

    <p>Hello <strong>World</strong></p>

## Indentation

Indentation makes HTML easier to read.

Bad:

    <html><head><title>Page</title></head><body><h1>Hello</h1></body></html>

Better:

    <html>
      <head>
        <title>Page</title>
      </head>
      <body>
        <h1>Hello</h1>
      </body>
    </html>

## Starter Template

Use this as a starter for basic pages:

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
      </head>
      <body>

      </body>
    </html>

## Common Beginner Mistakes

- Forgetting the doctype.
- Putting visible content inside head.
- Forgetting the viewport meta tag.
- Bad nesting.
- Not using lang on html.
- Using unclear page titles.

## Exercises

1. Create a valid HTML document.
2. Add a title that says My Practice Page.
3. Add h1 inside the body.
4. Add two paragraphs inside the body.
5. Add lang="en" to the html element.
6. Add charset and viewport meta tags.

## Summary

Every HTML page needs structure.

The head contains document information.

The body contains visible content.

Good structure improves accessibility, SEO, maintainability, and browser behavior.

## References

- https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/head
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
