# Lesson 08: API Project Structure and Production Practices

## Learning Objectives

By the end of this lesson, you should be able to:

- Organize an API project.
- Separate routes, services, config, and utilities.
- Understand production concerns.
- Create health checks.
- Understand logging and documentation.
- Prepare APIs for deployment.

## Why Structure Matters

Small demos can live in one file.

Real APIs need structure.

Bad:

    server.js

with everything inside.

Better:

    src/
      app.js
      server.js
      routes/
      services/
      config/
      utils/

## Example Structure

    bookstore-api/
    ├── src/
    │   ├── app.js
    │   ├── server.js
    │   ├── routes/
    │   │   └── books.routes.js
    │   ├── services/
    │   │   └── books.service.js
    │   ├── config/
    │   │   └── env.js
    │   └── utils/
    │       └── errors.js
    ├── package.json
    ├── .env
    ├── .gitignore
    └── README.md

## Routes

Routes define HTTP endpoints.

Example:

    GET /books

Routes should not contain too much business logic.

## Services

Services contain business logic.

Example:

    createBook()
    findBookById()
    deleteBook()

## Config

Config reads environment variables.

Example:

    export const config = {
      port: process.env.PORT || 3000
    };

## Health Check

A health route tells whether the service is alive.

    app.get("/health", async () => {
      return {
        status: "ok"
      };
    });

## Production Practices

Production APIs should include:

- Environment variables
- Logging
- Error handling
- Validation
- Authentication
- Rate limiting
- CORS configuration
- Health checks
- API documentation
- Tests

## README Documentation

A good API README includes:

- Project description
- Features
- Tech stack
- Setup steps
- Environment variables
- API endpoints
- Example requests
- Testing instructions

## Final BookStore API Challenge

Build a structured BookStore API with:

    GET /health
    GET /books
    GET /books/:id
    POST /books
    PUT /books/:id
    DELETE /books/:id

Include:

- Validation
- API key protection for write routes
- Structured errors
- README notes

## Summary

Professional APIs are organized, documented, validated, secured, and observable.

Project structure matters when APIs grow.

## References

https://fastify.dev/docs/latest/

https://expressjs.com/

https://12factor.net/
