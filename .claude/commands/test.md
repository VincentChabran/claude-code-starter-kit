---
description: Write and run tests for a file, a function, or the current changes
argument-hint: [file, function, or "diff"]
allowed-tools: Bash(git diff:*)
---

## Task

Add meaningful tests for the target: "$ARGUMENTS". If it is empty, test the code changed in the current diff: !`git diff --stat HEAD`

1. Find the project's existing test framework and conventions (config files, existing test files, the test script). Match them — do not introduce a new framework.
2. Write tests that cover: the happy path, boundary values, empty/invalid input, and at least one failure or error path. Prefer a few sharp cases over many redundant ones.
3. Name each test so a reader learns the expected behavior from the name alone.
4. Run the test suite and iterate until the new tests pass. Show the final command and its output.

Do not weaken assertions or delete existing tests to make things pass. If the code under test has a bug that a correct test exposes, report the bug instead of writing the test around it.
