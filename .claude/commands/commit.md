---
description: Create a well-formed git commit from the current changes
argument-hint: [optional message or intent]
allowed-tools: Bash(git status:*), Bash(git diff:*), Bash(git add:*), Bash(git commit:*), Bash(git log:*)
---

## Context

- Current status: !`git status --short`
- Staged diff: !`git diff --cached`
- Unstaged diff (for reference): !`git diff`
- Recent commits (match this style): !`git log --oneline -10`

## Task

Create one focused git commit for the changes above.

1. If nothing is staged, stage the files that clearly belong together for this change with `git add`. Do not stage unrelated files, build artifacts, or anything that looks like a secret.
2. Write a commit message in the Conventional Commits style, matching the tone of the recent commits shown above:
   - Format: `type(optional-scope): summary`, where `type` is one of `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`.
   - Summary in the imperative mood, 72 characters or fewer, no trailing period.
   - Add a body only when the change needs a "why": wrap at 72 columns and explain intent, not the obvious diff.
3. If an argument was passed, treat "$ARGUMENTS" as the intent or message to base the commit on.
4. Commit with `git commit`. Do **not** push. Do not add co-author trailers or tool advertising unless the repo already does so.

If the staged changes actually cover several unrelated concerns, say so and propose splitting them into separate commits instead of forcing one.
