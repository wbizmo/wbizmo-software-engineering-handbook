# Lesson 02: Installing Git And First Configuration

## Learning Objectives

- Install Git.
- Verify installation.
- Configure username.
- Configure email.
- Understand Git identity.

## Windows Installation

Download:

https://git-scm.com/downloads

Install using default options.

Verify:

    git --version

Example:

    git version 2.50.1

## Linux Installation

Ubuntu:

    sudo apt update
    sudo apt install git

Verify:

    git --version

## macOS Installation

Install using:

    brew install git

Verify:

    git --version

## First Configuration

Configure username:

    git config --global user.name "Williams Ashibuogwu"

Configure email:

    git config --global user.email "wbizmo@gmail.com"

Check settings:

    git config --list

## Why Username And Email Matter

Every commit records:

- Author name
- Author email
- Timestamp

Example:

    Williams Ashibuogwu
    wbizmo@gmail.com

This becomes part of project history.

## Useful Configuration

Default branch:

    git config --global init.defaultBranch main

View config:

    git config --global --list

## Exercises

1. Install Git.
2. Verify installation.
3. Configure username.
4. Configure email.
5. Set default branch to main.
6. View configuration list.

## Summary

Git must be installed and configured before use.

Username and email become part of commit history.

## References

https://git-scm.com/book/en/v2/Getting-Started-Installing-Git
