# Repo ControlZ — Current State

## Baseline
Starter manual files were created and pushed in commit `50227e2`.

## Current state
- Live repo control files are in place (`AGENTS.md`, `AI_PROJECT_CONTROL/`).
- Manual update workflow is documented in `GUIDE.md`.
- Stronger “Update guide/manual prompt” exists in `PROMPTS.md`.
- Codespaces workflow is documented in `GUIDE.md`.
- VS Code Chat custom instruction workflow is documented in `GUIDE.md`.
- Replit restart workflow is documented in `GUIDE.md`.
- Troubleshooting section is documented in `GUIDE.md`.

Repo contents:
- `README.md` exists
- `GUIDE.md` exists
- `PROMPTS.md` exists
- `CHANGELOG.md` exists
- `templates/` exists

## Current goal
- Keep Repo ControlZ current as workflow questions come up.

## Next approved task
- Maintain Repo ControlZ as new workflow questions come up.

## Verification
- No build required (docs-only repo).
- Run:
  - `find . -maxdepth 4 -type f -not -path './.git/*' | sort`
  - `git status`
