# Lesson 03: Functions, Objects and Arrays

## Learning Objectives

By the end of this lesson, you should be able to:

- Type function parameters.
- Type function return values.
- Type arrays.
- Type objects.
- Use optional properties.
- Understand readonly basics.

## Function Parameter Types

Function parameters should usually have types.

    function greet(name: string) {
      return `Hello, ${name}`;
    }

## Function Return Types

TypeScript can infer return types.

    function add(a: number, b: number) {
      return a + b;
    }

You can also write them explicitly:

    function add(a: number, b: number): number {
      return a + b;
    }

## void

void means a function does not return a meaningful value.

    function logMessage(message: string): void {
      console.log(message);
    }

## Typing Arrays

Array of strings:

    const names: string[] = ["Ada", "Tunde"];

Alternative syntax:

    const names: Array<string> = ["Ada", "Tunde"];

Array of numbers:

    const scores: number[] = [10, 20, 30];

## Typing Objects

    const user: {
      name: string;
      age: number;
      email: string;
    } = {
      name: "Ada",
      age: 25,
      email: "ada@example.com"
    };

This works, but for larger objects we usually use type aliases or interfaces.

## Optional Properties

Use ? for optional properties.

    const user: {
      name: string;
      email?: string;
    } = {
      name: "Ada"
    };

email is optional.

## readonly Properties

readonly prevents reassignment of a property.

    const user: {
      readonly id: string;
      name: string;
    } = {
      id: "user_1",
      name: "Ada"
    };

    user.name = "Grace";

    user.id = "user_2";

The id reassignment causes an error.

## Array Of Objects

    const users: {
      id: string;
      name: string;
    }[] = [
      {
        id: "1",
        name: "Ada"
      },
      {
        id: "2",
        name: "Tunde"
      }
    ];

## Common Beginner Mistakes

- Forgetting parameter types.
- Over-annotating obvious return values.
- Not typing empty arrays.
- Making optional properties required accidentally.
- Confusing readonly with const.
- Writing very long inline object types everywhere.

## Exercises

1. Write a function that accepts two numbers and returns a number.
2. Write a function that logs a string and returns void.
3. Create an array of strings.
4. Create an array of numbers.
5. Create a typed user object.
6. Add an optional email property.
7. Add a readonly id property.
8. Create an array of user objects.

## Summary

TypeScript improves functions by checking inputs and outputs.

Arrays can be typed by item type.

Objects can be typed by shape.

Optional and readonly properties improve accuracy.

## References

https://www.typescriptlang.org/docs/handbook/2/everyday-types.html

https://www.typescriptlang.org/docs/handbook/2/functions.html

https://www.typescriptlang.org/docs/handbook/2/objects.html
