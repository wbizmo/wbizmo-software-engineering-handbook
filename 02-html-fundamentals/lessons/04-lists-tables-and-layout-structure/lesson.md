# Lesson 04: Lists, Tables and Layout Structure

## Learning Objectives

By the end of this lesson, you should be able to:

- Create ordered and unordered lists.
- Create nested lists.
- Create basic tables.
- Understand table rows, headings, and cells.
- Use div and span correctly.
- Understand basic page structure elements.

## Unordered Lists

Unordered lists are used when order does not matter.

    <ul>
      <li>HTML</li>
      <li>CSS</li>
      <li>JavaScript</li>
    </ul>

## Ordered Lists

Ordered lists are used when order matters.

    <ol>
      <li>Install VS Code</li>
      <li>Create a file</li>
      <li>Write HTML</li>
    </ol>

## List Items

Each list item uses li.

    <li>Item</li>

## Nested Lists

A list can contain another list.

    <ul>
      <li>Frontend
        <ul>
          <li>HTML</li>
          <li>CSS</li>
        </ul>
      </li>
      <li>Backend</li>
    </ul>

## Tables

Tables display tabular data.

Use tables for data, not for page layout.

Basic table:

    <table>
      <tr>
        <th>Name</th>
        <th>Role</th>
      </tr>
      <tr>
        <td>Williams</td>
        <td>Developer</td>
      </tr>
    </table>

## Table Elements

table:
    Creates the table.

tr:
    Table row.

th:
    Table heading cell.

td:
    Table data cell.

## Table Sections

Larger tables can use:

    <thead>
    <tbody>
    <tfoot>

Example:

    <table>
      <thead>
        <tr>
          <th>Product</th>
          <th>Price</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Book</td>
          <td>$10</td>
        </tr>
      </tbody>
    </table>

## div

div is a generic block container.

    <div>
      <h2>Card Title</h2>
      <p>Card content.</p>
    </div>

Use div when no more meaningful semantic element fits.

## span

span is a generic inline container.

    <p>This is <span>special</span> text.</p>

Use span for small inline portions of content.

## Basic Page Structure

Before semantic HTML, many pages used mostly divs.

Modern HTML provides better structure elements such as:

- header
- nav
- main
- section
- article
- aside
- footer

These are covered more in Lesson 05.

## Common Beginner Mistakes

- Using tables for layout.
- Forgetting li inside ul or ol.
- Using div for everything.
- Not using th for table headings.
- Creating deeply nested lists that are hard to read.

## Exercises

1. Create an unordered list of five programming languages.
2. Create an ordered list of steps for creating an HTML file.
3. Create a nested list of frontend and backend technologies.
4. Create a table with three rows and three columns.
5. Create a div-based card containing a heading, paragraph, and link.

## Summary

Lists organize related items.

Tables display structured data.

div and span are generic containers.

Good structure makes content easier to read, style, and maintain.

## References

- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ul
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/ol
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/div
