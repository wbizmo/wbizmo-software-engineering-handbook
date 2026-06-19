# Lesson 08 Answers

1. Incorrect JavaScript syntax.
2. Using a variable that does not exist.
3. Using a value in the wrong way.
4. Handles runtime errors.
5. Creates an error intentionally.
6. Inspecting values and flow.
7. Logs errors.
8. Error type, message, file, line number, stack trace.
9. A point where code execution pauses during debugging.
10. Errors explain what is wrong and where to investigate.

## Exercise Solution

    function divide(a, b) {
      if (b === 0) {
        throw new Error("Cannot divide by zero");
      }

      return a / b;
    }

    try {
      const result = divide(10, 0);
      console.log(result);
    } catch (error) {
      console.error(error.message);
    }

    const user = {
      name: "Ada",
      email: "ada@example.com"
    };

    console.log(user);
    console.log(user.email);
