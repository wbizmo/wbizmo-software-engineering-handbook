# Lesson 02: Scalability Fundamentals

## Learning Objectives

By the end of this lesson you should be able to:

- Define scalability.
- Distinguish vertical and horizontal scaling.
- Understand bottlenecks.
- Understand throughput and latency.
- Understand stateless and stateful systems.
- Understand scaling challenges.
- Analyze scaling trade-offs.

---

## Introduction

Many applications work correctly with:

    10 users

The challenge begins when the application must support:

    10,000 users

or

    1,000,000 users

Scalability is the ability of a system to continue performing acceptably as demand increases.

A scalable system grows without requiring a complete redesign.

---

## What Is Scalability?

Scalability means:

A system can handle increasing load.

Load may include:

- users
- requests
- data
- background jobs
- storage requirements

Example:

Today:

    100 requests/minute

Tomorrow:

    100,000 requests/minute

Can the system still function?

That is a scalability question.

---

## Understanding Load

Common forms of load:

### User Load

Number of active users.

Example:

    100 users

vs

    1,000,000 users

### Request Load

API traffic.

Example:

    10 requests/sec

vs

    50,000 requests/sec

### Data Load

Storage growth.

Example:

    100 MB

vs

    50 TB

### Processing Load

Background jobs.

Example:

    10 jobs/min

vs

    5 million jobs/day

---

## Vertical Scaling

Vertical scaling means:

Increasing resources on a single machine.

Example:

Before:

    4 CPU
    8 GB RAM

After:

    32 CPU
    128 GB RAM

Diagram:

        Server
           |
           v
      Bigger Server

Benefits:

- simple
- minimal architecture changes

Drawbacks:

- expensive
- hardware limits
- single point of failure

---

## Horizontal Scaling

Horizontal scaling means:

Adding more machines.

Diagram:

          API
           |
    ----------------
    |      |      |
    v      v      v
  API1   API2   API3

Benefits:

- high scalability
- fault tolerance
- elasticity

Drawbacks:

- complexity
- networking challenges
- distributed systems problems

---

## Vertical vs Horizontal

Vertical:

+ Simpler

- Limited

Horizontal:

+ Nearly unlimited growth

- More complex

Modern large systems usually prefer horizontal scaling.

---

## Bottlenecks

A bottleneck is the component limiting system performance.

Example:

Users
  |
  v
API
  |
  v
Database

If database becomes overloaded:

The database is the bottleneck.

Adding API servers won't help.

You must identify the actual constraint.

---

## Throughput

Throughput measures:

Work completed per unit time.

Examples:

    Requests/second

    Jobs/minute

    Messages/second

Example:

System A:

    500 requests/sec

System B:

    50,000 requests/sec

System B has higher throughput.

---

## Latency

Latency measures:

Response delay.

Example:

    20ms

    100ms

    500ms

Lower latency is generally better.

---

## Throughput vs Latency

A system can have:

High throughput

but

Poor latency

Example:

Processes:

    50,000 requests/sec

but each request takes:

    5 seconds

Understanding both metrics is important.

---

## Stateless Services

Stateless services do not store user session data locally.

Example:

Request arrives.

↓

Process request.

↓

Return response.

↓

Forget state.

Benefits:

- easier scaling
- easier load balancing
- simpler deployment

Most modern APIs are stateless.

---

## Stateful Services

Stateful services retain information locally.

Example:

Local sessions.

Local files.

Benefits:

- simplicity in some cases

Drawbacks:

- difficult scaling
- migration challenges

---

## Why Stateless Systems Scale Better

Example:

            Load Balancer
                   |
      ------------------------
      |          |          |
      v          v          v
    API1       API2       API3

Any request can hit any server.

This works well when servers are stateless.

---

## Database Scaling Challenges

Applications scale faster than databases.

Common issues:

- slow queries
- lock contention
- storage growth
- connection limits

Database scaling often becomes the hardest problem.

---

## Read Scaling

One strategy:

Read replicas.

Diagram:

              Primary
                 |
         ----------------
         |              |
         v              v
     Replica1       Replica2

Writes:

Primary

Reads:

Replicas

Benefits:

- improved read throughput

Trade-offs:

- replication delay

---

## Write Scaling

Much harder.

Techniques:

- partitioning
- sharding
- distributed databases

These introduce complexity.

---

## Scaling Background Jobs

Example:

Worker 1

↓

Worker 2

↓

Worker 3

Instead of:

One overloaded worker.

Queues help distribute load.

---

## Real World Example

Consider SyncGrid.

Traffic increases:

    100 requests/day

to

    5 million requests/day

Possible scaling path:

Phase 1:

Single server

↓

Phase 2:

Load balancer

+

Multiple API servers

↓

Phase 3:

Redis cache

↓

Phase 4:

Queue workers

↓

Phase 5:

Read replicas

System design evolves gradually.

---

## Failure Scenarios

### Scenario 1

Traffic spike.

System crashes.

Cause:

No scaling plan.

### Scenario 2

Database overloaded.

Cause:

No caching.

### Scenario 3

Worker queue grows indefinitely.

Cause:

Insufficient workers.

### Scenario 4

Load balancer failure.

Cause:

Single point of failure.

---

## Common Mistakes

### Mistake 1

Scaling too early.

### Mistake 2

Ignoring bottlenecks.

### Mistake 3

Scaling the wrong component.

### Mistake 4

Confusing throughput and latency.

### Mistake 5

Keeping state inside API servers.

---

## Interview Questions

1. What is scalability?
2. Difference between vertical and horizontal scaling?
3. What is a bottleneck?
4. What is throughput?
5. What is latency?
6. Why are stateless services easier to scale?
7. Why are databases difficult to scale?
8. What are read replicas?
9. What is sharding?
10. How would you scale a growing API?

---

## Exercises

1. Identify bottlenecks in Cashflowr.
2. Design a scaling strategy for VaultBox.
3. Explain vertical scaling.
4. Explain horizontal scaling.
5. Draw a read replica architecture.
6. Explain why Redis helps scalability.

---

## Further Reading

System Design Primer

https://github.com/donnemartin/system-design-primer

AWS Scalability Concepts

https://aws.amazon.com

Google SRE

https://sre.google

---

## Summary

Scalability is the ability of a system to handle increasing demand.

The key concepts are:

- vertical scaling
- horizontal scaling
- throughput
- latency
- bottlenecks
- stateless services

Understanding these concepts is essential before discussing load balancers, distributed databases and large-scale architectures.
