# Lesson 08: TypeScript With DOM and APIs

## Learning Objectives

By the end of this lesson, you should be able to:

- Use TypeScript with DOM elements.
- Safely select HTML elements.
- Handle nullable DOM values.
- Type browser events.
- Work with fetch.
- Type API responses.
- Create reusable API response types.

## Why This Matters

Most frontend applications interact with:

- HTML elements
- Forms
- Buttons
- Inputs
- APIs
- JSON responses

TypeScript helps make these interactions safer.

## DOM Elements In TypeScript

HTML:

    <button id="saveBtn">
      Save
    </button>

TypeScript:

    const button =
      document.getElementById(
        "saveBtn"
      );

Problem:

TypeScript sees:

    HTMLElement | null

Why?

Because the element might not exist.

## Null Safety

Bad:

    button.addEventListener(
      "click",
      () => {}
    );

TypeScript error.

Because:

    button

might be null.

Safe:

    if (button) {
      button.addEventListener(
        "click",
        () => {
          console.log("Saved");
        }
      );
    }

## Type Assertions

Sometimes you know the type.

Example:

    const button =
      document.getElementById(
        "saveBtn"
      ) as HTMLButtonElement;

Now TypeScript understands:

    HTMLButtonElement

Use carefully.

Only when certain.

## Input Elements

HTML:

    <input
      id="email"
      type="email"
    />

TypeScript:

    const emailInput =
      document.getElementById(
        "email"
      ) as HTMLInputElement;

    console.log(
      emailInput.value
    );

## querySelector

Example:

    const button =
      document.querySelector(
        "#saveBtn"
      );

Type:

    Element | null

Often narrowed or asserted.

## Event Types

Example:

    button?.addEventListener(
      "click",
      (event) => {
        console.log(event);
      }
    );

TypeScript infers:

    MouseEvent

## Form Submit Events

Example:

    const form =
      document.querySelector(
        "form"
      );

    form?.addEventListener(
      "submit",
      (event) => {
        event.preventDefault();
      }
    );

Type:

    SubmitEvent

## Optional Chaining

Example:

    button?.addEventListener(
      "click",
      () => {}
    );

Meaning:

Run only if button exists.

## Working With APIs

Example:

    fetch("/users");

But TypeScript doesn't know the response structure.

We should define it.

## User Type

Example:

    type User = {
      id: string;
      name: string;
      email: string;
    };

## Typed API Response

Example:

    type ApiResponse<T> = {
      success: boolean;
      data: T;
    };

## Fetch Example

    async function getUsers() {
      const response =
        await fetch("/users");

      const data:
        ApiResponse<User[]> =
          await response.json();

      return data;
    }

Now TypeScript knows:

    data.data

contains:

    User[]

## Looping Through Typed Data

    const result =
      await getUsers();

    result.data.forEach(
      (user) => {
        console.log(
          user.email
        );
      }
    );

Autocomplete works.

Type checking works.

## Error Responses

Example:

    type Success<T> = {
      success: true;
      data: T;
    };

    type Failure = {
      success: false;
      error: string;
    };

    type Response<T> =
      Success<T> | Failure;

Handle safely:

    if (response.success) {
      console.log(
        response.data
      );
    } else {
      console.log(
        response.error
      );
    }

## Real Backend Example

Fastify route:

    GET /users

Response:

    {
      success: true,
      data: [...]
    }

Frontend:

    type User = {
      id: string;
      email: string;
    };

    type ApiResponse<T> = {
      success: boolean;
      data: T;
    };

Shared types make frontend and backend safer.

## Common Beginner Mistakes

### Mistake 1

Ignoring null.

Bad:

    button.addEventListener()

Good:

    if (button)

### Mistake 2

Using any.

Bad:

    const data: any

### Mistake 3

Trusting API responses blindly.

### Mistake 4

Using type assertions everywhere.

### Mistake 5

Not typing fetch results.

## Exercises

### Exercise 1

Create a typed button element.

### Exercise 2

Create a typed input element.

### Exercise 3

Create a click handler.

### Exercise 4

Create a User type.

### Exercise 5

Create:

    ApiResponse<User[]>

### Exercise 6

Fetch and display users.

### Exercise 7

Handle success and failure responses.

## Summary

DOM elements may be null.

TypeScript helps safely access them.

API responses should be typed.

Typed APIs improve reliability and autocomplete.

## References

https://www.typescriptlang.org/docs/handbook/dom-manipulation.html

https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API

https://www.typescriptlang.org/docs/handbook/2/narrowing.html
