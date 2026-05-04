# Verification Guide

This skill is modeled after the `verification-before-completion` workflow.

## Iron law

No completion claims without fresh verification evidence.

If the proving command has not been run in the current turn, do not claim the work is complete, fixed, or passing.

## Gate function

Before any success claim:

1. Identify what command proves the claim.
2. Run the full command fresh.
3. Read the full output.
4. Confirm the exit status.
5. Only then report the result.

Apply this at the right boundary:

- task verification: proves the current ticket
- wave verification: proves a whole dependency group before the next wave starts
- final verification: proves the integrated result before completion

## Common traps

- saying "should work" instead of proving it
- treating lint success as build success
- trusting a subagent report without independent verification
- proving only one requirement and implying all requirements are done
- relying on an earlier run instead of fresh evidence

## Verification checklist

Map the work to proof such as:

- targeted tests
- regression tests
- lint
- typecheck
- build
- manual evidence for user-facing flows when necessary

In multi-agent runs:

- do not unlock downstream work without the upstream proof
- do not let builders certify their own work as the only evidence
- keep verification evidence attached to the task or wave it proves
