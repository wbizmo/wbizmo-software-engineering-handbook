# Lesson 09: TypeScript Project Setup and Best Practices

## Learning Objectives

By the end of this lesson, you should be able to:

- Set up a TypeScript project.
- Install TypeScript correctly.
- Understand tsconfig.json.
- Understand build workflows.
- Organize TypeScript projects.
- Follow TypeScript best practices.
- Avoid common mistakes.

## Installing TypeScript

Create project:

    mkdir my-typescript-app

Enter project:

    cd my-typescript-app

Initialize package:

    npm init -y

Install TypeScript:

    npm install --save-dev typescript

Verify:

    npx tsc --version

## Creating tsconfig.json

Generate configuration:

    npx tsc --init

This creates:

    tsconfig.json

## What Is tsconfig.json?

This file controls how TypeScript behaves.

Examples:

- Compilation rules
- Strict mode
- Output folder
- Module system
- Target JavaScript version

## Example Configuration

    {
      "compilerOptions": {
        "target": "ES2022",
        "module": "NodeNext",
        "strict": true,
        "outDir": "dist",
        "rootDir": "src"
      }
    }

## Recommended Project Structure

    project/
    ├── src/
    │   ├── index.ts
    │   ├── types/
    │   ├── services/
    │   ├── utils/
    │   └── models/
    ├── dist/
    ├── package.json
    ├── tsconfig.json
    └── README.md

## Compilation

Compile project:

    npx tsc

Output:

    dist/

## Watch Mode

Automatically recompile:

    npx tsc --watch

Useful during development.

## Scripts

package.json:

    {
      "scripts": {
        "build": "tsc",
        "dev": "tsc --watch"
      }
    }

Run:

    npm run build

## Strict Mode

One of the most important settings.

Enable:

    "strict": true

Benefits:

- Better safety
- Better autocomplete
- Fewer bugs
- Better maintainability

Always use strict mode.

## Organizing Types

Bad:

Everything in one file.

Good:

    src/types/user.ts

Example:

    export interface User {
      id: string;
      email: string;
    }

## Avoid Excessive any

Bad:

    const user: any

Good:

    const user: User

Use:

- interfaces
- type aliases
- generics

instead of any.

## Use Meaningful Names

Bad:

    type X = {}

Good:

    type PaymentStatus = ...

Bad:

    interface A {}

Good:

    interface User {}

## Prefer Reusable Types

Bad:

    const user: {
      id: string;
      name: string;
      email: string;
    }

Good:

    interface User {
      id: string;
      name: string;
      email: string;
    }

## Validate External Data

TypeScript only checks at compile time.

API responses can still be wrong.

Validate external data whenever possible.

Libraries:

- Zod
- Valibot
- Yup

## Common Beginner Mistakes

### Mistake 1

Using any everywhere.

### Mistake 2

Ignoring compiler warnings.

### Mistake 3

Turning strict mode off.

### Mistake 4

Keeping everything in one file.

### Mistake 5

Using assertions unnecessarily.

### Mistake 6

Not learning JavaScript first.

## Professional Practices

- Use strict mode.
- Use interfaces.
- Use type aliases.
- Use generics.
- Organize types.
- Avoid any.
- Write reusable code.
- Document APIs.
- Keep types close to domain models.

## Exercises

1. Create a TypeScript project.
2. Generate tsconfig.json.
3. Enable strict mode.
4. Create src/index.ts.
5. Create a User interface.
6. Create a build script.
7. Compile project.
8. Create a reusable type alias.

## Summary

TypeScript projects require proper setup.

Strict mode should almost always be enabled.

Types should be organized and reusable.

Good structure makes projects easier to maintain.

## References

https://www.typescriptlang.org/docs/

https://www.typescriptlang.org/tsconfig

https://www.typescriptlang.org/docs/handbook/project-references.html
