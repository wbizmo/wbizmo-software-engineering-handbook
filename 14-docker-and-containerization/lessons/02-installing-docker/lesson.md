# Lesson 02: Installing Docker

## Learning Objectives

By the end of this lesson you should be able to:

- Install Docker.
- Verify Docker installation.
- Understand Docker Desktop.
- Understand Docker Engine.
- Run first container.

## Docker Components

Docker Engine

Responsible for container execution.

Docker CLI

Command-line interface.

Docker Desktop

Graphical interface.

## Verify Installation

Check version:

    docker --version

Example:

    Docker version 28.x

## Docker Info

Inspect environment:

    docker info

## First Container

Run:

    docker run hello-world

Expected:

Docker downloads image.

Creates container.

Prints success message.

## Docker Hub

Public registry.

Examples:

- node
- postgres
- redis
- nginx

Search:

https://hub.docker.com

## Pull Images

Example:

    docker pull node:22

## View Images

    docker images

Example:

    REPOSITORY
    node

## Remove Image

    docker rmi IMAGE_ID

## Common Installation Issues

### Permission Denied

Linux:

Add user to docker group.

### Docker Not Running

Start Docker service.

### Cannot Connect To Daemon

Ensure Docker daemon is active.

## Troubleshooting

Check:

    docker info

Check:

    docker ps

Check:

    docker version

## Exercises

1. Install Docker.
2. Verify version.
3. Run hello-world.
4. Pull node image.
5. List images.

## Summary

Docker installation is the foundation of all container workflows.

## References

https://docs.docker.com/get-docker/
