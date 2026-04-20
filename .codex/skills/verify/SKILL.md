---
name: verify
description: Verify work before any completion claim by running fresh commands and reporting tangible evidence, not assumptions. Use when about to say work is complete, fixed, or passing, or before review, commit, or PR creation.
---

# Verify

Evidence before claims, always.

## Workflow

1. Do not claim completion, correctness, or passing status without fresh verification evidence.
2. Identify the exact command that proves each claim.
3. Run the full command fresh.
4. Read the full output and confirm the exit status.
5. If evidence is missing or incomplete, report the actual status and why.
6. If subagents were used, verify their merged work independently.
7. Apply `$execution-guidelines` when deciding whether the proof is actually sufficient.

## Resources

- Verification guide: `references/verification-guide.md`
- Examples: `examples/verification-examples.md`
