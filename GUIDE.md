# Repo ControlZ: AI Build Foreman Training Guide

## Purpose
Repo ControlZ is a lightweight, durable “living manual” for running AI-assisted software work.

The point is simple: **the repo is the memory**. Chats are temporary. This repository holds the instructions, prompts, templates, and decision logs needed to reliably steer AI coding agents.

## The Three-Part System
1. **The Repo (durable memory):** files that define goals, constraints, current state, and decisions.
2. **The Foreman (ChatGPT):** reads the repo, turns goals into crisp tasks, writes agent prompts, reviews outputs.
3. **The Worker (agent tools):** Codex / VS Code Chat / Copilot / Replit agent executes tasks in code and reports back.

## What Goes in the Repo
- Project briefs and constraints (what success looks like)
- Source-of-truth files (decisions, requirements, known constraints)
- Worklogs (what was tried, what changed, what’s blocked)
- Reusable prompts and templates
- Checklists for review, testing, and release

## What ChatGPT Does
- Reads the repo’s source-of-truth docs before proposing work
- Breaks work into small, verifiable tasks
- Writes clear agent prompts (inputs, constraints, done-criteria)
- Reviews diffs and test results
- Produces next-step instructions and updates the manual when patterns emerge

## What Codex / VS Code Chat Does
- Works inside the repo (edits files, runs tests/builds when applicable)
- Follows the instructions in the repo (and any `copilot-instructions.md`)
- Keeps changes scoped to the assigned task
- Reports what changed and what’s unverified

## What the User Does
- Owns final decisions and merges
- Provides missing context (screenshots, error logs, requirements)
- Runs the work in real environments when needed
- Confirms outcomes ("works on my machine", “deployed”, etc.)

## Starting a New Repo
1. Create/open the repo.
2. Add this manual starter structure.
3. Fill in the AI Project Control templates under `templates/AI_PROJECT_CONTROL/` (or copy them into a project-specific folder).
4. Ask ChatGPT (foreman) to produce a first task prompt for your chosen agent tool.

## Restarting a Repo
Use this when you’re returning after a gap.
1. Read the latest `CHANGELOG.md` and any project worklog.
2. Update “Current State” (what works, what’s broken, what changed externally).
3. Rebuild a short task board (top 3–10 tasks).
4. Run a small “review-only” pass before resuming implementation.

## Deep-Dive Fix Workflow
Use this for stubborn bugs and messy failures.
1. Capture a clean reproduction path.
2. Collect the exact error output (full stack trace / logs).
3. Identify the last known good state (commit, tag, or release).
4. Make a minimal fix with a tight scope.
5. Verify with the closest possible test/build.
6. Write a short worklog entry: symptom → cause → fix → verification.

## How to Update This Manual
Use this when you’re changing Repo ControlZ itself (the manual, prompts, and templates).

1. Read the source of truth first:
   - `README.md`
   - `GUIDE.md`
   - `PROMPTS.md`
   - `AI_PROJECT_CONTROL/02_SOURCE_OF_TRUTH.md`
   - `AI_PROJECT_CONTROL/03_CURRENT_STATE.md`
2. Keep scope tight:
   - One task at a time.
   - Small, Markdown-only changes unless explicitly told otherwise.
   - Don’t add frameworks, `package.json`, dependencies, or a documentation site.
3. Make the change.
4. Bookkeeping (required for manual updates):
   - Update `CHANGELOG.md`.
   - Add an entry to `AI_PROJECT_CONTROL/05_WORKLOG.md`.
5. Validate:
   - For this docs-only repo, run `find . -maxdepth 4 -type f -not -path './.git/*' | sort` and `git status`.
   - If you ran anything else (lint/tests/build), include it in the report.
6. Commit and report:
   - Use a clear commit message (`docs: ...`).
   - Report files changed, validation commands run, `git status`, commit hash, and anything unverified.

## Commit Rules
- Keep commits small and single-purpose.
- Prefer descriptive messages (e.g., `docs: ...`, `fix: ...`, `chore: ...`).
- Do not commit generated artifacts unless explicitly required.
- If tests/build exist, run them (or state clearly when you did not).
- Record unverified items (anything you didn’t run or can’t validate).
