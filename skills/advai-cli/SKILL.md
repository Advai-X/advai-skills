---
name: "advai-cli"
description: "Discovers, installs, updates, uninstalls, and proxies external CLIs through `advai cli`. Invoke when a task needs an OpenCLI-backed tool or a GitHub CLI package via advai."
---

# Advai External CLI

Use this skill to work with external CLIs managed through `advai cli`.

## When to Invoke

Invoke this skill when the user wants to:

- Discover available external CLIs
- Inspect what an external CLI supports
- Install CLI definitions from a GitHub repository
- Update or uninstall an already managed external CLI
- Execute a supported external CLI through `advai cli <name> ...`

Do not use this skill for built-in `advai` commands such as `browser`, `skill`, `kb`, or `tui`.

## Preconditions

This skill depends on the `advai` CLI from `https://github.com/Advai-X/advai-cli`.

Before running commands:

- Ensure `advai` is installed and available on PATH.
- Ensure the `advai cli` subcommand is available in the current installation.
- If `advai cli` is missing, stop and guide the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.
- Ensure `opencli` is installed and available on PATH.

Start with:

```bash
advai cli list
```

If `opencli` is missing, report that clearly before attempting install or execution.

## Core Commands

Discover and inspect:

```bash
advai cli list
advai cli list --search <text>
advai cli info <name>
```

Install from GitHub:

```bash
advai cli install <github-url>
advai cli install <github-url> --cli <name>
```

Maintain installed CLIs:

```bash
advai cli update <name> --yes
advai cli uninstall <name> --yes
```

Execute through advai:

```bash
advai cli <name> ...
```

## Operating Guidelines

- Use `advai cli info <name>` before execution when the command set is unfamiliar.
- Use `--search` to narrow a large registry.
- Use `--cli <name>` when a GitHub repo contains multiple CLI definitions.
- Prefer the proxied `advai cli <name> ...` form when the user wants a stable entrypoint through `advai`.
- If install or update fails, capture both stdout and stderr because the wrapped toolchain can surface useful diagnostics there.
- If `advai cli` is not recognized at runtime, direct the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli` before proceeding.

## Examples

Inspect and install a CLI:

```bash
advai cli info github
advai cli install https://github.com/example/tooling-repo --cli github-helper
```

Run a proxied command:

```bash
advai cli github-helper issue list
```
