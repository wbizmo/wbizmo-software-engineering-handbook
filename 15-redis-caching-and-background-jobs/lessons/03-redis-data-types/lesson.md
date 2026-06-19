# Lesson 03: Redis Data Types

## Learning Objectives

By the end of this lesson you should be able to:

- Understand Redis data types.
- Use strings.
- Use lists.
- Use sets.
- Use hashes.

## Strings

Most common type.

Set:

    SET username ada

Get:

    GET username

## Lists

Create:

    LPUSH queue job1

    LPUSH queue job2

Read:

    LRANGE queue 0 -1

Useful for queues.

## Sets

Add:

    SADD users ada

    SADD users john

Read:

    SMEMBERS users

Useful for unique values.

## Hashes

Create:

    HSET user:1 \
      name Ada \
      role admin

Read:

    HGETALL user:1

Useful for objects.

## Expiration

Set TTL:

    SET token abc EX 60

Expires after:

    60 seconds

## Real World Usage

Strings:
    Cache

Lists:
    Queues

Sets:
    Unique collections

Hashes:
    User objects

## Exercises

1. Create string.
2. Create list.
3. Create set.
4. Create hash.
5. Create expiring value.

## Summary

Redis offers multiple data structures optimized for different use cases.

## References

https://redis.io/docs/latest/develop/data-types/
