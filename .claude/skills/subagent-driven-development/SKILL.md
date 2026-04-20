---
name: subagent-driven-development
description: Split a parallelizable implementation plan into isolated subagent tasks, coordinate their execution, and merge the results back to the current branch for review. Use when a plan has clear parallel tasks that can be done safely in parallel.
---

# Subagent-Driven Development

Use subagents only when the plan supports safe parallel execution.

## Workflow

1. Only use this skill for tasks already marked as safely parallelizable.
2. Do not delegate requirement gathering or unresolved product decisions.
3. Give each subagent a clear, isolated task with explicit boundaries.
4. Use worktrees, branches, or strict file-boundary isolation when needed to avoid conflicts.
5. If ownership boundaries overlap, do not parallelize.
6. Never trust a subagent success report without independent inspection.
7. Merge the results back into the current branch before review.
8. If safe parallelization is not actually possible, stop and continue sequentially instead.

## Resources

- Delegation guide: `references/delegation-guide.md`
