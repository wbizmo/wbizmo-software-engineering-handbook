# Lesson 04 Cheatsheet: Unions, Literals and Type Aliases

Union:

    string | number

Literal:

    "pending"

Literal union:

    type Status = "pending" | "paid" | "failed";

Type alias:

    type UserId = string | number;

Object alias:

    type User = {
      id: string;
      email: string;
    };

Nullable:

    let user: User | null = null;

Key takeaway:
    Use unions and literals to model valid states clearly.
