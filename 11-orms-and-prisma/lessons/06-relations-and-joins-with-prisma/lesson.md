# Lesson 06: Relations and Joins With Prisma

## Learning Objectives

By the end of this lesson you should be able to:

- Define relations.
- Create one-to-many relationships.
- Query related data.
- Use include.
- Understand Prisma joins.

## Author And Book

SQL:

Authors

↓

Books

Prisma:

    model Author {
      id Int @id
      name String

      books Book[]
    }

    model Book {
      id Int @id
      title String

      authorId Int

      author Author
        @relation(
          fields: [authorId],
          references: [id]
        )
    }

## One-To-Many

One author

↓

Many books

## Query Relations

Example:

    const authors =
      await prisma.author.findMany({
        include: {
          books: true
        }
      });

Result:

Author

+

Books

## Query Book With Author

    const books =
      await prisma.book.findMany({
        include: {
          author: true
        }
      });

## Many-To-Many

Students

↓

Courses

Prisma supports join tables.

## Library Project

Relationships:

Author

↓

Books

Category

↓

Books

User

↓

BorrowedBooks

Book

↓

BorrowedBooks

## Why Relations Matter

Without relations:

Duplicate data.

With relations:

Consistency.

Normalization.

Cleaner design.

## Exercises

1. Create Author model.
2. Create Book model.
3. Add relation.
4. Query author with books.
5. Query book with author.

## Summary

Relations connect models.

Prisma can load related records automatically.

## References

https://www.prisma.io/docs/orm/prisma-schema/data-model/relations
