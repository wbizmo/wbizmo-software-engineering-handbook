# Lesson 07 Answers: Generics

1. A reusable type parameter.
2. To create reusable type-safe code.
3. A type variable.
4. A function that works with multiple types.
5. Yes.
6. An interface that accepts type parameters.
7. A type alias that accepts type parameters.
8. It adds constraints.
9. APIs often return different data shapes using the same response structure.
10. Generics preserve type information while any removes it.

## Exercise Solution

    function getLast<T>(
      items: T[]
    ): T {
      return items[
        items.length - 1
      ];
    }

    function pair<T, U>(
      first: T,
      second: U
    ) {
      return {
        first,
        second
      };
    }

    type ApiResponse<T> = {
      success: boolean;
      data: T;
    };

    interface Repository<T> {
      getAll(): T[];
      getById(
        id: string
      ): T | null;
    }

    function printId<
      T extends {
        id: string;
      }
    >(item: T) {
      console.log(item.id);
    }

    const name =
      getLast([
        "Ada",
        "Tunde"
      ]);

    const result =
      pair(
        "Williams",
        25
      );

    printId({
      id: "user_1",
      name: "Ada"
    });

    console.log(
      name,
      result
    );
