# Lesson 06: Message Queues & Event-Driven Architecture

## Learning Objectives

By the end of this lesson you should be able to:

- Explain message queues.
- Understand event-driven architecture.
- Distinguish synchronous and asynchronous systems.
- Design producer-consumer workflows.
- Understand event propagation.
- Design scalable background processing systems.
- Analyze queue-based architectures.

---

## Introduction

One of the biggest mistakes junior developers make is trying to do everything during a request.

Example:

User signs up.

Application:

- creates account
- sends email
- generates profile
- creates workspace
- sends notification
- calls external APIs

All during a single HTTP request.

Result:

Slow responses.

Fragile systems.

Poor scalability.

Message queues solve this problem.

---

## The Synchronous Model

Traditional request flow:

    Client
       |
       v
      API
       |
       v
    Database

Request waits until work completes.

Simple.

Easy to understand.

Works well initially.

---

## The Problem With Synchronous Systems

Example:

User registers.

Request performs:

1. Create user
2. Send email
3. Create workspace
4. Generate analytics profile
5. Notify CRM
6. Send webhook

Architecture:

Client

↓

API

↓

Email

↓

CRM

↓

Webhook

↓

Database

The request becomes slow.

Failure in one dependency can break everything.

---

## The Asynchronous Model

Instead:

Client

↓

API

↓

Queue

↓

Response

Worker processes remaining tasks later.

Benefits:

- faster responses
- improved scalability
- better reliability

---

## What Is A Message Queue?

A queue stores work until a worker processes it.

Architecture:

Producer

↓

Queue

↓

Consumer

The producer creates work.

The consumer performs work.

---

## Queue Analogy

Think of a restaurant.

Customer:

Places order.

↓

Kitchen queue.

↓

Chef prepares food.

Customer does not cook the meal.

The queue separates responsibilities.

---

## Producer

A producer creates jobs.

Example:

User registers.

Application publishes:

    UserRegistered

event.

Producer responsibility:

Generate work.

Not execute work.

---

## Consumer

Consumer processes jobs.

Example:

UserRegistered

↓

Send Welcome Email

Consumer responsibility:

Execute work.

---

## Queue Benefits

Queues provide:

- decoupling
- scalability
- fault tolerance
- retries
- buffering

---

## Decoupling

Without queue:

API directly depends on email service.

Architecture:

API

↓

Email Service

If email service fails:

Request may fail.

---

With queue:

API

↓

Queue

↓

Email Worker

Email service failure does not immediately affect user requests.

---

## Buffering

Traffic is rarely constant.

Example:

Normal traffic:

    100 jobs/minute

Traffic spike:

    50,000 jobs/minute

Queue absorbs the spike.

Workers process jobs gradually.

---

## Event-Driven Architecture

Instead of direct calls:

Systems communicate through events.

Example:

UserRegistered

↓

Multiple consumers react

Architecture:

              UserRegistered
                     |
       --------------------------------
       |              |              |
       v              v              v
 Email Service   CRM Service   Analytics Service

Publisher does not know who consumes the event.

---

## What Is An Event?

An event describes something that happened.

Examples:

    UserRegistered

    PaymentCompleted

    FileUploaded

    WorkflowExecuted

    ServiceFailed

Events describe facts.

Not commands.

---

## Commands vs Events

Command:

    SendWelcomeEmail

Meaning:

Do something.

Event:

    UserRegistered

Meaning:

Something happened.

Event-driven systems usually prefer events.

---

## Event Flow Example

User registers.

API publishes:

    UserRegistered

Consumers:

- Email Worker
- Analytics Worker
- CRM Worker

Each reacts independently.

---

## Queue Architecture

                Producer
                    |
                    v
                 Queue
                    |
         -----------------------
         |          |          |
         v          v          v
      Worker1    Worker2    Worker3

Workers scale independently.

---

## Horizontal Scaling

One worker:

    100 jobs/minute

Five workers:

    500 jobs/minute

Approximate capacity increases.

This makes queues naturally scalable.

---

## Queue Persistence

Important question:

What happens if worker crashes?

Reliable queues persist jobs.

Job remains stored.

Another worker can process it later.

This improves reliability.

---

## At-Most-Once Delivery

Message processed:

0 or 1 time.

Risk:

Lost work.

---

## At-Least-Once Delivery

Message processed:

1 or more times.

Risk:

Duplicates.

Most production systems choose this model.

---

## Exactly-Once Delivery

The ideal.

Extremely difficult.

Usually requires significant complexity.

Many systems claim exactly-once behavior but implement sophisticated approximations.

---

## Idempotency

Critical concept.

Operation can run multiple times safely.

Example:

Bad:

Charge credit card twice.

Good:

Detect duplicate transaction.

Process once.

Queues often require idempotent consumers.

---

## Dead Letter Queues

Some jobs always fail.

Example:

Invalid payload.

Corrupted data.

Missing resource.

Retries won't help.

Architecture:

Queue

↓

Retry

↓

Retry

↓

Retry

↓

Dead Letter Queue

DLQ stores failed jobs for investigation.

---

## Retry Strategies

Simple retry:

Immediately retry.

