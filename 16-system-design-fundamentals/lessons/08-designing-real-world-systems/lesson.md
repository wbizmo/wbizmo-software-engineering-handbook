# Lesson 08: Designing Real World Systems

## Learning Objectives

By the end of this lesson you should be able to:

- Approach system design methodically.
- Gather requirements.
- Estimate scale.
- Identify bottlenecks.
- Select appropriate technologies.
- Design scalable architectures.
- Evaluate trade-offs.

---

## Introduction

Most engineers fail system design not because they lack technical knowledge.

They fail because they jump directly into solutions.

Bad approach:

    "Let's use Kubernetes."

Good approach:

    What problem are we solving?

System design begins with understanding requirements.

Technology choices come later.

---

## Step 1: Clarify Requirements

Before drawing architecture:

Ask questions.

Example:

Design a file storage platform.

Questions:

- Who are the users?
- How many users?
- File size limits?
- Public or private files?
- Expected traffic?
- Retention requirements?
- Security requirements?

Good design starts with understanding the problem.

---

## Functional Requirements

Functional requirements describe:

What the system must do.

Example:

VaultBox

Requirements:

- upload files
- download files
- create accounts
- manage storage quotas
- generate signed URLs

---

## Non-Functional Requirements

Describe quality attributes.

Examples:

- scalability
- reliability
- availability
- latency
- security
- maintainability

Example:

VaultBox

Requirement:

    Downloads should begin within 500ms.

This is non-functional.

---

## Step 2: Estimate Scale

System design requires rough estimates.

Example:

Users:

    1,000,000

Daily uploads:

    5,000,000

Average file:

    10MB

Daily storage:

    50TB

Estimates guide architecture.

---

## Capacity Planning

Questions:

- How much storage?
- How many requests?
- How many workers?
- How much bandwidth?

Good estimates prevent surprises.

---

## Step 3: Identify Core Components

Most systems contain:

- clients
- APIs
- databases
- caches
- queues
- workers
- monitoring

Example architecture:

Clients

↓

Load Balancer

↓

API Cluster

↓

Redis

↓

PostgreSQL

↓

Workers

---

## Example 1: Design VaultBox

### Requirements

Users can:

- upload files
- download files
- manage storage

---

### High Level Architecture

              Users
                 |
                 v
           Load Balancer
                 |
        -------------------
        |                 |
        v                 v
      API1             API2
        |
        v
      Redis
        |
        v
    PostgreSQL
        |
        v
   Object Storage

---

## Why Redis?

Used for:

- session data
- quotas
- metadata cache

Reduces database load.

---

## Why PostgreSQL?

Stores:

- users
- plans
- metadata
- permissions

Relational data fits well.

---

## Why Object Storage?

Files may become enormous.

Avoid storing large files directly in PostgreSQL.

Store:

- metadata in PostgreSQL
- file content in object storage

---

## Scaling VaultBox

Phase 1:

Single API.

Phase 2:

Load balancer.

Phase 3:

Redis cache.

Phase 4:

Read replicas.

Phase 5:

Worker fleet.

Architecture evolves gradually.

---

## Example 2: Design SyncGrid

### Requirements

- unified provider access
- API key management
- webhook processing
- usage tracking

---

### High Level Architecture

Clients

↓

Load Balancer

↓

API Cluster

↓

Redis

↓

PostgreSQL

↓

Webhook Queue

↓

Workers

---

## Why Queues?

Webhook delivery is slow.

Users should not wait.

Flow:

API

↓

Queue

↓

Worker

↓

Provider

---

## SyncGrid Scaling Strategy

Cache:

- providers
- API keys

Queue:

- webhooks
- retries

Database:

- request logs
- team data

---

## Example 3: Design inFlowForge

Requirements:

- workflows
- triggers
- actions
- schedules

---

### Architecture

Users

↓

API

↓

PostgreSQL

↓

Workflow Queue

↓

Execution Workers

↓

External Services

---

## Why Workers?

Workflow execution may take minutes.

Workers isolate long-running tasks.

---

## Event-Driven Workflow Design

Trigger fires.

↓

Event created.

↓

Queue receives event.

↓

Worker executes workflow.

Highly scalable.

---

## Example 4: Design Argus

Requirements:

- service monitoring
- health checks
- alerting
- metrics

---

### Architecture

Services

