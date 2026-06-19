# Lesson 01: Introduction To TypeScript

## Learning Objectives

By the end of this lesson, you should be able to:

- Explain what TypeScript is.
- Explain why TypeScript exists.
- Understand the difference between JavaScript and TypeScript.
- Understand static typing.
- Understand compilation.
- Know where TypeScript is useful.

## What Is TypeScript?

TypeScript is a programming language built on top of JavaScript.

A simple definition:

    TypeScript = JavaScript + Types

JavaScript is dynamically typed.

TypeScript adds static typing.

This means TypeScript can warn you about many mistakes before your code runs.

## JavaScript Example

    function greet(name) {
      return "Hello, " + name;
    }

    greet("Ada");
    greet(42);

JavaScript allows both calls.

But passing 42 may not be what the developer intended.

## TypeScript Example

    function greet(name: string) {
      return "Hello, " + name;
    }

    greet("Ada");
    greet(42);

TypeScript warns that 42 is not a string.

## Why TypeScript Exists

JavaScript is flexible.

That flexibility is powerful, but in large applications it can cause problems.

TypeScript helps with:

- Catching errors early
- Understanding data shapes
- Improving editor autocomplete
- Making refactoring safer
- Building large codebases
- Improving team collaboration

## Static Typing

Static typing means checking types before the program runs.

Example:

    const age: number = 25;

    age = "twenty five";

TypeScript warns because a string is being assigned to a number variable.

## Runtime vs Compile Time

Runtime:

    When the program is actually running.

Compile time:

    Before the program runs, when TypeScript checks and converts code.

TypeScript code does not run directly in most JavaScript environments.

It is compiled into JavaScript.

## Compilation

TypeScript files usually end with:

    .ts

Example:

    app.ts

The TypeScript compiler converts it to JavaScript:

    app.js

Command:

    tsc app.ts

## TypeScript Does Not Replace JavaScript

TypeScript becomes JavaScript.

Browsers and Node.js usually run JavaScript.

TypeScript helps during development.

## Where TypeScript Is Used

TypeScript is common in:

- React apps
- Node.js APIs
- Fastify backends
- Express backends
- CLI tools
- SDKs
- Monorepos
- Large frontend applications
- Enterprise applications

## Why Backend Developers Like TypeScript

Backend systems often handle structured data.

Examples:

- Users
- Orders
- Payments
- API requests
- Database records
- Config objects

TypeScript helps describe these structures clearly.

Example:

    type User = {
      id: string;
      email: string;
      role: string;
    };

## Common Beginner Mistakes

- Thinking TypeScript is a completely different language from JavaScript.
- Trying to use TypeScript without understanding JavaScript basics.
- Adding too many unnecessary types.
- Ignoring compiler errors.
- Using any everywhere.
- Thinking TypeScript prevents all runtime bugs.

## Exercises

1. Explain TypeScript in your own words.
2. Explain the difference between JavaScript and TypeScript.
3. Write a TypeScript function that accepts a string.
4. Write a variable with a number type.
5. Explain why TypeScript is useful for large projects.
6. Explain what compilation means.
7. List three projects where TypeScript would be useful.

## Summary

TypeScript is JavaScript with static typing.

It helps catch errors before runtime.

It improves maintainability, autocomplete, refactoring, and collaboration.

TypeScript compiles to JavaScript.

## References

https://www.typescriptlang.org/docs/

https://www.typescriptlang.org/docs/handbook/typescript-from-scratch.html

https://developer.mozilla.org/en-US/docs/Glossary/TypeScript
