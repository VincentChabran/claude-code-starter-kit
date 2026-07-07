---
description: Review the current changes for bugs, risks and quality before you commit
argument-hint: [optional path or focus]
allowed-tools: Bash(git status:*), Bash(git diff:*), Bash(git log:*)
---

## Context

- Changed files: !`git status --short`
- Full diff: !`git diff HEAD`

## Task

Act as a careful senior reviewer of the diff above (focus on "$ARGUMENTS" if provided).

Report findings grouped by severity — **Blocking**, **Should-fix**, **Nit** — and for each give the `file:line`, what is wrong, and a concrete fix. Look specifically for:

- **Correctness**: off-by-one, null/undefined, wrong operators, missed edge cases, error paths left unhandled.
- **Security**: injection, unsafe input handling, secrets committed, missing authorization checks.
- **Concurrency & resources**: races, leaks, unclosed handles, missing timeouts.
- **Contracts**: API changes that break callers or aren't reflected in tests/docs.
- **Readability & dead code** — keep these in **Nit**.

If the diff is clean, say so plainly instead of inventing problems. End with a one-line verdict: safe to commit, or not yet.
