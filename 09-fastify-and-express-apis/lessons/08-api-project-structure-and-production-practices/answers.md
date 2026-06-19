# Lesson 08 Answers

1. Maintainability and scalability.
2. HTTP endpoint definitions.
3. Business logic.
4. Environment and app configuration.
5. Endpoint that reports service status.
6. Config and secrets outside source code.
7. So users and developers know how to use the API.
8. Logging, validation, authentication, rate limiting, CORS, health checks, docs.
9. To prevent unauthorized changes.
10. Description, setup, env vars, endpoints, examples, tests.

## Final Project Structure

    bookstore-api/
    ├── src/
    │   ├── app.js
    │   ├── server.js
    │   ├── routes/
    │   │   └── books.routes.js
    │   ├── services/
    │   │   └── books.service.js
    │   └── config/
    │       └── env.js
    ├── package.json
    ├── .env
    ├── .gitignore
    └── README.md

## Final Project Notes

Routes:

    GET /health
    GET /books
    GET /books/:id
    POST /books
    PUT /books/:id
    DELETE /books/:id

Protected routes:

    POST /books
    PUT /books/:id
    DELETE /books/:id

Header:

    x-api-key
