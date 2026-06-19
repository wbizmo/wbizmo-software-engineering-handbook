# Lesson 05: Dockerfiles

## Learning Objectives

By the end of this lesson you should be able to:

- Create Dockerfiles.
- Build images.
- Understand image layers.
- Containerize applications.
- Follow Dockerfile best practices.

## What Is A Dockerfile?

A Dockerfile contains instructions used to build images.

Example:

    Application

↓

    Dockerfile

↓

    Docker Image

↓

    Container

## Simple Fastify Example

Project:

    app.js
    package.json

Dockerfile:

    FROM node:22-alpine

    WORKDIR /app

    COPY package*.json ./

    RUN npm install

    COPY . .

    EXPOSE 3000

    CMD ["npm", "start"]

## Dockerfile Instructions

FROM

Base image.

WORKDIR

Working directory.

COPY

Copies files.

RUN

Executes commands.

EXPOSE

Documents ports.

CMD

Default command.

## Build Image

    docker build \
      -t my-api .

## Run Image

    docker run \
      -p 3000:3000 \
      my-api

## Port Mapping

Host:

    3000

Container:

    3000

Example:

    -p 3000:3000

## .dockerignore

Example:

    node_modules
    .git
    coverage

Reduces build size.

## Best Practices

- Use small base images.
- Pin versions.
- Use .dockerignore.
- Keep images small.
- Avoid unnecessary packages.

## Common Mistakes

- Copying node_modules.
- Using huge images.
- Forgetting .dockerignore.
- Hardcoding secrets.

## Exercises

1. Create Dockerfile.
2. Build image.
3. Run image.
4. Create .dockerignore.
5. Expose application port.

## Interview Questions

1. What is a Dockerfile?
2. What does FROM do?
3. What does COPY do?
4. What does CMD do?

## Summary

Dockerfiles define how application images are built.

## References

https://docs.docker.com/reference/dockerfile/
