---
name: "advai-skill"
description: "Manages local skills with `advai skill`, including install, list, update, info, sync, unsync, and platform overrides. Invoke when user wants to add, maintain, or distribute skills."
---

# Advai Skill Manager

Use this skill to manage local skills and sync them into supported agent platforms through `advai skill`.

## When to Invoke

Invoke this skill when the user wants to:

- Install a skill from a GitHub repository
- List, inspect, update, or uninstall installed skills
- Sync a skill into Cursor, Claude Code, Codex, TRAE, or another supported platform
- Configure custom skill platforms or path overrides
- Troubleshoot where a skill is installed or synced

Do not use this skill for creating a brand-new skill definition from scratch unless the user specifically wants to manage that skill after creation.

## Core Commands

Inspect installed skills:

```bash
advai skill list
advai skill info <name>
advai skill update [name]
advai skill uninstall <name>
```

Install from GitHub:

```bash
advai skill install <github-url>
advai skill install <github-url> --skill <name>
advai skill install <github-url> --platform <key>
advai skill install <github-url> --platform <key> --sync-mode copy
```

Sync to agent platforms:

```bash
advai skill sync <name> --platform <key>
advai skill sync <name> --platform <key> --project-dir <dir>
advai skill unsync <name> --platform <key>
```

Manage platform metadata:

```bash
advai skill platform list
advai skill platform add <key> --name <name> --path <dir>
advai skill platform override <key> --path <dir>
advai skill platform clear-override <key>
```

## Preconditions

- This skill depends on the `advai` CLI from `https://github.com/Advai-X/advai-cli`.
- Ensure `advai` is installed and available on PATH.
- Ensure the `advai skill` subcommand is available in the current installation.
- If `advai skill` is missing, stop and guide the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.

## Operating Guidelines

- Start with `advai skill list` and `advai skill platform list` when the environment is unclear.
- Use `--skill <name>` when a GitHub repo contains multiple skills and the user wants only one.
- Use `--platform <key>` during install when the user wants the skill immediately available inside an agent.
- Use `--sync-mode symlink` for fast local iteration and `copy` for portable snapshots.
- Use `--project-dir` when a platform supports project-local skill folders and the user wants repo-scoped behavior.
- If `advai skill` is not recognized at runtime, direct the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.

## Examples

Install and sync a skill:

```bash
advai skill install https://github.com/example/skills-repo --skill data-review --platform cursor
```

Inspect platform targets:

```bash
advai skill platform list --project-dir /path/to/project
```

Resync a changed skill:

```bash
advai skill sync my-skill --platform trae --force
```
