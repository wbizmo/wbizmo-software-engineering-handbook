# Lesson 01: Introduction To Containers

## Learning Objectives

By the end of this lesson you should be able to:

- Explain containers.
- Explain virtualization.
- Explain why containers exist.
- Compare containers and virtual machines.
- Understand container benefits.

## The Problem Before Containers

Developers frequently heard:

    "It works on my machine."

Application works on:

- Developer laptop

But fails on:

- Staging
- Production
- Another developer machine

Why?

Environment differences.

## What Is A Container?

A container packages:

- Application code
- Dependencies
- Runtime
- Configuration

Into a portable unit.

Containers run consistently across environments.

## Real Example

Application:

    Fastify API

Dependencies:

    Node.js
    npm packages

Container packages everything together.

## Virtual Machines

Virtual Machine:

- Full operating system
- Hypervisor
- Large resource usage

Example:

VM 1

    Ubuntu

VM 2

    Ubuntu

VM 3

    Ubuntu

Each VM contains a full OS.

## Containers

Containers share the host kernel.

Smaller.

Faster.

More efficient.

## VM vs Container

Virtual Machine:

- Heavy
- Slower startup
- Full OS

Container:

- Lightweight
- Fast startup
- Shared kernel

## Why Companies Use Containers

Benefits:

- Consistency
- Scalability
- Portability
- Easier deployments
- Better resource utilization

## Real World Usage

Used heavily by:

- Google
- Netflix
- Spotify
- Uber
- Airbnb

## Portfolio Examples

Applications that benefit from containers:

- SyncGrid API
- VaultBox API
- inFlowForge API
- Argus
- NOMMO

## Interview Questions

1. What is a container?
2. Why are containers useful?
3. How do containers differ from VMs?
4. What problem do containers solve?

## Exercises

1. Define container.
2. Define virtual machine.
3. Compare VM and container.
4. List container benefits.
5. Explain portability.

## Summary

Containers package applications and dependencies into portable units.

They solve environment consistency problems.

## References

https://www.docker.com/resources/what-container/
