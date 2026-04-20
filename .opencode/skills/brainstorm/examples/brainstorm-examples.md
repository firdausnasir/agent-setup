# Brainstorm Examples

## Bad brainstorm

User request: "Add export support"

Bad response:

- asks only "what format?"
- assumes all records should be exported
- ignores privacy, scale, and delivery path

## Good brainstorm

User request: "Add export support"

Good batched questions:

1. Scope: export all records, filtered records, or only the current view?
2. Delivery: browser download, background job, emailed file, or API response?
3. Formats: CSV, JSON, or both?
4. Field safety: are any fields excluded for privacy or compliance reasons?
5. Data volume: should this support large exports asynchronously?

## Good handoff

After clarification, produce:

- problem summary
- confirmed requirements
- constraints
- edge cases
- risks
- complexity
- recommended next skill
