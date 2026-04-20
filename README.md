# Agentic Setup

This repository packages the `orchestrate` workflow and all of its dependent skills in three agent-native layouts:

- Codex: `.codex/skills/`
- Claude Code: `.claude/skills/`
- OpenCode: `.opencode/skills/`

Each layout contains the same skill set. The content is duplicated on purpose so you can copy the folders directly into the target agent's expected location without translating paths or rewriting instructions.

## Installation

### For Humans

Copy and paste this prompt to your LLM agent:

```text
Install and configure the agent-setup skills by following the instructions here:
https://raw.githubusercontent.com/firdausnasir/agent-setup/refs/heads/main/docs/guide/installation.md

Or read the Installation Guide, but seriously, let an agent do it.
```

You can also read the local guide here: [docs/guide/installation.md](./docs/guide/installation.md)

### For LLM Agents

Fetch the installation guide and follow it:

```bash
curl -fsSL https://raw.githubusercontent.com/firdausnasir/agent-setup/refs/heads/main/docs/guide/installation.md
```

## Included Skills

This bundle contains ten skills:

- `orchestrate`
- `brainstorm`
- `execution-guidelines`
- `write-prd`
- `write-plan`
- `implement`
- `subagent-driven-development`
- `verify`
- `code-philosophy`
- `frontend-philosophy`

`orchestrate` is the router. The other skills are the stages, guardrails, and implementation support prompts it depends on directly or transitively.

## How The Workflow Works

The workflow is intentionally staged. It separates requirement clarification, planning, implementation, delegation, and verification so the agent does not jump straight into code without enough context.

### 1. `orchestrate` chooses the route

The `orchestrate` skill does not contain deep task logic. Its job is to decide which stage skill should run next.

It routes work like this:

1. If there is already an approved implementation plan, apply `execution-guidelines`, then `implement`, then `subagent-driven-development` if the plan marks safe parallel tasks, then `verify`.
2. If there is a PRD but no plan, apply `execution-guidelines`, then `write-plan`, then `implement`, then optional `subagent-driven-development`, then `verify`.
3. If the user asked only for verification, use `verify`.
4. Otherwise start with `brainstorm`.
5. After `brainstorm`, send `hard` and `very-hard` work to `write-prd`, then `write-plan`.
6. After `brainstorm`, send `trivial`, `easy`, and `medium` work directly to `write-plan`.
7. Before any success claim, always use `verify`.

That makes `orchestrate` a traffic controller. It decides the next stage, but it delegates the actual stage behavior to the other skills.

### 2. `brainstorm` clarifies the task

`brainstorm` is the intake stage. It exists to stop the agent from making silent assumptions.

Its main rules are:

- inspect the repo and surrounding code before asking the user
- ask focused question batches instead of one question at a time
- avoid guessing about scope, UX, architecture, testing, rollout, or risk
- stop after a clarified summary if the user only wants brainstorming

Its output is meant to be structured enough for later stages to rely on:

- problem summary
- confirmed requirements
- constraints
- edge cases
- dependencies
- risks
- complexity
- why that complexity rating makes sense
- recommended next skill

This is the gating stage for unclear work. If requirements are still fuzzy, the workflow should not move on.

### 3. `execution-guidelines` applies shared guardrails

This is the behavioral baseline for non-trivial work. It is not a full workflow stage by itself. It reinforces the rules that should remain active during planning, implementation, review, and verification.

Its guardrails are:

- think before coding
- prefer the simplest correct solution
- make surgical changes
- define proof before claiming success

It is the skill that pushes the workflow away from common agent failure modes like hidden assumptions, speculative abstractions, broad diffs, and weak verification.

### 4. `write-prd` creates the product-level artifact

`write-prd` is only for work that is complex enough to deserve a formal product and implementation framing before planning.

The skill expects finalized `brainstorm` output and then turns it into a PRD with sections such as:

- problem statement
- solution
- user stories
- implementation decisions
- testing decisions
- out of scope
- further notes

