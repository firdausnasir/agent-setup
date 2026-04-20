# Implementation Guide

This skill is the execution stage for an already-defined task, plan, or implementation reference.

## Stage boundary

Do not use this skill to:

- gather requirements
- resolve product ambiguity
- invent scope
- replace planning

If the plan or task reference is not clear enough to implement safely, stop and send the work back to the prior stage.

## Implementation philosophy

Combine these principles during execution:

- use `$code-philosophy` for internal logic and data flow
- use `$frontend-philosophy` for visual work
- keep changes minimal and local
- match existing repo patterns
- avoid speculative abstractions

## Execution checklist

1. Confirm the task reference is sufficiently specific.
2. Read the relevant files and nearby examples.
3. Inspect branch state and working tree if in a git repo.
4. Make the smallest correct code changes.
5. Validate with the narrowest meaningful proof first.
6. Re-read the diff skeptically and fix problems before finishing.

## Anti-patterns

- adding flexibility that nobody asked for
- refactoring adjacent code just because it looks improvable
- implementing around unclear requirements instead of blocking on them
- claiming correctness before verification
- solving tomorrow's problem instead of today's problem
