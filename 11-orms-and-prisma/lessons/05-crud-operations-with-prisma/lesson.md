# Lesson 05: CRUD Operations With Prisma

## Learning Objectives

By the end of this lesson you should be able to:

- Create records.
- Read records.
- Update records.
- Delete records.
- Query data safely.

## Prisma Client

Import:

    import { PrismaClient }
      from "@prisma/client";

    const prisma =
      new PrismaClient();

## Create

Example:

    await prisma.user.create({
      data: {
        name: "Ada",
        email: "ada@email.com"
      }
    });

## Find All

    const users =
      await prisma.user.findMany();

## Find One

    const user =
      await prisma.user.findUnique({
        where: {
          id: 1
        }
      });

## Update

    await prisma.user.update({
      where: {
        id: 1
      },
      data: {
        name: "Updated"
      }
    });

## Delete

    await prisma.user.delete({
      where: {
        id: 1
      }
    });

## Create Book

    await prisma.book.create({
      data: {
        title: "Node.js Guide",
        author: "Ada"
      }
    });

## Real Example

VaultBox:

Create user.

SyncGrid:

Create API key.

inFlowForge:

Create workflow.

All use CRUD operations.

## Mini Project

Build:

- Create book
- List books
- Update book
- Delete book

using Prisma.

## Exercises

1. Create user.
2. Read users.
3. Update user.
4. Delete user.
5. Create book.
6. Read books.

## Summary

CRUD operations are the foundation of most backend applications.

Prisma makes CRUD concise and type-safe.

## References

https://www.prisma.io/docs/orm/prisma-client
