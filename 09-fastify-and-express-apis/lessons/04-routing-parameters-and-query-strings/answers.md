# Lesson 04 Answers

1. Dynamic route value.
2. Resource identifier.
3. Extra URL data.
4. After ? in a URL.
5. Route parameters.
6. Query parameters.
7. Splitting results into pages.
8. Limiting results.
9. Finding matching results.
10. To identify resources.

## Mini Project Solution

    app.get(
      "/books/:id",
      async (request) => {
        const { id } =
          request.params;

        return {
          id,
          title:
            "Node.js Guide"
        };
      }
    );

    app.get(
      "/books",
      async (request) => {
        const { q } =
          request.query;

        return books.filter(
          (book) =>
            book.title
              .toLowerCase()
              .includes(
                q?.toLowerCase() || ""
              )
        );
      }
    );
