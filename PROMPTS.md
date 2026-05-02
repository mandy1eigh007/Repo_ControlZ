# Repo ControlZ — Reusable Prompts

These prompts are designed to be copy/pasted into ChatGPT (foreman) or directly into an agent tool.

## Standard agent task prompt

Use this when you want an agent to implement a clearly scoped task.

**Prompt**

- You are working in the GitHub repo `<owner>/<repo>`.
- Goal: <one sentence goal>
- Constraints:
  - Follow repo instructions (read source-of-truth files first).
  - One task at a time; no unrelated refactors.
  - No redesign unless assigned.
  - No new dependencies unless explicitly approved.
- Deliverables:
  - Files to change: <list or “discover as needed”>
  - Definition of done:
    - <bullet>
    - <bullet>
- Validation:
  - Run: <tests/build command> (or explain why not possible).
- Report back with:
  - What changed (file list)
  - How to verify
  - Anything unverified

## Error fix prompt

Use this when there is a failing build, test, or runtime error.

**Prompt**

- Fix this error with the smallest safe change.
- Provide:
  - Root cause (brief)
  - Fix summary
  - Files changed
  - How you validated
  - What remains unverified
- Error output:

```
<paste full error log here>
```

## Review-only prompt

Use this when you want a code review without changes.

**Prompt**

- Review the current repo state for correctness, risk, and clarity.
- Do not modify files.
- Output:
  - Top issues (ranked)
  - Suggested next steps
  - Any missing source-of-truth docs

## Commit-and-report prompt

Use this when you want the agent to commit changes and produce a clean report.

**Prompt**

- Implement the assigned task.
- Run the applicable validation steps.
- Then:
  1. Show `git status`.
  2. Commit with message: `<message>`.
  3. Report:
     - Files changed/created
     - Commit hash
     - Validation run + result
     - Unverified items

## Update guide/manual prompt

Use this when the repo should learn from what just happened.

**Prompt**

- You are updating **Repo ControlZ itself** (docs/prompts/templates). This repo is documentation-only.
- Before making changes, read:
  - `README.md`
  - `GUIDE.md`
  - `PROMPTS.md`
  - `AI_PROJECT_CONTROL/02_SOURCE_OF_TRUTH.md`
  - `AI_PROJECT_CONTROL/03_CURRENT_STATE.md`
- Make the smallest Markdown-only change that captures the new workflow knowledge.
- Hard rules:
  - Do not add an app framework.
  - Do not add `package.json`, build systems, or dependencies.
  - Do not create a documentation website.
  - Do not use icons.
  - Do not change templates unless explicitly requested.
- Bookkeeping (required for manual updates):
  - Add a clear entry to `CHANGELOG.md`.
  - Add a worklog entry to `AI_PROJECT_CONTROL/05_WORKLOG.md`.
- Validation (docs-only repo):
  - Run `git diff`.
  - Run `find . -maxdepth 4 -type f -not -path './.git/*' | sort`.
  - Run `git status`.
- Commit and report:
  - Commit with a clear message (usually `docs: ...`).
  - Report files changed, validation commands run, `git status`, commit hash, and anything unverified.
