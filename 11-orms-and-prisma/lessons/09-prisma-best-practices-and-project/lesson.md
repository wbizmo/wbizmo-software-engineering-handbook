# Lesson 09: Prisma Best Practices and Project

## Learning Objectives

- Apply Prisma best practices.
- Design scalable schemas.
- Build a complete data layer.
- Prepare for production systems.

## Best Practices

### Use Migrations

Prefer:

    prisma migrate dev

Avoid relying entirely on:

    prisma db push

### Use Relations

Avoid duplicate data.

### Use Indexes

Index:

- emails
- usernames
- foreign keys

### Keep Schema Organized

Group related models.

### Use Services

Avoid database logic directly in routes.

## Final Project

Library Management Database Layer

Models:

- User
- Author
- Category
- Book
- BorrowedBook

Features:

- CRUD
- Relations
- Pagination
- Filtering
- Sorting

## Deliverables

- schema.prisma
- migrations
- service layer
- queries

## Exercises

1. Design schema.
2. Add relations.
3. Add indexes.
4. Add pagination.
5. Add filtering.

## Summary

Prisma combines:

- ORM
- Migrations
- Type safety
- Developer productivity

and is one of the most valuable backend tools in the TypeScript ecosystem.
