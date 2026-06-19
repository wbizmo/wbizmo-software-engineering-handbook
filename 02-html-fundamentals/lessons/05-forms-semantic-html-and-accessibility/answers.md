# Lesson 05 Answers: Forms, Semantic HTML and Accessibility

1. A form collects and submits user data.
2. A label describes a form input.
3. Matching for and id connects the label to the input for accessibility and usability.
4. text, email, password, number, date, checkbox, radio, file.
5. textarea is used for longer text input.
6. It submits the form.
7. Semantic HTML uses elements that describe meaning.
8. header, nav, main, section, article, aside, footer.
9. Accessibility means making websites usable by as many people as possible.
10. Alt text describes images for screen readers and when images fail to load.

## Exercise Solution

Login form:

    <form action="/login" method="POST">
      <label for="email">Email</label>
      <input id="email" name="email" type="email">

      <label for="password">Password</label>
      <input id="password" name="password" type="password">

      <button type="submit">Log In</button>
    </form>

Contact form:

    <form action="/contact" method="POST">
      <label for="name">Name</label>
      <input id="name" name="name" type="text">

      <label for="email">Email</label>
      <input id="email" name="email" type="email">

      <label for="message">Message</label>
      <textarea id="message" name="message"></textarea>

      <button type="submit">Send Message</button>
    </form>

Semantic layout:

    <header>
      <nav>
        <a href="index.html">Home</a>
        <a href="about.html">About</a>
      </nav>
    </header>

    <main>
      <section>
        <h1>Welcome</h1>
        <p>This is the main content.</p>
      </section>
    </main>

    <footer>
      <p>Copyright 2026</p>
    </footer>
