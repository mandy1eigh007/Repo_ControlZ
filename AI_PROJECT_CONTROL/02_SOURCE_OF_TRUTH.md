# Repo ControlZ — Source of Truth

This file locks the core decisions for this repository. If advice from chat conflicts with this file, **this file wins**.

## Core decisions
- Repo ControlZ is **documentation/manual/template storage**.
- **Markdown files are the source of truth.**
- ZIP/DOCX/PDF/image exports are optional artifacts, not the main truth.
- Keep workflows simple and repo-driven.
- Roles:
  - ChatGPT acts as the **foreman** (planning, prompts, review, next steps).
  - Codex / VS Code Chat / Copilot / Replit agents act as **workers** (execute tasks in the repo).
- GitHub (the repo) is the durable memory.

## Do-not-change rules
- Do not add an app framework.
- Do not add dependencies.
- Do not restructure the repo without explicit approval.
- Do not replace simple Markdown with a complex documentation site.
- Do not use icons.

## Definition of done (for changes to this manual)
A change is “done” when:
- The requested docs/templates are created/updated.
- The change is small and scoped to the task.
- `CHANGELOG.md` is updated.
- `AI_PROJECT_CONTROL/05_WORKLOG.md` includes an entry.
- Validation commands (appropriate to a docs-only repo) were run and results reported.
- A commit exists with a clear message, and `git status` is clean after commit.
