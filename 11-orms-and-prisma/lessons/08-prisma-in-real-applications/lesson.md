# Lesson 08: Prisma In Real Applications

## Learning Objectives

- Use Prisma in API routes.
- Separate business logic.
- Build service layers.
- Understand production patterns.

## API Route Example

    app.get(
      "/users",
      async () => {
        return prisma.user.findMany();
      }
    );

## Better Structure

routes/

services/

repositories/

config/

## Service Example

    export async function
    getUsers() {
      return prisma.user.findMany();
    }

## Route

    app.get(
      "/users",
      async () => {
        return getUsers();
      }
    );

## Benefits

- Cleaner code
- Easier testing
- Reusability

## Portfolio Examples

Used in:

- SyncGrid API
- VaultBox API
- inFlowForge API

## Exercises

1. Create service.
2. Move query into service.
3. Call service from route.
4. Explain separation of concerns.
5. Create repository function.

## Summary

Prisma should not be scattered everywhere.

Use structured architecture.
