# Lesson 07: Filtering, Pagination and Sorting

## Learning Objectives

By the end of this lesson you should be able to:

- Filter records
- Sort records
- Paginate results
- Build API-friendly queries
- Improve query efficiency

## Filtering

Find users named Ada:

    const users =
      await prisma.user.findMany({
        where: {
          name: "Ada"
        }
      });

## Contains

    const books =
      await prisma.book.findMany({
        where: {
          title: {
            contains: "Node"
          }
        }
      });

## Multiple Conditions

    const users =
      await prisma.user.findMany({
        where: {
          active: true,
          country: "Nigeria"
        }
      });

## Sorting

Ascending:

    const books =
      await prisma.book.findMany({
        orderBy: {
          title: "asc"
        }
      });

Descending:

    const books =
      await prisma.book.findMany({
        orderBy: {
          createdAt: "desc"
        }
      });

## Pagination

First page:

    const books =
      await prisma.book.findMany({
        skip: 0,
        take: 10
      });

Second page:

    const books =
      await prisma.book.findMany({
        skip: 10,
        take: 10
      });

## API Example

Page parameter:

    /books?page=2

Calculation:

    skip = (page - 1) * limit

## Real World Usage

Used in:

- VaultBox file listings
- SyncGrid logs
- Covenant contracts
- Cashflowr transactions

## Exercises

1. Filter users.
2. Filter books.
3. Sort books.
4. Paginate books.
5. Combine filters and sorting.

## Summary

Filtering reduces results.

Sorting organizes results.

Pagination improves scalability.

## References

https://www.prisma.io/docs/orm/prisma-client/queries/filtering-and-sorting
