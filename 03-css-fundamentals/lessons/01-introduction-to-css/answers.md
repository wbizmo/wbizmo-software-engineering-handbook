# Lesson 01 Answers: Introduction To CSS

1. CSS means Cascading Style Sheets.
2. CSS styles HTML and controls webpage presentation.
3. HTML provides structure and meaning.
4. CSS provides styling and layout.
5. A selector chooses which HTML elements to style.
6. A property is the style feature being changed.
7. A value is the setting assigned to a property.
8. Inline, internal, and external CSS.
9. External CSS.
10. link.

## Exercise Solution

HTML:

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
        <p>I am learning CSS.</p>
        <img src="photo.jpg" alt="Practice image">
      </body>
    </html>

CSS:

    body {
      background: #f5f5f5;
      font-family: Arial, sans-serif;
    }

    h1 {
      color: #222;
    }

    p {
      font-size: 18px;
      color: #555;
    }

    img {
      border: 2px solid #222;
    }
