---
description: Explain how a file, function or concept in this codebase works
argument-hint: [file path, symbol, or question]
---

## Task

Explain: $ARGUMENTS

If the argument names a file or symbol, read it (and, when useful, the things it imports or that call it) before answering. Then explain, in this order:

1. **Purpose** — what problem this code solves, in one or two sentences.
2. **Flow** — the main path of execution or data, step by step, referencing the real function and variable names.
3. **Key decisions** — non-obvious choices, invariants, and assumptions the code relies on.
4. **Gotchas** — edge cases, side effects, and the places that would break if changed carelessly.

Be concrete and cite the actual code. If something is genuinely unclear from the source, say so rather than guessing. Keep it tight — clarity over length.

> Tip: you can also point at a specific file inline, e.g. `/explain @src/auth/session.js`, to load its contents directly.
