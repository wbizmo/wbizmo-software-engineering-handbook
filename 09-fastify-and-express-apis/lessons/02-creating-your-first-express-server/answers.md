# Lesson 02 Answers

1. npm install express
2. express()
3. Starts server.
4. Creates GET route.
5. Sends JSON.
6. Local machine address.
7. API endpoint.
8. 3000.
9. JSON.
10. Simpler API development.

## Mini Project Solution

    app.get("/books", (req, res) => {
      res.json([
        {
          id: 1,
          title: "Node.js Guide"
        },
        {
          id: 2,
          title: "Fastify Handbook"
        },
        {
          id: 3,
          title: "TypeScript Essentials"
        }
      ]);
    });
