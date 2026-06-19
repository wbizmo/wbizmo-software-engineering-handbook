# Lesson 08 Cheatsheet: TypeScript With DOM and APIs

Element:

    HTMLElement | null

Input:

    HTMLInputElement

Button:

    HTMLButtonElement

Check:

    if (button) {}

Optional chaining:

    button?.click()

Assertion:

    as HTMLInputElement

Fetch:

    const response =
      await fetch(url);

Typed response:

    const result:
      ApiResponse<User[]>

Generic API:

    type ApiResponse<T> = {
      success: boolean;
      data: T;
    };

Key takeaway:
    Type your DOM elements and API responses.
