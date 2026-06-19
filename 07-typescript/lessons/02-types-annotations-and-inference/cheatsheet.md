# Lesson 02 Cheatsheet: Types, Annotations and Inference

string:

    const name: string = "Ada";

number:

    const age: number = 25;

boolean:

    const active: boolean = true;

Inference:

    const city = "Lagos";

any:

    let value: any = 10;

unknown:

    let value: unknown = "Hello";

Check unknown:

    if (typeof value === "string") {
      console.log(value);
    }

Key takeaway:
    Let TypeScript infer when obvious, annotate when useful.
