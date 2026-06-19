# Lesson 03: Prisma Schema and Models

## Learning Objectives

By the end of this lesson you should be able to:

- Understand Prisma models.
- Create fields.
- Define data types.
- Define primary keys.
- Understand model mapping.

## What Is A Model?

A Prisma model represents a database table.

Example:

    model User {
      id Int @id
    }

Database:

    users table

## User Model

    model User {
      id    Int    @id @default(autoincrement())
      email String @unique
      name  String
    }

## Common Types

String

    String

Number

    Int

Decimal

    Float

Boolean

    Boolean

Date

    DateTime

## Primary Keys

Example:

    id Int @id

## Auto Increment

    @default(
      autoincrement()
    )

Automatically generates IDs.

## Unique Fields

Example:

    email String @unique

Prevents duplicates.

## Optional Fields

Example:

    phone String?

Question mark:

    optional

## Default Values

Example:

    createdAt DateTime
      @default(now())

## Book Model

    model Book {
      id        Int      @id @default(autoincrement())
      title     String
      author    String
      createdAt DateTime @default(now())
    }

## Library Project

Create:

- User
- Author
- Category
- Book

models.

## Exercises

1. Create User model.
2. Create Book model.
3. Create Author model.
4. Add unique email.
5. Add createdAt.

## Summary

Models define database structure.

Prisma models become tables.

Fields become columns.

## References

https://www.prisma.io/docs/orm/prisma-schema
