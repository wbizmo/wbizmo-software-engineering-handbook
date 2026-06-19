# Lesson 09 Cheatsheet

JSON:
    JavaScript Object Notation.

Stringify:

    JSON.stringify(value)

Parse:

    JSON.parse(json)

GET:

    const response = await fetch(url);
    const data = await response.json();

POST:

    await fetch(url, {
      method: "POST",
      headers: {
        "Content-Type": "application/json"
      },
      body: JSON.stringify(data)
    });

Check response:

    if (!response.ok) {
      throw new Error("Request failed");
    }

Key takeaway:
    JSON and fetch connect frontend JavaScript to APIs.
