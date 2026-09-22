# claude-guidelines

Personal copy of my `CLAUDE.md` — behavioral guidelines for Claude Code and other LLM coding agents. Persisted here so it doesn't get lost and can be dropped into new projects.

## Provenance

| Sections | Origin |
|---|---|
| Title, intro and tradeoff note; 1–4 — Think Before Coding, Simplicity First, Surgical Changes, Goal-Driven Execution | Copied from `CLAUDE.md` in [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) (commit [`8462496`](https://github.com/multica-ai/andrej-karpathy-skills/commit/8462496b34419f20b32778610571ac723e91f94c), retrieved 2026-09-20), derived from Andrej Karpathy's observations on LLM coding pitfalls. Word for word, apart from the §1 bullet noted in the last row. Upstream licensing is unresolved — see [Upstream license status](#upstream-license-status) |
| 5–11, 14 — Verify Before Claiming Done, Test Integrity, Don't Mask Errors, When Blocked, Dangerous Operations, Dependencies, Project Commands, Task Report | Extensions drafted with Claude (Anthropic), July 2026 |
| 12 — Secrets and Untrusted Input; §5 bullets on invented APIs and unsearched "doesn't exist" claims | Added September 2026, adapted and condensed from [coding-agent-rules](https://github.com/jitendravyas/coding-agent-rules) (MIT License, Copyright (c) 2026 Jitendra Vyas) |
| 13 — When Corrected; §1 bullet on investigate-only tasks; §5 bullet on proof per change type | Added September 2026, adapted and condensed from [grokbot-field-notes](https://github.com/unicodef1wn/grokbot-field-notes) (MIT License, Copyright (c) 2026 unicodef1wn) |

### Upstream license status

Checked against `multica-ai/andrej-karpathy-skills` on 2026-09-20:

- The repository carries no `LICENSE` file, and GitHub's license API reports none for it.
- Its `README.md` has a "License" section whose entire content is "MIT", and `.claude-plugin/plugin.json` sets `"license": "MIT"`. Neither carries a copyright line: no file in the repository contains the word "Copyright" or the MIT permission text.
- The plugin and marketplace manifests do name `forrestchang` as author — the only person named anywhere in the repository.

The terms under which the copied material may be reused are therefore not established by the upstream repository. This note records what was checked, nothing more; it is not legal advice, and the question is still open for this repository's owner.

The other two upstream projects each ship a `LICENSE` file with a copyright line, which is why their rows can name one.

## Usage

- Copy `CLAUDE.md` into a project root — Claude Code loads it automatically at session start.
- For use across all projects, place it at `~/.claude/CLAUDE.md` instead.
- Fill in **section 11 (Project Commands)** per project — it's a template.

See the [Claude Code memory docs](https://code.claude.com/docs/en/memory) for how these files are loaded.
