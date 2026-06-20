# Lesson 06: Service Discovery And Coordination

## Learning Objectives

By the end of this lesson you should be able to:

- Explain service discovery.
- Understand dynamic infrastructure.
- Understand service registration.
- Understand service lookup.
- Understand coordination systems.
- Explain the role of etcd, Consul and ZooKeeper.
- Design service discovery architectures.

---

## Introduction

In small systems, service locations are often hardcoded.

Example:

    DATABASE_HOST=10.0.0.5

Simple.

But what happens when:

- servers restart
- IP addresses change
- containers move
- nodes fail

Hardcoded addresses stop working.

Distributed systems solve this through service discovery.

---

## What Is Service Discovery?

Service discovery is the process of locating services dynamically.

Instead of:

    Payment API = 10.0.0.5

Applications ask:

    Where is Payment API?

The infrastructure provides the answer.

---

## Why Service Discovery Exists

Modern infrastructure changes constantly.

Examples:

- containers start
- containers stop
- nodes fail
- deployments occur
- autoscaling happens

Static configuration becomes unreliable.

---

## Service Registry

Most discovery systems use a registry.

Architecture:

Service

↓

Registry

↓

Consumers

The registry stores service locations.

---

## Registration

When a service starts:

Example:

    payments-api

Registers itself.

Registry stores:

- name
- address
- port
- health status

---

## Lookup

Consumers query registry.

Example:

    Where is payments-api?

Registry responds:

    10.0.1.25:3000

Connection established.

---

## Basic Discovery Architecture

           Registry
               |
     -------------------
     |                 |
     v                 v
 Service A        Service B

Services register.

Consumers discover.

---

## DNS-Based Discovery

A common approach.

Example:

    payments.internal

DNS resolves to current service location.

Widely used in cloud systems.

---

## Client-Side Discovery

Client queries registry directly.

Architecture:

Client

↓

Registry

↓

Service

Benefits:

- flexible

Costs:

- more client complexity

---

## Server-Side Discovery

Client contacts load balancer.

Load balancer performs lookup.

Architecture:

Client

↓

Load Balancer

↓

Registry

↓

Service

Simpler for clients.

---

## Health Checks

Service discovery requires health information.

Example:

Service crashes.

Registry removes service.

Traffic stops flowing to unhealthy node.

---

## Coordination

Discovery alone is not enough.

Distributed systems often require coordination.

Examples:

- leader election
- configuration management
- distributed locks
- membership tracking

---

## Coordination Systems

Popular examples:

### ZooKeeper

Apache coordination system.

### etcd

Used by Kubernetes.

### Consul

Service discovery and coordination.

---

## Why Coordination Exists

Without coordination:

Nodes may disagree.

Example:

Two schedulers assign same task.

Result:

Duplicate work.

Coordination prevents conflicts.

---

## Cluster Membership

Question:

Which nodes belong to cluster?

Membership tracking answers:

- who joined
- who left
- who failed

Important for orchestration systems.

---

## Dynamic Infrastructure

Modern infrastructure is dynamic.

Examples:

- Kubernetes pods
- Docker containers
- cloud instances

Discovery systems track these changes automatically.

---

## Service Discovery In Kubernetes

Pod starts.

↓

Registers.

↓

Receives service endpoint.

↓

Traffic begins.

Discovery is automatic.

---

## Service Discovery In NOMMO

Potential architecture:

Worker

↓

Registry

↓

Control Plane

Registry tracks:

- worker ID
- capabilities
- status
- address

Control plane can locate workers dynamically.

---

## Service Discovery In Argus

Agents register.

↓

Registry stores information.

↓

Monitoring platform locates agents.

---

## Service Discovery In SyncGrid

Potential discovery targets:

- providers
- workers
- webhook processors

---

## Failure Scenario 1

Service crashes.

Registry removes entry.

Traffic rerouted.

---

## Failure Scenario 2

Stale registry entry.

Clients receive invalid address.

Requests fail.

---

## Failure Scenario 3

Registry unavailable.

Discovery stops.

System degrades.

---

## Failure Scenario 4

Incorrect health checks.

Healthy service removed.

Traffic disrupted.

---

## Trade-Offs

### Central Registry

Benefits:

- simplicity

Costs:

- potential bottleneck

---

### Distributed Registry

Benefits:

- reliability

Costs:

- complexity

---

## Common Mistakes

### Mistake 1

Hardcoding service addresses.

### Mistake 2

Ignoring health checks.

### Mistake 3

No service registration.

### Mistake 4

No membership tracking.

### Mistake 5

No coordination strategy.

---

## Interview Questions

1. What is service discovery?
2. Why is service discovery needed?
3. What is a service registry?
4. What is service registration?
5. What is service lookup?
6. What is coordination?
7. What is cluster membership?
8. What is etcd?
9. What is ZooKeeper?
10. What is Consul?
11. How does Kubernetes perform service discovery?
12. How would NOMMO use service discovery?

---

## Exercises

1. Draw a service discovery architecture.
2. Design service registration for NOMMO.
3. Design membership tracking.
4. Compare client-side and server-side discovery.
5. Explain coordination systems.
6. Explain health checks.
7. Explain dynamic infrastructure.
8. Design a registry schema.
9. Explain registry failure scenarios.
10. Explain why discovery becomes critical at scale.

---

## Further Reading

etcd

https://etcd.io

Consul

https://www.consul.io

ZooKeeper

https://zookeeper.apache.org

Kubernetes Services

https://kubernetes.io/docs/concepts/services-networking/service/

---

## Summary

Service discovery enables systems to locate services dynamically.

Coordination systems extend this capability by helping distributed systems agree on membership, leadership and shared state.
