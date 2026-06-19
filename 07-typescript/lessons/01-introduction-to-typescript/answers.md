# Lesson 01 Answers: Introduction To TypeScript

1. TypeScript is JavaScript with static typing.
2. TypeScript is built on JavaScript.
3. Static typing means types are checked before the program runs.
4. No. TypeScript compiles to JavaScript.
5. .ts.
6. It checks TypeScript and converts it to JavaScript.
7. It catches errors early and makes large codebases easier to maintain.
8. React, Node.js APIs, Fastify apps, CLI tools, SDKs.
9. It removes much of TypeScript's safety.
10. TypeScript builds on JavaScript, so JavaScript fundamentals are required.

## Exercise Solution

    function greet(name: string) {
      return "Hello, " + name;
    }

    const age: number = 25;

    type User = {
      id: string;
      email: string;
      role: string;
    };

    const user: User = {
      id: "user_1",
      email: "ada@example.com",
      role: "admin"
    };

    console.log(greet(user.email));
    console.log(age);
