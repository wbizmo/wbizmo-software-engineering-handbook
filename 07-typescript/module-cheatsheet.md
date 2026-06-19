# TypeScript Module Cheatsheet

Primitive Types:
    string
    number
    boolean

Union:
    string | number

Type Alias:
    type UserId = string | number

Interface:
    interface User {}

Generic:
    function getFirst<T>()

Nullable:
    User | null

Optional:
    email?: string

Readonly:
    readonly id: string

Compile:
    npx tsc

Initialize:
    npx tsc --init

Strict:
    "strict": true
