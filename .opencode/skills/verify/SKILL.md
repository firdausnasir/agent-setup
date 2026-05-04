---
name: verify
description: Verify work before any completion claim by running fresh commands and reporting tangible evidence, not assumptions. Use when about to say work is complete, fixed, or passing, or before review, commit, or PR creation.
---

# Verify

Evidence before claims, always.

## Workflow

1. Do not claim completion, correctness, or passing status without fresh verification evidence.
2. Identify the exact command that proves each claim.
3. Verify at the smallest useful boundary first:
   - current task
   - current wave
   - full integrated result
4. Run the full command fresh.
5. Read the full output and confirm the exit status.
6. If evidence is missing or incomplete, report the actual status and why.
7. If subagents were used, verify their merged work independently.
8. Apply `$execution-guidelines` when deciding whether the proof is actually sufficient.

## Rules

- Do not treat final verification as the only checkpoint when the workflow runs in tasks or waves.
- For parallel work, verify each task or wave before downstream tasks depend on it.
- When possible, separate the builder from the verifier.
- A subagent success report is not verification.

## Resources

- Verification guide: `references/verification-guide.md`
- Examples: `examples/verification-examples.md`
