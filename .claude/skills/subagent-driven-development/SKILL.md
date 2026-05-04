---
name: subagent-driven-development
description: Split a parallelizable implementation plan into isolated subagent tasks, coordinate their execution, and merge the results back to the current branch for review. Use when a plan has clear parallel tasks that can be done safely in parallel.
---

# Subagent-Driven Development

Use subagents only when the plan supports safe parallel execution.

## Workflow

1. Only use this skill when the plan already contains an execution contract.
2. Do not delegate requirement gathering or unresolved product decisions.
3. Choose the execution shape from the contract:
   - dinner rush for one parallel wave of disjoint tasks
   - courses in sequence for multiple ordered waves
   - prep-to-plate for sequential handoff pipelines
   - prep line for independent variations
4. Give each subagent a clear, isolated task with explicit boundaries and minimum viable context.
5. Use worktrees, branches, or strict file-boundary isolation when needed to avoid conflicts.
6. If ownership boundaries overlap, do not parallelize.
7. Run verification at the end of each task or wave before unlocking downstream work.
8. Never trust a subagent success report without independent inspection.
9. Merge the results back into the current branch before review.
10. If safe parallelization is not actually possible, stop and continue sequentially instead.

## Rules

- One active builder per file at a time.
- Verifiers may inspect the same files, but they should not edit builder-owned files in the same pass.
- Keep builder and verifier roles separate when the workflow uses subagents.
- Every subagent handoff must include:
  - summary
  - changed files
  - verification run
  - open risks or unresolved questions
- If a task cannot be assigned with a clear allowed scope and forbidden scope, it is not ready for delegation.

## Resources

- Delegation guide: `references/delegation-guide.md`
