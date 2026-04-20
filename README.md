# Agentic Setup

## Intro

This repo is a reusable skill bundle for coding agents.

It gives the agent a staged workflow instead of one large prompt. The main entrypoint is `orchestrate`, which routes work through clarification, planning, implementation, and verification.

Supported agent layouts in this repo:

- Codex
- Claude Code
- OpenCode

Use this when you want the agent to:

- ask before guessing
- plan before coding on larger tasks
- keep changes small
- verify before saying the work is done

## How To Use

Use this repo in this order:

1. Install the skills into your agent.
2. Open the codebase you want the agent to work on.
3. Start your agent in that codebase.
4. Tell the agent to use `orchestrate` for your task.
5. Give the task in plain language.

Minimal example:

```text
Use orchestrate for this task.
Add X.
Keep the change minimal.
Verify the result before you say it is done.
```

Slash command example:

```text
/orchestrate
I need you to add X.
Keep the change minimal.
Verify the result before you say it is done.
```

What the agent should do after that:

1. If the task is unclear, start with `brainstorm`.
2. If the task is large or complex, write a PRD and then a plan.
3. Implement only after the task is clear enough.
4. Verify the result before making a completion claim.

What you should expect as the user:

- the agent may ask focused questions before coding
- the agent may write a plan before editing files
- the agent should not skip verification

If you want the full staged workflow, always mention `orchestrate` in your request.

## Installation

### For Humans

Copy and paste this prompt into your LLM agent:

```text
Install and configure the agent-setup skills by following the instructions here:
https://raw.githubusercontent.com/firdausnasir/agent-setup/refs/heads/main/docs/guide/installation.md
```

Local copy of the guide: [docs/guide/installation.md](docs/guide/installation.md)

### For LLM Agents

Fetch the installation guide and follow it:

```bash
curl -fsSL https://raw.githubusercontent.com/firdausnasir/agent-setup/refs/heads/main/docs/guide/installation.md
```

## Included Skills

This bundle includes:

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

Repo layout:

```text
.codex/skills/
.claude/skills/
.opencode/skills/
docs/guide/installation.md
```

Each agent directory contains the same skill set in that agent's native layout.

## Workflow Summary

`orchestrate` is the entrypoint.

High-level flow:

1. `brainstorm`
   Clarify requirements when the task is not fully defined.
2. `write-prd`
   Use for hard or very hard work that needs a durable artifact before planning.
3. `write-plan`
   Turn the clarified task or PRD into an implementation plan.
4. `implement`
   Execute the plan with minimal, targeted changes.
5. `subagent-driven-development`
   Use only when parallel work is clearly safe.
6. `verify`
   Prove the result before saying the work is complete.

`execution-guidelines` applies across non-trivial stages.

`code-philosophy` and `frontend-philosophy` support implementation when relevant.

## Skill Reference

### `orchestrate`

Main router. Use this first when you want the full workflow.

### `brainstorm`

Clarifies requirements before planning or implementation.

### `execution-guidelines`

Shared guardrails for non-trivial work: think first, keep it simple, keep changes surgical, verify claims.

### `write-prd`

Creates a PRD for harder work before planning begins.

### `write-plan`

Creates an implementation plan from clarified requirements or a PRD.

### `implement`

Implements a defined task or plan. It should not invent scope or make product decisions.

### `subagent-driven-development`

Splits implementation into isolated parallel tasks when the plan supports it.

### `verify`

Checks the work with fresh evidence before any completion claim.

### `code-philosophy`

Guidance for simple, explicit, readable internal logic.

### `frontend-philosophy`

Guidance for intentional UI work instead of generic UI output.
