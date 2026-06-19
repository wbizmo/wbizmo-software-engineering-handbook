# Lesson 04: Routing, Parameters and Query Strings

## Learning Objectives

By the end of this lesson, you should be able to:

- Create dynamic routes.
- Use route parameters.
- Use query strings.
- Read request values.
- Build searchable endpoints.

## Dynamic Routes

Static route:

    GET /books

Dynamic route:

    GET /books/:id

The id changes.

Examples:

    /books/1

    /books/2

    /books/99

## Fastify Route Parameters

Example:

    app.get(
      "/books/:id",
      async (request) => {
        const { id } =
          request.params;

        return {
          id
        };
      }
    );

## Express Route Parameters

Example:

    app.get(
      "/books/:id",
      (req, res) => {
        res.json({
          id: req.params.id
        });
      }
    );

## Query Strings

Example:

    GET /books?page=1

Contains:

    page=1

Another example:

    GET /books?author=Ada

Contains:

    author=Ada

## Fastify Query Access

    app.get(
      "/books",
      async (request) => {
        const { page } =
          request.query;

        return {
          page
        };
      }
    );

## Express Query Access

    app.get(
      "/books",
      (req, res) => {
        res.json({
          page:
            req.query.page
        });
      }
    );

## Real API Examples

Pagination:

    GET /books?page=2

Search:

    GET /books?q=node

Filtering:

    GET /books?category=backend

Sorting:

    GET /books?sort=title

## BookStore API Upgrade

Create:

    GET /books/:id

Example:

    GET /books/1

Response:

    {
      "id": 1,
      "title": "Node.js Guide"
    }

## Search Endpoint

Example:

    GET /books?q=node

Response:

    Matching books only.

## Mini Project

Add:

    GET /books/:id

Add:

    GET /books?q=value

## Exercises

1. Create a route parameter.
2. Read id.
3. Return id.
4. Read query string.
5. Implement search endpoint.
6. Implement pagination parameter.

## Summary

Parameters identify specific resources.

Query strings filter, search, paginate and sort data.

## References

https://fastify.dev/docs/latest/Reference/Routes/

https://expressjs.com/en/guide/routing.html
