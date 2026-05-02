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

## Codespaces Workflow
Use this when you want a clean, repeatable dev environment in GitHub Codespaces.

1. Start Codespaces
   - Open the repo on GitHub.
   - Create or open a Codespace for the branch you intend to work on.
2. Sync and orient
   - Confirm the branch (`git status`).
   - Read the repo’s source of truth before changing anything.
   - Identify the smallest next task.
3. Do the work
   - Make the smallest correct change.
   - Keep scope to one task; avoid unrelated refactors.
4. Validate and capture evidence
   - Run the closest available tests/build if they exist.
   - If this is a docs-only repo, validate with `git diff` + file listing + `git status`.
5. Commit and report
   - Commit with a clear message.
   - Report changed files, validation commands run, `git status`, commit hash, and anything unverified.

## VS Code Chat Custom Instruction Workflow
Use VS Code Chat / GitHub Copilot Chat when you’re working inside a repo and want an agent to follow rules consistently.

Repo-level custom instructions help the agent remember guardrails across prompts, but they **do not replace** the repo’s source-of-truth docs. Agents must still be told to read the source of truth before editing.

Key file:
- `.github/copilot-instructions.md`

Starter template:
- `templates/copilot-instructions.md`

### Workflow
1. Open the repo in VS Code or Codespaces.
2. Add `.github/copilot-instructions.md` to the working repo.
3. Copy the starter content from `templates/copilot-instructions.md`.
4. Add or update `AGENTS.md` and `AI_PROJECT_CONTROL/` files if needed.
5. Start every VS Code Chat task by telling it to read:
   - `.github/copilot-instructions.md`
   - `AGENTS.md`
   - `AI_PROJECT_CONTROL/02_SOURCE_OF_TRUTH.md`
   - `AI_PROJECT_CONTROL/03_CURRENT_STATE.md`
6. Give it one task at a time.
7. Require it to report changed files, build/test commands, git status, commit hash, and unverified items.
8. Push after the commit.

### Warning: drift still happens
VS Code Chat can still lose context or drift.

If it starts changing unrelated files:
1. Stop it.
2. Run `git status`.
3. Run `git diff`.
4. Bring the output back to ChatGPT (foreman) for review before continuing.

## Replit Restart Workflow
Use this when returning to a Replit project after a gap, when the agent lost context, or when the app is half-built.

GitHub should remain the source of truth. Treat Replit as a build/work environment, not the permanent memory.

Before asking the Replit agent to build anything, confirm the repo state. Do not let Replit redesign, rename, restructure, or add dependencies unless that is the assigned task.

### Workflow
1. Open the Replit project.
2. Confirm it is connected to the correct GitHub repo.
3. Pull latest changes from GitHub if available.
4. Check what files exist.
5. Check current errors or broken behavior.
6. Bring the current state back to ChatGPT for foreman review.
7. Ask ChatGPT for one scoped Replit agent prompt.
8. Paste the prompt into Replit.
9. Review the agent report.
10. Commit and push changes back to GitHub.
11. Bring the final report back to ChatGPT.

### Emergency recovery
If Replit gets weird, stops responding, breaks the app, or changes too much:
- Stop the agent.
- Do not keep prompting randomly.
- Check Git status/version control panel.
- Identify changed files.
- Copy the error/output/report.
- Bring it back to ChatGPT before accepting more changes.
- If needed, revert unwanted changes before continuing.

### Do Not Let Replit Do This
- Do not rebuild the whole app.
- Do not change architecture without approval.
- Do not rename files or folders without approval.
- Do not add dependencies without approval.
- Do not restyle the app unless styling is the task.
- Do not overwrite source-of-truth docs.

## Guardrails
Use these guardrails to keep AI agents safe, scoped, and predictable.

### Scope Guardrails
- One task at a time.
- No broad “make it better” tasks.
- No drive-by fixes.
- No unrelated refactors.
- If the task grows, stop and split it into smaller tasks.

### Repo Guardrails
- GitHub is the source of truth.
- Check branch and repo before work.
- Do not change repo structure without approval.
- Do not overwrite source-of-truth files.
- Do not delete control files.
- Keep `AGENTS.md` and `AI_PROJECT_CONTROL` files intact.

### Code Guardrails
- Do not change architecture unless assigned.
- Do not rename files/folders unless assigned.
- Do not add dependencies unless approved.
- Do not restyle unless styling is the task.
- Do not remove working features.
- Make the smallest safe change.

### Documentation Guardrails
- Markdown is the source of truth.
- ZIP, PDF, DOCX, and image files are exports or artifacts, not the master copy.
- Every manual update requires `CHANGELOG.md` and `AI_PROJECT_CONTROL/05_WORKLOG.md` updates.
- Keep wording direct and practical.

### Agent Reporting Guardrails
Every agent report should include:
- Files changed
- What changed
- Tests/build/validation commands run
- Git status
- Commit hash or reason no commit was made
- Anything unverified

### Stop-Work Guardrails
Stop the agent and bring the situation back to ChatGPT if:
- The agent changes unrelated files.
- The agent wants to redesign or restructure without approval.
- The agent adds dependencies without approval.
- The agent cannot explain the root cause.
- The build fails and the fix is unclear.
- The wrong repo or branch is active.
- There are uncommitted changes that are not understood.
- The agent starts looping or guessing.

### Minimum Evidence to Collect Before Asking for Help
- `git status`
- `git diff`
- `git log --oneline -5`
- Full error output
- Agent report
- Screenshot if the issue is visual

## Troubleshooting
Use this when AI coding workflows go sideways: drift, missed commits, tool disconnects, broken builds, or lost context.

### 1. Agent changed too much
- Stop the agent.
- Run `git status`.
- Run `git diff`.
- Identify changed files.
- Bring the diff/status back to ChatGPT for review.
- Do not keep prompting the same agent until scope is understood.

### 2. Agent forgot to commit
- Run `git status`.
- If changes are correct, commit them.
- If unsure, bring changed files/status back to ChatGPT.
- Push only after the commit is confirmed.

### 3. Local VS Code disconnected or crashed
- Reopen the repo or switch to Codespaces.
- Run `git status`.
- Run `git log --oneline -5`.
- Check for uncommitted files.
- Do not restart the task until the repo state is understood.

### 4. Wrong branch or wrong repo
- Run `git branch --show-current`.
- Run `git remote -v`.
- Confirm the repo name and branch before continuing.
- Stop if the repo/branch is wrong.

### 5. Build is broken
- Copy the full error output.
- Do not ask for a broad rebuild.
- Ask ChatGPT for a scoped error-fix prompt.
- Require the agent to explain root cause and changed files.

### 6. Deployed app is blank or broken
- Confirm whether the page shell loads.
- Check browser console errors.
- Check routing/base path.
- Check app mount point.
- Check missing assets/data.
- Make the smallest safe fix.

### 7. Agent wants to redesign/restructure
- Stop.
- Reconfirm source-of-truth files.
- Only allow redesign/restructure if the task explicitly says so.

### 8. Lost context / returning after a gap
- Read `AI_PROJECT_CONTROL/03_CURRENT_STATE.md`.
- Read `AI_PROJECT_CONTROL/04_TASK_BOARD.md`.
- Read latest `AI_PROJECT_CONTROL/05_WORKLOG.md`.
- Ask ChatGPT for the next scoped prompt.

### When in doubt
Stop and collect:
- `git status`
- `git diff`
- `git log --oneline -5`
- error output
- agent report

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
