# HTML Fundamentals Module Answers

1. HTML means HyperText Markup Language.
2. HTML structures webpage content.
3. HTML structures, CSS styles, JavaScript adds behavior.
4. An element is usually an opening tag, content, and closing tag.
5. An attribute adds extra information to an element.
6. doctype tells the browser to use modern standards mode.
7. head contains metadata, title, CSS links, and document information.
8. body contains visible page content.
9. The viewport meta tag helps pages display properly on mobile devices.
10. h1, h2, h3, h4, h5, h6.
11. href tells a link where to go.
12. alt describes an image.
13. Absolute URLs include the full address. Relative URLs point from the current file location.
14. An unordered list is a list where order does not matter.
15. An ordered list is a list where order matters.
16. th is a table heading cell. td is a table data cell.
17. A form collects and submits user data.
18. Labels describe inputs and improve accessibility.
19. Semantic HTML uses elements that describe meaning.
20. Accessibility matters because websites should be usable by as many people as possible.

## Module Practice Solution

A simple semantic page:

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>HTML Practice</title>
      </head>
      <body>
        <header>
          <nav>
            <a href="index.html">Home</a>
            <a href="about.html">About</a>
          </nav>
        </header>

        <main>
          <section>
            <h1>Learning HTML</h1>
            <p>HTML gives structure to webpages.</p>
            <img src="html.jpg" alt="HTML code on a computer screen">
          </section>

          <section>
            <h2>Contact</h2>
            <form action="/contact" method="POST">
              <label for="name">Name</label>
              <input id="name" name="name" type="text">

              <label for="email">Email</label>
              <input id="email" name="email" type="email">

              <button type="submit">Send</button>
            </form>
          </section>
        </main>

        <footer>
          <p>Copyright 2026</p>
        </footer>
      </body>
    </html>
