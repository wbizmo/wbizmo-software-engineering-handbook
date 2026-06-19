# Lesson 02: Creating Your First Express Server

## Learning Objectives

By the end of this lesson, you should be able to:

- Install Express.
- Create an Express server.
- Define routes.
- Send JSON responses.
- Run an API locally.

## Installing Express

Create project:

    npm init -y

Install:

    npm install express

## Creating Server

server.js

    import express from "express";

    const app = express();

    app.listen(3000, () => {
      console.log(
        "Server running"
      );
    });

Run:

    node server.js

## First Route

    app.get("/", (req, res) => {
      res.json({
        message: "Hello API"
      });
    });

Visit:

    http://localhost:3000

Response:

    {
      "message": "Hello API"
    }

## Multiple Routes

    app.get("/books", (req, res) => {
      res.json([]);
    });

    app.get("/health", (req, res) => {
      res.json({
        status: "ok"
      });
    });

## BookStore API

Create:

    GET /books

Return:

    [
      {
        "id": 1,
        "title": "Node.js Guide"
      }
    ]

## Exercises

1. Install Express.
2. Create server.
3. Create root route.
4. Create health route.
5. Create books route.

## Mini Project

Build:

    GET /books

Return three books.

## Summary

Express makes API development simple.

Routes define endpoints.

Responses are usually JSON.

## References

https://expressjs.com
