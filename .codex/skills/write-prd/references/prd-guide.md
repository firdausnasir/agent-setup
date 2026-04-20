# Write PRD Guide

This skill is modeled after the `write-a-prd` workflow.

## Required process

1. Start from finalized brainstorm output.
2. Explore the repo to verify the current state and likely module boundaries.
3. Interrogate only the remaining unknowns that materially affect the solution.
4. Sketch the major modules or subsystems that must be built or changed.
5. Prefer deep modules where a simple interface can hide substantial complexity.
6. Decide what deserves direct testing coverage and find prior art in the repo.

## PRD structure

Use these sections:

## Problem Statement

Describe the problem from the user's perspective.

## Solution

Describe the proposed solution from the user's perspective.

## User Stories

Write a long, numbered set of user stories using this format:

1. As an <actor>, I want a <feature>, so that <benefit>

## Implementation Decisions

Include durable decisions such as:

- modules to build or modify
- interfaces that will change
- technical clarifications
- architectural decisions
- schema changes
- API contracts
- important interactions

Do not include fragile file-path detail or code snippets.

## Testing Decisions

Include:

- what good tests look like for this feature
- which modules will be tested
- prior art from the repo

## Out of Scope

State what is intentionally excluded.

## Further Notes

Capture anything useful that does not fit elsewhere.
