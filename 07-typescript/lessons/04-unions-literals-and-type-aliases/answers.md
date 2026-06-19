# Lesson 04 Answers: Unions, Literals and Type Aliases

1. A type that allows more than one possible type.
2. The pipe symbol: |
3. A type that allows only one exact value.
4. A type that allows one of several exact values.
5. A reusable name for a type.
6. They make types reusable, readable, and easier to maintain.
7. type PaymentStatus = "pending" | "paid" | "failed";
8. The value can be a User or null.
9. It prevents invalid strings.
10. Making unions too broad or not handling all cases.

## Exercise Solution

    type Id = string | number;

    type PaymentStatus = "pending" | "paid" | "failed";

    type User = {
      id: Id;
      name: string;
      email: string;
    };

    function updatePaymentStatus(status: PaymentStatus): void {
      console.log(`Payment status: ${status}`);
    }

    let selectedUser: User | null = null;

    const user: User = {
      id: "user_1",
      name: "Ada",
      email: "ada@example.com"
    };

    selectedUser = user;

    updatePaymentStatus("paid");

    console.log(selectedUser);
