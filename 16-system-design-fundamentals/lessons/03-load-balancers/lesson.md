# Lesson 03: Load Balancers

## Learning Objectives

By the end of this lesson you should be able to:

- Explain load balancers.
- Understand why load balancers exist.
- Understand reverse proxies.
- Explain load balancing algorithms.
- Understand health checks.
- Understand failover.
- Design scalable API architectures.

---

## Introduction

Imagine you have a Fastify API.

Architecture:

        Users
          |
          v
        API

Works fine.

Until traffic grows.

Example:

    100 users

becomes

    100,000 users

One server eventually becomes overloaded.

You need a way to distribute traffic.

That is where load balancers help.

---

## What Is A Load Balancer?

A load balancer sits between clients and servers.

Diagram:

            Users
              |
              v
       Load Balancer
              |
      ----------------
      |      |       |
      v      v       v
    API1   API2    API3

Instead of all requests hitting one server:

Traffic is distributed.

---

## Why Load Balancers Exist

Without load balancing:

            Users
              |
              v
             API

Problems:

- CPU overload
- Memory exhaustion
- Slow response times
- Single point of failure

With load balancing:

            Users
              |
              v
       Load Balancer
              |
      ----------------
      |      |       |
      v      v       v
    API1   API2    API3

Benefits:

- scalability
- fault tolerance
- higher availability

---

## Reverse Proxy

Most load balancers are reverse proxies.

Client thinks:

    Talking to one server

Reality:

Client talks to load balancer.

Load balancer talks to backend servers.

Diagram:

Client

↓

Load Balancer

↓

Backend Servers

---

## Forward Proxy vs Reverse Proxy

Forward Proxy:

Protects clients.

Example:

Corporate internet proxy.

Client

↓

Proxy

↓

Internet

Reverse Proxy:

Protects servers.

Client

↓

Reverse Proxy

↓

Backend Servers

---

## Basic Traffic Distribution

Goal:

Spread requests evenly.

Example:

Request 1 → API1

Request 2 → API2

Request 3 → API3

Request 4 → API1

And so on.

---

## Round Robin

Most common algorithm.

Requests distributed sequentially.

Example:

Request 1 → API1

Request 2 → API2

Request 3 → API3

Request 4 → API1

Request 5 → API2

Request 6 → API3

Benefits:

- simple
- predictable

Drawbacks:

- ignores server load

---

## Weighted Round Robin

Not all servers are equal.

Example:

API1:

    16 CPU

API2:

    8 CPU

API3:

    8 CPU

Weights:

API1:

    50%

API2:

    25%

API3:

    25%

More traffic goes to stronger servers.

---

## Least Connections

Route requests to server with fewest active connections.

Example:

API1:

    500 connections

API2:

    30 connections

API3:

    40 connections

New request:

↓

API2

Benefits:

- adapts to workload

Often better than round robin.

---

## Least Response Time

Traffic goes to fastest server.

Example:

API1

    120ms

API2

    40ms

API3

    60ms

New requests favor API2.

---

## IP Hash

Client IP determines server.

Example:

192.168.1.1

↓

API2

Same user often reaches same server.

Useful for:

- legacy session systems
- sticky sessions

---

## Sticky Sessions

Normally:

Request A

↓

API1

Request B

↓

API2

Request C

↓

API3

Sticky sessions:

Same user always routed to same server.

Benefits:

- session compatibility

Drawbacks:

- uneven load distribution

Modern systems prefer stateless APIs instead.

---

## Health Checks

What if a server crashes?

Without health checks:

Load balancer continues sending traffic.

Users receive errors.

Health checks solve this.

---

## Health Check Example

Every few seconds:

Load Balancer

↓

GET /health

Server Response:

    200 OK

Server considered healthy.

---

## Failed Health Check

Example:

API2 crashes.

Health check fails.

Diagram:

       Load Balancer
             |
     ----------------
     |              |
     v              v
   API1           API3

