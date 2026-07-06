# Advai Skills

This repository contains skill definitions for the `advai` CLI.

Each skill lives under the `skills/` directory and provides a `SKILL.md` file that defines when the skill should be invoked, what commands it covers, and how an agent should operate it.

## Skills

- `advai-browser`: browser automation through `advai browser`
- `advai-cli`: external CLI discovery, install, update, uninstall, and proxy execution through `advai cli`
- `advai-knowledge`: local knowledge base creation, search, and sync through `advai kb`
- `advai-info`: runtime, installation, and update guidance through `advai info` and `advai update`
- `advai-skill`: local skill lifecycle management through `advai skill`

## Repository Layout

- `skills/*/SKILL.md`: skill metadata and operating instructions
- `skills.sh.json`: repo-level grouping config for the skills.sh repository page
- `.gitignore`: shared ignore rules for local editor files and temporary artifacts

## Notes

- Keep skill names, directory names, and top-level descriptions aligned when renaming a skill.
- Prefer concise, task-oriented command examples in each `SKILL.md`.
- Use `skills.sh.json` to curate how this repo is grouped and presented on skills.sh.
