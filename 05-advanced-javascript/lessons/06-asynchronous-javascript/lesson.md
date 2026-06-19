# Lesson 06: Asynchronous JavaScript

## Learning Objectives

By the end of this lesson, you should understand synchronous code, asynchronous code, timers, the event loop at a beginner level, and why async behavior matters.

## Synchronous Code

Synchronous code runs line by line.

    console.log("One");
    console.log("Two");
    console.log("Three");

Output:

    One
    Two
    Three

## Asynchronous Code

Asynchronous code allows some tasks to happen later.

Example:

    console.log("Start");

    setTimeout(() => {
      console.log("Later");
    }, 1000);

    console.log("End");

Output:

    Start
    End
    Later

## Why Async Exists

Some tasks take time:

- API requests
- Database calls
- File uploads
- Timers
- Reading files
- Network operations

JavaScript should not freeze while waiting.

## setTimeout

Runs code after a delay.

    setTimeout(() => {
      console.log("Runs after 1 second");
    }, 1000);

## setInterval

Runs code repeatedly.

    setInterval(() => {
      console.log("Repeats");
    }, 1000);

Use carefully.

## The Event Loop

The event loop helps JavaScript handle asynchronous tasks.

Simple explanation:

JavaScript runs normal code first, then handles completed async tasks later.

## Common Mistakes

- Expecting async code to run immediately.
- Not understanding order of output.
- Creating intervals that never stop.
- Trying to return async results like normal synchronous values.

## Exercises

1. Print Start, End, then Later using setTimeout.
2. Create a timer that logs after 2 seconds.
3. Create an interval that logs every second.
4. Explain why async is needed for API requests.
5. Predict output order for async code.

## Summary

Synchronous code runs line by line.

Asynchronous code allows delayed tasks.

JavaScript uses async behavior for timers, APIs, and other slow operations.

## References

- https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Asynchronous
- https://developer.mozilla.org/en-US/docs/Web/API/setTimeout
- https://developer.mozilla.org/en-US/docs/Web/API/setInterval
