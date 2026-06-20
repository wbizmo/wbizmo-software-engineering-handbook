# Lesson 04: Leader Election

## Learning Objectives

By the end of this lesson you should be able to:

- Explain leader election.
- Understand why leaders exist.
- Understand coordinator patterns.
- Understand failover.
- Understand split-brain problems.
- Explain election algorithms at a high level.
- Design systems that use leaders safely.

---

## Introduction

Many distributed systems need coordination.

Examples:

- scheduling jobs
- assigning work
- managing cluster state
- processing critical updates
- coordinating deployments

Question:

Who makes decisions?

One common answer:

A leader.

---

## What Is A Leader?

A leader is a node responsible for coordination.

Example:

Cluster:

    Node A
    Node B
    Node C

Leader:

    Node A

Node A coordinates activity.

Other nodes follow.

---

## Why Leaders Exist

Without leaders:

Every node may try to make decisions.

Result:

- conflicts
- duplication
- inconsistent state

Leaders reduce coordination complexity.

---

## Example: Task Scheduling

Three nodes:

Node A

Node B

Node C

Task arrives.

Without coordination:

All nodes schedule task.

Result:

Duplicate execution.

With leader:

Leader schedules.

Workers execute.

Much safer.

---

## Leader-Based Architecture

                Leader
                   |
        -----------------------
        |          |          |
        v          v          v
     Worker1    Worker2    Worker3

Leader coordinates.

Workers perform work.

---

## Real World Examples

### Kubernetes

Leader components coordinate cluster state.

### etcd

Uses leadership for consensus.

### ZooKeeper

Elects leaders.

### Redis Sentinel

Can promote new primaries.

### NOMMO

Future orchestrator leaders could coordinate:

- scheduling
- routing
- service placement

---

## Responsibilities Of Leaders

Examples:

- scheduling
- coordination
- metadata management
- cluster state updates
- resource allocation

Leaders often manage shared state.

---

## Single Leader Model

Architecture:

      Leader
         |
    ----------
    |        |
    v        v
 Node B   Node C

Simple.

Common.

Widely used.

---

## The Failure Problem

Question:

What happens if leader dies?

Example:

Leader:

    Node A

Failure:

Node A crashes.

Now:

Who is leader?

System must decide.

---

## Leader Election

Leader election is the process of choosing a new leader.

Goal:

Exactly one leader.

Not zero.

Not two.

---

## Election Trigger

Common triggers:

- heartbeat missing
- node crash
- network partition
- planned shutdown

Election begins automatically.

---

## Simple Election Example

Cluster:

Node A

Node B

Node C

Leader:

Node A

Node A fails.

Election occurs.

Node B becomes leader.

Cluster continues.

---

## Heartbeats

Leaders often send heartbeats.

Example:

Every 2 seconds:

    I am alive

Followers monitor heartbeats.

Missing heartbeat:

Election may begin.

---

## Election Timeout

Example:

Heartbeat expected:

Every 2 seconds.

No heartbeat for:

6 seconds.

Leader assumed failed.

Election starts.

---

## Why Timeouts Matter

Too short:

False elections.

Too long:

Slow recovery.

Balance required.

---

## Split-Brain

One of the most dangerous distributed systems failures.

Scenario:

Node A thinks:

    I am leader

Node B thinks:

    I am leader

Now two leaders exist.

This is split-brain.

---

## Why Split-Brain Is Dangerous

Example:

Leader A schedules task.

Leader B schedules same task.

Duplicate execution occurs.

State diverges.

Data may become corrupted.

---

## Preventing Split-Brain

Common approaches:

- quorum
- consensus
- leader leases
- fencing tokens

Modern systems take this very seriously.

---

## Quorum

Quorum means majority agreement.

Example:

5 nodes.

Need:

3 approvals.

Benefits:

Reduces risk of multiple leaders.

---

## Election Safety

Good election systems guarantee:

At most one leader.

This property is critical.

---

## Bully Algorithm

Classic election algorithm.

