# Delegation Guide

This skill exists to parallelize implementation work only when the plan has clean isolation boundaries.

## When to use it

Use it when:

- the plan already exists
- the execution contract already exists
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
- owned files or ownership boundary
- allowed scope
- forbidden scope
- dependencies
- acceptance criteria
- required verification
- handoff format

Use minimum viable context. Do not paste the entire parent thread or a long master plan when the task can be described locally.

## Pattern mapping

- prep line: same brief, many isolated variants, results compared after the run
- dinner rush: one wave of independent builders on disjoint files
- courses in sequence: multiple waves, each wave blocked on the prior wave's verification
- prep-to-plate: sequential handoff where each subagent advances one observable stage

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

## Verification discipline

- verify each task before declaring it done
- verify each wave before unlocking the next wave
- run a final top-level verification pass after integration
- do not let the builder self-certify the whole workflow without independent checks

## Anti-patterns

- splitting tasks that modify the same unstable files
- delegating before the plan is specific enough
- accepting subagent output without reviewing the diff
- optimizing for concurrency when sequential work would be safer
