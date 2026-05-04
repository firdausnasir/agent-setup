# Skill Authoring Guide

This skill is modeled after the Matt Pocock `write-a-skill` pattern and adapted to Codex conventions.

## Structure

Each skill should use this shape:

```
skill-name/
├── SKILL.md
├── references/
├── examples/
└── scripts/
```

Only create the optional folders when they are actually useful.

## Description rules

The description is the main trigger mechanism. It should explain:

1. what the skill does
2. when Codex should use it

Good format:

"Create new agent skills with proper structure, progressive disclosure, and bundled resources. Use when the user wants to create, write, build, or improve a skill."

## Authoring rules

- keep `SKILL.md` concise
- move richer guidance into `references/`
- keep references one level deep from `SKILL.md`
- avoid time-sensitive details
- prefer imperative instructions over abstract descriptions
- add scripts only for deterministic helpers or repeated operations
