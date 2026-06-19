# Lesson 07 Cheatsheet

Middleware:
    Code around requests.

Fastify hook:

    app.addHook("preHandler", async () => {})

API key header:

    x-api-key

Unauthorized:

    401

Protect route:

    preHandler: requireApiKey

Security:
    Validate input.
    Use env vars.
    Use HTTPS.
    Rate limit.
    Avoid stack traces.
