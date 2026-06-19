# Lesson 03 Answers

1. Database table definition.
2. Primary key.
3. Prevents duplicates.
4. Current timestamp.
5. Optional field.
6. String.
7. DateTime.
8. Boolean.
9. Model.
10. Fields.

## Exercise Solution

    model User {
      id        Int      @id @default(autoincrement())
      email     String   @unique
      name      String
      createdAt DateTime @default(now())
    }
