---
name: "advai-browser"
description: "Drives browser automation with `advai browser` for navigation, DOM actions, extraction, screenshots, cookies, tabs, and network capture. Invoke when a task needs live browser interaction or web scraping."
---

# Advai Browser

Use this skill to operate a live browser through `advai browser`.

## When to Invoke

Invoke this skill when the user wants to:

- Open or navigate real web pages
- Click, type, fill, select, or scroll in a browser
- Read DOM content, extract structured data, or execute JavaScript
- Capture screenshots, inspect cookies, or manage tabs
- Scrape public web content or validate browser-side behavior

Do not use this skill for static codebase inspection or for platforms that already have a more specific native skill.

## Preconditions

Before running browser actions:

1. This skill depends on the `advai` CLI from `https://github.com/Advai-X/advai-cli`.
2. Ensure `advai` is installed and available on PATH.
3. Ensure the `advai browser` subcommand is available in the current installation.
4. If `advai browser` is missing, stop and guide the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli` before continuing.
5. Ensure the browser extension/runtime is installed and connected.
6. Start with:

```bash
advai browser doctor
```

If browser support is unavailable, surface the doctor output and explain what is missing.

## Core Workflow

Use a named session for each task, for example `demo`, `zhihu`, `checkout`, or `research`.

Basic flow:

```bash
advai browser open demo https://example.com
advai browser wait demo --selector "h1"
advai browser get demo
advai browser exec demo "document.title"
```

Reuse the current tab instead of creating a new one:

```bash
advai browser open demo https://example.com --replace
```

Important behavior:

- `open` creates a new tab by default
- `open --replace` reuses the current tab when the session already has one
- If the session has no active page, `open --replace` falls back to opening a new tab
- Tabs are not closed automatically after the action completes

## Common Commands

Open and navigate:

```bash
advai browser open <session> <url>
advai browser open <session> <url> --replace
advai browser navigate <session> <url>
advai browser state <session>
```

Interact with the page:

```bash
advai browser click <session> <selector>
advai browser type <session> <selector> <text>
advai browser fill <session> <selector> <text>
advai browser select <session> <selector> <option>
advai browser keys <session> <text>
advai browser scroll <session> --selector <css>
advai browser back <session>
```

Read and extract:

```bash
advai browser get <session> [--selector <css>]
advai browser find <session> <selector>
advai browser extract <session> [code]
advai browser exec <session> "<js>"
advai browser wait <session> --selector <css>
advai browser wait <session> --text <text>
```

Session utilities:

```bash
advai browser cookies <session> [--domain <domain>]
advai browser tabs list <session>
advai browser tabs new <session> --url <url>
advai browser tabs select <session> <index>
advai browser tabs close <session> <index>
advai browser close <session>
```

Advanced capture:

```bash
advai browser screenshot <session> --output page.png
advai browser network start <session> --pattern <text>
advai browser network read <session>
advai browser frames <session>
advai browser cdp <session> <method> --params '{"key":"value"}'
```

## Operating Guidelines

- Prefer `wait` before reading or clicking dynamic content.
- Prefer `get`, `find`, `extract`, or `exec` over brittle string parsing.
- Use stable selectors whenever possible.
- Use explicit session names so multi-step tasks remain traceable.
- Clean up with `tabs close` or `close` when the workflow intentionally ends.
- For scraping tasks, first validate page readiness, then extract structured data.
- If `advai browser` is not recognized at runtime, do not guess alternate commands; direct the user to install or upgrade `advai` from `https://github.com/Advai-X/advai-cli`.

## Examples

Search a page:

```bash
advai browser open zhihu https://www.zhihu.com/hot
advai browser wait zhihu --selector "body"
advai browser extract zhihu "Array.from(document.querySelectorAll('a')).slice(0,10).map(a => a.innerText).filter(Boolean)"
```

Reuse an existing session tab:

```bash
advai browser open research https://trends24.in/ --replace
advai browser wait research --selector "body"
advai browser screenshot research --output trends.png
```
