# Lesson 03 Answers: Box Model, Spacing and Sizing

1. Content, padding, border, margin.
2. Content is the actual text, image, or child elements.
3. Padding is space inside the element.
4. Border surrounds the padding and content.
5. Margin is space outside the element.
6. Width controls horizontal size.
7. Height controls vertical size.
8. It makes width include content, padding, and border.
9. margin: 20px;
10. Set a width and use margin: 0 auto;

## Exercise Solution

CSS:

    * {
      box-sizing: border-box;
    }

    .card {
      width: 300px;
      padding: 20px;
      border: 1px solid #ddd;
      margin: 20px auto;
    }

    .button {
      padding: 12px 18px;
      border: 1px solid #222;
    }

HTML:

    <div class="card">
      <h2>Card Title</h2>
      <p>This card uses padding, border, and margin.</p>
      <button class="button">Read More</button>
    </div>
