# Lesson 07: Generics

## Learning Objectives

By the end of this lesson, you should be able to:

- Understand what generics are.
- Understand why generics exist.
- Create generic functions.
- Create generic interfaces.
- Create generic type aliases.
- Understand generic constraints.
- Understand real-world use cases.

## What Are Generics?

Generics allow us to write reusable code that works with many types while preserving type safety.

Think of generics as:

    Type Variables

Just as variables hold values:

    const name = "Ada";

Generics hold types.

Example:

    T

can represent:

    string

or

    number

or

    User

or

    Product

depending on usage.

## Why Generics Exist

Without generics:

    function getFirstString(
      items: string[]
    ): string {
      return items[0];
    }

Works only for strings.

Need another function:

    function getFirstNumber(
      items: number[]
    ): number {
      return items[0];
    }

Need another:

    function getFirstUser(
      items: User[]
    ): User {
      return items[0];
    }

This becomes repetitive.

Generics solve this.

## Generic Function

Example:

    function getFirst<T>(
      items: T[]
    ): T {
      return items[0];
    }

Usage:

    const name = getFirst([
      "Ada",
      "Tunde"
    ]);

TypeScript infers:

    string

Another example:

    const score = getFirst([
      100,
      90,
      80
    ]);

TypeScript infers:

    number

Same function.

Different types.

## Reading Generic Syntax

Example:

    function getFirst<T>(
      items: T[]
    ): T

Meaning:

T represents any type.

Input:

    T[]

Output:

    T

## Explicit Generic Type

Sometimes you provide the type manually.

Example:

    const value =
      getFirst<string>([
        "Ada",
        "Tunde"
      ]);

Usually TypeScript infers automatically.

## Multiple Generic Types

Example:

    function pair<T, U>(
      first: T,
      second: U
    ) {
      return {
        first,
        second
      };
    }

Usage:

    pair("Ada", 25);

TypeScript infers:

    T = string
    U = number

Result:

    {
      first: string;
      second: number;
    }

## Generic Type Alias

Example:

    type ApiResponse<T> = {
      success: boolean;
      data: T;
    };

Usage:

    type User = {
      id: string;
      name: string;
    };

    const response:
      ApiResponse<User> = {
        success: true,
        data: {
          id: "1",
          name: "Ada"
        }
      };

## Generic Interface

Example:

    interface Repository<T> {
      getAll(): T[];
      getById(id: string): T | null;
    }

Now it can work with:

    User

or

    Product

or

    Order

## Real Backend Example

User:

    interface User {
      id: string;
      email: string;
    }

Product:

    interface Product {
      id: string;
      name: string;
    }

Reusable repository:

    interface Repository<T> {
      findById(
        id: string
      ): T | null;
    }

Use:

    Repository<User>

or

    Repository<Product>

Same logic.

Different data.

## Generic Constraints

Sometimes we need rules.

Example:

    function printId<
      T extends {
        id: string;
      }
    >(item: T) {
      console.log(item.id);
    }

Valid:

    printId({
      id: "1",
      name: "Ada"
    });

Invalid:

    printId({
      name: "Ada"
    });

Why?

Because:

    id

is required.

## extends Keyword

Used to constrain generics.

Example:

    T extends User

Means:

T must behave like User.

## Generic Array Example

Example:

    function logItems<T>(
      items: T[]
    ): void {
      items.forEach(
        (item) =>
          console.log(item)
      );
    }

Works with:

    string[]

    number[]

    User[]

## Generic API Example

Common pattern:

    type ApiResponse<T> = {
      success: boolean;
      data: T;
    };

Users:

    ApiResponse<User>

Products:

    ApiResponse<Product>

Orders:

    ApiResponse<Order>

One structure.

Many data types.

## Why Generics Matter

Generics are heavily used in:

- React
- Node.js
- Fastify
- Express
- Prisma
- SDKs
- APIs
- Libraries
- Utility functions

Many modern TypeScript libraries rely heavily on generics.

## Common Beginner Mistakes

### Mistake 1

Avoiding generics completely.

### Mistake 2

Using any instead.

Bad:

    function getFirst(
      items: any[]
    ) {
      return items[0];
    }

Good:

    function getFirst<T>(
      items: T[]
    ): T {
      return items[0];
    }

### Mistake 3

Making generics unnecessarily complex.

### Mistake 4

Using constraints incorrectly.

### Mistake 5

Adding generics when a normal type would be simpler.

## Exercises

### Exercise 1

Create:

    getLast<T>()

Returns last item.

### Exercise 2

Create:

    pair<T, U>()

Returns object with both values.

### Exercise 3

Create:

    ApiResponse<T>

### Exercise 4

Create:

    Repository<T>

### Exercise 5

Create constrained generic requiring:

    id: string

## Summary

Generics create reusable type-safe code.

They eliminate duplication.

They preserve type information.

They are essential in modern TypeScript applications.

## References

https://www.typescriptlang.org/docs/handbook/2/generics.html

https://www.typescriptlang.org/docs/handbook/2/types-from-types.html
