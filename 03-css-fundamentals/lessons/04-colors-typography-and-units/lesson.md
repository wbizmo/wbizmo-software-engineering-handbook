# Lesson 04: Colors, Typography and Units

## Learning Objectives

By the end of this lesson, you should be able to:

- Use CSS colors.
- Understand hex, rgb, and named colors.
- Style text.
- Control font family, size, weight, and line height.
- Understand px, rem, em, %, vw, and vh.
- Create readable typography.

## Colors

CSS supports many color formats.

Named color:

    color: red;

Hex:

    color: #ff0000;

RGB:

    color: rgb(255, 0, 0);

RGBA:

    color: rgba(255, 0, 0, 0.5);

## Background Colors

    body {
      background: #f5f5f5;
    }

## Text Color

    p {
      color: #333;
    }

## Typography

Typography controls how text looks and reads.

Important properties:

- font-family
- font-size
- font-weight
- line-height
- letter-spacing
- text-align
- text-decoration

## Font Family

    body {
      font-family: Arial, sans-serif;
    }

Always provide a fallback font.

## Font Size

    p {
      font-size: 16px;
    }

## Font Weight

    h1 {
      font-weight: 700;
    }

Common values:

    400 normal
    500 medium
    600 semibold
    700 bold

## Line Height

Line height controls vertical spacing between lines of text.

    p {
      line-height: 1.6;
    }

Readable text often uses line-height between 1.4 and 1.8.

## Text Align

    h1 {
      text-align: center;
    }

## Text Decoration

    a {
      text-decoration: none;
    }

## CSS Units

### px

Pixels are fixed units.

    font-size: 16px;

### %

Percentage is relative to parent size.

    width: 50%;

### rem

rem is relative to the root font size.

    font-size: 1rem;

Commonly:

    1rem = 16px

unless changed.

### em

em is relative to the current element's font size.

### vw

vw means viewport width.

    width: 100vw;

### vh

vh means viewport height.

    min-height: 100vh;

## Common Beginner Mistakes

- Using too many fonts.
- Using low contrast text.
- Using tiny font sizes.
- Using fixed widths everywhere.
- Not setting line-height.
- Center-aligning long paragraphs.
- Using colors without consistency.

## Exercises

1. Style body with a font family.
2. Set paragraph color and line-height.
3. Create a heading with large font size.
4. Create a button with background and text color.
5. Use rem for font size.
6. Use min-height: 100vh on a hero section.
7. Improve a paragraph's readability.

## Summary

Colors create visual identity.

Typography controls readability.

Units control size and spacing.

Good CSS makes content easy to read and pleasant to use.

## References

- https://developer.mozilla.org/en-US/docs/Web/CSS/color
- https://developer.mozilla.org/en-US/docs/Learn/CSS/Styling_text
- https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units
