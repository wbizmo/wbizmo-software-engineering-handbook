# Lesson 07: Middleware, Authentication and Security

## Learning Objectives

By the end of this lesson, you should be able to:

- Understand middleware.
- Understand authentication.
- Understand basic API key authentication.
- Protect routes.
- Understand basic API security practices.

## What Is Middleware?

Middleware is code that runs before or during request handling.

It can:

- Log requests
- Check authentication
- Validate data
- Add headers
- Handle errors

## Express Middleware

    app.use((req, res, next) => {
      console.log(req.method, req.url);
      next();
    });

## Fastify Hooks

Fastify uses hooks.

Example:

    app.addHook("preHandler", async (request) => {
      console.log(request.method, request.url);
    });

## What Is Authentication?

Authentication answers:

    Who are you?

Examples:

- Email and password
- API key
- JWT
- OAuth

## API Key Authentication

API keys are common for developer APIs.

Client sends:

    x-api-key: secret-key

Server checks if key is valid.

## Fastify API Key Example

    const API_KEY = "secret-key";

    async function requireApiKey(request, reply) {
      const apiKey = request.headers["x-api-key"];

      if (apiKey !== API_KEY) {
        return reply.status(401).send({
          success: false,
          message: "Invalid API key"
        });
      }
    }

Use:

    app.get("/protected", {
      preHandler: requireApiKey
    }, async () => {
      return {
        success: true
      };
    });

## Security Basics

Important practices:

- Never commit secrets.
- Use environment variables.
- Validate request bodies.
- Return safe error messages.
- Use HTTPS in production.
- Rate limit public APIs.
- Avoid exposing stack traces.
- Use proper CORS settings.

## Protected Book Creation

Protect:

    POST /books

Only users with API key can create books.

## Common Mistakes

- Hardcoding production secrets.
- Returning too much error detail.
- Not validating input.
- No rate limiting.
- No authentication on sensitive routes.
- Logging secrets accidentally.

## Exercises

1. Create a logging middleware/hook.
2. Create requireApiKey.
3. Protect POST /books.
4. Return 401 for invalid key.
5. Move API key to environment variable.
6. Explain why secrets must not be committed.

## Summary

Middleware and hooks run around requests.

Authentication protects private routes.

Security must be designed into APIs from the beginning.

## References

https://fastify.dev/docs/latest/Reference/Hooks/

https://expressjs.com/en/guide/using-middleware.html

https://owasp.org/www-project-api-security/
