# Lesson 05: Forms, Semantic HTML and Accessibility

## Learning Objectives

By the end of this lesson, you should be able to:

- Create basic HTML forms.
- Use labels and inputs correctly.
- Understand common input types.
- Create buttons.
- Understand semantic HTML.
- Understand basic accessibility.
- Understand basic SEO benefits of good HTML.

## What Is A Form?

A form allows users to submit data.

Examples:

- Login form
- Registration form
- Contact form
- Search form
- Newsletter form
- Checkout form

Basic form:

    <form>
      <label for="email">Email</label>
      <input id="email" type="email" name="email">
      <button type="submit">Submit</button>
    </form>

## form Element

The form element wraps form controls.

    <form>
    </form>

Important attributes:

action:
    Where the form sends data.

method:
    How the form sends data.

Example:

    <form action="/login" method="POST">
    </form>

## label Element

Labels describe form inputs.

    <label for="username">Username</label>
    <input id="username" name="username" type="text">

The for attribute should match the input id.

This improves accessibility.

## input Element

input creates form controls.

Common input types:

    text
    email
    password
    number
    date
    checkbox
    radio
    file

Examples:

    <input type="text">
    <input type="email">
    <input type="password">

## textarea

textarea is used for longer text.

    <textarea name="message"></textarea>

## select

select creates dropdown options.

    <select name="country">
      <option value="ng">Nigeria</option>
      <option value="gh">Ghana</option>
    </select>

## button

Buttons trigger actions.

    <button type="submit">Submit</button>

Common button types:

submit:
    Submits form.

button:
    Regular button.

reset:
    Resets form fields.

## Semantic HTML

Semantic HTML means using elements that describe meaning.

Examples:

header:
    Top section of a page or section.

nav:
    Navigation links.

main:
    Main content.

section:
    Thematic section.

article:
    Independent content.

aside:
    Side content.

footer:
    Bottom section.

Example:

    <header>
      <nav>
        <a href="index.html">Home</a>
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

## Why Semantic HTML Matters

Semantic HTML helps:

- Browsers understand structure
- Search engines understand content
- Screen readers support users
- Developers maintain code

## Accessibility

Accessibility means making websites usable by as many people as possible, including people with disabilities.

Basic accessibility practices:

- Use labels for form inputs.
- Use alt text for images.
- Use headings in logical order.
- Use buttons for actions.
- Use links for navigation.
- Do not rely only on color.
- Write meaningful link text.

Bad link text:

    <a href="about.html">Click here</a>

Better:

    <a href="about.html">Read more about our company</a>

## Basic SEO

SEO means Search Engine Optimization.

Good HTML helps search engines understand pages.

Helpful practices:

- Use one clear h1.
- Use descriptive title text.
- Use semantic sections.
- Use alt text.
- Use meaningful links.
- Structure content logically.

## Contact Form Example

    <form action="/contact" method="POST">
      <label for="name">Name</label>
      <input id="name" name="name" type="text">

      <label for="email">Email</label>
      <input id="email" name="email" type="email">

      <label for="message">Message</label>
      <textarea id="message" name="message"></textarea>

      <button type="submit">Send Message</button>
    </form>

## Common Beginner Mistakes

- Inputs without labels.
- Labels not connected to inputs.
- Using div for everything.
- Using buttons as links.
- Using links as buttons.
- Skipping alt text.
- Bad heading order.
- Writing vague link text.

## Exercises

1. Create a login form with email and password.
2. Create a contact form with name, email, and message.
3. Use labels correctly.
4. Create a semantic page layout with header, nav, main, section, and footer.
5. Improve this bad link text: Click here.
6. Add alt text to three image examples.
7. Explain why semantic HTML helps accessibility.

## Summary

Forms collect user input.

Labels make forms easier to use.

Semantic HTML gives meaning to page structure.

Accessibility helps more people use your websites.

Good HTML improves usability, SEO, and maintainability.

## References

- https://developer.mozilla.org/en-US/docs/Learn/Forms
- https://developer.mozilla.org/en-US/docs/Glossary/Semantics
- https://developer.mozilla.org/en-US/docs/Learn/Accessibility/HTML
- https://web.dev/learn/accessibility
