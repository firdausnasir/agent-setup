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