↓

Agents

↓

Argus API

↓

Redis

↓

PostgreSQL

↓

Alert Workers

↓

Notification Providers

---

## Why Redis?

Fast metric storage.

Short-lived monitoring data.

---

## Example 5: Design NOMMO

Requirements:

- service orchestration
- node management
- worker coordination
- service lifecycle management

---

### Architecture

Workers

↓

Control Plane

↓

Redis

↓

PostgreSQL

↓

Scheduler

↓

Routing Layer

---

## Why Event Driven?

Events:

- worker joined
- worker failed
- deployment started
- deployment completed

Drive orchestration decisions.

---

## API Design Considerations

Good APIs:

- versioned
- documented
- predictable

Examples:

    /v1/files

    /v1/workflows

    /v1/providers

Avoid breaking clients.

---

## Database Design Considerations

Questions:

- relational?
- document?
- key-value?

Most business systems fit relational databases surprisingly well.

PostgreSQL is often enough.

---

## Cache Design Considerations

Cache:

- expensive queries
- frequently accessed data
- configuration

Avoid:

- caching everything

---

## Queue Design Considerations

Queue:

- emails
- webhooks
- reports
- workflow execution

Avoid:

- critical synchronous logic

---

## Monitoring Design Considerations

Monitor:

- latency
- throughput
- errors
- queue depth
- database performance

If you cannot observe a system:

You cannot operate it reliably.

---

## Security Considerations

Always consider:

- authentication
- authorization
- encryption
- secrets management
- audit logs

Security is not optional.

---

## Cost Considerations

Architecture choices have costs.

Example:

Redis Cluster

Benefits:

- scalability

Costs:

- operational complexity
- infrastructure expenses

Always evaluate trade-offs.

---

## Failure Scenario 1

Database Failure

Mitigation:

- backups
- replicas
- failover

---

## Failure Scenario 2

Redis Failure

Mitigation:

- graceful degradation
- replication

---

## Failure Scenario 3

Worker Failure

Mitigation:

- retries
- DLQs

---

## Failure Scenario 4

Traffic Spike

Mitigation:

- load balancing
- autoscaling
- caching

---

## Failure Scenario 5

Third-Party Provider Outage

Mitigation:

- queues
- retries
- circuit breakers

---

## Design Trade-Offs

### Simplicity

Benefits:

- maintainability

Costs:

- may limit scale

---

### Scalability

Benefits:

- growth

Costs:

- complexity

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

- temporary inconsistency

---

## Common Mistakes

### Mistake 1

Designing before understanding requirements.

### Mistake 2

Premature optimization.

### Mistake 3

Overusing microservices.

### Mistake 4

Ignoring monitoring.

### Mistake 5

Ignoring failure scenarios.

### Mistake 6

Choosing technology first.

### Mistake 7

Not estimating scale.

---

## System Design Framework

A useful approach:

1. Clarify requirements.
2. Estimate scale.
3. Design high-level architecture.
4. Design data model.
5. Add caching.
6. Add queues.
7. Address scaling.
8. Address reliability.
9. Address security.
10. Discuss trade-offs.

---

## Interview Questions

1. How do you approach system design?
2. Why estimate scale?
3. Why clarify requirements?
4. Why use queues?
5. Why use caches?
6. Why use workers?
7. How would you design a storage platform?
8. How would you design a workflow engine?
9. How would you design a monitoring platform?
10. How do trade-offs affect design?

---

## Exercises

1. Design a URL shortener.
2. Design a chat platform.
3. Design a notification service.
4. Design a file storage platform.
5. Design an API gateway.
6. Design a monitoring system.
7. Design a workflow engine.
8. Identify bottlenecks in VaultBox.
9. Identify bottlenecks in SyncGrid.
10. Identify bottlenecks in NOMMO.

---

## Further Reading

System Design Primer

https://github.com/donnemartin/system-design-primer

Designing Data Intensive Applications

https://dataintensive.net

AWS Architecture Center

https://aws.amazon.com/architecture

Google Cloud Architecture Framework

https://cloud.google.com/architecture

---

## Summary

Real-world system design is about solving business problems through architecture.

The best engineers:

- gather requirements
- estimate scale
- choose appropriate technologies
- evaluate trade-offs
- plan for failures

Technology knowledge is valuable.

Engineering judgment is even more valuable.
