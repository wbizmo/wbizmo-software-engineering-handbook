# Lesson 03: Creating Repositories And Making Commits

## Learning Objectives

- Initialize Git repositories.
- Track files.
- Stage files.
- Create commits.
- Understand Git workflow.

## Create Project

    mkdir my-project
    cd my-project

Initialize Git:

    git init

Git creates:

    .git

This hidden folder stores repository history.

## Check Status

    git status

Shows:

- tracked files
- untracked files
- staged files

## Create File

    touch README.md

Check status:

    git status

Git will show:

    untracked files

## Stage File

    git add README.md

Or:

    git add .

## Create Commit

    git commit -m "Create README"

Now Git stores a snapshot.

## View History

    git log

Compact:

    git log --oneline

## Standard Workflow

Edit file

↓

git add .

↓

git commit -m "Meaningful message"

Repeat.

## Good Commit Messages

Good:

    Add login page
    Create API routes
    Fix dashboard bug

Bad:

    update
    changes
    stuff

## Exercises

1. Create a repository.
2. Create README.md.
3. Stage file.
4. Commit file.
5. View history.
6. Make another commit.

## Summary

Git repositories track projects.

Files are staged before commits.

Commits record meaningful project history.

## References

https://git-scm.com/docs/git-init

https://git-scm.com/docs/git-commit
