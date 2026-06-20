# Lesson 05: Caching In Distributed Systems

## Learning Objectives

By the end of this lesson you should be able to:

- Explain why distributed systems use caches.
- Design cache architectures.
- Understand cache-aside patterns.
- Understand write-through and write-behind caching.
- Handle cache invalidation.
- Prevent cache stampedes.
- Understand hot keys.
- Design scalable Redis-backed caching systems.

---

## Introduction

Caching is one of the most powerful tools available to engineers.

A well-designed cache can:

- reduce latency
- reduce database load
- reduce infrastructure costs
- improve scalability

Many systems become dramatically faster after introducing caching.

However:

Caching is easy to add.

Caching correctly is difficult.

---

## Why Caches Exist

Without cache:

        User
          |
          v
         API
          |
          v
      PostgreSQL

Every request hits the database.

If:

    10,000 users

request the same data,

the database processes the same query repeatedly.

This wastes resources.

---

## Adding A Cache

Architecture:

        User
          |
          v
         API
          |
          v
        Redis
          |
          v
      PostgreSQL

Flow:

1. Check cache
2. Return if found
3. Query database if missing
4. Store result in cache
5. Return result

---

## Cache Hits

Cache hit:

Requested data already exists.

Example:

    GET user:123

Redis contains:

    user:123

Result:

Database never touched.

Fast response.

---

## Cache Misses

Cache miss:

Requested data not found.

Flow:

Request

↓

Redis

↓

Miss

↓

Database

↓

Store in Redis

↓

Return response

Misses are slower than hits.

---

## Cache Hit Ratio

One of the most important cache metrics.

Formula:

    Hits / Total Requests

Example:

    950 hits

    1000 requests

Hit ratio:

    95%

Higher hit ratios generally mean better cache effectiveness.

---

## What Should Be Cached?

Good candidates:

- user profiles
- product catalogs
- pricing plans
- feature flags
- settings
- workflow definitions
- provider configurations

Poor candidates:

- highly volatile data
- frequently changing counters
- sensitive temporary state

---

## Cache-Aside Pattern

Most common caching strategy.

Architecture:

Application

↓

Cache

↓

Database

Flow:

1. Check cache
2. Cache miss
3. Query DB
4. Store cache
5. Return result

Example:

    const cached =
      await redis.get(key);

    if (cached) {
      return JSON.parse(cached);
    }

    const user =
      await db.user.findUnique();

    await redis.set(
      key,
      JSON.stringify(user)
    );

    return user;

Benefits:

- simple
- flexible
- widely adopted

---

## Write-Through Cache

Write operation:

Application

↓

Database

↓

Cache

Both updated immediately.

Benefits:

- cache always fresh

Drawbacks:

- slower writes
- more complexity

---

## Write-Behind Cache

Write operation:

Application

↓

Cache

↓

Database later

Benefits:

- fast writes

Risks:

- data loss
- synchronization issues

Usually used carefully in specialized systems.

---

## Cache Invalidation

One of the hardest problems in software engineering.

Problem:

User updates profile.

Database changes.

Cache still contains old profile.

Result:

Stale data.

---

## Cache Invalidation Strategies

### TTL

Example:

    EX 300

Cache expires after:

    5 minutes

Simple.

Popular.

---

### Explicit Deletion

Update:

    user:123

Then:

    DEL user:123

Next request rebuilds cache.

---

### Event Driven Invalidation

User Updated

↓

Event Published

↓

Cache Service Receives Event

↓

Cache Cleared

Useful in large distributed systems.

---

## Distributed Cache Architecture

Single Redis:

        API
          |
          v
        Redis

Works initially.

As scale grows:

      API Cluster
            |
     ----------------
     |              |
     v              v
 Redis Node 1   Redis Node 2

Further scaling:

Redis Cluster

Used in larger systems.

---

## Hot Keys

A hot key is a cache key receiving enormous traffic.

Example:

    homepage

Millions of requests.

Problems:

- Redis overload
- uneven traffic distribution

Solutions:

- replication
- local caching
- key sharding

---

## Cache Stampede

One of the most common cache failures.

Scenario:

Popular key expires.

Thousands of requests arrive simultaneously.

All requests hit database.

Architecture:

Request

↓

Cache Miss

↓

Database

↓

Database Overload

This is a cache stampede.

---

## Preventing Cache Stampedes

### Early Refresh

Refresh before expiration.

### Request Coalescing

One request rebuilds cache.

Others wait.

### Distributed Locks

Example:

    lock:user:123

Only one request regenerates data.

---

## Cache Warming

Cache warming preloads common data.

