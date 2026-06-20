# Lesson 02: Networking And Failure

## Learning Objectives

By the end of this lesson you should be able to:

- Understand network communication.
- Understand network failures.
- Understand latency.
- Understand packet loss.
- Understand timeouts.
- Understand retries.
- Design systems that survive network problems.

---

## Introduction

The biggest difference between a local application and a distributed system is the network.

Inside a single process:

Function calls are predictable.

Example:

    calculateTotal()

returns immediately.

Across a network:

Nothing is guaranteed.

Messages may:

- arrive late
- arrive twice
- arrive out of order
- never arrive

Distributed systems are fundamentally about dealing with unreliable networks.

---

## Local Calls vs Remote Calls

Local call:

    function()

Remote call:

    HTTP Request

The mistake many engineers make:

Treating remote calls like local calls.

They are not.

---

## Local Call Characteristics

Usually:

- fast
- predictable
- reliable

Example:

    getUser()

inside same process.

---

## Remote Call Characteristics

Network calls involve:

- routing
- switches
- firewalls
- operating systems
- cloud providers
- network links

Many things can fail.

---

## Latency

Latency is the delay between sending and receiving data.

Example:

Request sent:

    12:00:00

Response received:

    12:00:00.050

Latency:

    50ms

---

## Why Latency Matters

A request touching multiple services accumulates latency.

Example:

Client

↓

API (50ms)

↓

Redis (5ms)

↓

Database (80ms)

↓

Provider API (400ms)

Total latency grows quickly.

---

## Network Jitter

Latency is not always constant.

Example:

Request 1:

    20ms

Request 2:

    100ms

Request 3:

    250ms

This variation is called jitter.

---

## Packet Loss

Data travels in packets.

Sometimes packets disappear.

Causes:

- congestion
- faulty hardware
- routing issues

Lost packets often trigger retransmission.

Performance suffers.

---

## Network Partitions

One of the most important concepts.

Node A:

Cannot reach Node B.

Node B:

Cannot reach Node A.

Both still running.

Communication broken.

This is a network partition.

---

## Why Partitions Matter

Question:

Did the node fail?

Or

Did the network fail?

Often impossible to know immediately.

Distributed systems must make decisions despite uncertainty.

---

## Timeouts

Never wait forever.

Bad:

Request hangs indefinitely.

Good:

Fail after timeout.

Example:

    Timeout: 3 seconds

If response never arrives:

Request fails.

System recovers.

---

## Timeout Trade-Offs

Timeout too short:

False failures.

Timeout too long:

Slow recovery.

Choosing timeouts requires balance.

---

## Retries

Temporary failures happen.

Retrying often succeeds.

Example:

Request

↓

Failure

↓

Retry

↓

Success

---

## Retry Dangers

Retries can worsen outages.

Example:

Provider overloaded.

Every client retries immediately.

Load increases further.

System collapses.

---

## Exponential Backoff

Safer retry strategy.

Attempt 1:

    1 second

Attempt 2:

    2 seconds

Attempt 3:

    4 seconds

Attempt 4:

    8 seconds

Reduces pressure.

---

## Retry Storms

Many systems retry simultaneously.

Traffic explodes.

Failure becomes worse.

This is a retry storm.

Observability should detect this.

---

## Idempotency

Retries create duplicate requests.

Example:

Charge card.

Retry.

Charge card again.

Disaster.

Operations should often be idempotent.

Meaning:

Safe to execute multiple times.

---

## Connection Failures

Possible failures:

- DNS issues
- TCP connection failure
- TLS handshake failure
- timeout
- packet loss

Network communication involves many layers.

---

## DNS Failure

Application requests:

    api.example.com

DNS unavailable.

Service becomes unreachable.

Even though application is healthy.

---

## Slow Dependencies

Example:

SyncGrid calls payment provider.

Provider response:

    10 seconds

Your API becomes slow.

Dependency latency affects user experience.

---

## Cascading Failures

One failure triggers others.

Example:

Database slows.

↓

API waits.

↓

Requests accumulate.

↓

Workers wait.

↓

Queues grow.

↓

Entire platform degrades.

This is a cascading failure.

---

## Circuit Breakers

Protect against repeated failures.

Normal:

API

↓

Provider

Provider unhealthy:

Circuit opens.

Requests fail fast.

System remains stable.

---

## Bulkheads

Separate workloads.

Example:

Notification Queue

Analytics Queue

Webhook Queue

Failure in one area does not affect others.

---

## Heartbeats

Nodes often send periodic heartbeats.

Example:

Every 5 seconds:

    "I am alive"

Missed heartbeats may indicate failure.

NOMMO relies heavily on this idea.

---

## Failure Detection

Questions:

- Is node dead?
- Is network slow?
- Is heartbeat delayed?

Failure detection is surprisingly difficult.

---

## The Two Generals Problem

Classic distributed systems thought experiment.

Two generals must coordinate attack.

Communication happens via unreliable messenger.

Neither can know with certainty whether the other received the message.

Distributed systems face similar uncertainty.

---

## SyncGrid Example

Failures:

- provider timeout
- webhook delivery failure
- network outage

Mitigation:

- retries
- queues
- monitoring

---

## VaultBox Example

Failures:

- storage unavailable
- database latency
- upload interruption

Mitigation:

- retries
- redundancy
- monitoring

---

## NOMMO Example

Failures:

- node unreachable
- scheduler partition
- worker isolation

Mitigation:

- heartbeats
- leader election
- failover

---

## Common Mistakes

### Mistake 1

Assuming requests always succeed.

### Mistake 2

No timeouts.

### Mistake 3

Infinite retries.

### Mistake 4

Ignoring latency.

### Mistake 5

Ignoring network partitions.

### Mistake 6

No circuit breakers.

---

## Failure Scenarios

### Scenario 1

Provider timeout.

Users wait indefinitely.

Cause:

No timeout configured.

---

### Scenario 2

Retry storm.

Outage worsens.

Cause:

Aggressive retries.

---

### Scenario 3

Partition.

Nodes disagree.

Cause:

Network disruption.

---

### Scenario 4

Slow dependency.

Entire platform slows.

Cause:

Dependency bottleneck.

---

## Interview Questions

1. Why are remote calls different from local calls?
2. What is latency?
3. What is jitter?
4. What is packet loss?
5. What is a network partition?
6. Why are timeouts important?
7. Why are retries dangerous?
8. What is exponential backoff?
9. What is a retry storm?
10. What is a circuit breaker?
11. What is a heartbeat?
12. What is a cascading failure?
13. Why is failure detection difficult?
14. What is the Two Generals Problem?
15. How would you handle provider outages?

---

## Exercises

1. Design retry logic for SyncGrid.
2. Design timeout strategy for VaultBox.
3. Design heartbeat strategy for NOMMO.
4. Explain cascading failures.
5. Explain circuit breakers.
6. Compare local and remote calls.
7. Draw a dependency chain.
8. Identify network failure risks in your projects.
9. Explain why retries require idempotency.
10. Explain why uncertainty is fundamental in distributed systems.

---

## Further Reading

Distributed Systems For Fun And Profit

https://book.mixu.net/distsys/

Designing Data Intensive Applications

https://dataintensive.net

Martin Kleppmann

https://martin.kleppmann.com

---

## Summary

Distributed systems operate across unreliable networks.

Engineers must account for:

- latency
- packet loss
- timeouts
- retries
- partitions
- cascading failures

Most distributed systems challenges begin with one simple reality:

The network cannot be trusted.
