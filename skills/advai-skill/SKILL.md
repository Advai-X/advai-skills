---
name: "advai-skill"
description: "Manages local skills with `advai skill`, including search, install, list, update, sync, unsync, uninstall, and platform path management. Invoke when user wants to add, maintain, or distribute skills."
---

# Advai Skill Manager

Use this skill to manage local skills and sync them into supported agent platforms through `advai skill`.

## When to Invoke

Invoke this skill when the user wants to:

- Search installable skills before choosing one
- Install a skill by name from a source provider or from a GitHub repository URL
- List, inspect, update, or uninstall installed skills
- Sync a skill into Cursor, Claude Code, Codex, TRAE, or another supported platform
- Configure custom skill platforms or override global or project-relative paths
- Troubleshoot where a skill is installed or synced

Do not use this skill for creating a brand-new skill definition from scratch unless the user specifically wants to manage that skill after creation.

## Core Commands

Discover and inspect:

```bash
advai skill search <query>
advai skill search <query> --source <provider>
advai skill list
advai skill info <name>
```

Install and update:

```bash
advai skill install <skill-name>
advai skill install <skill-name> --source <provider> --version <version>
advai skill install <skill-name> --platform <key> --sync-mode copy
advai skill install <skill-name> --platform <key> --project-dir <dir>
advai skill install <github-url>
advai skill install <github-url> --skill <name> --platform <key>
advai skill update [name]
```

Sync and remove:

```bash
advai skill sync <name> --platform <key>
advai skill sync <name> --platform <key> --platform <key>
advai skill sync <name> --platform <key> --project-dir <dir> --force
advai skill unsync <name> --platform <key>
advai skill uninstall <name>
```

Manage platform metadata:

```bash
advai skill platform list
advai skill platform list --project-dir <dir>
advai skill platform add <key> --name <name> --path <dir> --category custom
advai skill platform add <key> --name <name> --path <dir> --project-path .agent/skills
advai skill platform override <key> --path <dir> --project-path .agent/skills
advai skill platform clear-override <key>
advai skill platform remove <key>
```

## Preconditions

- This skill depends on the `advai` CLI from `https://github.com/Advai-X/advai-cli`.
- Ensure `advai` is installed and available on PATH.
- Ensure the `advai skill` subcommand is available in the current installation.
- If `advai skill` is missing, stop and guide the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.
- Start with `advai skill list` and `advai skill platform list` when the local skill state is unclear.

## Operating Guidelines

- Use `advai skill search <query>` before installation when the user does not already know the exact skill name.
- Use `--source <provider>` to constrain installs or searches to a specific skill source.
- Use `--version <version>` only when the user explicitly wants a pinned version.
- Use a GitHub repository URL when the user wants to install directly from a repo instead of a named registry entry.
- Use `--skill <name>` when a GitHub repo contains multiple skills and the user wants only one.
- Use repeated `--platform <key>` flags when the user wants the same skill synced into multiple targets.
- Use `--sync-mode symlink` for fast local iteration and `copy` for portable snapshots.
- Use `--project-dir` when a platform supports project-local skill folders and the user wants repo-scoped behavior.
- Use `platform add` with `--project-path` when defining a custom platform that supports project-local sync targets.
- Use `platform override` to adjust built-in or custom paths without redefining the whole platform.
- Use `platform remove` only for custom platforms; use `clear-override` to reset path overrides on existing platforms.
- If `advai skill` is not recognized at runtime, direct the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.

## Examples

Search and inspect:

```bash
advai skill search browser --limit 10
advai skill info advai-browser
```

Install and sync to a platform:

```bash
advai skill install advai-browser --source github --platform trae
```

Install directly from a GitHub repository:

```bash
advai skill install https://github.com/Advai-X/advai-skills --skill advai-browser --platform trae
```

Inspect platform targets for a project:

```bash
advai skill platform list --project-dir /path/to/project
```

Add a custom platform with project-local support:

```bash
advai skill platform add my-agent --name "My Agent" --path ~/.my-agent/skills --project-path .my-agent/skills
```

Resync a changed skill:

```bash
advai skill sync my-skill --platform trae --force
```
