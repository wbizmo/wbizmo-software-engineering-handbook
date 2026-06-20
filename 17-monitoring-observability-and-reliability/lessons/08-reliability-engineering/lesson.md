# Lesson 08: Reliability Engineering

## Learning Objectives

By the end of this lesson you should be able to:

- Define reliability engineering.
- Understand service reliability.
- Design resilient systems.
- Reduce operational risk.
- Improve system availability.
- Build fault-tolerant architectures.

---

## Introduction

Reliable systems do not happen accidentally.

Reliability is engineered.

Organizations such as Google created Site Reliability Engineering (SRE) to systematically improve service reliability.

Reliability engineering combines:

- software engineering
- operations
- monitoring
- automation
- incident management

---

## What Is Reliability?

Reliability is the probability that a system performs its intended function over time.

Examples:

- API responds successfully.
- Database remains available.
- Workflows execute correctly.
- Files remain accessible.

---

## Reliability vs Availability

Availability:

Can users access the service?

Reliability:

Does the service consistently work correctly?

A service may be available but unreliable.

Example:

Returns errors frequently.

---

## Reliability Principles

Reliable systems:

- fail gracefully
- recover quickly
- tolerate faults
- minimize downtime
- automate repetitive operations

---

## Fault Tolerance

Fault tolerance means continuing to operate despite failures.

Example:

API1 fails.

Traffic automatically moves to:

API2

API3

Users remain unaffected.

---

## Redundancy

Redundancy improves reliability.

Example:

Single Database

↓

Failure

↓

Outage

Better:

Primary

↓

Replica

Failure becomes survivable.

---

## Eliminating Single Points Of Failure

Single point of failure:

One component whose failure causes total outage.

Examples:

- one database
- one API server
- one load balancer

Reliable systems remove them.

---

## Graceful Degradation

Not all failures require complete outages.

Example:

Recommendation engine unavailable.

Core checkout still works.

Users retain essential functionality.

---

## Reliability Patterns

Examples:

- retries
- failover
- redundancy
- circuit breakers
- bulkheads
- timeouts

These patterns appear repeatedly in production systems.

---

## Circuit Breakers

Prevent repeated calls to failing services.

Normal:

API

↓

Provider

Failure:

Provider unavailable.

Circuit breaker opens.

Requests fail fast.

Prevents cascading failures.

---

## Bulkheads

Separate workloads.

Example:

Webhook Queue

Notification Queue

Analytics Queue

Failure in one queue does not impact others.

---

## Timeouts

Never wait forever.

Bad:

Request hangs indefinitely.

Good:

Request fails after timeout.

Systems recover faster.

---

## SyncGrid Example

Reliability measures:

- retries
- queue isolation
- provider failover
- monitoring

---

## VaultBox Example

Reliability measures:

- storage redundancy
- backups
- replication
- cache fallback

---

## NOMMO Example

Reliability measures:

- node failover
- worker redistribution
- heartbeat monitoring
- scheduler redundancy

---

## Reliability Metrics

Examples:

- uptime
- error rate
- MTTR
- MTBF

---

## MTTR

Mean Time To Recovery.

How quickly incidents are resolved.

Lower is better.

---

## MTBF

Mean Time Between Failures.

How often failures occur.

Higher is better.

---

## Common Mistakes

### Mistake 1

No redundancy.

### Mistake 2

No failover.

### Mistake 3

No monitoring.

### Mistake 4

No backups.

### Mistake 5

Ignoring reliability testing.

---

## Interview Questions

1. What is reliability?
2. What is fault tolerance?
3. What is graceful degradation?
4. What is a circuit breaker?
5. What is MTTR?
6. What is MTBF?

---

## Exercises

1. Identify single points of failure in VaultBox.
2. Identify single points of failure in SyncGrid.
3. Design redundancy for NOMMO.
4. Explain graceful degradation.
5. Explain circuit breakers.

---

## Further Reading

Google SRE

https://sre.google

Martin Fowler Reliability Patterns

https://martinfowler.com

---

## Summary

Reliability engineering focuses on keeping systems functioning despite failures through redundancy, fault tolerance, automation and operational discipline.
