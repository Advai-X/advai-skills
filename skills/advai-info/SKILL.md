---
name: "advai-info"
description: "Inspects advai installation, runtime, and update guidance with `advai info` and `advai update`. Invoke when user asks how advai is installed, where it runs from, or how to upgrade it."
---

# Advai Project Info

Use this skill to inspect the local `advai` installation and surface environment details.

## When to Invoke

Invoke this skill when the user wants to:

- Confirm the installed `advai` version
- See runtime, entrypoint, or Python environment details
- Understand how `advai` was installed
- Get the recommended upgrade command for the current install method

Do not use this skill for browser automation, skill management, or external CLI workflows.

## Core Commands

```bash
advai info
advai update
```

## Preconditions

- This skill depends on the `advai` CLI from `https://github.com/Advai-X/advai-cli`.
- Ensure `advai` is installed and available on PATH.
- Ensure the `advai info` and `advai update` subcommands are available in the current installation.
- If either subcommand is missing, stop and guide the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.

## Operating Guidelines

- Use `advai info` first when debugging installation-path confusion.
- Use `advai update` when the user wants the correct package-manager upgrade command.
- If multiple copies of `advai` appear on the machine, explain which binary is actually active.
- If `advai info` or `advai update` is not recognized at runtime, direct the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.

## Examples

Check current runtime details:

```bash
advai info
```

Print the recommended update command:

```bash
advai update
```
