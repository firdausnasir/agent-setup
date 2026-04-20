# Write Plan Guide

This skill is modeled after the `prd-to-plan` workflow.

## Planning principles

- use a PRD when available; otherwise use finalized brainstorm output
- break work into tracer-bullet vertical slices, not horizontal layers
- prefer many thin slices over a few broad phases
- make each slice end-to-end and independently verifiable
- include durable decisions, not brittle implementation trivia

## Durable decisions to capture

- route structures
- schema shape
- key data models
- authorization approach
- third-party boundaries

## Slice quality bar

Each slice should:

- deliver a complete path through relevant layers
- be demoable or verifiable on its own
- have acceptance criteria and verification steps
- contain enough context for another agent to execute without extra conversation

## Parallelization guidance

When a task can be parallelized, record:

- that it is parallelizable
- the exact isolation boundary
- dependencies that must be complete first
- the verification expected from the assignee

## Recommended plan shape

- goal
- durable decisions
- task title
- objective
- context
- inputs and dependencies
- parallelizable: yes or no
- isolation boundary
- ordered steps
- acceptance criteria
- verification
