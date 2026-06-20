# Lesson 09: System Design Interviews

## Learning Objectives

By the end of this lesson you should be able to:

- Understand the purpose of system design interviews.
- Approach system design questions methodically.
- Gather requirements effectively.
- Estimate scale.
- Communicate trade-offs.
- Design systems under constraints.
- Avoid common interview mistakes.

---

## Introduction

Many developers approach system design interviews incorrectly.

They think:

    The goal is to find the perfect architecture.

It is not.

The goal is to demonstrate engineering thinking.

Interviewers want to see:

- problem solving
- communication
- trade-off analysis
- scalability reasoning
- architectural judgment

A good interview is a collaborative discussion.

Not a memorization contest.

---

## What Interviewers Evaluate

Interviewers are usually assessing:

### Requirements Gathering

Can you clarify ambiguity?

### System Thinking

Can you see the entire system?

### Scalability

Can your design grow?

### Reliability

Can your design survive failures?

### Communication

Can others understand your reasoning?

### Trade-Off Analysis

Can you justify decisions?

---

## Common Interview Questions

Examples:

- Design WhatsApp
- Design Twitter
- Design YouTube
- Design Dropbox
- Design Uber
- Design Google Drive
- Design a URL Shortener
- Design a Notification Service
- Design a Payment Platform
- Design a Monitoring System

The specific product matters less than the approach.

---

## The System Design Framework

A practical framework:

1. Clarify requirements
2. Estimate scale
3. Design high-level architecture
4. Design data model
5. Identify bottlenecks
6. Scale the system
7. Discuss failures
8. Discuss trade-offs

Use this repeatedly.

---

## Step 1: Clarify Requirements

Never start drawing architecture immediately.

Example:

Design Dropbox.

Questions:

- File size limits?
- Public or private files?
- Expected users?
- Download traffic?
- Version history?
- Mobile support?

Clarification often determines architecture.

---

## Functional Requirements

Ask:

What must the system do?

Example:

URL Shortener:

- shorten URLs
- redirect URLs
- analytics
- expiration

These define core functionality.

---

## Non-Functional Requirements

Ask:

How well must it perform?

Examples:

- latency
- availability
- scalability
- reliability
- consistency

Many candidates forget this step.

---

## Step 2: Estimate Scale

Back-of-the-envelope estimation is important.

Example:

Users:

    10 million

Daily requests:

    100 million

Average request:

    2KB

Daily traffic:

    200GB

The goal is not precision.

The goal is understanding magnitude.

---

## Capacity Planning Example

Example:

5 million uploads/day

Average file:

    10MB

Storage:

    50TB/day

Now architecture choices become clearer.

---

## Step 3: High-Level Architecture

Draw major components first.

Example:

Users

↓

Load Balancer

↓

API Cluster

↓

Cache

↓

Database

Avoid jumping into details immediately.

---

## Good Architecture Discussion

Explain:

- why Redis exists
- why PostgreSQL exists
- why queues exist
- why workers exist

Interviewers care about reasoning.

---

## Step 4: Data Model

Discuss:

- users
- files
- workflows
- messages
- transactions

Example:

URL Shortener

Table:

    short_urls

Fields:

    id
    short_code
    destination
    created_at

Simple.

Clear.

---

## Step 5: Identify Bottlenecks

Ask:

What breaks first?

Potential bottlenecks:

- database
- cache
- queue
- workers
- network
- storage

Good engineers anticipate bottlenecks.

---

## Step 6: Scaling Discussion

Example:

Traffic grows.

Possible improvements:

- load balancing
- caching
- read replicas
- worker scaling
- partitioning

Discuss progressively.

Avoid premature complexity.

---

## Step 7: Failure Analysis

Many candidates forget this.

Ask:

What happens if:

- database fails?
- Redis fails?
- workers fail?
- network fails?

Failure discussions often differentiate strong candidates.

---

## Step 8: Trade-Offs

Every design has trade-offs.

Example:

Redis Cache

Benefits:

- speed

Costs:

- invalidation complexity

Interviewers love trade-off discussions.

---

## Example Question: Design VaultBox

Requirements:

- upload files
- download files
- quotas
- permissions

Architecture:

Users

↓

Load Balancer

↓

API

↓

Redis

↓

PostgreSQL

↓

Object Storage

Scaling:

- cache metadata
- add read replicas
- add workers

Trade-offs:

- consistency vs speed
- storage cost vs performance

---

## Example Question: Design SyncGrid

Requirements:

- provider integrations
- webhooks
- API keys

Architecture:

Users

↓

API

↓

Redis

↓

PostgreSQL

↓

Webhook Queue

↓

Workers

Focus:

- retries
- scalability
- provider failures

---

## Example Question: Design inFlowForge

Requirements:

- workflows
- triggers
- actions

Architecture:

Users

↓

API

↓

Queue

↓

Workers

↓

External Services

Focus:

- asynchronous processing
- retries
- monitoring

---

## Whiteboard Communication

Good candidates:

- speak clearly
- explain assumptions
- narrate decisions

Bad candidates:

- silently draw boxes

Communication matters.

---

## Time Management

Typical interview:

45 minutes

Suggested allocation:

Requirements:
    5 minutes

Scale:
    5 minutes

Architecture:
    15 minutes

Scaling:
    10 minutes

Failures:
    5 minutes

Trade-offs:
    5 minutes

---

## Common Mistakes

### Mistake 1

Jumping into technology immediately.

### Mistake 2

Ignoring requirements.

### Mistake 3

Ignoring scale.

### Mistake 4

No trade-off discussion.

### Mistake 5

No failure analysis.

### Mistake 6

Over-engineering.

### Mistake 7

Not communicating.

### Mistake 8

Memorizing architectures.

---

## What Strong Candidates Do

Strong candidates:

- clarify assumptions
- estimate scale
- reason systematically
- discuss trade-offs
- discuss failures
- communicate clearly

---

## What Weak Candidates Do

Weak candidates:

- memorize diagrams
- skip requirements
- skip scaling
- skip reliability
- jump to technologies

---

## Interview Checklist

Before finishing:

✓ Requirements clarified

✓ Scale estimated

✓ Architecture drawn

✓ Data model discussed

✓ Bottlenecks identified

✓ Scaling strategy discussed

✓ Failure scenarios covered

✓ Trade-offs explained

---

## Failure Scenario Discussion

Example:

Redis unavailable.

Possible response:

- bypass cache
- read database directly
- accept increased latency

This demonstrates operational thinking.

---

## Interview Questions

1. Why clarify requirements?
2. Why estimate scale?
3. Why discuss bottlenecks?
4. Why discuss failures?
5. Why discuss trade-offs?
6. What is capacity planning?
7. How would you design a file storage platform?
8. How would you design a workflow engine?
9. How would you scale a growing API?
10. What makes a good system design answer?

---

## Exercises

1. Design a URL shortener.
2. Design a notification service.
3. Design a monitoring platform.
4. Design a payment platform.
5. Design a chat application.
6. Design a file storage service.
7. Design an orchestration platform.
8. Identify trade-offs in VaultBox.
9. Identify trade-offs in SyncGrid.
10. Identify trade-offs in NOMMO.

---

## Further Reading

System Design Primer

https://github.com/donnemartin/system-design-primer

Designing Data Intensive Applications

https://dataintensive.net

Grokking System Design

https://www.designgurus.io

---

## Summary

System design interviews are not about perfect architectures.

They are about demonstrating:

- structured thinking
- scalability reasoning
- communication
- trade-off analysis
- engineering judgment

The best answers are systematic, practical and well-reasoned.
