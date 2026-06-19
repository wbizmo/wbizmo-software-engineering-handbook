# CSS Fundamentals Module Cheatsheet

CSS:
    Cascading Style Sheets.

Rule:

    selector {
      property: value;
    }

External CSS:

    <link rel="stylesheet" href="styles.css">

Selectors:

    p
    .class
    #id
    parent child
    a:hover

Specificity:

    Inline
    ID
    Class
    Element

Box Model:

    Content
    Padding
    Border
    Margin

Global box sizing:

    * {
      box-sizing: border-box;
    }

Colors:

    red
    #ff0000
    rgb(255, 0, 0)
    rgba(255, 0, 0, 0.5)

Typography:

    font-family
    font-size
    font-weight
    line-height
    text-align

Units:

    px
    %
    rem
    em
    vw
    vh

Flexbox:

    display: flex;
    justify-content: center;
    align-items: center;
    gap: 20px;

Grid:

    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 20px;

Responsive:

    @media (min-width: 768px) {
      .grid {
        grid-template-columns: repeat(3, 1fr);
      }
    }

Key takeaway:
    CSS turns structured HTML into usable, readable, responsive interfaces.
