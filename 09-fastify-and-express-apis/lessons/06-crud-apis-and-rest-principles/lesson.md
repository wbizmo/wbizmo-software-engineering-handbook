# Lesson 06: CRUD APIs and REST Principles

## Learning Objectives

By the end of this lesson, you should be able to:

- Explain CRUD.
- Understand REST resource naming.
- Build list, detail, create, update, and delete endpoints.
- Use correct HTTP methods.
- Use correct status codes.

## What Is CRUD?

CRUD means:

    Create
    Read
    Update
    Delete

Most APIs are built around CRUD operations.

## BookStore CRUD

Resource:

    books

Endpoints:

    GET /books
    GET /books/:id
    POST /books
    PUT /books/:id
    DELETE /books/:id

## REST Principles

REST APIs usually model data as resources.

Good:

    /books

    /books/1

Bad:

    /getBooks

    /deleteBook

Use nouns, not verbs.

## HTTP Method Mapping

GET:

    Read

POST:

    Create

PUT:

    Replace/update

PATCH:

    Partial update

DELETE:

    Delete

## In-Memory BookStore API

    const books = [];

    app.get("/books", async () => {
      return books;
    });

    app.get("/books/:id", async (request, reply) => {
      const { id } = request.params;

      const book = books.find((item) => item.id === id);

      if (!book) {
        return reply.status(404).send({
          success: false,
          message: "Book not found"
        });
      }

      return book;
    });

    app.post("/books", async (request, reply) => {
      const { title, author } = request.body;

      const book = {
        id: Date.now().toString(),
        title,
        author
      };

      books.push(book);

      return reply.status(201).send(book);
    });

## Update Endpoint

    app.put("/books/:id", async (request, reply) => {
      const { id } = request.params;
      const { title, author } = request.body;

      const book = books.find((item) => item.id === id);

      if (!book) {
        return reply.status(404).send({
          success: false,
          message: "Book not found"
        });
      }

      book.title = title;
      book.author = author;

      return book;
    });

## Delete Endpoint

    app.delete("/books/:id", async (request, reply) => {
      const { id } = request.params;

      const index = books.findIndex((item) => item.id === id);

      if (index === -1) {
        return reply.status(404).send({
          success: false,
          message: "Book not found"
        });
      }

      books.splice(index, 1);

      return reply.status(204).send();
    });

## Common Mistakes

- Using verbs in route names.
- Returning 200 for every situation.
- Not handling missing resources.
- Not validating request bodies.
- Confusing PUT and PATCH.
- Deleting without checking if resource exists.

## Exercises

1. Create GET /books.
2. Create GET /books/:id.
3. Create POST /books.
4. Create PUT /books/:id.
5. Create DELETE /books/:id.
6. Return 404 when book is missing.
7. Return 201 when book is created.
8. Return 204 when book is deleted.

## Summary

CRUD is the foundation of many APIs.

REST routes should describe resources.

HTTP methods should match the operation.

Status codes should describe the result.

## References

https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods

https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
