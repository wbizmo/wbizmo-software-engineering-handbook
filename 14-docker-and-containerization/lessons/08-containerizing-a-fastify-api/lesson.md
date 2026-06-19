# Lesson 08: Containerizing A Fastify API

## Learning Objectives

By the end of this lesson you should be able to:

- Containerize a Fastify application.
- Build Docker images.
- Run APIs inside containers.
- Use environment variables.
- Connect API to PostgreSQL and Redis.

## Project Structure

    app/
      src/
      package.json
      Dockerfile
      docker-compose.yml

## Fastify Dockerfile

    FROM node:22-alpine

    WORKDIR /app

    COPY package*.json ./

    RUN npm ci

    COPY . .

    EXPOSE 3000

    CMD ["npm", "start"]

## Build Image

    docker build \
      -t fastify-api .

## Run Container

    docker run \
      -p 3000:3000 \
      fastify-api

## Compose Setup

    services:

      api:
        build: .

      postgres:
        image: postgres:17

      redis:
        image: redis:8

## Environment Variables

Example:

    DATABASE_URL

    REDIS_URL

    JWT_SECRET

Never hardcode secrets.

## Example DATABASE_URL

    postgres://user:pass@postgres:5432/app

Notice:

    postgres

service name.

Not:

    localhost

## Health Check Endpoint

    app.get(
      "/health",
      async () => ({
        status: "ok"
      })
    );

## Testing Container

    curl http://localhost:3000/health

Expected:

    {
      "status":"ok"
    }

## Common Problems

- Missing environment variables.
- Wrong port mapping.
- Wrong database hostname.
- Missing dependencies.

## Portfolio Relevance

Applies directly to:

- SyncGrid
- VaultBox
- inFlowForge
- Argus
- NOMMO

## Exercises

1. Create Dockerfile.
2. Build image.
3. Run image.
4. Add PostgreSQL.
5. Add Redis.
6. Test health endpoint.

## Summary

Containerizing APIs creates reproducible backend environments.

## References

https://fastify.dev
