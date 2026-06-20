# Lesson 06: Platform Reliability And SRE

## Learning Objectives

- Understand Site Reliability Engineering.
- Understand platform reliability.
- Understand SLIs, SLOs and SLAs.
- Understand error budgets.
- Understand operational excellence.

---

## Introduction

Building platforms is not enough.

Platforms must remain reliable.

Platform engineers and SREs work together to ensure systems remain healthy and available.

---

## What Is SRE?

Site Reliability Engineering is the application of software engineering principles to operations and reliability.

Goal:

Reliable systems at scale.

---

## Reliability Goals

Examples:

- 99.9% uptime
- low latency
- predictable performance
- fast recovery

---

## SLI

Service Level Indicator.

Measurement.

Examples:

- latency
- availability
- error rate

---

## SLO

Service Level Objective.

Target.

Example:

99.95% availability.

---

## SLA

Service Level Agreement.

Business commitment.

May involve penalties or credits.

---

## Error Budgets

Allowed unreliability.

Example:

99.9% uptime

↓

0.1% downtime allowed.

Helps balance innovation and stability.

---

## Incident Management

Process:

Detection

↓

Investigation

↓

Mitigation

↓

Recovery

↓

Postmortem

---

## Platform Reliability Responsibilities

- monitoring
- alerting
- incident response
- capacity planning
- resilience engineering

---

## Argus Connection

Argus directly supports:

- metrics
- alerts
- observability
- reliability

---

## NOMMO Connection

NOMMO reliability concerns:

- scheduler health
- node availability
- deployment recovery

---

## Summary

Reliable platforms require engineering discipline, observability and operational excellence.
