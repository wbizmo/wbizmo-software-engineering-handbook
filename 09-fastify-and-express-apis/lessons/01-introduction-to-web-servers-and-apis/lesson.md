# Lesson 01: Introduction To Web Servers And APIs

## Learning Objectives

By the end of this lesson, you should be able to:

- Explain what a web server is.
- Explain what an API is.
- Understand requests and responses.
- Understand HTTP basics.
- Understand backend application architecture.

## What Is A Web Server?

A web server is software that listens for requests and sends responses.

Example:

Browser requests:

    https://example.com

Server responds:

    HTML

or

    JSON

or

    files

## What Is An API?

API means:

    Application Programming Interface

In backend development, APIs usually allow applications to communicate.

Example:

Frontend:

    GET /users

Backend:

    Returns users

## Real Example

Request:

    GET /users

Response:

    [
      {
        "id": 1,
        "name": "Ada"
      }
    ]

## HTTP Methods

GET

Retrieve data.

POST

Create data.

PUT

Update data.

PATCH

Partially update data.

DELETE

Remove data.

## Request Components

Example:

    GET /users?page=1

Contains:

- Method
- URL
- Headers
- Query parameters

## Response Components

Contains:

- Status code
- Headers
- Body

Example:

    {
      "success": true
    }

## Common Status Codes

200

Success.

201

Created.

400

Bad Request.

401

Unauthorized.

403

Forbidden.

404

Not Found.

500

Server Error.

## API Architecture

Client

↓

API

↓

Database

↓

Response

## Portfolio Examples

APIs you have built:

- SyncGrid API
- VaultBox API
- inFlowForge API

All follow this pattern.

## BookStore API Project

Throughout this module we will build:

    BookStore API

Features:

- List books
- View book
- Create book
- Update book
- Delete book

## Exercises

1. Explain what a server is.
2. Explain what an API is.
3. List HTTP methods.
4. List common status codes.
5. Draw the request-response flow.

## Summary

Servers process requests.

APIs expose functionality.

HTTP powers communication between clients and servers.

## References

https://developer.mozilla.org/en-US/docs/Web/HTTP
