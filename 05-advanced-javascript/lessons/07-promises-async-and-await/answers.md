# Lesson 07 Answers

1. A promise represents a future result.
2. pending, fulfilled, rejected.
3. Success.
4. Errors or rejection.
5. Creates an async function that returns a promise.
6. Waits for a promise to settle.
7. Usually no, it should be inside async functions.
8. To handle errors.
9. A promise.
10. They make async code easier to read.

## Exercise Solution

    const successPromise = new Promise((resolve) => {
      resolve("Hello");
    });

    successPromise.then((value) => {
      console.log(value);
    });

    const failPromise = new Promise((resolve, reject) => {
      reject("Something went wrong");
    });

    failPromise.catch((error) => {
      console.log(error);
    });

    async function getMessage() {
      return "Async Hello";
    }

    async function run() {
      try {
        const message = await getMessage();
        console.log(message);
      } catch (error) {
        console.log(error);
      }
    }

    run();
