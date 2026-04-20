---
name: write-prd
description: Write a PRD from finalized brainstorm output for hard or very-hard work, including user stories, implementation decisions, and testing decisions. Use when requirements are complete and a formal PRD is needed before planning.
---

# Write PRD

Write a PRD only after `$brainstorm` has produced complete enough requirements.

## Workflow

1. Treat the brainstorm output as the source of truth.
2. Do not re-ask already resolved questions.
3. If critical product or architecture unknowns remain, ask only those remaining questions.
4. Explore the repo to verify the current system and integration surfaces.
5. Prefer durable decisions over file-level implementation detail.
6. Do not implement here.
7. Write the PRD using the sections in `references/prd-guide.md`.

## Output

- If the user wants a repo artifact, write the PRD to `./plans/<feature-name>.prd.md`.
- Otherwise return the PRD in chat and make it ready for `$write-plan`.

## Resources

- PRD guide: `references/prd-guide.md`
