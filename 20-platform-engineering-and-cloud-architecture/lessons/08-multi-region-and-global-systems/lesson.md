# Lesson 08: Multi-Region And Global Systems

## Learning Objectives

- Understand multi-region systems.
- Understand geographic distribution.
- Understand disaster recovery.
- Understand global availability.
- Understand trade-offs.

---

## Introduction

As systems grow globally, a single region becomes risky.

Example:

Entire region fails.

↓

Service unavailable.

Multi-region architecture reduces this risk.

---

## Regions

Cloud providers operate multiple regions.

Examples:

- us-east
- eu-west
- ap-southeast

Each region is independent.

---

## Availability Zones

Regions contain multiple availability zones.

Purpose:

Reduce local failures.

---

## Multi-Region Benefits

- higher availability
- disaster recovery
- lower latency
- global reach

---

## Multi-Region Challenges

- replication
- consistency
- cost
- complexity

---

## Disaster Recovery

Questions:

- How quickly can recovery occur?
- How much data can be lost?

Important metrics:

RTO

Recovery Time Objective

RPO

Recovery Point Objective

---

## Active-Passive

Primary region active.

Secondary region waiting.

Failover occurs during disaster.

---

## Active-Active

Multiple regions serve traffic simultaneously.

Higher availability.

More complexity.

---

## Global Load Balancing

Traffic routed intelligently.

Benefits:

- lower latency
- resilience
- better user experience

---

## SyncGrid Example

Future architecture:

Multiple regions.

Provider routing remains operational during regional failures.

---

## VaultBox Example

Files replicated across regions.

Improved durability.

---

## NOMMO Example

Control plane distributed across regions.

Improved survivability.

---

## Summary

Multi-region architectures improve resilience and global reach at the cost of additional complexity.
