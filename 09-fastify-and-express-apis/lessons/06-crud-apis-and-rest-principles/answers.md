# Lesson 06 Answers

1. Create, Read, Update, Delete.
2. GET.
3. POST.
4. PUT or PATCH.
5. DELETE.
6. 201.
7. 404.
8. 204.
9. Nouns.
10. Because the requested resource does not exist.

## Mini Project Solution

    const books = [];

    app.get("/books", async () => {
      return books;
    });

    app.get("/books/:id", async (request, reply) => {
      const { id } = request.params;

      const book = books.find((item) => item.id === id);

      if (!book) {
        return reply.status(404).send({
          success: false,
          message: "Book not found"
        });
      }

      return book;
    });

    app.post("/books", async (request, reply) => {
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

    app.put("/books/:id", async (request, reply) => {
      const { id } = request.params;
      const { title, author } = request.body;

      const book = books.find((item) => item.id === id);

      if (!book) {
        return reply.status(404).send({
          success: false,
          message: "Book not found"
        });
      }

      book.title = title;
      book.author = author;

      return book;
    });

    app.delete("/books/:id", async (request, reply) => {
      const { id } = request.params;

      const index = books.findIndex((item) => item.id === id);

      if (index === -1) {
        return reply.status(404).send({
          success: false,
          message: "Book not found"
        });
      }

      books.splice(index, 1);

      return reply.status(204).send();
    });
