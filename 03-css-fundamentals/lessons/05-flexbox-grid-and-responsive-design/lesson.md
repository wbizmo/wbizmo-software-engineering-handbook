# Lesson 05: Flexbox, Grid and Responsive Design

## Learning Objectives

By the end of this lesson, you should be able to:

- Understand why layout matters.
- Use Flexbox for one-dimensional layouts.
- Use Grid for two-dimensional layouts.
- Understand responsive design.
- Use media queries.
- Build layouts that work on different screen sizes.

## What Is Layout?

Layout is how elements are arranged on a page.

Examples:

- Navbar
- Card grid
- Sidebar layout
- Hero section
- Dashboard
- Footer

## Flexbox

Flexbox is useful for arranging items in one direction.

Either row or column.

Basic example:

    .container {
      display: flex;
    }

## Flex Direction

    .container {
      display: flex;
      flex-direction: row;
    }

or:

    .container {
      display: flex;
      flex-direction: column;
    }

## Justify Content

Controls alignment on the main axis.

    .container {
      justify-content: center;
    }

Common values:

- flex-start
- center
- flex-end
- space-between
- space-around
- space-evenly

## Align Items

Controls alignment on the cross axis.

    .container {
      align-items: center;
    }

## Gap

Adds space between flex or grid items.

    .container {
      gap: 20px;
    }

## Grid

Grid is useful for two-dimensional layouts.

Rows and columns.

Basic example:

    .grid {
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      gap: 20px;
    }

## fr Unit

fr means fraction of available space.

Example:

    grid-template-columns: 1fr 1fr 1fr;

creates three equal columns.

## Responsive Design

Responsive design means a website adapts to different screen sizes.

Examples:

- Phone
- Tablet
- Laptop
- Desktop

A responsive layout should be usable on all major screen sizes.

## Media Queries

Media queries apply CSS only under certain conditions.

Example:

    @media (max-width: 768px) {
      .grid {
        grid-template-columns: 1fr;
      }
    }

This makes the grid one column on smaller screens.

## Mobile First

Mobile-first design means writing styles for small screens first, then adding larger screen styles.

Example:

    .grid {
      display: grid;
      grid-template-columns: 1fr;
    }

    @media (min-width: 768px) {
      .grid {
        grid-template-columns: repeat(3, 1fr);
      }
    }

## Common Beginner Mistakes

- Using fixed widths everywhere.
- Not testing on mobile.
- Using Flexbox when Grid is better.
- Using Grid when Flexbox is simpler.
- Forgetting gap.
- Creating horizontal scroll.
- Not using media queries.

## Exercises

1. Create a navbar using Flexbox.
2. Create a card row using Flexbox.
3. Create a three-column card layout using Grid.
4. Make the grid one column on mobile.
5. Add gap between items.
6. Create a responsive hero section.
7. Explain when to use Flexbox vs Grid.

## Summary

Flexbox is great for one-dimensional layouts.

Grid is great for two-dimensional layouts.

Responsive design makes websites work across devices.

Media queries help layouts adapt.

## References

- https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox
- https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Grids
- https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design
