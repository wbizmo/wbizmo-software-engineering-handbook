# Lesson 03 Answers: Functions, Objects and Arrays

1. To ensure callers pass correct values.
2. The type of value a function returns.
3. The function returns no meaningful value.
4. string[].
5. number[].
6. The expected properties and property types of an object.
7. The property is optional.
8. It prevents reassignment of a property.
9. Use object type followed by [].
10. They reduce readability and are hard to reuse.

## Exercise Solution

    function add(a: number, b: number): number {
      return a + b;
    }

    function logMessage(message: string): void {
      console.log(message);
    }

    const names: string[] = ["Ada", "Tunde", "Williams"];
    const scores: number[] = [80, 90, 100];

    const user: {
      readonly id: string;
      name: string;
      email?: string;
    } = {
      id: "user_1",
      name: "Ada"
    };

    const users: {
      id: string;
      name: string;
      email?: string;
    }[] = [
      {
        id: "1",
        name: "Ada",
        email: "ada@example.com"
      },
      {
        id: "2",
        name: "Tunde"
      }
    ];

    console.log(add(2, 3));
    logMessage(user.name);
    console.log(names, scores, users);
