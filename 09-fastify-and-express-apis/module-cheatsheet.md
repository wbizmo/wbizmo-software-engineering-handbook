# Fastify & Express APIs Module Cheatsheet

HTTP Methods:

    GET
    POST
    PUT
    PATCH
    DELETE

Status Codes:

    200 OK
    201 Created
    204 No Content
    400 Bad Request
    401 Unauthorized
    403 Forbidden
    404 Not Found
    500 Server Error

Express:

    app.get("/", handler)

Fastify:

    app.get("/", async () => {})

Params:

    /books/:id

Query:

    /books?page=1

Body:

    request.body

CRUD:

    GET /books
    GET /books/:id
    POST /books
    PUT /books/:id
    DELETE /books/:id

Security:

    x-api-key
    environment variables
    validation

Structure:

    routes/
    services/
    config/
