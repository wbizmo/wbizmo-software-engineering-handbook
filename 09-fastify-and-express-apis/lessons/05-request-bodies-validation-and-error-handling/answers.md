# Lesson 05 Answers

1. Data sent to the server.
2. POST.
3. To prevent bad data.
4. 400.
5. 201.
6. Express request body.
7. Fastify request body.
8. Better developer experience.
9. Invalid data enters the system.
10. Reliability and security.

## Mini Project Solution

    app.post(
      "/books",
      async (request, reply) => {
        const {
          title,
          author
        } = request.body;

        if (!title || !author) {
          return reply
            .status(400)
            .send({
              success: false,
              message:
                "Title and author required"
            });
        }

        return reply
          .status(201)
          .send({
            success: true
          });
      }
    );
