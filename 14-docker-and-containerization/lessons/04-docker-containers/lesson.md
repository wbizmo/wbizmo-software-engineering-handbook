# Lesson 04: Docker Containers

## Learning Objectives

By the end of this lesson you should be able to:

- Run containers.
- Stop containers.
- Remove containers.
- Inspect containers.
- Understand container lifecycle.

## Image vs Container

Image:

    Blueprint

Container:

    Running instance

Example:

    node:22

can create

    many containers

## Run Container

    docker run node:22

## Interactive Container

    docker run -it node:22 bash

Flags:

    -i

Interactive

    -t

Terminal

## Run Detached

    docker run -d nginx

Detached means:

Runs in background.

## List Running Containers

    docker ps

## List All Containers

    docker ps -a

## Stop Container

    docker stop CONTAINER_ID

## Start Container

    docker start CONTAINER_ID

## Restart Container

    docker restart CONTAINER_ID

## Remove Container

    docker rm CONTAINER_ID

## Container Logs

    docker logs CONTAINER_ID

## Execute Command

    docker exec -it CONTAINER_ID bash

Useful for debugging.

## Container Lifecycle

Create

↓

Run

↓

Stop

↓

Remove

## Common Mistakes

- Forgetting detached mode.
- Removing running containers.
- Ignoring logs.
- Not naming containers.

## Name Container

    docker run \
      --name my-nginx \
      nginx

## Exercises

1. Run nginx.
2. List containers.
3. View logs.
4. Enter container.
5. Stop container.
6. Remove container.

## Interview Questions

1. Difference between image and container?
2. What does docker ps do?
3. What does docker exec do?
4. What does detached mode mean?

## Summary

Containers are running instances of images.

Managing containers is a core Docker skill.

## References

https://docs.docker.com/engine/containers/run/