Example:

Application startup:

Load:

- plans
- settings
- providers

Into Redis.

Benefits:

- fewer cold starts
- faster early requests

---

## Local Cache vs Distributed Cache

### Local Cache

Stored inside application memory.

Example:

    Map()

Benefits:

- extremely fast

Problems:

- inconsistent across servers

---

### Distributed Cache

Redis.

Benefits:

- shared cache

Problems:

- network overhead

Most production systems use both.

---

## Multi-Level Caching

Architecture:

Request

↓

Local Cache

↓

Redis

↓

Database

Benefits:

- lower latency
- lower Redis traffic
- lower DB traffic

Used heavily at scale.

---

## Cache Consistency

Question:

Should cache always match database?

Strong consistency:

Always correct.

Higher complexity.

Eventual consistency:

May be briefly stale.

Simpler.

More scalable.

Many systems accept eventual consistency.

---

## Redis Memory Management

Redis stores data in memory.

Memory is finite.

Strategies:

- expiration
- eviction
- monitoring

Policies:

- LRU
- LFU
- TTL-based eviction

Important for large deployments.

---

## Case Study: SyncGrid

Frequently accessed data:

- providers
- API key metadata
- team permissions

Caching candidates:

    provider:stripe

    provider:paystack

    api_key:xyz

Benefits:

- fewer DB queries
- faster request validation

---

## Case Study: VaultBox

Frequently accessed:

- user plans
- quotas
- storage allocations

Example:

    plan:premium

Instead of querying database repeatedly:

Store in Redis.

---

## Case Study: inFlowForge

Frequently accessed:

- workflow definitions
- trigger rules
- action metadata

Workflow execution can become much faster when definitions are cached.

---

## Failure Scenario 1

Redis Failure

Architecture:

API

↓

Redis

↓

Database

Redis crashes.

Result:

All traffic hits database.

Database overloads.

Mitigation:

- Redis replication
- graceful degradation
- circuit breakers

---

## Failure Scenario 2

Infinite TTL

Cache never refreshed.

Old data remains forever.

Users see stale information.

---

## Failure Scenario 3

Cache Stampede

Popular key expires.

Thousands of requests hit database.

Database becomes bottleneck.

---

## Failure Scenario 4

Hot Key

Single cache key receives huge traffic.

Redis CPU spikes.

Latency increases.

---

## Design Trade-Offs

### More Caching

Benefits:

- speed
- scalability

Costs:

- complexity
- stale data

---

### Longer TTL

Benefits:

- fewer DB queries

Costs:

- older data

---

### Short TTL

Benefits:

- fresher data

Costs:

- more DB traffic

---

### Distributed Cache

Benefits:

- shared state

Costs:

- network latency

---

## Common Mistakes

### Mistake 1

Caching everything.

### Mistake 2

No invalidation strategy.

### Mistake 3

Infinite TTL.

### Mistake 4

Ignoring memory limits.

### Mistake 5

Ignoring cache hit ratio.

### Mistake 6

No protection against stampedes.

### Mistake 7

Using cache as permanent storage.

---

## Interview Questions

1. What is caching?
2. What is cache-aside?
3. What is write-through caching?
4. What is write-behind caching?
5. What is cache invalidation?
6. What is a cache hit?
7. What is a cache miss?
8. What is a cache stampede?
9. What is a hot key?
10. What is cache warming?
11. What is multi-level caching?
12. Why is Redis commonly used?
13. What metrics would you monitor?
14. When should data not be cached?
15. How would you scale a Redis cache?

---

## Exercises

1. Design a cache architecture for VaultBox.
2. Design a cache architecture for SyncGrid.
3. Design a cache architecture for inFlowForge.
4. Compare cache-aside and write-through.
5. Explain cache stampede prevention.
6. Design a cache invalidation strategy for user profiles.
7. Identify hot-key risks in your projects.
8. Draw a multi-level cache architecture.
9. Explain eventual consistency.
10. Calculate cache hit ratio from sample data.

---

## Further Reading

Redis Documentation

https://redis.io/docs

Redis Caching Guide

https://redis.io/docs/latest/develop/use/patterns/

AWS Caching Strategies

https://aws.amazon.com/caching/

System Design Primer

https://github.com/donnemartin/system-design-primer

---

## Summary

Caching is one of the most effective scalability tools in modern systems.

Key concepts include:

- cache-aside
- invalidation
- TTLs
- stampedes
- hot keys
- cache warming
- distributed caching

A properly designed cache can dramatically reduce latency and database load, but poor cache design introduces complexity, stale data and operational risks.