Traffic automatically bypasses API2.

---

## High Availability

Load balancing improves availability.

Single server:

        Users
          |
          v
         API

Failure:

Everything down.

Multiple servers:

      Load Balancer
             |
     ----------------
     |      |       |
     v      v       v
   API1   API2    API3

One failure does not destroy system.

---

## Active-Passive Failover

Architecture:

Primary

↓

Backup

Backup waits.

If primary fails:

Backup takes over.

Benefits:

- simple

Drawbacks:

- wasted resources

---

## Active-Active Architecture

All servers handle traffic.

Example:

      Load Balancer
             |
     ----------------
     |      |       |
     v      v       v
   API1   API2    API3

Benefits:

- efficient
- scalable

Most modern systems prefer this.

---

## Nginx

One of the most popular load balancers.

Common uses:

- reverse proxy
- load balancing
- SSL termination
- caching

Example:

    upstream backend {
      server api1:3000;
      server api2:3000;
      server api3:3000;
    }

---

## HAProxy

Purpose-built load balancer.

Popular in:

- fintech
- SaaS
- enterprise systems

Known for:

- performance
- reliability

---

## Cloud Load Balancers

Cloud providers offer managed solutions.

Examples:

AWS:

    Application Load Balancer

Google:

    Cloud Load Balancer

Azure:

    Azure Load Balancer

Benefits:

- managed
- scalable
- highly available

---

## SSL Termination

HTTPS is expensive.

Instead:

Client

↓

HTTPS

↓

Load Balancer

↓

HTTP

↓

Backend Servers

Load balancer handles encryption.

Backend servers do less work.

---

## Real World Example

Consider SyncGrid.

Phase 1:

            Users
              |
              v
            API

Phase 2:

            Users
              |
              v
       Load Balancer
              |
      ----------------
      |      |       |
      v      v       v
    API1   API2    API3

Phase 3:

            Users
              |
              v
       Load Balancer
              |
      ----------------
      |      |       |
      v      v       v
    API1   API2    API3
      |
      v
     Redis
      |
      v
 PostgreSQL

This is a typical scaling evolution.

---

## Failure Scenarios

### Scenario 1

One API server crashes.

Health checks remove it.

Users unaffected.

---

### Scenario 2

Traffic spike.

Load balancer distributes requests.

System survives.

---

### Scenario 3

Load balancer crashes.

Entire system becomes unavailable.

Solution:

Redundant load balancers.

---

### Scenario 4

Uneven server capacity.

Round robin overloads smaller servers.

Solution:

Weighted balancing.

---

## Common Mistakes

### Mistake 1

Using sticky sessions unnecessarily.

### Mistake 2

No health checks.

### Mistake 3

Single load balancer.

### Mistake 4

Ignoring server capacity differences.

### Mistake 5

Keeping APIs stateful.

---

## Interview Questions

1. What is a load balancer?
2. Why use load balancing?
3. What is a reverse proxy?
4. What is round robin?
5. What is weighted round robin?
6. What is least connections?
7. What are sticky sessions?
8. Why are health checks important?
9. What is SSL termination?
10. Difference between active-passive and active-active?

---

## Exercises

1. Draw a three-node API cluster.
2. Explain why a load balancer improves availability.
3. Compare round robin and least connections.
4. Explain sticky sessions.
5. Design a load-balanced architecture for VaultBox.
6. Design a load-balanced architecture for inFlowForge.

---

## Further Reading

Nginx Documentation

https://nginx.org

HAProxy Documentation

https://www.haproxy.org

AWS Load Balancing

https://aws.amazon.com/elasticloadbalancing/

Google Cloud Load Balancing

https://cloud.google.com/load-balancing

---

## Summary

Load balancers are one of the most important components in scalable architectures.

They:

- distribute traffic
- improve availability
- enable horizontal scaling
- support failover
- improve reliability

Nearly every modern production platform uses load balancing in some form.
