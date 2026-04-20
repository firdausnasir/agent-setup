# Delegation Guide

This skill exists to parallelize implementation work only when the plan has clean isolation boundaries.

## When to use it

Use it when:

- the plan already exists
- tasks are explicitly parallelizable
- ownership boundaries are clear enough to avoid merge chaos

Do not use it when:

- requirements are still changing
- product decisions are unresolved
- multiple tasks need to edit the same unstable area
- the coordination cost is higher than the likely time saved

## Delegation template

Each subagent should receive:

- task title
- objective
- context
- allowed scope
- forbidden scope
- dependencies
- required verification
- handoff format

## Isolation strategies

Prefer one of these, from strongest to weakest:

1. separate worktrees
2. separate branches with non-overlapping file ownership
3. strict file-boundary isolation in one worktree

## Merge discipline

After a subagent reports completion:

1. inspect the diff yourself
2. verify the task actually matches the assignment
3. merge only after the result is reviewable
4. resolve conflicts in favor of the approved plan, not the loudest diff

## Anti-patterns

- splitting tasks that modify the same unstable files
- delegating before the plan is specific enough
- accepting subagent output without reviewing the diff
- optimizing for concurrency when sequential work would be safer
