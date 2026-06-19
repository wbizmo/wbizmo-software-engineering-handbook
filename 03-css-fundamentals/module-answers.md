# CSS Fundamentals Module Answers

1. CSS means Cascading Style Sheets.
2. CSS styles and lays out HTML.
3. A selector chooses which elements to style.
4. A property is the style feature being changed.
5. A value is the setting assigned to a property.
6. Inline, internal, and external CSS.
7. The cascade is how CSS decides which rules apply.
8. Specificity determines which selector is stronger.
9. Inheritance means some styles pass from parent to child.
10. Content, padding, border, margin.
11. Padding is space inside the element.
12. Margin is space outside the element.
13. It makes width include content, padding, and border.
14. Named colors, hex, rgb, rgba.
15. line-height controls vertical spacing between lines of text.
16. px, %, rem, em, vw, vh.
17. Flexbox is best for one-dimensional layouts.
18. Grid is best for two-dimensional layouts.
19. Responsive design means layouts adapt to different screen sizes.
20. A media query applies CSS under certain conditions.

## Module Practice Solution

HTML:

    <section class="hero">
      <h1>CSS Fundamentals</h1>
      <p>Learning layout, spacing, color, and responsiveness.</p>
      <a class="button" href="#">Start Learning</a>
    </section>

    <section class="cards">
      <article class="card">
        <h2>HTML</h2>
        <p>Structure.</p>
      </article>
      <article class="card">
        <h2>CSS</h2>
        <p>Style.</p>
      </article>
      <article class="card">
        <h2>JavaScript</h2>
        <p>Behavior.</p>
      </article>
    </section>

CSS:

    * {
      box-sizing: border-box;
    }

    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      color: #222;
    }

    .hero {
      min-height: 60vh;
      padding: 40px 20px;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      text-align: center;
    }

    .hero h1 {
      font-size: 3rem;
      line-height: 1.1;
    }

    .hero p {
      max-width: 600px;
      line-height: 1.6;
      color: #555;
    }

    .button {
      padding: 12px 18px;
      background: #111;
      color: #fff;
      text-decoration: none;
    }

    .cards {
      display: grid;
      grid-template-columns: 1fr;
      gap: 20px;
      padding: 20px;
    }

    .card {
      background: #fff;
      padding: 20px;
      border: 1px solid #ddd;
    }

    @media (min-width: 768px) {
      .cards {
        grid-template-columns: repeat(3, 1fr);
      }
    }
