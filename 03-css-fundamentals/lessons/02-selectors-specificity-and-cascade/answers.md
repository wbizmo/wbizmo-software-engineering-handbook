# Lesson 02 Answers: Selectors, Specificity and Cascade

1. A selector chooses which HTML elements to style.
2. p.
3. Use a dot, for example .card.
4. Use a hash, for example #hero.
5. No. IDs should be unique.
6. The cascade is how CSS decides which rules apply.
7. The later rule usually wins.
8. Class selector.
9. Inheritance means some styles pass from parent elements to child elements.
10. !important makes CSS harder to maintain and debug.

## Exercise Solution

HTML:

    <section id="hero">
      <h1>Welcome</h1>
      <p class="text">Hello world.</p>
      <a href="about.html">About</a>
    </section>

    <div class="card">
      <p>Card content</p>
    </div>

CSS:

    p {
      color: red;
    }

    p {
      color: blue;
    }

    .text {
      color: green;
    }

    .card {
      padding: 20px;
      border: 1px solid #ddd;
    }

    #hero {
      padding: 40px;
    }

    a:hover {
      text-decoration: underline;
    }
