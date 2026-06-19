# Lesson 06: Docker Compose

## Learning Objectives

By the end of this lesson you should be able to:

- Explain Docker Compose.
- Run multi-container applications.
- Define services.
- Use environment variables.
- Manage local development stacks.

## What Is Docker Compose?

Docker Compose manages multiple containers together.

Example:

Fastify API

+

PostgreSQL

+

Redis

Instead of multiple commands:

Use one compose file.

## Example Architecture

API

↓

PostgreSQL

↓

Redis

## docker-compose.yml

Example:

    services:

      api:
        build: .

        ports:
          - "3000:3000"

      postgres:
        image: postgres:17

      redis:
        image: redis:8

## Start Services

    docker compose up

## Detached Mode

    docker compose up -d

## Stop Services

    docker compose down

## View Containers

    docker compose ps

## View Logs

    docker compose logs

## Environment Variables

Example:

    environment:

      DATABASE_URL:
        postgres://...

## Benefits

- One command startup.
- Reproducible environments.
- Easier local development.

## Real World Example

SyncGrid:

API

Redis

PostgreSQL

All started together.

## Common Mistakes

- Wrong port mappings.
- Missing environment variables.
- Forgetting persistent volumes.
- Using latest tags.

## Exercises

1. Create compose file.
2. Add API service.
3. Add PostgreSQL service.
4. Add Redis service.
5. Start stack.

## Interview Questions

1. Why use Docker Compose?
2. What is a service?
3. What does docker compose up do?
4. What does docker compose down do?

## Summary

Docker Compose simplifies multi-container development environments.

## References

https://docs.docker.com/compose/
