# Lesson 02: Introduction To Prisma

## Learning Objectives

By the end of this lesson you should be able to:

- Understand Prisma architecture.
- Install Prisma.
- Initialize Prisma.
- Understand Prisma components.
- Generate Prisma Client.

## What Is Prisma?

Prisma is a modern ORM for Node.js and TypeScript.

Features:

- Type safety
- Migrations
- Query builder
- Excellent developer experience
- Strong TypeScript integration

## Installing Prisma

Project:

    npm init -y

Install:

    npm install prisma

Install client:

    npm install @prisma/client

## Initialize Prisma

Run:

    npx prisma init

Creates:

    prisma/
    prisma/schema.prisma

## Prisma Components

### Prisma Schema

Defines database structure.

### Prisma Client

Used by application code.

### Prisma Migrate

Handles schema changes.

## Example Schema

    model User {
      id    Int    @id
      email String
    }

## Generate Client

Run:

    npx prisma generate

Prisma generates typed database access code.

## Example Usage

    const users =
      await prisma.user.findMany();

## Why Prisma Is Popular

- Strong TypeScript support
- Excellent migrations
- Clean syntax
- Great documentation

## Portfolio Examples

Used heavily in:

- SyncGrid API
- VaultBox API
- inFlowForge API

## Exercises

1. Install Prisma.
2. Install Prisma Client.
3. Run prisma init.
4. Explore schema.prisma.
5. Run prisma generate.

## Summary

Prisma provides a modern ORM workflow.

Schema, client, and migrations are the core building blocks.

## References

https://www.prisma.io/docs
