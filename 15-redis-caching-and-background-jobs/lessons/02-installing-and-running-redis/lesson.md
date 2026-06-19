# Lesson 02: Installing And Running Redis

## Learning Objectives

By the end of this lesson you should be able to:

- Install Redis.
- Run Redis locally.
- Verify Redis operation.
- Connect to Redis.
- Use Redis CLI.

## Docker Installation

Run:

    docker run \
      --name redis \
      -p 6379:6379 \
      redis:8

## Verify Container

    docker ps

## Redis CLI

Enter:

    docker exec -it redis redis-cli

## Test Redis

    PING

Expected:

    PONG

## Set Value

    SET username ada

## Get Value

    GET username

Result:

    "ada"

## Delete Value

    DEL username

## Redis Port

Default:

    6379

## Node.js Client

Install:

    npm install redis

## Connection Example

    import { createClient }
      from "redis";

    const client =
      createClient();

    await client.connect();

## Exercises

1. Start Redis.
2. Run redis-cli.
3. Set value.
4. Get value.
5. Delete value.

## Summary

Redis is easy to install and interact with.

## References

https://redis.io/docs
