# Lesson 05: Request Bodies, Validation and Error Handling

## Learning Objectives

By the end of this lesson, you should be able to:

- Read request bodies.
- Create POST endpoints.
- Validate incoming data.
- Return proper errors.
- Handle invalid requests.

## What Is A Request Body?

Request bodies send data to the server.

Example:

    POST /books

Body:

    {
      "title": "Node.js Guide"
    }

## Fastify Body Access

    app.post(
      "/books",
      async (request) => {
        return request.body;
      }
    );

## Express Body Access

Enable JSON:

    app.use(express.json());

Access:

    req.body

## Creating Books

Example:

    POST /books

Request:

    {
      "title": "Node.js Guide",
      "author": "Ada"
    }

Response:

    {
      "success": true
    }

## Validation

Validation checks incoming data.

Examples:

- Required fields
- Length checks
- Format checks
- Numeric checks

## Simple Validation

    if (!title) {
      return {
        error:
          "Title required"
      };
    }

## Better Validation

Fastify supports schemas.

Example:

    schema: {
      body: {
        type: "object",
        required: [
          "title"
        ]
      }
    }

## Why Validation Matters

Without validation:

Bad data enters systems.

Examples:

- Empty names
- Missing emails
- Invalid numbers

## Error Responses

Bad:

    Error

Good:

    {
      "success": false,
      "message": "Title required"
    }

## Status Codes

Validation:

    400

Not found:

    404

Server error:

    500

Created:

    201

## BookStore API Upgrade

Create:

    POST /books

Validate:

- title
- author

## Mini Project

Add book creation endpoint.

Return:

    201

on success.

Return:

    400

on failure.

## Exercises

1. Create POST route.
2. Read body.
3. Validate title.
4. Validate author.
5. Return 400 on failure.
6. Return 201 on success.

## Summary

Request bodies create and update data.

Validation protects systems.

Good APIs return meaningful errors.

## References

https://fastify.dev/docs/latest/Reference/Validation-and-Serialization/

https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
