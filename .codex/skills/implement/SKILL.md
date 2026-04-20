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
4. Apply `$code-philosophy` to internal logic.
5. Apply `$frontend-philosophy` when changing visual UI, while respecting the existing design system if one exists.
6. If inside a git repo, inspect branch state and working tree before editing.
7. Read every file that must change, plus nearby examples.
8. Make the smallest correct code changes that satisfy the referenced task.
9. Run the narrowest validation that proves the change, then expand to lint, typecheck, or build when relevant.
10. Re-read the diff skeptically and reduce it if it is broader than the task.

## Resources

- Implementation guide: `references/implementation-guide.md`
- Examples: `examples/implementation-examples.md`
