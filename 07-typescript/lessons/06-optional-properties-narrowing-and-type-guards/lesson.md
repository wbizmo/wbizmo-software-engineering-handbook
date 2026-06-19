# Lesson 06: Optional Properties, Narrowing and Type Guards

## Learning Objectives

By the end of this lesson, you should be able to:

- Understand optional properties.
- Understand nullable values.
- Understand type narrowing.
- Use typeof checks.
- Use in checks.
- Use custom type guards.
- Safely work with union types.

## Why This Lesson Matters

Real applications rarely deal with perfect data.

Examples:

- API responses may be incomplete.
- Users may leave fields blank.
- Database records may contain nullable values.
- Different request types may have different structures.

TypeScript helps us safely handle these situations.

## Optional Properties

Optional properties use the question mark symbol.

Example:

    interface User {
      id: string;
      name: string;
      phone?: string;
    }

phone is optional.

Valid:

    const user: User = {
      id: "1",
      name: "Ada"
    };

Also valid:

    const user: User = {
      id: "1",
      name: "Ada",
      phone: "08012345678"
    };

## Optional Does Not Mean Null

Optional means the property may not exist.

Example:

    interface User {
      phone?: string;
    }

Possible:

    {}

Possible:

    {
      phone: "08012345678"
    }

Not automatically:

    {
      phone: null
    }

unless null is included in the type.

## Nullable Types

Sometimes a value may be null.

Example:

    let selectedUser: User | null = null;

This means:

- User object
- or null

Nothing else.

## Why Nullable Values Exist

Examples:

- No logged-in user.
- No selected product.
- No uploaded file.
- No payment record yet.

## Union Types Revisited

Example:

    let id: string | number;

Possible:

    "user_1"

Possible:

    123

Not possible:

    true

## The Problem

TypeScript sees:

    string | number

Which means:

    "Could be either."

Example:

    let id: string | number;

    console.log(id.toUpperCase());

Error.

Why?

Because numbers do not have:

    toUpperCase()

TypeScript requires proof.

## Type Narrowing

Type narrowing reduces possibilities.

Example:

    let id: string | number;

    if (typeof id === "string") {
      console.log(id.toUpperCase());
    }

Inside the block:

TypeScript now knows:

    id is string

This is called narrowing.

## typeof Narrowing

Common checks:

    typeof value === "string"

    typeof value === "number"

    typeof value === "boolean"

Example:

    function printValue(value: string | number) {
      if (typeof value === "string") {
        console.log(value.toUpperCase());
      } else {
        console.log(value.toFixed(2));
      }
    }

## Truthy Narrowing

Example:

    function printUser(user: User | null) {
      if (user) {
        console.log(user.name);
      }
    }

Inside:

    if (user)

TypeScript knows:

    user is not null

## The in Operator

Used for object unions.

Example:

    interface Admin {
      role: string;
    }

    interface Customer {
      loyaltyPoints: number;
    }

    type Account = Admin | Customer;

Check:

    if ("role" in account) {
      console.log(account.role);
    }

TypeScript narrows automatically.

## Example

    interface Admin {
      role: string;
    }

    interface Customer {
      loyaltyPoints: number;
    }

    function printAccount(account: Admin | Customer) {
      if ("role" in account) {
        console.log(account.role);
      } else {
        console.log(account.loyaltyPoints);
      }
    }

## Custom Type Guards

You can create reusable checks.

Example:

    interface Admin {
      role: string;
    }

    interface Customer {
      loyaltyPoints: number;
    }

    function isAdmin(
      account: Admin | Customer
    ): account is Admin {
      return "role" in account;
    }

Usage:

    if (isAdmin(account)) {
      console.log(account.role);
    }

TypeScript now knows the type.

## Why Type Guards Matter

They become extremely useful when:

- Working with APIs
- Handling request bodies
- Processing database results
- Validating external data
- Building SDKs

## API Example

Imagine:

    type ApiResponse =
      | {
          success: true;
          data: User;
        }
      | {
          success: false;
          error: string;
        };

Handle safely:

    if (response.success) {
      console.log(response.data.name);
    } else {
      console.log(response.error);
    }

TypeScript narrows automatically.

## Common Beginner Mistakes

### Mistake 1

Ignoring null.

Bad:

    user.name

Good:

    if (user) {
      console.log(user.name);
    }

### Mistake 2

Using any.

Bad:

    const user: any

Good:

    const user: User | null

### Mistake 3

Forcing values.

Bad:

    user!.name

Only use when absolutely certain.

### Mistake 4

Not narrowing union types.

Bad:

    value.toUpperCase()

Good:

    if (typeof value === "string") {
      value.toUpperCase();
    }

## Exercises

### Exercise 1

Create:

    User | null

Check before accessing properties.

### Exercise 2

Create:

    string | number

Use typeof to handle both.

### Exercise 3

Create:

    Admin | Customer

Use in operator.

### Exercise 4

Create a custom type guard.

### Exercise 5

Create a response type:

    SuccessResponse
    ErrorResponse

Handle safely.

## Summary

Optional properties may not exist.

Nullable values may be null.

Type narrowing reduces possible types.

Type guards help TypeScript understand values safely.

These concepts are heavily used in real-world TypeScript applications.

## References

https://www.typescriptlang.org/docs/handbook/2/narrowing.html

https://www.typescriptlang.org/docs/handbook/2/everyday-types.html

https://www.typescriptlang.org/docs/handbook/2/objects.html
