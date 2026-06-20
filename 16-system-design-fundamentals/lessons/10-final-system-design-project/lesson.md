# Lesson 10: Final System Design Project

## Learning Objectives

By the end of this lesson you should be able to:

- Apply the concepts learned throughout this module.
- Gather requirements systematically.
- Estimate scale.
- Design scalable architectures.
- Identify bottlenecks.
- Design for reliability.
- Communicate architecture decisions.

---

## Introduction

This project brings together everything learned in the System Design Fundamentals module.

You will design a production-style SaaS platform.

The goal is not to write code.

The goal is to think like an architect.

---

# Project

Design A Global Workflow Automation Platform

Inspired by:

- inFlowForge
- Zapier
- n8n
- Make
- Temporal

---

## Business Requirements

Users can:

- create accounts
- create workspaces
- create workflows
- execute workflows
- schedule workflows
- view execution history
- receive notifications

Administrators can:

- monitor activity
- inspect failures
- manage accounts

---

## Functional Requirements

The system must:

- authenticate users
- create workflows
- execute workflows
- schedule workflows
- store logs
- send notifications
- expose APIs

---

## Non-Functional Requirements

The system should:

- support millions of executions
- remain highly available
- scale horizontally
- tolerate failures
- process jobs reliably
- support future growth

---

## Scale Assumptions

Assume:

Users:

    2,000,000

Workflows:

    100,000,000

Executions:

    50,000,000/day

API Requests:

    500,000,000/day

These estimates influence architecture.

---

# Step 1: High-Level Architecture

                Users
                   |
                   v
             Load Balancer
                   |
       -------------------------
       |                       |
       v                       v
     API 1                  API 2
       |                       |
       -------------------------
                   |
                   v
                 Redis
                   |
                   v
              PostgreSQL
                   |
                   v
             Job Queue
                   |
      --------------------------------
      |              |              |
      v              v              v
   Worker 1      Worker 2      Worker 3

---

## Why Load Balancers?

Benefits:

- horizontal scaling
- fault tolerance
- traffic distribution

Without load balancers:

Single point of failure.

---

## Why Multiple APIs?

Benefits:

- scalability
- redundancy
- availability

If one API fails:

Others continue serving traffic.

---

## Why Redis?

Use Redis for:

- caching
- rate limiting
- temporary state
- queue infrastructure

Benefits:

- low latency
- reduced database load

---

## Why PostgreSQL?

Stores:

- users
- workspaces
- workflows
- executions
- permissions

Relational data fits naturally.

---

## Why Queues?

Workflow execution can take:

- seconds
- minutes
- hours

Users should not wait.

Architecture:

API

↓

Queue

↓

Workers

---

## Why Workers?

Workers execute:

- workflows
- notifications
- retries
- scheduled jobs

Separating workers from APIs improves scalability.

---

# Step 2: Data Model

Core entities:

Users

Workspaces

Workflows

Triggers

Executions

Notifications

Audit Logs

---

## Example Relationships

User

↓

Workspace

↓

Workflow

↓

Execution

This hierarchy keeps ownership clear.

---

# Step 3: Caching Strategy

Cache candidates:

- workflow definitions
- workspace settings
- permissions
- frequently accessed metadata

Example:

    workflow:123

stored in Redis.

Benefits:

- lower latency
- fewer database queries

---

# Step 4: Queue Strategy

Queues:

Execution Queue

Notification Queue

Retry Queue

Analytics Queue

Benefits:

- isolation
- scalability
- fault tolerance

---

# Step 5: Reliability Design

Reliability mechanisms:

- retries
- dead letter queues
- monitoring
- backups
- replication

Never assume success.

Assume failure.

---

## Retry Strategy

Temporary failures:

- network timeout
- provider outage
- rate limiting

Retry with:

Exponential backoff.

---

## Dead Letter Queue

Permanent failures:

Move to DLQ.

Benefits:

- investigation
- auditing
- recovery

---

# Step 6: Database Scaling

Phase 1:

Single PostgreSQL instance.

Phase 2:

Indexes.

Phase 3:

Redis cache.

Phase 4:

Read replicas.

Phase 5:

Partition execution logs.

Phase 6:

Consider sharding if necessary.

---

## Read Replicas

Architecture:

          Primary
              |
      ----------------
      |              |
      v              v
   Replica A     Replica B

Reads:

Replicas

Writes:

Primary

---

# Step 7: Monitoring

Monitor:

- API latency
- error rate
- queue depth
- worker failures
- cache hit ratio
- database performance

If you cannot observe a system:

You cannot operate it effectively.

---

## Alerting

Create alerts for:

- API outages
- worker crashes
- queue growth
- database failures

---

# Step 8: Security

Security considerations:

- JWT authentication
- RBAC
- encryption
- audit logs
- secrets management

Never expose sensitive credentials.

---

## Audit Logging

Track:

- workflow changes
- permission changes
- authentication events

Important for compliance and investigations.

---

# Step 9: Failure Scenarios

Scenario:

Redis unavailable.

Response:

Bypass cache.

Use database directly.

Accept slower performance.

---

Scenario:

Worker crash.

Response:

Reassign jobs.

Use queue persistence.

---

Scenario:

Database failure.

Response:

Promote replica.

Restore service.

---

Scenario:

Provider outage.

Response:

Retry jobs.

Use DLQ for persistent failures.

---

# Step 10: Trade-Offs

### More Caching

Benefits:

- speed

Costs:

- invalidation complexity

---

### More Workers

Benefits:

- throughput

Costs:

- infrastructure expense

---

### Strong Consistency

Benefits:

- correctness

Costs:

- performance

---

### Eventual Consistency

Benefits:

- scalability

Costs:

- temporary stale data

---

# Extended Challenge

Design a second architecture for:

NOMMO

Requirements:

- node registration
- worker heartbeats
- service scheduling
- orchestration
- health monitoring
- failover

Identify:

- events
- queues
- caches
- databases
- monitoring systems

---

# Project Deliverables

Produce:

1. Requirements document.
2. Scale estimates.
3. Architecture diagram.
4. Data model.
5. Caching strategy.
6. Queue strategy.
7. Reliability strategy.
8. Monitoring strategy.
9. Security strategy.
10. Trade-off analysis.

---

# Self-Assessment

Can you explain:

✓ Why Redis exists?

✓ Why queues exist?

✓ Why workers exist?

✓ Why caching exists?

✓ Why replicas exist?

✓ Why monitoring exists?

✓ Why failures must be planned for?

If yes, you are thinking like a systems engineer.

---

## Interview Questions

1. Why begin with requirements?
2. Why estimate scale?
3. Why use queues?
4. Why use Redis?
5. Why use workers?
6. Why use read replicas?
7. Why use monitoring?
8. Why use DLQs?
9. How would you scale the platform?
10. What trade-offs exist in your design?

---

## Exercises

1. Design a SaaS CRM.
2. Design a notification platform.
3. Design a monitoring platform.
4. Design a cloud storage platform.
5. Design a workflow engine.
6. Design an orchestration platform.
7. Design a payment platform.
8. Design a document management platform.
9. Design a CI/CD platform.
10. Design a deployment orchestrator.

---

## Further Reading

System Design Primer

https://github.com/donnemartin/system-design-primer

Designing Data Intensive Applications

https://dataintensive.net

Google SRE

https://sre.google

AWS Architecture Center

https://aws.amazon.com/architecture

---

## Summary

System design is the discipline of making engineering decisions under constraints.

The best architectures:

- solve business problems
- scale appropriately
- tolerate failures
- remain maintainable
- evolve gradually

The goal is not complexity.

The goal is building systems that continue working as demand grows.
