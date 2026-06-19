# Lesson 05 Answers: Interfaces and Object Shapes

1. An interface describes the shape of an object.
2. Objects such as users, products, orders, configs, and API responses.
3. The property is optional.
4. The property cannot be reassigned.
5. Yes.
6. It allows one interface to inherit from another.
7. Use interfaces for object shapes and type aliases for unions.
8. They clearly describe expected request and response shapes.
9. TypeScript reports an error.
10. The set of properties and property types an object should have.

## Exercise Solution

    interface BaseEntity {
      readonly id: string;
      createdAt: string;
    }

    interface User extends BaseEntity {
      name: string;
      email: string;
      phone?: string;
    }

    interface Product extends BaseEntity {
      name: string;
      price: number;
      inStock: boolean;
    }

    interface CreateUserInput {
      name: string;
      email: string;
    }

    function createUser(input: CreateUserInput): User {
      return {
        id: "user_1",
        createdAt: new Date().toISOString(),
        name: input.name,
        email: input.email
      };
    }

    const user = createUser({
      name: "Ada",
      email: "ada@example.com"
    });

    const product: Product = {
      id: "product_1",
      createdAt: new Date().toISOString(),
      name: "Keyboard",
      price: 100,
      inStock: true
    };

    console.log(user, product);
