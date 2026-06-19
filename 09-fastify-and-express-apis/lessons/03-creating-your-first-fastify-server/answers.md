# Lesson 03 Answers

1. npm install fastify
2. Fastify()
3. app.get
4. Speed and developer experience.
5. Yes.
6. Starts the server.
7. Endpoint that reports service status.
8. JSON.
9. SyncGrid API, VaultBox API or inFlowForge API.
10. Performance, validation, TypeScript support.

## Mini Project Solution

    import Fastify from "fastify";

    const app = Fastify();

    app.get("/books", async () => {
      return [
        {
          id: 1,
          title: "Node.js Guide"
        },
        {
          id: 2,
          title: "Fastify Handbook"
        }
      ];
    });

    await app.listen({
      port: 3000
    });
