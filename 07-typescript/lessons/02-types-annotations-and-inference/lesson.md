# Lesson 02: Types, Annotations and Inference

## Learning Objectives

By the end of this lesson, you should be able to:

- Understand primitive types.
- Add type annotations.
- Understand type inference.
- Use string, number, boolean, null, and undefined.
- Understand any and unknown.
- Avoid unnecessary annotations.

## Primitive Types

Common TypeScript primitive types:

    string
    number
    boolean
    null
    undefined

## string

Used for text.

    const name: string = "Ada";

## number

Used for integers and decimals.

    const age: number = 25;
    const price: number = 19.99;

## boolean

Used for true or false.

    const isLoggedIn: boolean = true;

## null

Represents intentional empty value.

    const selectedUser: null = null;

## undefined

Represents a value that has not been assigned.

    let email: undefined = undefined;

## Type Annotations

A type annotation explicitly tells TypeScript the type.

    const username: string = "Williams";

Annotation:

    : string

## Type Inference

TypeScript can often figure out the type automatically.

    const username = "Williams";

TypeScript infers:

    string

You do not always need to write the type.

## When To Use Annotations

Use annotations when:

- Function parameters need types.
- Empty arrays need types.
- Object shapes need clarity.
- Variables may have multiple possible types.
- Public APIs need documentation.

## any

any disables type checking for a value.

    let value: any = "Hello";

    value = 42;
    value = true;

Use any carefully.

It weakens TypeScript.

## unknown

unknown is safer than any.

    let value: unknown = "Hello";

Before using unknown, you must check its type.

    if (typeof value === "string") {
      console.log(value.toUpperCase());
    }

## Type Errors

Example:

    const age: number = "25";

TypeScript reports an error because string is not assignable to number.

## Common Beginner Mistakes

- Adding annotations everywhere.
- Using any to silence errors.
- Thinking inferred types are weaker.
- Forgetting that TypeScript checks before runtime.
- Confusing unknown and any.

## Exercises

1. Create a string variable.
2. Create a number variable.
3. Create a boolean variable.
4. Let TypeScript infer a string.
5. Create a variable with any and assign different types.
6. Create a variable with unknown and safely check it.
7. Fix a type error.

## Summary

Type annotations explicitly declare types.

Type inference allows TypeScript to detect types automatically.

any disables safety.

unknown is safer because it requires checks.

## References

https://www.typescriptlang.org/docs/handbook/2/everyday-types.html

https://www.typescriptlang.org/docs/handbook/type-inference.html