Problem:

Can overload dependencies.

Better:

Backoff strategy.

---

## Exponential Backoff

Example:

Attempt 1:

    1 second

Attempt 2:

    2 seconds

Attempt 3:

    4 seconds

Attempt 4:

    8 seconds

Reduces pressure during failures.

---

## Event Ordering

Ordering can matter.

Example:

    AccountCreated

must happen before

    AccountDeleted

Some systems require strict ordering.

Others do not.

Ordering guarantees often reduce scalability.

---

## Eventual Consistency

Event-driven systems frequently embrace eventual consistency.

Example:

User updates profile.

Analytics service updates 2 seconds later.

System is temporarily inconsistent.

Eventually consistent.

Many large systems operate this way.

---

## Event Storming

Useful design technique.

Identify events first.

Example:

UserRegistered

PaymentCompleted

FileUploaded

WorkflowStarted

WorkflowFinished

Then build services around events.

---

## Real World Example: SyncGrid

Event:

    WebhookReceived

Published.

Consumers:

- Delivery Worker
- Retry Worker
- Audit Worker

Benefits:

Independent scaling.

---

## Real World Example: VaultBox

Event:

    FileUploaded

Consumers:

- Virus Scanner
- Metadata Extractor
- Thumbnail Generator
- Audit Logger

Upload remains fast.

Processing occurs asynchronously.

---

## Real World Example: inFlowForge

Event:

    WorkflowTriggered

Consumers:

- Execution Engine
- Audit Logger
- Analytics Service

Workflow processing becomes highly scalable.

---

## Real World Example: Argus

Events:

    NodeDown

    ServiceRecovered

    HealthCheckFailed

Consumers:

- Alerting
- Dashboard
- Incident Tracking

Perfect fit for event-driven architecture.

---

## Real World Example: NOMMO

Events:

    WorkerJoined

    WorkerLeft

    ServiceFailed

    DeploymentStarted

Consumers:

- Scheduler
- Router
- Monitoring Engine
- State Manager

Distributed orchestration is fundamentally event-driven.

---

## Failure Scenario 1

Worker Crash

Worker dies during processing.

Reliable queue reassigns work.

No data loss.

---

## Failure Scenario 2

Traffic Spike

100x increase in jobs.

Queue absorbs spike.

Workers catch up gradually.

---

## Failure Scenario 3

Dependency Outage

Email provider unavailable.

Retries activate.

DLQ stores permanent failures.

---

## Failure Scenario 4

Duplicate Messages

Message delivered twice.

Non-idempotent consumer causes duplicate actions.

Solution:

Idempotency keys.

---

## Failure Scenario 5

Poison Message

Malformed payload always fails.

Without DLQ:

Infinite retries.

With DLQ:

Message isolated.

---

## Trade-Offs

### Synchronous

Benefits:

- simple
- predictable

Drawbacks:

- tightly coupled
- slower

---

### Event Driven

Benefits:

- scalable
- flexible
- resilient

Drawbacks:

- complexity
- debugging difficulty
- eventual consistency

---

### More Queues

Benefits:

- better separation

Costs:

- operational overhead

---

### Strong Ordering

Benefits:

- consistency

Costs:

- reduced scalability

---

## Common Mistakes

### Mistake 1

Doing heavy work inside requests.

### Mistake 2

No retries.

### Mistake 3

No DLQ.

### Mistake 4

Ignoring idempotency.

### Mistake 5

Treating queues like databases.

### Mistake 6

Creating events with unclear meaning.

### Mistake 7

Ignoring monitoring.

### Mistake 8

Building synchronous systems where asynchronous processing is appropriate.

---

## Interview Questions

1. What is a message queue?
2. Why use queues?
3. What is event-driven architecture?
4. Difference between synchronous and asynchronous processing?
5. What is a producer?
6. What is a consumer?
7. What is idempotency?
8. What is a dead letter queue?
9. What is exponential backoff?
10. What is eventual consistency?
11. What are events?
12. What are commands?
13. Why do queues improve scalability?
14. Why are workers useful?
15. How would you design a webhook processing system?

---

## Exercises

1. Design a queue architecture for SyncGrid webhooks.
2. Design a queue architecture for VaultBox uploads.
3. Design a queue architecture for inFlowForge workflow execution.
4. Explain why idempotency matters.
5. Compare synchronous and asynchronous systems.
6. Draw a producer-consumer architecture.
7. Design a retry strategy.
8. Design a DLQ strategy.
9. Identify events for NOMMO.
10. Identify events for Argus.

---

## Further Reading

BullMQ

https://docs.bullmq.io

RabbitMQ

https://www.rabbitmq.com

Apache Kafka

https://kafka.apache.org

AWS Event-Driven Architecture

https://aws.amazon.com/event-driven-architecture/

System Design Primer

https://github.com/donnemartin/system-design-primer

---

## Summary

Message queues and event-driven architectures are foundational building blocks of modern scalable systems.

They enable:

- decoupling
- scalability
- retries
- fault tolerance
- asynchronous processing

Many large-scale systems rely heavily on events and queues because they allow work to be distributed, retried and scaled independently of user-facing requests.
