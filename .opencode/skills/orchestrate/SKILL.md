---
name: orchestrate
description: Route work through the local brainstorm, execution-guidelines, write-prd, write-plan, implement, subagent-driven-development, and verify skills. Use when the user wants an end-to-end workflow, a multi-stage delivery process, or mentions orchestrate.
---

# Orchestrate

Use this skill to route a request through the local workflow skills. This skill owns stage selection, not stage details.

## Local skills

- `$brainstorm`
- `$execution-guidelines`
- `$write-prd`
- `$write-plan`
- `$implement`
- `$subagent-driven-development`
- `$verify`

## Routing rules

1. If the user already has an approved implementation plan, apply `$execution-guidelines`, then use `$implement`, then `$subagent-driven-development` if the plan marks safe parallel tasks, then `$verify`.
2. If the user has a PRD but no plan, apply `$execution-guidelines`, then use `$write-plan`, then `$implement`, then `$subagent-driven-development` if needed, then `$verify`.
3. If the user asked only for verification, use `$verify`.
4. Otherwise start with `$brainstorm`.
5. After `$brainstorm`, route `hard` and `very-hard` work to `$write-prd`, then `$write-plan`.
6. After `$brainstorm`, route `trivial`, `easy`, and `medium` work directly to `$write-plan`.
7. After `$write-plan`, route to `$implement`.
8. Before any completion claim, route to `$verify`.

## Rules

- Do not inline stage-specific detail here; rely on the stage skills.
- If a required stage artifact is missing, stop and ask for the missing input or go back to the prior stage.
- Never skip `$brainstorm` when requirements are unclear.
- Never skip `$verify` before claiming success.
- Use `$execution-guidelines` as the shared behavioral baseline for non-trivial stages.
