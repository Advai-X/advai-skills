# Contributing

Thanks for contributing to `advai-skills`.

## Scope

This repository contains task-focused skill definitions for the [`advai` CLI](https://github.com/Advai-X/advai-cli). Contributions should keep skills concise, actionable, and safe for agent use.

## Repository Rules

- Put every skill in `skills/<name>/SKILL.md`.
- Use the `advai-` prefix for every skill name.
- Keep the `name` field aligned with the directory name.
- Document the exact `advai` subcommand the skill covers.
- Require a preflight check that verifies the needed `advai <subcommand>` exists.
- If a subcommand is missing, instruct the user to install or upgrade `advai`; do not guess fallback commands.

## When Updating a Skill

- Clarify when the skill should be invoked.
- Keep examples short and copy-pasteable.
- Prefer operational guidance over marketing language.
- Update the root `README.md` if the skill list or command mapping changes.
- Update `skills.sh.json` if a new skill should appear in the grouped repository listing.

## Suggested Workflow

1. Create a branch for your change.
2. Edit the relevant `SKILL.md` file.
3. Verify that the skill name starts with `advai-` and matches the directory name.
4. Review the examples and command names for correctness.
5. Open a pull request with a concise summary of the change.

## Pull Request Checklist

- The skill name starts with `advai-` and matches its directory name.
- Commands and examples use the correct `advai` subcommand.
- Preconditions clearly state what must exist before use.
- The README and `skills.sh.json` are updated when needed.
- Changes stay focused and do not introduce unrelated rewrites.
