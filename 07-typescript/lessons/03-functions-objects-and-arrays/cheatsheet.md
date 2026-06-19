# Lesson 03 Cheatsheet: Functions, Objects and Arrays

Function:

    function greet(name: string): string {
      return `Hello, ${name}`;
    }

void:

    function log(message: string): void {
      console.log(message);
    }

String array:

    const names: string[] = [];

Number array:

    const scores: number[] = [];

Object:

    const user: {
      name: string;
      age: number;
    } = {
      name: "Ada",
      age: 25
    };

Optional:

    email?: string;

Readonly:

    readonly id: string;

Array of objects:

    const users: { id: string; name: string }[] = [];

Key takeaway:
    Type functions, arrays, and objects to prevent data mistakes.
