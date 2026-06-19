# Lesson 07: Volumes and Networking

## Learning Objectives

By the end of this lesson you should be able to:

- Understand Docker volumes.
- Understand Docker networking.
- Persist data.
- Connect containers together.
- Troubleshoot connectivity issues.

## The Problem With Container Storage

Containers are ephemeral.

Example:

Create file.

↓

Delete container.

↓

File disappears.

This is often undesirable.

## What Is A Volume?

Volumes provide persistent storage.

Data survives container recreation.

## Create Volume

    docker volume create postgres_data

## List Volumes

    docker volume ls

## Inspect Volume

    docker volume inspect postgres_data

## Mount Volume

    docker run \
      -v postgres_data:/var/lib/postgresql/data \
      postgres:17

## Why Databases Need Volumes

Without volumes:

Database data disappears.

With volumes:

Database survives restarts.

## Docker Networking

Containers communicate through networks.

Example:

API

↓

PostgreSQL

↓

Redis

## Create Network

    docker network create app-network

## List Networks

    docker network ls

## Connect Container

    docker run \
      --network app-network \
      redis

## Service Discovery

Inside a Docker network:

Containers can communicate by service name.

Example:

    postgres

instead of:

    localhost

## Compose Example

    services:

      api:

      postgres:

      redis:

Docker automatically creates networking.

## Common Problems

Wrong host:

    localhost

Correct:

    postgres

inside Docker.

## Troubleshooting

Check networks:

    docker network ls

Inspect network:

    docker network inspect app-network

Check volumes:

    docker volume ls

## Exercises

1. Create volume.
2. Mount volume.
3. Create network.
4. Connect containers.
5. Inspect network.

## Interview Questions

1. Why use volumes?
2. Why use networks?
3. Why not store database data inside container filesystem?
4. How do containers discover each other?

## Summary

Volumes provide persistence.

Networks provide communication.

Most real applications require both.

## References

https://docs.docker.com/engine/storage/volumes/
