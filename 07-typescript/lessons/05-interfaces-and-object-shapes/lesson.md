# Lesson 05: Interfaces and Object Shapes

## Learning Objectives

By the end of this lesson, you should be able to:

- Understand interfaces.
- Use interfaces to describe object shapes.
- Understand optional properties.
- Understand readonly properties.
- Extend interfaces.
- Compare interfaces and type aliases at a beginner level.

## What Is An Interface?

An interface describes the shape of an object.

Example:

    interface User {
      id: string;
      name: string;
      email: string;
    }

    const user: User = {
      id: "1",
      name: "Ada",
      email: "ada@example.com"
    };

## Why Interfaces Are Useful

Interfaces help describe structured data.

Examples:

- User
- Product
- Order
- BlogPost
- ApiResponse
- Config

## Optional Properties

    interface User {
      id: string;
      name: string;
      email?: string;
    }

email is optional.

## readonly Properties

    interface User {
      readonly id: string;
      name: string;
    }

id cannot be reassigned after creation.

## Interface With Methods

    interface Logger {
      log(message: string): void;
    }

    const consoleLogger: Logger = {
      log(message: string) {
        console.log(message);
      }
    };

## Extending Interfaces

Interfaces can extend other interfaces.

    interface BaseEntity {
      id: string;
      createdAt: string;
    }

    interface User extends BaseEntity {
      name: string;
      email: string;
    }

## Interface vs Type Alias

Both can describe object shapes.

Type alias:

    type User = {
      id: string;
      name: string;
    };

Interface:

    interface User {
      id: string;
      name: string;
    }

Beginner rule:

Use either consistently.

Many teams use interfaces for object shapes and type aliases for unions.

## Function Parameters With Interfaces

    interface CreateUserInput {
      name: string;
      email: string;
    }

    function createUser(input: CreateUserInput): void {
      console.log(input.email);
    }

## Common Beginner Mistakes

- Forgetting required properties.
- Adding properties not expected by the interface.
- Confusing optional with nullable.
- Using interfaces for simple literal unions.
- Creating duplicate names accidentally.

## Exercises

1. Create a User interface.
2. Add readonly id.
3. Add optional phone.
4. Create a Product interface.
5. Create an interface that extends another interface.
6. Create a function that accepts CreateUserInput.
7. Create an object that satisfies the User interface.

## Summary

Interfaces describe object shapes.

They make structured data clearer.

They support optional, readonly, methods, and extension.

Interfaces are common in TypeScript applications.

## References

https://www.typescriptlang.org/docs/handbook/2/objects.html

https://www.typescriptlang.org/docs/handbook/interfaces.html
