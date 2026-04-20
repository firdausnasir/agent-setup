---
name: brainstorm
description: Gather and clarify requirements in bulk without making assumptions, then classify task complexity and hand off to PRD or planning. Use when the user wants to brainstorm, scope work, clarify requirements, or start an orchestrated workflow.
---

# Brainstorm

Clarify the work before any PRD, plan, or implementation.

## Workflow

1. Inspect the repo, referenced files, and nearby patterns before asking the user.
2. Prefer codebase evidence over user questions when the answer already exists in the workspace.
3. Never assume missing requirements. If anything material is unclear, ask the user.
4. Ask questions in focused batches, not one-by-one.
5. Only ask about scope, UX, architecture, rollout, risk, testing, or delivery.
6. If the user wants brainstorming only, stop after the clarified summary.
7. Once requirements are complete enough to proceed, output:
   - problem summary
   - confirmed requirements
   - constraints
   - edge cases
   - dependencies
   - risks
   - complexity
   - why this complexity
   - recommended next skill

## Complexity routing

- Recommend `$write-prd` for `hard` and `very-hard` work.
- Recommend `$write-plan` for `trivial`, `easy`, and `medium` work.

## Resources

- Interview guidance: `references/interview-guide.md`
- Examples: `examples/brainstorm-examples.md`
