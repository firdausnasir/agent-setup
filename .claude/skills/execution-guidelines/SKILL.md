---
name: execution-guidelines
description: Apply behavioral guardrails that reduce common agent coding mistakes such as hidden assumptions, overcomplication, broad diffs, and weak success criteria. Use when planning, implementing, reviewing, or verifying non-trivial work.
---

# Execution Guidelines

Use these guardrails across non-trivial workflow stages.

## Principles

1. Think before coding. If something material is unclear, surface it instead of guessing.
2. Prefer the simplest correct solution over speculative abstractions.
3. Make surgical changes that map directly to the request.
4. Define success criteria that can be verified with evidence.

## Rules

1. State assumptions explicitly when they matter.
2. If multiple interpretations exist, do not silently choose one.
3. Avoid adding flexibility, configuration, or abstractions that were not requested.
4. Do not refactor adjacent code unless the task requires it.
5. Convert vague tasks into proof-oriented checks before acting.

## Resources

- Behavioral model: `references/behavioral-model.md`
