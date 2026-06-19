# Lesson 01: Introduction To Redis

## Learning Objectives

By the end of this lesson you should be able to:

- Explain Redis.
- Understand in-memory databases.
- Explain common Redis use cases.
- Understand performance benefits.
- Understand where Redis fits in backend systems.

## What Is Redis?

Redis stands for:

    Remote Dictionary Server

Redis is an in-memory data store.

Unlike PostgreSQL:

Redis primarily stores data in memory.

This makes Redis extremely fast.

## Why Redis Is Fast

Database:

Disk Access

↓

Milliseconds

Redis:

Memory Access

↓

Microseconds

or

Very low milliseconds

## Common Redis Use Cases

- Caching
- Sessions
- Rate Limiting
- Queues
- Pub/Sub
- Real-time systems

## Example Architecture

Client

↓

API

↓

Redis Cache

↓

PostgreSQL

If cache exists:

Database avoided.

## Why Companies Use Redis

Benefits:

- Speed
- Scalability
- Reduced DB load
- Simplicity

## Portfolio Examples

SyncGrid:

Queue processing.

VaultBox:

Caching.

inFlowForge:

Workflow queues.

Argus:

State tracking.

NOMMO:

Distributed coordination.

## When Not To Use Redis

Avoid Redis for:

- Permanent primary storage
- Large relational queries
- Complex reporting

Use PostgreSQL for those.

## Exercises

1. Define Redis.
2. Explain in-memory storage.
3. List Redis use cases.
4. Compare Redis and PostgreSQL.
5. Explain why Redis is fast.

## Summary

Redis is one of the most important backend infrastructure technologies.

## References

https://redis.io
