# Lesson 09: Distributed Transactions And Sagas

## Learning Objectives

By the end of this lesson you should be able to:

- Explain distributed transactions.
- Understand transaction boundaries.
- Understand consistency challenges.
- Explain Two-Phase Commit (2PC).
- Explain Saga patterns.
- Understand compensating actions.
- Design reliable cross-service workflows.

---

## Introduction

Transactions are simple on a single database.

Example:

Transfer money.

Step 1:

Debit Account A

Step 2:

Credit Account B

Both succeed.

Or both fail.

Easy.

Now imagine:

Account Service

↓

Payment Service

↓

Notification Service

Multiple services.

Multiple databases.

Multiple failures.

Transactions become much harder.

---

## What Is A Distributed Transaction?

A distributed transaction spans multiple systems.

Example:

Service A

↓

Service B

↓

Service C

All must agree on outcome.

This is a distributed transaction.

---

## Why Distributed Transactions Are Difficult

Failures may occur at any step.

Example:

Payment charged.

↓

Notification failed.

Question:

Should payment be reversed?

These decisions become complicated.

---

## Local Transactions

Single database.

Example:

BEGIN

Update balance

Insert transaction

COMMIT

Database guarantees consistency.

Simple.

---

## Distributed Transactions

Multiple databases.

Multiple services.

Multiple networks.

Failures become much more likely.

---

## Example: E-Commerce Checkout

Steps:

1. Reserve inventory.
2. Charge payment.
3. Create order.
4. Send confirmation.

What happens if:

Step 4 fails?

Order already exists.

Consistency becomes difficult.

---

## ACID Transactions

Traditional databases provide:

### Atomicity

All or nothing.

### Consistency

Valid state maintained.

### Isolation

Transactions don't interfere.

### Durability

Committed data survives.

---

## Distributed ACID Challenges

ACID becomes harder across services.

Problems:

- network failures
- partitions
- timeouts
- independent databases

---

## Two-Phase Commit (2PC)

Classic distributed transaction protocol.

Participants:

Coordinator

Workers

Goal:

All commit

or

All rollback

---

## Phase 1: Prepare

Coordinator asks:

    Can you commit?

Participants respond:

    Yes

or

    No

---

## Phase 2: Commit

If everyone agrees:

Commit.

Otherwise:

Rollback.

---

## Example

Coordinator

↓

Inventory Service

↓

Payment Service

↓

Order Service

All agree.

Commit executed.

---

## Advantages Of 2PC

Benefits:

- strong consistency
- coordinated outcome

---

## Problems With 2PC

Issues:

- slow
- blocking
- coordinator failure
- poor scalability

Modern cloud systems often avoid it.

---

## Coordinator Failure

Coordinator crashes after prepare.

Participants wait.

System may become stuck.

One reason 2PC is unpopular in large systems.

---

## Modern Alternative: Sagas

Many cloud systems use:

    Saga Pattern

Instead of one large transaction.

---

## What Is A Saga?

A saga is a sequence of local transactions.

Each service manages its own transaction.

Failures trigger compensating actions.

---

## Example Saga

Reserve Inventory

↓

Charge Payment

↓

Create Order

↓

Send Email

Failure occurs.

Compensation begins.

---

## Compensating Actions

Undo previous work.

Example:

Inventory reserved.

↓

Payment charged.

↓

Order creation fails.

Compensation:

Refund payment.

Release inventory.

Consistency restored.

---

## Why Sagas Scale Better

Benefits:

- decentralized
- scalable
- resilient

Popular in microservices.

---

## Orchestration Saga

Central coordinator controls workflow.

Architecture:

Saga Coordinator

↓

Service A

↓

Service B

↓

Service C

Coordinator manages execution.

---

## Choreography Saga

No central coordinator.

Services communicate through events.

Example:

Inventory Reserved

↓

Payment Service reacts

↓

Order Service reacts

Fully event-driven.

---

## Orchestration vs Choreography

### Orchestration

Benefits:

- easier visibility
- centralized control

Costs:

- coordinator complexity

---

### Choreography

Benefits:

- loose coupling

Costs:

- harder debugging

---

## Saga Example: SyncGrid

Workflow:

Create Charge

↓

Provider Processes

↓

Webhook Received

↓

Transaction Updated

Failure:

Compensating action may reverse state.

---

## Saga Example: VaultBox

Upload File

↓

Store Metadata

↓

Generate Thumbnail

↓

Virus Scan

Failure:

Cleanup actions remove partial state.

---

## Saga Example: inFlowForge

Workflow Trigger

↓

Action A

↓

Action B

↓

Action C

Failure:

Rollback actions executed.

---

## Saga Example: NOMMO

Deploy Service

↓

Assign Node

↓

Start Service

↓

Register Service

Failure:

Undo deployment.

Release resources.

Restore cluster consistency.

---

## Idempotency

Critical for distributed workflows.

Retries happen.

Actions may execute multiple times.

Operations should remain safe.

---

## Eventual Consistency

Many saga systems embrace:

Eventual consistency.

Temporary inconsistencies exist.

Eventually state converges.

---

## Outbox Pattern

Popular reliability pattern.

Transaction:

Database Write

↓

Outbox Record

↓

Event Published

Prevents lost events.

Widely used.

---

## Failure Scenario 1

Payment succeeds.

Order creation fails.

Compensation required.

---

## Failure Scenario 2

Coordinator crashes.

Workflow incomplete.

Recovery needed.

---

## Failure Scenario 3

Duplicate event.

Idempotency required.

---

## Failure Scenario 4

Network timeout.

Unknown outcome.

Recovery logic needed.

---

## Trade-Offs

### Two-Phase Commit

Benefits:

- strong consistency

Costs:

- slow
- blocking

---

### Sagas

Benefits:

- scalable
- cloud-friendly

Costs:

- eventual consistency
- compensation complexity

---

## Common Mistakes

### Mistake 1

Ignoring compensation logic.

### Mistake 2

No idempotency.

### Mistake 3

Assuming retries are harmless.

### Mistake 4

Using 2PC everywhere.

### Mistake 5

Ignoring eventual consistency.

---

## Interview Questions

1. What is a distributed transaction?
2. Why are distributed transactions difficult?
3. What is Two-Phase Commit?
4. What are the phases of 2PC?
5. Why is 2PC unpopular in cloud systems?
6. What is a saga?
7. What is a compensating action?
8. What is orchestration?
9. What is choreography?
10. What is eventual consistency?
11. Why is idempotency important?
12. What is the Outbox Pattern?
13. How would SyncGrid use sagas?
14. How would NOMMO use sagas?
15. How would VaultBox use sagas?

---

## Exercises

1. Design a checkout saga.
2. Design a SyncGrid saga.
3. Design a VaultBox saga.
4. Design an inFlowForge saga.
5. Design a NOMMO deployment saga.
6. Explain compensation logic.
7. Compare 2PC and sagas.
8. Explain idempotency.
9. Explain eventual consistency.
10. Explain why distributed transactions are difficult.

---

## Further Reading

Designing Data Intensive Applications

https://dataintensive.net

Saga Pattern

https://microservices.io/patterns/data/saga.html

Martin Fowler

https://martinfowler.com

---

## Summary

Distributed transactions coordinate work across multiple services.

Traditional systems often use:

- Two-Phase Commit

Modern cloud systems frequently prefer:

- Sagas
- Compensation
- Eventual Consistency

These approaches enable scalable and resilient distributed architectures.
