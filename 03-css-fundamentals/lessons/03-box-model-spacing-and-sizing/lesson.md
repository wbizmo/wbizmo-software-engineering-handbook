# Lesson 03: Box Model, Spacing and Sizing

## Learning Objectives

By the end of this lesson, you should be able to:

- Understand the CSS box model.
- Use margin, border, padding, and content.
- Control width and height.
- Understand box-sizing.
- Use spacing properly.
- Avoid common layout problems.

## What Is The Box Model?

Every HTML element is treated like a box.

The box model has four main parts:

    Content
    Padding
    Border
    Margin

Diagram:

    Margin
      Border
        Padding
          Content

## Content

Content is the actual text, image, or child elements inside the box.

Example:

    <p>Hello World</p>

The text is the content.

## Padding

Padding is space inside the element, between content and border.

    .box {
      padding: 20px;
    }

## Border

Border surrounds padding and content.

    .box {
      border: 1px solid #222;
    }

## Margin

Margin is space outside the element.

    .box {
      margin: 20px;
    }

## Width and Height

Width controls horizontal size.

Height controls vertical size.

    .box {
      width: 300px;
      height: 200px;
    }

## The Sizing Problem

By default, width may only apply to content.

If you write:

    width: 300px;
    padding: 20px;
    border: 2px solid black;

the final visual width may be larger than 300px.

## box-sizing

Use this:

    * {
      box-sizing: border-box;
    }

This makes width include content, padding, and border.

Many developers include this in every project.

## Margin Shorthand

    margin: 20px;

All sides.

    margin: 10px 20px;

Top and bottom: 10px.
Left and right: 20px.

    margin: 10px 20px 30px 40px;

Top, right, bottom, left.

## Padding Shorthand

Padding works the same way:

    padding: 20px;
    padding: 10px 20px;
    padding: 10px 20px 30px 40px;

## Centering A Block

    .box {
      width: 300px;
      margin: 0 auto;
    }

This centers a fixed-width block horizontally.

## Common Beginner Mistakes

- Confusing margin and padding.
- Forgetting box-sizing.
- Setting fixed heights unnecessarily.
- Using margin for internal spacing.
- Using padding for external spacing.
- Creating overflow by using large fixed widths.

## Exercises

1. Create a card with padding, border, and margin.
2. Create two boxes with different margins.
3. Add box-sizing border-box globally.
4. Center a 300px wide box.
5. Explain the difference between margin and padding.
6. Create a button with padding and border.

## Summary

The box model controls how elements occupy space.

Padding is inside.

Margin is outside.

Border surrounds the element.

box-sizing border-box makes sizing easier.

## References

- https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model
- https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing
