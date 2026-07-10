# Claude Code Starter Kit

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](./LICENSE)
![Made for Claude Code](https://img.shields.io/badge/made%20for-Claude%20Code-6b4fbb)

**Claude Code Starter Kit is a free, MIT-licensed set of ready-to-use configuration files for [Claude Code](https://docs.anthropic.com/en/docs/claude-code)** — four slash commands (`/commit`, `/review`, `/test`, `/explain`), a `code-reviewer` subagent, and an auto-format hook. Copy them into a `.claude/` folder, restart Claude Code, and you have a power-user Claude Code setup in minutes. No setup, no dependencies to wire up — just files.

> **Unofficial, community-made. Not affiliated with or endorsed by Anthropic.**
> "Claude" and "Claude Code" are trademarks of Anthropic.

## What's inside

| File | What it does |
|---|---|
| `.claude/commands/commit.md` | `/commit` — stage and write a clean Conventional Commit that matches your repo's style |
| `.claude/commands/review.md` | `/review` — senior-style review of your current diff, ranked Blocking / Should-fix / Nit |
| `.claude/commands/test.md` | `/test` — write and run meaningful tests using your existing framework |
| `.claude/commands/explain.md` | `/explain` — clear walkthrough of a file, function, or concept |
| `.claude/agents/code-reviewer.md` | a `code-reviewer` subagent Claude can delegate to automatically |
| `.claude/settings.example.json` | one hook: auto-format files right after Claude edits them |
| `CLAUDE.md` | a minimal project-memory template to fill in |

Everything is generic and works in any codebase and any language.

## Install

**In one project** — copy the `.claude/` folder and `CLAUDE.md` into the repo root:

```sh
cp -r .claude /path/to/your/project/
cp CLAUDE.md  /path/to/your/project/
```

**For every project** — install the commands and the subagent globally in your home directory:

```sh
mkdir -p ~/.claude/commands ~/.claude/agents
cp .claude/commands/*.md ~/.claude/commands/
cp .claude/agents/*.md   ~/.claude/agents/
```

`.claude/` in a repo applies to that project (and can be committed for your team); `~/.claude/` applies to all your projects. You can use both — project settings win when they collide.

Then restart Claude Code, type `/`, and you'll see the new commands. Fill in `CLAUDE.md` with your project's stack, commands, and conventions so Claude has context from the first message.

### Enable the auto-format hook (optional)

Merge the `hooks` block from `.claude/settings.example.json` into your `~/.claude/settings.json` (all projects) or `.claude/settings.json` (this project). It runs your formatter — `prettier`, `black`, `gofmt`, or `rustfmt` — on each file right after Claude edits it, and quietly does nothing if that formatter isn't installed. Reading the hook payload uses [`jq`](https://jqlang.github.io/jq/) (`brew install jq` / `sudo apt install jq`).

## Install as a plugin

Prefer not to copy files by hand? Install the whole kit as a Claude Code plugin. From inside Claude Code:

```
/plugin marketplace add VincentChabran/claude-code-starter-kit
/plugin install cc-starter-kit@cc-starter-kit-market
```

Restart Claude Code and you'll have the four commands, the `code-reviewer` subagent, and the auto-format hook — same files as above, wired up for you. Update later with `/plugin marketplace update cc-starter-kit-market`, and remove it any time with `/plugin uninstall cc-starter-kit`.

The commands are read straight from `.claude/commands/`, the hook from `hooks/hooks.json`, and the subagent from `agents/code-reviewer.md` (a mirror of `.claude/agents/code-reviewer.md` so both the manual-copy and plugin installs stay in sync).

> **Unofficial, community-made. Not affiliated with or endorsed by Anthropic.** "Claude" and "Claude Code" are trademarks of Anthropic.

## Example

Make some changes, then let the commands do the busywork:

```
/review                         # senior-style review of your current diff
/test src/auth/session.js       # write and run tests for that file
/commit                         # a clean Conventional Commit from what's staged
/explain src/queue/worker.js    # understand code before you touch it
```

The `code-reviewer` subagent also kicks in on its own after you change code — or ask for it by name: *"have the code-reviewer look at this."*

## Requirements

- A recent version of Claude Code (slash commands, subagents, and hooks support).
- Your own Claude Code access — a Claude plan or API access. This kit is configuration you run *with* Claude Code; it doesn't include it.
- `jq` for the hook (optional — only if you enable it).
- macOS or Linux out of the box; Windows via WSL or Git Bash.

## FAQ

**How do custom slash commands work in Claude Code?**
Each command is a markdown file in `.claude/commands/`. The file name becomes the command — `commit.md` → `/commit` — and the file's body is the prompt Claude runs. Optional YAML frontmatter sets a description, an argument hint, and which tools the command may use.

**Where do the files go — project or home directory (`.claude` vs `~/.claude`)?**
`.claude/` in a repository applies to that project and can be committed to share with your team. `~/.claude/` in your home directory applies to every project you open. You can use both at once; when a project file and a global file collide, the project one wins.

**Do I need a paid Claude Code plan to use this?**
Yes — you need your own Claude Code access, either a Claude plan or API access. This starter kit is a set of configuration files; it does not include Claude Code or any Claude usage.

**Is this official / affiliated with Anthropic?**
No. It's an independent, community-made kit for Claude Code, released under the MIT license. It is not affiliated with, sponsored by, or endorsed by Anthropic. "Claude" and "Claude Code" are trademarks of Anthropic.

**What's the difference between this and the Power Pack?**
This free starter kit has 4 commands, 1 subagent, and 1 hook. The paid Claude Code Power Pack adds 8 more commands, 5 more subagents, 4 more hooks, a git-aware status line, and a full commented CLAUDE.md template — see below.

## Learn more

Two articles walk through this kit in depth:

- **[The Claude Code setup I install in every repo: slash commands, a review subagent, and hooks](https://dev.to/vincentchabran/the-claude-code-setup-i-install-in-every-repo-slash-commands-a-review-subagent-and-hooks-404j)** — the full tour of this setup and the reasoning behind each file.
- **[Why Claude Code keeps asking for permission — and how to fix your setup so it stops](https://dev.to/vincentchabran/why-claude-code-keeps-asking-for-permission-and-how-to-fix-your-setup-so-it-stops-3ho8)** — a deep dive into Claude Code permissions, and why commands like `/commit` and `/review` declare `allowed-tools` in their frontmatter.

## License

[MIT](./LICENSE) © 2026 Vincent Chabran. Use it, modify it, ship it — no strings attached.

---

### Want the full toolkit?

This is the free starter. The **Claude Code Power Pack** adds the rest:

- **12 slash commands** (adds `/pr` `/refactor` `/document` `/debug` `/optimize` `/scaffold` `/changelog` `/tidy`)
- **6 subagents** (adds `test-writer` `debugger` `doc-writer` `refactor-specialist` `security-auditor`)
- **5 hooks**, a **git-aware status line**, a full commented **CLAUDE.md** template, and a step-by-step guide.

→ **[Get the Claude Code Power Pack](https://vincentdu2a.gumroad.com/l/bqndfi)**
