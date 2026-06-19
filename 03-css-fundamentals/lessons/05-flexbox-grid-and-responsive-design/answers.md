# Lesson 05 Answers: Flexbox, Grid and Responsive Design

1. Layout is how elements are arranged on a page.
2. Flexbox is best for one-dimensional layouts.
3. Grid is best for two-dimensional layouts.
4. display: flex turns an element into a flex container.
5. justify-content controls alignment on the main axis.
6. align-items controls alignment on the cross axis.
7. gap adds space between items.
8. fr means fraction of available space.
9. Responsive design means layouts adapt to different screen sizes.
10. A media query applies CSS under certain conditions.

## Exercise Solution

HTML:

    <nav class="navbar">
      <a href="#">Home</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </nav>

    <section class="grid">
      <article class="card">Card 1</article>
      <article class="card">Card 2</article>
      <article class="card">Card 3</article>
    </section>

CSS:

    .navbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      gap: 20px;
    }

    .grid {
      display: grid;
      grid-template-columns: 1fr;
      gap: 20px;
    }

    .card {
      padding: 20px;
      border: 1px solid #ddd;
    }

    @media (min-width: 768px) {
      .grid {
        grid-template-columns: repeat(3, 1fr);
      }
    }
