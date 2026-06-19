# Lesson 03 Answers: Text, Links and Images

1. HTML has six heading levels.
2. p creates a paragraph.
3. strong represents strong importance.
4. em represents emphasis.
5. a creates a link.
6. href tells the browser where the link goes.
7. An absolute URL includes the full address.
8. A relative URL points to a file relative to the current file.
9. img displays an image.
10. alt text improves accessibility and describes images.

## Exercise Solution

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Text Links Images</title>
      </head>
      <body>
        <h1>My Article</h1>
        <h2>Introduction</h2>
        <p>This is my first paragraph.</p>
        <p>This paragraph contains <strong>important text</strong>.</p>
        <p>This paragraph contains <em>emphasized text</em>.</p>

        <h3>Useful Links</h3>
        <a href="https://github.com" target="_blank" rel="noopener noreferrer">GitHub</a>
        <a href="about.html">About Page</a>

        <img src="images/laptop.jpg" alt="A laptop on a desk">
      </body>
    </html>
