# Lesson 03: Creating Your First Fastify Server

## Learning Objectives

By the end of this lesson, you should be able to:

- Install Fastify.
- Create a Fastify server.
- Define routes.
- Return JSON.
- Understand why Fastify is popular.

## What Is Fastify?

Fastify is a modern Node.js framework.

Benefits:

- Fast
- Lightweight
- Schema support
- Great TypeScript support
- Production ready

Many of your portfolio APIs use Fastify.

Examples:

- SyncGrid API
- VaultBox API
- inFlowForge API

## Install Fastify

    npm install fastify

## Create Server

server.js

    import Fastify from "fastify";

    const app = Fastify();

    await app.listen({
      port: 3000
    });

## Route

    app.get("/", async () => {
      return {
        message: "Hello Fastify"
      };
    });

## Health Route

    app.get("/health", async () => {
      return {
        status: "ok"
      };
    });

## Books Route

    app.get("/books", async () => {
      return [
        {
          id: 1,
          title: "Node.js Guide"
        }
      ];
    });

## Why Fastify?

- Faster startup
- Schema validation
- Better TypeScript experience
- Plugin architecture

## Exercises

1. Install Fastify.
2. Create server.
3. Create root route.
4. Create health route.
5. Create books route.

## Mini Project

Rebuild BookStore API using Fastify.

## Summary

Fastify is a modern API framework.

It provides speed, validation, and strong TypeScript support.

## References

https://fastify.dev
