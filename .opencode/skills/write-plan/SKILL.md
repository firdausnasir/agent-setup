---
name: write-plan
description: Turn finalized brainstorm output or a PRD into a detailed implementation plan with agent-ready context and explicit parallelization boundaries. Use when requirements are ready and the next step is an implementation plan.
---

# Write Plan

Create the implementation plan from approved requirements.

## Workflow

1. Use a PRD if one exists. Otherwise use the finalized brainstorm output.
2. Explore the codebase if architecture and integration boundaries are not already confirmed.
3. Prefer tracer-bullet vertical slices over horizontal layer-only phases.
4. Write enough context that another agent can execute each task without extra conversation.
5. Mark whether each task can be parallelized.
6. For parallel work, define the isolation boundary clearly.
7. Do not implement here.

## Output

- Unless the user explicitly wants chat-only output, write the final plan to `./plans/<feature-name>.md`.

## Resources

- Planning guide: `references/planning-guide.md`
