# Lesson 07: Promises, Async and Await

## Learning Objectives

By the end of this lesson, you should understand promises, then, catch, async functions, await, and how to handle asynchronous results.

## What Is A Promise?

A promise represents a value that may be available now, later, or never.

A promise can be:

- pending
- fulfilled
- rejected

## Basic Promise

    const promise = new Promise((resolve, reject) => {
      resolve("Success");
    });

## then

then handles success.

    promise.then((value) => {
      console.log(value);
    });

## catch

catch handles failure.

    promise.catch((error) => {
      console.log(error);
    });

## Promise With Delay

    const wait = new Promise((resolve) => {
      setTimeout(() => {
        resolve("Done");
      }, 1000);
    });

    wait.then((message) => {
      console.log(message);
    });

## async Function

An async function always returns a promise.

    async function getData() {
      return "Data";
    }

## await

await waits for a promise to settle.

    async function run() {
      const result = await getData();
      console.log(result);
    }

    run();

await can only be used inside async functions in most beginner contexts.

## try...catch With async

    async function run() {
      try {
        const result = await getData();
        console.log(result);
      } catch (error) {
        console.log(error);
      }
    }

## Common Mistakes

- Forgetting await.
- Using await outside async.
- Not handling errors.
- Thinking async removes waiting completely.
- Forgetting async functions return promises.

## Exercises

1. Create a promise that resolves with Hello.
2. Handle the promise with then.
3. Create a promise that rejects.
4. Handle error with catch.
5. Create an async function.
6. Use await inside async.
7. Use try...catch.

## Summary

Promises represent future results.

then handles success.

catch handles errors.

async and await make asynchronous code easier to read.

## References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await
