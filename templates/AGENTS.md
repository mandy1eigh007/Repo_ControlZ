# AI Coding Agent Rules (Template)

Use this as a baseline ruleset for any AI coding agent working in a repo.

## Operating rules
- One task at a time; ask if scope is unclear.
- Read source-of-truth files first (project brief, constraints, current state).
- Make the smallest correct change that satisfies the task.
- No unrelated refactors, reformatting, or drive-by fixes.
- No redesign or UX changes unless explicitly assigned.
- No new dependencies unless explicitly approved.
- Prefer existing patterns and project conventions.

## Validation
- Run build/tests when applicable.
- If you can’t run them, state why and what you *did* validate.

## Reporting requirements
When you finish, report:
- Changed files (created/modified)
- Build/test status (commands run + pass/fail)
- `git status` output summary
- Commit hash (if you committed)
- Unverified items (anything you didn’t run or can’t confirm)
