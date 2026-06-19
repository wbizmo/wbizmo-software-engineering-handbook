# Lesson 02 Answers: Types, Annotations and Inference

1. A type annotation explicitly declares a value's type.
2. Type inference means TypeScript figures out the type automatically.
3. string.
4. boolean.
5. number.
6. any disables type checking for that value.
7. unknown requires type checks before use.
8. Because TypeScript often cannot infer parameter types from function declarations alone.
9. Yes.
10. It removes much of TypeScript's safety.

## Exercise Solution

    const username: string = "Williams";
    const age: number = 25;
    const isLearning: boolean = true;

    const city = "Lagos";

    let looseValue: any = "Hello";
    looseValue = 123;
    looseValue = false;

    let safeValue: unknown = "TypeScript";

    if (typeof safeValue === "string") {
      console.log(safeValue.toUpperCase());
    }

    const score: number = 100;

    console.log(username, age, isLearning, city, looseValue, score);
