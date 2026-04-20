# Installation Guide

This guide is for LLM agents. Follow it directly instead of asking the user to copy files by hand.

## Goal

Install the skill bundle from this repository into the user's agent-specific global skills directory.

Supported targets:

- Codex
- Claude Code
- OpenCode

If the current agent is not one of those three, stop and tell the user this repository only ships native layouts for Codex, Claude Code, and OpenCode.

## Source Of Truth

Use this repository as the source of truth.

If the repository is already open in the current session, install from the local checkout.

If it is not available locally, fetch this repository first:

- Repository URL: `https://github.com/firdausnasir/agent-setup`
- Guide URL: `https://raw.githubusercontent.com/firdausnasir/agent-setup/refs/heads/main/docs/guide/installation.md`

## What To Install

Install the full skill folders, not just `SKILL.md`.

Preserve all bundled files, including:

- `references/`
- `examples/`

The expected installed skills are:

- `orchestrate`
- `brainstorm`
- `execution-guidelines`
- `write-prd`
- `write-plan`
- `implement`
- `subagent-driven-development`
- `verify`
- `code-philosophy`
- `frontend-philosophy`

## Agent Detection

Detect the active target and use the matching source layout from this repository.

### Codex

Use when the user is installing for OpenAI Codex.

Source directory in this repo:

- `.codex/skills/`

Target directory:

- `$CODEX_HOME/skills` if `CODEX_HOME` is set
- otherwise `~/.codex/skills`

Notes:

- Prefer real copied files over a setup that only symlinks `SKILL.md`.
- If global skill discovery requires a restart, tell the user at the end.

### Claude Code

Use when the user is installing for Claude Code.

Source directory in this repo:

- `.claude/skills/`

Target directory:

- `~/.claude/skills`

Notes:

- Copy the full skill folders.
- Tell the user whether Claude Code should detect the change live or whether a restart is safer.

### OpenCode

Use when the user is installing for OpenCode.

Source directory in this repo:

- `.opencode/skills/`

Target directory:

- `~/.config/opencode/skills`

Notes:

- Keep each folder name aligned with the `name:` field in `SKILL.md`.
- If reload or restart is needed, tell the user at the end.

## Procedure

1. Determine whether the current session already has this repository available locally.
2. If not, fetch or clone `https://github.com/firdausnasir/agent-setup`.
3. Detect which supported target the user wants or which agent environment is currently active.
4. Select the matching source directory from this repository.
5. Create the target skills directory if it does not already exist.
6. Copy every skill folder from the source directory into the target directory.
7. Preserve bundled supporting files.
8. Verify that all expected skills exist in the destination and are readable.
9. Report:
   - detected target
   - source path used
   - destination path used
   - installed skill names
   - whether restart or reload is recommended

## Verification Standard

Do not claim success until you have checked the destination directory directly.

Minimum proof:

- the destination directory exists
- the ten expected skill folders exist
- each installed skill contains `SKILL.md`
- bundled supporting files are still present where expected

## Failure Behavior

If installation fails:

- report the exact failing step
- report the path you were trying to use
- do not say the install is complete

If the target agent is unsupported:

- say that this repository currently provides native install layouts only for Codex, Claude Code, and OpenCode
- stop instead of guessing
