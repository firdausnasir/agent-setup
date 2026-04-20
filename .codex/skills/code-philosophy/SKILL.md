---
name: code-philosophy
description: Guide internal logic and data flow toward simple, defensive, readable code. Use when implementing backend logic, React state logic, hooks, or other functional behavior where correctness and clarity matter.
---

# Code Philosophy

Apply these rules to internal logic and data flow.

## Rules

1. Prefer guard clauses and early exits over deep nesting.
2. Parse inputs at the boundary so internal logic works on trusted state.
3. Keep functions predictable and avoid hidden mutations where possible.
4. Fail fast and loudly on invalid states.
5. Use names that make the code read clearly without comments.

## Checklist

- Are edge cases handled early?
- Is invalid state blocked at the boundary?
- Is behavior predictable?
- Are failures explicit?
- Do names communicate intent?
