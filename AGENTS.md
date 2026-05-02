# Repo ControlZ — Live Agent Rules

This repository is **documentation-only**: it stores a living manual, prompts, and templates for controlling AI coding agents.

It is **not an app**. Do not turn it into an app unless the user explicitly changes the repo’s purpose.

## Hard constraints
- Do **not** add an app framework.
- Do **not** add `package.json`, build systems, or scaffolding tools.
- Do **not** add dependencies.
- Do **not** create a documentation website.
- Do **not** add unnecessary tooling (linters, formatters, generators) unless explicitly approved.
- Keep changes small and **Markdown-only** unless explicitly told otherwise.

## Required reading (before any change)
You must read these files first:
- `README.md`
- `GUIDE.md`
- `PROMPTS.md`
- `AI_PROJECT_CONTROL/02_SOURCE_OF_TRUTH.md`
- `AI_PROJECT_CONTROL/03_CURRENT_STATE.md`

If your plan conflicts with any of the above, stop and ask for clarification.

## Workflow rules
- One task at a time.
- No unrelated changes.
- No redesign or restructuring unless explicitly approved.
- Prefer the simplest wording and structure that satisfies the request.

## Documentation bookkeeping (required)
For every completed manual update:
- Update `CHANGELOG.md` with a clear entry.
- Add a worklog entry in `AI_PROJECT_CONTROL/05_WORKLOG.md`.

## Validation & reporting (required)
- Run the repo’s validation steps when applicable (for this repo, usually file listing + `git status`).
- Report:
  - Files created
  - Files modified
  - Validation commands run
  - `git status` after commit
  - Commit hash
  - Anything unverified
