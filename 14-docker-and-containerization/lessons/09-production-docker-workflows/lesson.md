# Lesson 09: Production Docker Workflows

## Learning Objectives

By the end of this lesson you should be able to:

- Understand production Docker workflows.
- Build deployment-ready images.
- Improve security.
- Improve performance.
- Understand release processes.

## Development vs Production

Development:

- Fast iteration
- Debugging
- Convenience

Production:

- Security
- Reliability
- Performance

## Multi-Stage Builds

Example:

    FROM node:22-alpine AS builder

    WORKDIR /app

    COPY . .

    RUN npm ci

    RUN npm run build

    FROM node:22-alpine

    WORKDIR /app

    COPY --from=builder /app/dist ./dist

Benefits:

- Smaller images
- Faster deployments

## Security Practices

- Run non-root users.
- Pin image versions.
- Avoid unnecessary packages.
- Scan images.
- Store secrets outside images.

## Example User

    RUN addgroup app

    RUN adduser -D app

    USER app

## Image Tags

Good:

    app:v1.2.0

Avoid:

    latest

## CI/CD Flow

Commit

↓

Build Image

↓

Run Tests

↓

Push Image

↓

Deploy

## Container Registry

Examples:

- Docker Hub
- GitHub Container Registry
- AWS ECR

## Monitoring

Monitor:

- CPU
- Memory
- Logs
- Health checks

## Common Production Mistakes

- Using latest tags.
- Running as root.
- No health checks.
- Large images.
- Hardcoded secrets.

## Interview Questions

1. What is a multi-stage build?
2. Why avoid latest?
3. Why avoid root users?
4. What is a container registry?

## Exercises

1. Create multi-stage Dockerfile.
2. Add non-root user.
3. Tag image.
4. Explain CI/CD flow.
5. Explain image registry.

## Summary

Production Docker workflows focus on security, reliability and maintainability.

## References

https://docs.docker.com/build/building/multi-stage/
