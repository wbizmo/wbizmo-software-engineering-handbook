# Lesson 09 Answers

1. JSON means JavaScript Object Notation.
2. JSON is used to exchange data.
3. JSON is a data format with double-quoted keys. JavaScript objects are actual JS values.
4. Converts JavaScript value to JSON string.
5. Converts JSON string to JavaScript value.
6. Application Programming Interface.
7. Sends HTTP requests.
8. Parses response body as JSON.
9. It tells the server what type of data is being sent.
10. To prevent crashes and handle failed requests gracefully.

## Exercise Solution

    const user = {
      name: "Ada",
      age: 25,
      isDeveloper: true
    };

    const json = JSON.stringify(user);
    console.log(json);

    const parsed = JSON.parse(json);
    console.log(parsed);

    async function getUsers() {
      try {
        const response = await fetch("https://jsonplaceholder.typicode.com/users");

        if (!response.ok) {
          throw new Error("Request failed");
        }

        const users = await response.json();

        users.forEach((user) => {
          console.log(user.name);
        });
      } catch (error) {
        console.error(error.message);
      }
    }

    getUsers();

    async function createPost() {
      try {
        const response = await fetch("https://jsonplaceholder.typicode.com/posts", {
          method: "POST",
          headers: {
            "Content-Type": "application/json"
          },
          body: JSON.stringify({
            title: "Hello",
            body: "Learning APIs",
            userId: 1
          })
        });

        if (!response.ok) {
          throw new Error("Create request failed");
        }

        const data = await response.json();
        console.log(data);
      } catch (error) {
        console.error(error.message);
      }
    }

    createPost();
