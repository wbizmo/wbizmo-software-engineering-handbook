# Lesson 09: JSON, Fetch and API Basics

## Learning Objectives

By the end of this lesson, you should understand JSON, APIs, fetch, GET requests, POST requests, response parsing, and basic API error handling.

## What Is JSON?

JSON means JavaScript Object Notation.

It is a lightweight data format.

Example:

    {
      "name": "Ada",
      "age": 25,
      "isDeveloper": true
    }

JSON is commonly used by APIs.

## JavaScript Object vs JSON

JavaScript object:

    const user = {
      name: "Ada"
    };

JSON:

    {
      "name": "Ada"
    }

JSON keys must use double quotes.

## JSON.stringify

Converts JavaScript value to JSON string.

    const user = { name: "Ada" };

    const json = JSON.stringify(user);

## JSON.parse

Converts JSON string to JavaScript value.

    const data = JSON.parse(json);

## What Is An API?

API means Application Programming Interface.

In web development, an API often allows frontend apps to communicate with backend servers.

Example:

    Frontend → API → Database

## fetch

fetch sends HTTP requests from JavaScript.

GET example:

    async function getUsers() {
      const response = await fetch("https://jsonplaceholder.typicode.com/users");
      const users = await response.json();

      console.log(users);
    }

    getUsers();

## POST Example

    async function createPost() {
      const response = await fetch("https://jsonplaceholder.typicode.com/posts", {
        method: "POST",
        headers: {
          "Content-Type": "application/json"
        },
        body: JSON.stringify({
          title: "Hello",
          body: "Learning fetch",
          userId: 1
        })
      });

      const data = await response.json();

      console.log(data);
    }

    createPost();

## Checking Response Status

    if (!response.ok) {
      throw new Error("Request failed");
    }

## Common Mistakes

- Forgetting await.
- Forgetting response.json().
- Forgetting JSON.stringify for POST body.
- Forgetting Content-Type header.
- Not handling errors.
- Exposing private API keys in frontend code.

## Exercises

1. Create a JavaScript object.
2. Convert it to JSON using JSON.stringify.
3. Convert it back using JSON.parse.
4. Fetch users from a public API.
5. Print user names.
6. Send a POST request.
7. Add error handling with try...catch.
8. Check response.ok.

## Summary

JSON is a common data format for APIs.

fetch sends HTTP requests.

Frontend applications use APIs to communicate with backend services.

Understanding JSON and fetch prepares you for React, Node.js, and full stack development.

## References

- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/JSON
- https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API
- https://developer.mozilla.org/en-US/docs/Web/API/Response/json
