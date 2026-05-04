---
name: orchestrate
description: Route work through the local brainstorm, execution-guidelines, write-prd, write-plan, implement, subagent-driven-development, and verify skills. Use when the user wants an end-to-end workflow, a multi-stage delivery process, or mentions orchestrate.
---

# Orchestrate

Use this skill to route a request through the local workflow skills. This skill owns stage selection and execution mode selection, not stage details.

## Local skills

- `$brainstorm`
- `$execution-guidelines`
- `$write-prd`
- `$write-plan`
- `$implement`
- `$subagent-driven-development`
- `$verify`

## Routing rules

1. If the user already has an approved implementation plan, apply `$execution-guidelines`, confirm it contains an execution contract, then route to the execution mode it defines.
2. If the user has a PRD but no plan, apply `$execution-guidelines`, then use `$write-plan`, then route from the execution contract in that plan.
3. If the user asked only for verification, use `$verify`.
4. Otherwise start with `$brainstorm`.
5. After `$brainstorm`, route `hard` and `very-hard` work to `$write-prd`, then `$write-plan`.
6. After `$brainstorm`, route `trivial`, `easy`, and `medium` work directly to `$write-plan`.
7. After `$write-plan`, confirm the plan includes an execution contract with:
   - task graph
   - ownership boundaries
   - dependencies
   - acceptance criteria
   - proving command for each task or wave
   - chosen execution pattern
8. Choose one execution pattern before implementation starts:
   - single-threaded: one builder, sequential execution
   - prep line: many independent variants, human or orchestrator selects the winner
   - dinner rush: parallel builders on disjoint files
   - courses in sequence: parallel waves with strict dependencies between waves
   - prep-to-plate: sequential handoff pipeline across bounded stages
9. Route single-threaded work to `$implement`.
10. Route parallel or multi-wave work to `$subagent-driven-development`, then return to `$implement` only for final integration when needed.
11. Route to `$verify` at task boundaries, wave boundaries, and before any completion claim.

## Rules

- Do not inline stage-specific detail here; rely on the stage skills.
- If a required stage artifact is missing, stop and ask for the missing input or go back to the prior stage.
- Never skip `$brainstorm` when requirements are unclear.
- Never start implementation until the execution contract is explicit enough for another agent to follow without extra conversation.
- Never start parallel builders unless file ownership boundaries are clear.
- Never let two active builders own the same unstable file.
- Keep subagent context minimal. Give each subagent only the task-local context it needs.
- Separate builders from verifiers whenever the workflow uses subagents.
- Never skip `$verify` before claiming success.
- Use `$execution-guidelines` as the shared behavioral baseline for non-trivial stages.
