# Lesson 01: Introduction To ORMs

## Learning Objectives

By the end of this lesson you should be able to:

- Explain what an ORM is.
- Understand why ORMs exist.
- Compare raw SQL and ORM workflows.
- Identify ORM benefits and tradeoffs.
- Understand where ORMs fit in application architecture.

## What Is An ORM?

ORM means:

    Object Relational Mapper

An ORM translates:

    Objects

into

    Database Operations

Example:

Instead of:

    SELECT *
    FROM users;

You write:

    prisma.user.findMany()

The ORM generates SQL behind the scenes.

## Why ORMs Exist

Writing SQL repeatedly can become:

- Repetitive
- Error-prone
- Difficult to maintain

ORMs provide:

- Abstraction
- Safety
- Productivity

## Raw SQL Example

    SELECT *
    FROM users
    WHERE id = 1;

## ORM Example

    await prisma.user.findUnique({
      where: {
        id: 1
      }
    });

Both perform similar operations.

## Benefits Of ORMs

### Faster Development

Less SQL.

More application logic.

### Type Safety

TypeScript can understand your database.

### Easier Refactoring

Schema changes become easier to manage.

### Better Tooling

Autocomplete.

Validation.

Developer experience.

## ORM Tradeoffs

### Less Control

Raw SQL gives maximum control.

### Learning Curve

You must learn ORM syntax.

### Performance Considerations

Complex queries sometimes require raw SQL.

## Popular ORMs

JavaScript Ecosystem:

- Prisma
- Sequelize
- TypeORM
- MikroORM

PHP:

- Eloquent

Python:

- SQLAlchemy

## Architecture

Application

↓

ORM

↓

Database

## Portfolio Examples

Used in:

- SyncGrid API
- VaultBox API
- inFlowForge API
- Covenant

## Exercises

1. Define ORM.
2. Explain why ORMs exist.
3. Compare SQL vs ORM.
4. List ORM benefits.
5. List ORM tradeoffs.

## Summary

ORMs simplify database interactions.

They improve productivity and developer experience.

Modern backend systems commonly use ORMs.

## References

https://www.prisma.io/docs
