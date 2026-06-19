# Lesson 04: Migrations and Database Sync

## Learning Objectives

By the end of this lesson you should be able to:

- Understand Prisma migrations.
- Create migrations.
- Apply schema changes.
- Synchronize databases.
- Understand migration workflows.

## What Is A Migration?

A migration is a tracked database schema change.

Example:

Version 1:

    User

Version 2:

Add:

    phoneNumber

Migration records that change.

## Why Migrations Matter

Without migrations:

- Databases drift
- Teams become inconsistent
- Deployments become risky

With migrations:

- Changes are reproducible
- History is preserved
- Teams stay synchronized

## Migration Workflow

Step 1:

Edit:

    schema.prisma

Step 2:

Run:

    npx prisma migrate dev

Step 3:

Migration generated.

Step 4:

Database updated.

## Example

Original:

    model User {
      id Int @id
      email String
    }

Updated:

    model User {
      id Int @id
      email String
      phoneNumber String?
    }

Apply:

    npx prisma migrate dev \
      --name add-phone-number

## Generated Files

Prisma creates:

    prisma/migrations/

Each migration becomes part of project history.

## Database Synchronization

Sometimes during development:

    npx prisma db push

Pushes schema without migration history.

Useful for quick prototyping.

Not ideal for production.

## Generate Client

After schema changes:

    npx prisma generate

## Real Workflow

Change schema

↓

Run migration

↓

Generate client

↓

Update code

## Exercises

1. Add field to User model.
2. Create migration.
3. Run migration.
4. Generate client.
5. Explain migration history.

## Summary

Migrations safely evolve databases.

Prisma makes schema changes predictable and repeatable.

## References

https://www.prisma.io/docs/orm/prisma-migrate
