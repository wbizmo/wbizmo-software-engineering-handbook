# Lesson 04: Unions, Literals and Type Aliases

## Learning Objectives

By the end of this lesson, you should be able to:

- Use union types.
- Use literal types.
- Create type aliases.
- Use type aliases for objects.
- Understand when unions are useful.
- Avoid overly broad types.

## Union Types

A union type allows more than one possible type.

    let id: string | number;

    id = "user_1";
    id = 123;

This means id can be a string or a number.

## Why Unions Are Useful

Real data can sometimes have multiple valid forms.

Examples:

    string | number

    "pending" | "paid" | "failed"

    User | null

    ApiResponse | ErrorResponse

## Literal Types

A literal type allows only specific values.

    let status: "pending";

    status = "pending";

This variable can only be "pending".

## Union Of Literals

This is very common.

    let status: "pending" | "paid" | "failed";

    status = "paid";

Invalid:

    status = "unknown";

## Type Aliases

A type alias gives a name to a type.

    type UserId = string | number;

    let id: UserId = "user_1";

## Object Type Alias

    type User = {
      id: string;
      name: string;
      email: string;
    };

    const user: User = {
      id: "1",
      name: "Ada",
      email: "ada@example.com"
    };

## Reusing Type Aliases

    function sendEmail(user: User): void {
      console.log(user.email);
    }

## Status Example

    type PaymentStatus = "pending" | "paid" | "failed";

    function updatePaymentStatus(status: PaymentStatus): void {
      console.log(status);
    }

    updatePaymentStatus("paid");

## Null Unions

A value may be an object or null.

    type User = {
      id: string;
      name: string;
    };

    let selectedUser: User | null = null;

## Common Beginner Mistakes

- Using string when specific literals would be better.
- Making unions too broad.
- Forgetting to handle all union cases.
- Creating too many unnecessary aliases.
- Confusing type aliases with variables.

## Exercises

1. Create a union type for string or number ID.
2. Create a PaymentStatus type with three possible values.
3. Create a User type alias.
4. Create a function that accepts PaymentStatus.
5. Create a selectedUser variable that can be User or null.
6. Try assigning an invalid status and observe the TypeScript error.

## Summary

Unions allow multiple possible types.

Literal types restrict values to exact options.

Type aliases make types reusable and readable.

These features are heavily used in APIs, backend systems, and frontend states.

## References

https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#union-types

https://www.typescriptlang.org/docs/handbook/2/everyday-types.html#type-aliases
