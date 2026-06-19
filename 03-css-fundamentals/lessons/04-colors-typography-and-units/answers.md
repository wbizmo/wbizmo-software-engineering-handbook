# Lesson 04 Answers: Colors, Typography and Units

1. Named colors, hex, rgb, rgba.
2. font-family controls the typeface.
3. font-size controls text size.
4. font-weight controls text thickness.
5. line-height controls space between lines.
6. px is a fixed pixel unit.
7. rem relates to the root font size.
8. % relates to the parent size.
9. vw means viewport width.
10. line-height improves readability.

## Exercise Solution

CSS:

    body {
      font-family: Arial, sans-serif;
      background: #f5f5f5;
      color: #222;
    }

    h1 {
      font-size: 3rem;
      font-weight: 700;
      line-height: 1.1;
    }

    p {
      font-size: 1rem;
      line-height: 1.6;
      color: #444;
    }

    .hero {
      min-height: 100vh;
    }

    .button {
      background: #111;
      color: #fff;
      padding: 12px 18px;
    }
