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
5. Build an execution contract, not just a task list.
6. Mark whether each task can be parallelized.
7. For parallel work, define the isolation boundary clearly.
8. Group dependent tasks into waves when the work benefits from phased parallel execution.
9. Choose the execution pattern that fits the work:
   - single-threaded
   - prep line
   - dinner rush
   - courses in sequence
   - prep-to-plate
10. Record the proving command for each task or wave.
11. Do not implement here.

## Output

- Unless the user explicitly wants chat-only output, write the final plan to `./plans/<feature-name>.md`.
- The plan must include an execution contract with:
  - chosen pattern
  - task graph or ordered waves
  - ownership boundary per task
  - dependencies per task
  - acceptance criteria per task
  - proving command per task or wave
  - integration checkpoint and final verification checkpoint

## Resources

- Planning guide: `references/planning-guide.md`
