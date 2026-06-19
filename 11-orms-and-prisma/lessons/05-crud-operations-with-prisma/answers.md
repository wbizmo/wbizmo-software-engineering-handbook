# Lesson 05 Answers

1. create().
2. findMany().
3. findUnique().
4. update().
5. delete().
6. Generated database client.
7. Multiple records.
8. One record.
9. Generated types.
10. Most applications manage data.

## Mini Project Solution

    await prisma.book.create({
      data: {
        title: "Node.js Guide",
        author: "Ada"
      }
    });

    const books =
      await prisma.book.findMany();

    await prisma.book.update({
      where: {
        id: 1
      },
      data: {
        title: "Updated"
      }
    });

    await prisma.book.delete({
      where: {
        id: 1
      }
    });
