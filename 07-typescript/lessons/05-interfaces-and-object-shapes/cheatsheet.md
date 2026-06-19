# Lesson 05 Cheatsheet: Interfaces and Object Shapes

Interface:

    interface User {
      id: string;
      name: string;
    }

Optional:

    email?: string;

Readonly:

    readonly id: string;

Method:

    interface Logger {
      log(message: string): void;
    }

Extends:

    interface User extends BaseEntity {
      name: string;
    }

Function input:

    function createUser(input: CreateUserInput) {}

Beginner rule:
    Interfaces for object shapes.
    Type aliases for unions and literals.

Key takeaway:
    Interfaces make object structures clear and reusable.
