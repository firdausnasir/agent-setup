# Implementation Examples

## Bad implementation behavior

Task: fix empty email handling in validation.

Bad diff behavior:

- rewrites email validation entirely
- adds unrelated username rules
- changes comments and formatting
- adds abstractions nobody asked for

## Good implementation behavior

Task: fix empty email handling in validation.

Good diff behavior:

- changes only the lines needed to treat blank emails as invalid
- keeps the existing style
- adds or updates the narrowest relevant test
- runs the specific proof command first

## Goal-driven execution

Task: fix sorting bug with duplicate scores.

Good execution shape:

1. Write or locate a test that reproduces the bug.
2. Make the minimal code change.
3. Run the bug-repro test.
4. Run adjacent regression checks.
