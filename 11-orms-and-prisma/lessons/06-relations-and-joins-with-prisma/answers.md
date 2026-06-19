# Lesson 06 Answers

1. Connection between models.
2. One record linked to many.
3. Loads related records.
4. Consistency and structure.
5. Foreign key.
6. Reducing duplication.
7. Book.
8. Author.
9. Consistency.
10. include.

## Exercise Solution

    const authors =
      await prisma.author.findMany({
        include: {
          books: true
        }
      });

    const books =
      await prisma.book.findMany({
        include: {
          author: true
        }
      });
