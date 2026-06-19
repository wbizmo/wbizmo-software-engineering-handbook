# Lesson 09 Answers: TypeScript Project Setup and Best Practices

1. npm install --save-dev typescript
2. npx tsc --init
3. TypeScript compiler behavior.
4. Enables stricter type checking.
5. Automatic recompilation.
6. It removes type safety.
7. Better maintainability.
8. dist.
9. npx tsc
10. External data can be invalid even when TypeScript compiles.

## Exercise Solution

    mkdir my-typescript-app
    cd my-typescript-app

    npm init -y

    npm install --save-dev typescript

    npx tsc --init

    mkdir src

    touch src/index.ts

Example interface:

    export interface User {
      id: string;
      email: string;
    }

Build:

    npm run build
