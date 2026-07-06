---
name: "advai-knowledge"
description: "Creates and manages local knowledge bases with `advai kb`, including doc add, search, and sync. Invoke when user wants searchable local documents or lightweight project memory."
---

# Advai Knowledge Base

Use this skill to create and maintain local knowledge bases with `advai kb`.

## When to Invoke

Invoke this skill when the user wants to:

- Create a lightweight local knowledge base
- Add project files or documents into a searchable store
- Search stored documents by keyword
- Resync stored documents from their original source files
- Build a small local memory layer for notes, docs, or reference material

Do not use this skill for full-text search over the live repository when direct code search tools are better suited.

## Core Commands

Create and populate:

```bash
advai kb create <name>
advai kb doc add <name> <path>
```

Search and refresh:

```bash
advai kb search <name> <query>
advai kb sync <name>
```

## Preconditions

- This skill depends on the `advai` CLI from `https://github.com/Advai-X/advai-cli`.
- Ensure `advai` is installed and available on PATH.
- Ensure the `advai kb` subcommand is available in the current installation.
- If `advai kb` is missing, stop and guide the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.

## Operating Guidelines

- Use a concise, durable KB name such as `product-docs`, `runbooks`, or `design-notes`.
- Add source documents with stable paths so later `sync` can refresh them correctly.
- Use `search` for quick keyword lookup across the stored document set.
- If `sync` reports missing source files, surface those paths explicitly and ask whether to replace or remove them.
- Prefer one KB per topic or project area instead of one giant mixed store.
- If `advai kb` is not recognized at runtime, direct the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.

## Examples

Create a KB and add documents:

```bash
advai kb create runbooks
advai kb doc add runbooks ./docs/incident-response.md
advai kb doc add runbooks ./docs/oncall-checklist.md
```

Search the KB:

```bash
advai kb search runbooks rollback
```

Refresh from source files:

```bash
advai kb sync runbooks
```
