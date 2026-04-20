# Brainstorm Interview Guide

This skill is modeled after the `grill-me` workflow, with one deliberate change: ask focused question batches instead of one question at a time.

## Goals

- reach shared understanding before PRD, planning, or implementation
- walk the decision tree deeply enough that later stages do not need to guess
- use codebase evidence first and ask the user only where the workspace cannot answer

## Interview style

1. Explore the codebase first whenever the answer may already exist.
2. Group related open questions into a single batched set.
3. Include a short recommended answer when there is enough evidence to do so.
4. If a branch remains unresolved, ask a second focused batch.
5. Do not stop at partial clarity when missing answers would change scope, UX, architecture, rollout, testing, or risk.

## What to interrogate

Use the smallest relevant subset of these areas:

- goals and non-goals
- users and actors
- UX flow and success path
- permissions and access control
- data model and schema implications
- APIs and integration boundaries
- failure modes and rollback behavior
- observability and metrics
- performance constraints
- security constraints
- testing expectations
- rollout or migration constraints

## Completion gate

Do not hand off until you can clearly produce:

- a problem summary
- confirmed requirements
- constraints
- edge cases
- dependencies
- risks
- a justified complexity rating
- the next skill to use