Its job is not to implement. Its job is to turn clarified requirements into durable decisions that planning can consume.

### 5. `write-plan` creates the implementation plan

`write-plan` translates either finalized `brainstorm` output or a completed PRD into an execution plan.

The planning model is deliberately opinionated:

- prefer tracer-bullet vertical slices over broad horizontal phases
- make each slice end-to-end and independently verifiable
- include enough context that another agent can execute the task without extra chat
- mark whether work is parallelizable
- define isolation boundaries when parallel work is allowed

The expected plan shape includes:

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

This is the handoff artifact for `implement`.

### 6. `implement` executes the plan

`implement` is the stage that actually changes code or files.

Its boundaries matter:

- do not brainstorm here
- do not resolve product ambiguity here
- do not invent extra scope here

Its operating model is:

- read repo conventions first
- inspect git state before editing
- read the files that actually need to change
- make the smallest correct change
- validate narrowly first, then broaden checks if needed
- re-read the diff skeptically before finishing

It also points the agent toward more specialized local guidance when relevant:

- `code-philosophy` for logic and data flow
- `frontend-philosophy` for UI work

### 6a. `code-philosophy` keeps internal logic simple

This skill is a lightweight implementation companion. It is meant for backend logic, state logic, hooks, and other behavior-heavy code.

Its bias is toward:

- guard clauses over deep nesting
- input validation at the boundary
- predictable behavior
- explicit failure states
- names that make the code readable without extra explanation

### 6b. `frontend-philosophy` keeps UI work intentional

This skill is the visual companion to `implement`. It is only relevant when the task touches UI, styling, layout, motion, or interaction design.

Its bias is toward:

- non-generic interface design
- typography with character
- committed visual hierarchy
- purposeful motion
- respecting an existing design system when one already exists

### 7. `subagent-driven-development` parallelizes only when safe

This skill exists for one narrow purpose: split implementation into isolated parallel tasks when the plan explicitly supports it.

It should only be used when:

- the plan already exists
- tasks are clearly marked parallelizable
- file ownership boundaries are clean

It should not be used when:

- requirements are still moving
- product decisions are unresolved
- tasks overlap in unstable files
- coordination cost is higher than the time saved

The skill expects explicit task ownership, isolated scope, and independent verification before anything is merged back.

### 8. `verify` proves the work

`verify` is the final gate. It exists to prevent completion claims based on confidence instead of evidence.

Its rule is simple:

- no claim of done, fixed, or passing without fresh proof from the current turn

Typical proof includes:

- targeted tests
- regression tests
- lint
- typecheck
- build
- manual evidence when user-facing behavior is involved

This skill is mandatory before the workflow says the task is complete.

## Why The Skills Are Split

The split is intentional. A single large prompt usually blurs the lines between clarification, planning, coding, and verification. This bundle keeps those stages separate so the agent can:

- ask questions before coding when requirements are unclear
- produce planning artifacts before implementation when complexity justifies it
- parallelize only when task boundaries are explicit
- verify with evidence before making success claims

This reduces a common failure pattern in coding agents: jumping straight to edits and only later discovering that the task was underspecified or overcomplicated.

## Repository Layout

```text
.codex/skills/
.claude/skills/
.opencode/skills/
```

Each of those directories contains the same ten skill folders, and each skill folder includes:

- `SKILL.md`
- optional `references/`
- optional `examples/`

The supporting files are part of the skill. Do not strip them out when copying.

## Expected Usage Pattern

For an agent, the intended usage looks like this:

1. Invoke `orchestrate` when the user asks for an end-to-end workflow or explicitly mentions orchestration.
2. Let `orchestrate` choose the next stage based on the current artifact state.
3. Keep `execution-guidelines` active for non-trivial work.
4. Do not skip backward stage boundaries:
   - unclear requirements go back to `brainstorm`
   - hard work goes through `write-prd`
   - implementation needs a plan or direct task reference
5. Do not skip `verify` before declaring success.

This keeps the workflow deterministic enough for agents while still being lightweight enough for normal coding tasks.
