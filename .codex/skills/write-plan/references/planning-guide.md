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

## Execution contract

Every plan should contain an execution contract. This is the minimum artifact that lets an orchestrator decide how to run the work.

Capture:

- chosen execution pattern
- task graph or wave order
- owned files or ownership boundaries per task
- forbidden scope when file ownership is tight
- dependencies that gate each task
- acceptance criteria
- proof command for each task or wave
- integration checkpoint
- final verification checkpoint

Choose the simplest pattern that fits:

- single-threaded: use when the work is small or ownership overlaps too much
- prep line: use for independent variations where a human or orchestrator will select results
- dinner rush: use for parallel builders on disjoint files
- courses in sequence: use for parallel waves with strict ordering between waves
- prep-to-plate: use for sequential handoff pipelines such as research, build, test, document

## Recommended plan shape

- goal
- durable decisions
- execution contract
- task title
- objective
- context
- inputs and dependencies
- parallelizable: yes or no
- isolation boundary
- ordered steps
- acceptance criteria
- verification
