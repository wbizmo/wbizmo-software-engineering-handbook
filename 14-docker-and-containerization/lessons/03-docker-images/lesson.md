# Lesson 03: Docker Images

## Learning Objectives

By the end of this lesson you should be able to:

- Explain Docker images.
- Pull images.
- Tag images.
- Remove images.
- Understand image layers.

## What Is A Docker Image?

Image:

Read-only template used to create containers.

Think of:

Image

↓

Blueprint

Container

↓

Running instance

## Example

Image:

    node:22

Container:

Running Node.js environment.

## Pull Image

    docker pull node:22

## List Images

    docker images

## Image Tags

Example:

    node:22

Repository:

    node

Tag:

    22

## Latest Tag

Example:

    node:latest

Avoid relying heavily on latest.

Prefer fixed versions.

## Remove Image

    docker rmi IMAGE_ID

## Image Layers

Docker images use layers.

Benefits:

- Smaller downloads
- Better caching
- Faster builds

## Inspect Image

    docker inspect node:22

## Image History

    docker history node:22

## Common Images

Node:

    node

PostgreSQL:

    postgres

Redis:

    redis

Nginx:

    nginx

## Interview Questions

1. What is an image?
2. What is a tag?
3. Why avoid latest?
4. What are image layers?

## Exercises

1. Pull node image.
2. Pull redis image.
3. Inspect image.
4. View history.
5. Remove image.

## Summary

Images are templates used to create containers.

Understanding images is fundamental to Docker.

## References

https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/
