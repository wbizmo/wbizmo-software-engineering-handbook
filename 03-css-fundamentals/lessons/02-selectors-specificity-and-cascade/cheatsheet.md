# Lesson 02 Cheatsheet: Selectors, Specificity and Cascade

Element selector:

    p {
      color: red;
    }

Class selector:

    .card {
      padding: 20px;
    }

ID selector:

    #hero {
      padding: 40px;
    }

Group selector:

    h1,
    h2 {
      color: #222;
    }

Descendant selector:

    article p {
      color: #444;
    }

Hover:

    a:hover {
      text-decoration: underline;
    }

Specificity order:

    Inline
    ID
    Class
    Element

Cascade:
    Later equal rules can override earlier rules.

Inheritance:
    Some styles pass from parent to child.
