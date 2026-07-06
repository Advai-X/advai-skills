# Advai Skills

[![skills.sh](https://skills.sh/b/Advai-X/advai-skills)](https://skills.sh/Advai-X/advai-skills)

Skill definitions for the [`advai` CLI](https://github.com/Advai-X/advai-cli).

This repository is the source of truth for a small set of task-focused skills that help coding agents use `advai` subcommands correctly. Each skill documents:

- when it should be invoked
- which `advai` subcommands it covers
- required preflight checks
- safe operating patterns and examples

## Repository

- GitHub: `github.com/Advai-X/advai-skills`
- Clone URL: `git@github.com:Advai-X/advai-skills.git`
- Primary dependency: `https://github.com/Advai-X/advai-cli`

## Included Skills

| Skill | Advai Command | Purpose |
| --- | --- | --- |
| `advai-browser` | `advai browser` | Browser automation, DOM interaction, extraction, screenshots, tabs, cookies, and network capture |
| `advai-cli` | `advai cli` | Discover, install, update, uninstall, and proxy external CLIs |
| `advai-info` | `advai info`, `advai update` | Inspect runtime details and show upgrade guidance |
| `advai-knowledge` | `advai kb` | Create, search, and sync local knowledge bases |
| `advai-skill` | `advai skill` | Install, inspect, sync, update, and uninstall skills |

## Usage

Install from the `skills.sh` ecosystem with the `skills` CLI:

```bash
npx skills add Advai-X/advai-skills
```

Install this repository as a skill source with `advai skill`:

```bash
advai skill install https://github.com/Advai-X/advai-skills
```

Install and immediately sync a single skill to a supported platform:

```bash
advai skill install https://github.com/Advai-X/advai-skills --skill advai-browser --platform trae
```

Sync an already installed skill to another platform:

```bash
advai skill sync advai-browser --platform codex
```

## Authoring Conventions

- Every skill lives in `skills/<name>/SKILL.md`.
- Every skill name must use the `advai-` prefix.
- The `name` field in each `SKILL.md` must match the directory name.
- Skill instructions must verify that the required `advai <subcommand>` exists before use.
- If a required subcommand is missing, the skill must tell the user to install or upgrade `advai`; it must not guess alternative commands.
- Command examples should stay concise and task-oriented.

## Publishing Notes

- `skills.sh.json` controls how this repo is grouped on `skills.sh`.
- Keep GitHub-facing descriptions and per-skill descriptions aligned when renaming or expanding a skill.
- Update this README whenever a new skill is added or an existing command mapping changes.

## Contributing

See `CONTRIBUTING.md` for contribution guidelines and pull request expectations.

## License

This repository is licensed under the MIT License. See `LICENSE` for details.
