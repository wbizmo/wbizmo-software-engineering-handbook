# Lesson 07 Answers

1. Code that runs before or during request handling.
2. Fastify lifecycle functions.
3. Verifying identity.
4. Grants access to protected API routes.
5. x-api-key.
6. 401.
7. To keep config and secrets outside code.
8. To prevent bad or unsafe data.
9. They may reveal sensitive implementation details.
10. Validate input, use HTTPS, rate limit, protect routes, avoid committing secrets.

## Mini Project Solution

    const API_KEY = process.env.API_KEY || "dev-secret";

    async function requireApiKey(request, reply) {
      const apiKey = request.headers["x-api-key"];

      if (apiKey !== API_KEY) {
        return reply.status(401).send({
          success: false,
          message: "Invalid API key"
        });
      }
    }

    app.addHook("preHandler", async (request) => {
      console.log(request.method, request.url);
    });

    app.post("/books", {
      preHandler: requireApiKey
    }, async (request, reply) => {
      const { title, author } = request.body;

      if (!title || !author) {
        return reply.status(400).send({
          success: false,
          message: "Title and author required"
        });
      }

      const book = {
        id: Date.now().toString(),
        title,
        author
      };

      books.push(book);

      return reply.status(201).send(book);
    });
