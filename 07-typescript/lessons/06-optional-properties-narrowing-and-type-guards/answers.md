# Lesson 06 Answers: Optional Properties, Narrowing and Type Guards

1. The property may be omitted.
2. No.
3. A type that may be null.
4. A type with multiple possible types.
5. Reducing possible types to a more specific one.
6. Narrowing primitive types.
7. Narrowing object unions.
8. A reusable function that identifies a specific type.
9. They make union handling safe and reusable.
10. Accessing null values causes errors.

## Exercise Solution

    interface User {
      id: string;
      name: string;
      phone?: string;
    }

    let selectedUser: User | null = null;

    if (selectedUser) {
      console.log(selectedUser.name);
    }

    function printValue(value: string | number) {
      if (typeof value === "string") {
        console.log(value.toUpperCase());
      } else {
        console.log(value.toFixed(2));
      }
    }

    interface Admin {
      role: string;
    }

    interface Customer {
      loyaltyPoints: number;
    }

    function isAdmin(
      account: Admin | Customer
    ): account is Admin {
      return "role" in account;
    }

    const account: Admin = {
      role: "super-admin"
    };

    if (isAdmin(account)) {
      console.log(account.role);
    }
