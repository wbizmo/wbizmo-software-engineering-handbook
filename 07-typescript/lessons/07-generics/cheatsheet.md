# Lesson 07 Cheatsheet: Generics

Generic function:

    function getFirst<T>(
      items: T[]
    ): T {
      return items[0];
    }

Multiple generics:

    function pair<T, U>(
      first: T,
      second: U
    ) {}

Generic alias:

    type ApiResponse<T> = {
      success: boolean;
      data: T;
    };

Generic interface:

    interface Repository<T> {
      getById(
        id: string
      ): T | null;
    }

Constraint:

    function printId<
      T extends {
        id: string;
      }
    >(item: T) {}

Key takeaway:
    Generics allow reusable code without sacrificing type safety.
