# Lesson 06 Cheatsheet: Optional Properties, Narrowing and Type Guards

Optional property:

    phone?: string

Nullable:

    User | null

Union:

    string | number

typeof:

    if (typeof value === "string") {
      console.log(value);
    }

Truthy check:

    if (user) {
      console.log(user.name);
    }

in operator:

    if ("role" in account) {
      console.log(account.role);
    }

Custom guard:

    function isAdmin(
      account: Admin | Customer
    ): account is Admin {
      return "role" in account;
    }

Key takeaway:
    Narrow values before using them.
