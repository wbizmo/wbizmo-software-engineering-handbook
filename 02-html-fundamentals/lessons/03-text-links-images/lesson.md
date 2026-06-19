# Lesson 03: Text, Links and Images

## Learning Objectives

By the end of this lesson, you should be able to:

- Use headings correctly.
- Write paragraphs.
- Use emphasis and strong importance.
- Create links.
- Add images.
- Understand absolute and relative URLs.
- Use alt text properly.

## Headings

HTML has six heading levels.

    <h1>Main Heading</h1>
    <h2>Section Heading</h2>
    <h3>Subsection Heading</h3>
    <h4>Small Heading</h4>
    <h5>Smaller Heading</h5>
    <h6>Smallest Heading</h6>

Use headings for structure, not just size.

A page should usually have one main h1.

## Paragraphs

Paragraphs are created with p.

    <p>This is a paragraph.</p>

Paragraphs are used for normal text content.

## Strong and Emphasis

Strong importance:

    <strong>Important text</strong>

Emphasis:

    <em>Emphasized text</em>

strong usually appears bold.

em usually appears italic.

But their real purpose is meaning, not styling.

## Line Breaks

A line break uses br.

    First line<br>
    Second line

Do not overuse br for spacing.

Use CSS for spacing later.

## Horizontal Rule

A thematic break uses hr.

    <hr>

It separates sections of content.

## Links

Links are created with a.

    <a href="https://example.com">Visit Example</a>

The href attribute tells the browser where to go.

## Absolute URLs

An absolute URL includes the full address.

    https://github.com

Use absolute URLs for external websites.

## Relative URLs

A relative URL points to a file or page relative to the current file.

    about.html

or

    pages/contact.html

Use relative URLs for pages inside your own project.

## Opening Links In A New Tab

    <a href="https://example.com" target="_blank" rel="noopener noreferrer">Visit</a>

target="_blank" opens a new tab.

rel="noopener noreferrer" improves security and privacy.

## Images

Images use img.

    <img src="photo.jpg" alt="A person using a laptop">

img does not need a closing tag.

## src Attribute

src tells the browser where the image is.

Example:

    <img src="images/logo.png" alt="Company logo">

## alt Attribute

alt describes the image.

It helps:

- Screen readers
- Accessibility
- Search engines
- Users when images fail to load

Bad:

    <img src="dog.jpg" alt="image">

Better:

    <img src="dog.jpg" alt="A brown dog sitting on grass">

## Common Beginner Mistakes

- Using h1 multiple times without structure.
- Using headings only to make text big.
- Forgetting href on links.
- Forgetting alt on images.
- Using broken image paths.
- Using target="_blank" without rel.

## Exercises

1. Create a page with h1, h2, and h3.
2. Add three paragraphs.
3. Add a link to GitHub.
4. Add a link to an about page using a relative path.
5. Add an image with alt text.
6. Create a short article using headings and paragraphs.
7. Add strong and emphasized text.

## Summary

Text elements give content structure.

Links connect pages and websites.

Images add visual content.

Good alt text improves accessibility and user experience.

## References

- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/Heading_Elements
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a
- https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img
