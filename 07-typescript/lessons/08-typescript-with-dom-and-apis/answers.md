# Lesson 08 Answers: TypeScript With DOM and APIs

1. The element might not exist.
2. HTMLElement | null.
3. A way to tell TypeScript a more specific type.
4. Safe access using ?.
5. Because they may be null.
6. To improve safety and autocomplete.
7. Reusable API response typing.
8. It preserves structure and type checking.
9. Prevents default browser behavior.
10. It reduces mismatches and bugs.

## Exercise Solution

    type User = {
      id: string;
      name: string;
      email: string;
    };

    type ApiResponse<T> = {
      success: boolean;
      data: T;
    };

    const button =
      document.getElementById(
        "saveBtn"
      ) as HTMLButtonElement;

    const emailInput =
      document.getElementById(
        "email"
      ) as HTMLInputElement;

    button?.addEventListener(
      "click",
      () => {
        console.log(
          emailInput.value
        );
      }
    );

    async function getUsers() {
      const response =
        await fetch("/users");

      const result:
        ApiResponse<User[]> =
          await response.json();

      return result;
    }
