# Lesson 02: Service Boundaries And Domain Design

## Learning Objectives

By the end of this lesson you should be able to:

- Understand service boundaries.
- Explain bounded contexts.
- Identify business domains.
- Avoid poor service decomposition.
- Design maintainable microservice architectures.
- Understand coupling and cohesion.

---

## Introduction

The hardest part of microservices is not:

- Docker
- Kubernetes
- APIs
- Messaging

The hardest part is deciding:

    Where should service boundaries exist?

Bad boundaries create:

- complexity
- duplication
- tight coupling
- operational pain

Good boundaries create:

- autonomy
- ownership
- scalability

---

## The Core Question

Imagine building SyncGrid.

Should you create:

Auth Service

Billing Service

Webhook Service

Provider Service

API Key Service

Or something else?

Choosing correctly is difficult.

---

## What Is A Domain?

A domain is a business area.

Examples:

Banking:

- Accounts
- Payments
- Loans

E-Commerce:

- Orders
- Inventory
- Payments

SyncGrid:

- Providers
- Billing
- Webhooks
- Teams

Domains help identify boundaries.

---

## Domain Driven Design (DDD)

Popular design methodology.

Encourages organizing systems around business concepts.

Not technical layers.

Focus:

Business capabilities.

---

## Bounded Context

A bounded context defines a clear area of responsibility.

Example:

Billing Context

Owns:

- invoices
- subscriptions
- charges

Only billing handles billing logic.

---

## Why Bounded Contexts Matter

Without boundaries:

Business rules become scattered.

Result:

Confusion.

Duplication.

Coupling.

Bounded contexts reduce chaos.

---

## Example: E-Commerce

Bad:

User Service owns:

- users
- orders
- inventory
- payments

Too much responsibility.

---

Better:

User Service

Order Service

Inventory Service

Payment Service

Clear ownership.

---

## High Cohesion

A service should contain related functionality.

Example:

Billing Service:

- invoices
- subscriptions
- payments

Related concepts.

High cohesion.

---

## Low Cohesion

Example:

Billing Service:

- payments
- image uploads
- notifications

Unrelated responsibilities.

Poor cohesion.

---

## Loose Coupling

Services should depend on each other as little as possible.

Benefits:

- easier deployment
- easier testing
- independent evolution

---

## Tight Coupling

Example:

Service A cannot function without Service B.

Service B cannot function without Service C.

Changes become risky.

---

## SyncGrid Example

Potential domains:

Identity

Billing

Provider Routing

Webhooks

Analytics

Each could become a service.

---

## VaultBox Example

Potential domains:

Authentication

Storage

Billing

Analytics

Permissions

Clear separation possible.

---

## inFlowForge Example

Potential domains:

Workflow Management

Execution Engine

Triggers

Notifications

Audit Logs

---

## NOMMO Example

Potential domains:

Scheduler

Registry

Orchestrator

Monitoring

Routing

Strong natural boundaries.

---

## The Database Mistake

Many beginners split services like this:

User Service

↓

Shared Database

Order Service

↓

Shared Database

Payment Service

↓

Shared Database

Not true independence.

Database coupling remains.

---

## Database Per Service

Preferred model:

User Service

↓

User Database

Order Service

↓

Order Database

Payment Service

↓

Payment Database

Ownership becomes clearer.

---

## Service Ownership

A service should own:

- business logic
- database
- APIs
- lifecycle

Ownership reduces ambiguity.

---

## Service Size

Microservice does not mean:

Tiny service.

Avoid:

NotificationEmailTemplateService

NotificationSMTPService

NotificationButtonColorService

Excessive fragmentation.

---

## The Distributed Monolith

Dangerous anti-pattern.

Looks like microservices.

Behaves like monolith.

Symptoms:

- constant synchronous calls
- shared database
- coordinated deployments

Complexity without benefits.

---

## Team Alignment

Service boundaries often align with teams.

Example:

Billing Team

↓

Billing Service

Identity Team

↓

Auth Service

Operational ownership improves.

---

## Evolutionary Design

Boundaries change over time.

Normal.

Good architects evolve services gradually.

Avoid permanent assumptions.

---

## Failure Scenario 1

Poor boundary.

Service becomes huge.

Maintenance suffers.

---

## Failure Scenario 2

Too many services.

Operational complexity explodes.

---

## Failure Scenario 3

Shared database.

Teams become tightly coupled.

---

## Failure Scenario 4

Domain ownership unclear.

Responsibilities overlap.

---

## Trade-Offs

### Larger Services

Benefits:

- simpler operations

Costs:

- broader responsibility

---

### Smaller Services

Benefits:

- focused ownership

Costs:

- more complexity

---

## Common Mistakes

### Mistake 1

Splitting by technical layer.

### Mistake 2

Creating services too early.

### Mistake 3

Shared databases.

### Mistake 4

Ignoring domains.

### Mistake 5

Excessive fragmentation.

---

## Interview Questions

1. What is a domain?
2. What is a bounded context?
3. What is cohesion?
4. What is coupling?
5. Why is service ownership important?
6. Why avoid shared databases?
7. What is a distributed monolith?
8. How would you decompose SyncGrid?
9. How would you decompose VaultBox?
10. How would you decompose NOMMO?

---

## Exercises

1. Identify domains in SyncGrid.
2. Identify domains in VaultBox.
3. Identify domains in NOMMO.
4. Design service boundaries for inFlowForge.
5. Explain bounded contexts.
6. Explain cohesion.
7. Explain coupling.
8. Explain distributed monoliths.
9. Compare shared databases vs database-per-service.
10. Design a service ownership model.

---

## Further Reading

Domain Driven Design

https://domainlanguage.com

Martin Fowler

https://martinfowler.com

Microservices.io

https://microservices.io

---

## Summary

Good microservices begin with good boundaries.

The most successful architectures are organized around:

- business capabilities
- ownership
- bounded contexts
- clear responsibilities

Technology choices matter.

Service boundaries matter more.
