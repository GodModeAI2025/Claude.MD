# claude-guidelines

Personal copy of my `CLAUDE.md` — behavioral guidelines for Claude Code and other LLM coding agents. Persisted here so it doesn't get lost and can be dropped into new projects.

## Provenance

| Sections | Origin |
|---|---|
| 1–4 — Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution | Original guidelines from [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills), derived from Andrej Karpathy's observations on LLM coding pitfalls |
| 5–11, 13 — Verify Before Claiming Done, Test Integrity, Don't Mask Errors, When Blocked, Dangerous Operations, Dependencies, Project Commands, Task Report | Extensions drafted with Claude (Anthropic), July 2026 |
| 12 — Secrets and Untrusted Input; §5 bullets on invented APIs and unsearched "doesn't exist" claims | Added September 2026, ideas from [coding-agent-rules](https://github.com/jitendravyas/coding-agent-rules) (MIT), rewritten in this file's style |

## Usage

- Copy `CLAUDE.md` into a project root — Claude Code loads it automatically at session start.
- For use across all projects, place it at `~/.claude/CLAUDE.md` instead.
- Fill in **section 11 (Project Commands)** per project — it's a template.

See the [Claude Code memory docs](https://code.claude.com/docs/en/memory) for how these files are loaded.
