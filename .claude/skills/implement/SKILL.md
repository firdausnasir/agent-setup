---
name: implement
description: Implement an approved plan or task reference without doing requirements work, using the local execution, code, and frontend philosophy skills when relevant. Use when a plan exists and the next step is code changes.
---

# Implement

Implement only from a plan or direct task reference that is already defined.

## Workflow

1. Do not brainstorm, gather requirements, or make product decisions here.
2. Read `CLAUDE.md` or the repo convention file if it exists.
3. Apply `$execution-guidelines` before and during implementation.
4. Read the execution contract when one exists, and stay inside the current task's ownership boundary.
5. Apply `$code-philosophy` to internal logic.
6. Apply `$frontend-philosophy` when changing visual UI, while respecting the existing design system if one exists.
7. If inside a git repo, inspect branch state and working tree before editing.
8. Read every file that must change, plus nearby examples.
9. Make the smallest correct code changes that satisfy the referenced task.
10. If the task is part of a multi-agent run, act as the builder for only the current ticket. Do not absorb reviewer or tester responsibilities into the same pass.
11. Run the narrowest validation that proves the current task, then expand to lint, typecheck, or build when relevant.
12. Re-read the diff skeptically and reduce it if it is broader than the task.

## Rules

- If the current task lacks clear ownership, dependencies, or acceptance criteria, stop and return to planning instead of guessing.
- If another active task owns the same unstable file, do not proceed in parallel.
- Keep the handoff small: summary, changed files, verification run, and open risks.

## Resources

- Implementation guide: `references/implementation-guide.md`
- Examples: `examples/implementation-examples.md`
