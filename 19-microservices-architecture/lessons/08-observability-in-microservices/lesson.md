# Lesson 08: Observability In Microservices

## Learning Objectives

- Understand observability challenges.
- Understand distributed tracing.
- Understand correlation IDs.
- Understand centralized logging.
- Understand metrics collection.
- Understand service monitoring.

---

## Introduction

Observability becomes harder as systems become distributed.

Monolith:

Request

↓

Application

↓

Database

Easy.

Microservices:

Request

↓

Gateway

↓

Auth

↓

Billing

↓

Provider

↓

Database

Visibility becomes difficult.

---

## Why Observability Matters

Questions:

- Which service failed?
- Where did latency occur?
- Which dependency is slow?
- Why did request fail?

Observability answers these questions.

---

## Three Pillars

### Logs

Events.

### Metrics

Measurements.

### Traces

Request journeys.

---

## Centralized Logging

All logs collected in one place.

Benefits:

- searchability
- debugging
- visibility

Examples:

- ELK
- OpenSearch
- Loki

---

## Correlation IDs

Unique request identifier.

Request enters gateway.

↓

Correlation ID generated.

↓

Propagated everywhere.

Allows tracing across services.

---

## Distributed Tracing

Tracks request flow.

Example:

Gateway

↓

Auth

↓

Billing

↓

Provider

Latency visible at each step.

---

## Popular Tools

- OpenTelemetry
- Jaeger
- Zipkin
- Grafana Tempo

---

## Metrics

Examples:

- latency
- throughput
- error rate
- saturation

Collected continuously.

---

## Dashboards

Provide visibility.

Examples:

- Grafana
- Datadog
- New Relic

---

## Alerts

Detect issues automatically.

Examples:

- error rate spike
- latency increase
- node failure

---

## SyncGrid Example

Observe:

- webhook latency
- provider failures
- queue depth

---

## VaultBox Example

Observe:

- uploads
- storage latency
- quota processing

---

## inFlowForge Example

Observe:

- workflow execution time
- queue backlog
- retry volume

---

## NOMMO Example

Observe:

- node health
- scheduling latency
- heartbeat failures

---

## Common Mistakes

- missing correlation IDs
- local-only logs
- no tracing
- poor dashboards

---

## Interview Questions

1. What is observability?
2. What are the three pillars?
3. What is distributed tracing?
4. What is a correlation ID?
5. Why are centralized logs useful?

---

## Summary

Microservices require strong observability because failures and latency become harder to locate as systems grow.