Highest node ID wins.

Example:

Nodes:

1

2

3

Leader:

3

If 3 fails:

Leader becomes:

2

Simple.

Educational.

Rare in modern systems.

---

## Raft Elections

Raft uses elections.

Nodes become:

- follower
- candidate
- leader

Followers detect failure.

Candidates request votes.

Majority wins.

New leader elected.

Widely used today.

---

## Leadership Terms

Raft introduces:

Term

Example:

Term 1

Leader A

Leader fails.

Term 2

Leader B

Terms prevent confusion.

---

## Leader Leases

Leader receives temporary authority.

Lease expires.

Must renew periodically.

If renewal fails:

Leadership ends.

Helps prevent stale leaders.

---

## Fencing Tokens

Protect resources from old leaders.

Example:

Leader A:

Token 5

Leader B:

Token 6

Only newest token accepted.

Prevents stale leader actions.

---

## Active Leader Architecture

Example:

              Leader
                 |
        ----------------
        |              |
        v              v
     Worker1       Worker2

Common pattern.

---

## Leader And Followers

Leader:

Handles writes.

Followers:

Replicate state.

Common in databases.

Example:

PostgreSQL replication.

---

## SyncGrid Example

Potential leader responsibilities:

- webhook scheduling
- retry management
- queue coordination

---

## VaultBox Example

Potential leader responsibilities:

- storage cleanup
- quota recalculation
- maintenance jobs

---

## inFlowForge Example

Potential leader responsibilities:

- workflow scheduling
- cron management
- execution assignment

---

## NOMMO Example

Leader responsibilities:

- node registry
- service placement
- worker assignment
- routing decisions

Leader election is central to orchestration systems.

---

## Failure Scenario 1

Leader crashes.

Election begins.

New leader selected.

---

## Failure Scenario 2

Network partition.

Multiple nodes believe leader unavailable.

Risk:

Split-brain.

---

## Failure Scenario 3

Election timeout too short.

Frequent unnecessary elections.

---

## Failure Scenario 4

Election timeout too long.

Slow recovery.

---

## Common Mistakes

### Mistake 1

Assuming leader never fails.

### Mistake 2

Ignoring split-brain.

### Mistake 3

No heartbeat monitoring.

### Mistake 4

No quorum requirements.

### Mistake 5

No failover testing.

---

## Trade-Offs

### Leader-Based Coordination

Benefits:

- simpler reasoning
- centralized decisions

Costs:

- leader bottleneck
- election complexity

---

### Decentralized Coordination

Benefits:

- fewer bottlenecks

Costs:

- more complexity

---

## Interview Questions

1. What is leader election?
2. Why do distributed systems need leaders?
3. What is a heartbeat?
4. What is split-brain?
5. Why is split-brain dangerous?
6. What is quorum?
7. What is a leader lease?
8. What is a fencing token?
9. What is the Bully Algorithm?
10. How does Raft elect leaders?
11. What happens when a leader fails?
12. Why are election timeouts important?
13. How would NOMMO use leader election?
14. Why are leaders common in orchestration systems?
15. How would you prevent multiple leaders?

---

## Exercises

1. Draw a leader-worker architecture.
2. Explain split-brain.
3. Explain quorum.
4. Simulate a leader failure.
5. Simulate a Raft election.
6. Design leader responsibilities for NOMMO.
7. Design leader responsibilities for Argus.
8. Explain election timeouts.
9. Explain leader leases.
10. Explain why distributed coordination is difficult.

---

## Further Reading

Raft

https://raft.github.io

In Search Of An Understandable Consensus Algorithm

https://raft.github.io/raft.pdf

ZooKeeper

https://zookeeper.apache.org

etcd

https://etcd.io

---

## Summary

Leader election allows distributed systems to coordinate work through a single decision-maker.

Key concepts include:

- leaders
- followers
- heartbeats
- elections
- quorum
- split-brain prevention

Leader election is one of the fundamental building blocks of orchestration systems, databases and distributed platforms.
