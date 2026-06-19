# Lesson 06 Answers

1. Code that runs line by line.
2. Code that allows tasks to complete later.
3. To avoid freezing while waiting for slow tasks.
4. Runs code after a delay.
5. Runs code repeatedly after intervals.
6. A mechanism that helps JavaScript handle async tasks.
7. Normal code usually runs first.
8. API requests, timers, file uploads.
9. Network requests take time.
10. Expecting async code to behave like sync code.

## Exercise Solution

    console.log("Start");

    setTimeout(() => {
      console.log("Later");
    }, 1000);

    console.log("End");

    setTimeout(() => {
      console.log("Two seconds passed");
    }, 2000);

    const intervalId = setInterval(() => {
      console.log("Repeating");
    }, 1000);

    setTimeout(() => {
      clearInterval(intervalId);
      console.log("Interval stopped");
    }, 5000);
