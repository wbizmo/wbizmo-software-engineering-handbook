# Lesson 07 Cheatsheet

Promise states:

    pending
    fulfilled
    rejected

then:

    promise.then((value) => {});

catch:

    promise.catch((error) => {});

async:

    async function run() {}

await:

    const result = await promise;

try catch:

    try {
      const data = await getData();
    } catch (error) {
      console.log(error);
    }

Key takeaway:
    async and await make promise-based code cleaner.
