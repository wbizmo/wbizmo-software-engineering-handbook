# Lesson 02: Selectors, Specificity and Cascade

## Learning Objectives

By the end of this lesson, you should be able to:

- Use common CSS selectors.
- Understand classes and IDs.
- Understand the cascade.
- Understand specificity.
- Understand inheritance.
- Debug why a style is or is not applying.

## What Is A Selector?

A selector chooses which HTML elements CSS should style.

Example:

    p {
      color: blue;
    }

This selects all p elements.

## Element Selector

Styles all elements of a type.

    h1 {
      color: black;
    }

## Class Selector

A class can be reused across many elements.

HTML:

    <p class="highlight">Important text</p>

CSS:

    .highlight {
      background: yellow;
    }

## ID Selector

An ID should be unique on a page.

HTML:

    <section id="hero"></section>

CSS:

    #hero {
      padding: 40px;
    }

Use IDs carefully. Classes are usually better for reusable styling.

## Grouping Selectors

    h1,
    h2,
    h3 {
      font-family: Arial, sans-serif;
    }

## Descendant Selector

Selects elements inside another element.

    article p {
      color: #444;
    }

This selects p elements inside article.

## Pseudo-classes

Pseudo-classes style elements in a special state.

Example:

    a:hover {
      text-decoration: underline;
    }

Common pseudo-classes:

- :hover
- :focus
- :active
- :visited
- :first-child

## The Cascade

Cascade means CSS rules can override other CSS rules depending on order, specificity, and importance.

If two rules target the same element with equal specificity, the later rule wins.

Example:

    p {
      color: red;
    }

    p {
      color: blue;
    }

The paragraph becomes blue.

## Specificity

Specificity decides which selector is stronger.

Simple order:

    Inline styles
    ID selectors
    Class selectors
    Element selectors

Example:

    p {
      color: red;
    }

    .text {
      color: blue;
    }

If the paragraph has class text, blue wins.

## Inheritance

Some CSS properties are inherited by child elements.

Example:

    body {
      font-family: Arial, sans-serif;
      color: #222;
    }

Text inside body may inherit the font and color.

Not all properties inherit.

For example:

- color usually inherits.
- font-family usually inherits.
- margin does not usually inherit.
- border does not usually inherit.

## Common Beginner Mistakes

- Using IDs for everything.
- Not understanding why a style is overridden.
- Forgetting the dot before class selectors.
- Forgetting the hash before ID selectors.
- Writing selectors that do not match the HTML.
- Overusing !important.

## Exercises

1. Style all p elements.
2. Create a reusable class called card.
3. Create an ID called hero.
4. Add hover style to links.
5. Demonstrate cascade by writing two rules for the same element.
6. Demonstrate specificity using an element selector and class selector.

## Summary

Selectors choose elements.

The cascade decides which styles win.

Specificity controls rule strength.

Inheritance passes some styles from parent to child.

## References

- https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_selectors
- https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity
- https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance
