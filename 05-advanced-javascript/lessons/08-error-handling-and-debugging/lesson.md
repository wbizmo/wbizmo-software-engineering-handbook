# Lesson 08: Error Handling and Debugging

## Learning Objectives

By the end of this lesson, you should understand common JavaScript errors, try...catch, throwing errors, debugging with console, and reading error messages.

## Why Errors Happen

Errors happen when code cannot run correctly.

Common causes:

- Misspelled variables
- Invalid syntax
- Wrong data type
- Missing DOM element
- Failed network request
- Logic mistakes

## Syntax Error

A syntax error means JavaScript code is written incorrectly.

Example:

    if (true {
      console.log("Broken");
    }

## Reference Error

A reference error happens when a variable does not exist.

    console.log(username);

## Type Error

A type error happens when a value is used in the wrong way.

    const name = null;

    console.log(name.length);

## try...catch

try...catch handles runtime errors.

    try {
      const result = riskyTask();
      console.log(result);
    } catch (error) {
      console.log(error.message);
    }

## throw

You can throw your own errors.

    function divide(a, b) {
      if (b === 0) {
        throw new Error("Cannot divide by zero");
      }

      return a / b;
    }

## Debugging With console.log

console.log helps inspect values.

    console.log(user);
    console.log(user.email);

## console.error

    console.error("Something went wrong");

## Reading Error Messages

Good developers read error messages carefully.

Look for:

- Error type
- Error message
- File name
- Line number
- Stack trace

## Browser Debugger

Browser developer tools include debugging features.

You can:

- Set breakpoints
- Step through code
- Inspect variables
- Watch expressions

## Common Mistakes

- Ignoring error messages.
- Deleting code randomly.
- Not checking line numbers.
- Using try...catch to hide bugs.
- Not validating input.
- Not handling async errors.

## Exercises

1. Create and fix a syntax error.
2. Create and fix a reference error.
3. Create and fix a type error.
4. Write a divide function that throws on zero.
5. Use try...catch around divide.
6. Use console.log to inspect values.
7. Read an error message and identify line number.

## Summary

Errors are normal.

Debugging is part of programming.

Read error messages carefully.

Use try...catch for recoverable errors.

Use console and debugger tools to understand code behavior.

## References

- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/try...catch
- https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error
- https://developer.chrome.com/docs/devtools/javascript
