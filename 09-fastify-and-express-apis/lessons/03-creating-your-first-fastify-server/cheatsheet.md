# Lesson 03 Cheatsheet

Install:

    npm install fastify

Create:

    const app = Fastify();

Route:

    app.get("/", async () => {});

Listen:

    await app.listen({
      port: 3000
    });

Key takeaway:
    Fastify is a fast modern framework for building APIs.
