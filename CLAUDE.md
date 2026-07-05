# 
Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

## 5. Verify Before Claiming Done

**Never say "done", "fixed", or "works" without running the proof.**

- Run the build, tests, or the code itself before reporting success.
- If you cannot verify (missing environment, needs manual QA), say so explicitly: "Implemented, but unverified because X."
- "It should work" is not a status. Either it's verified or it's unverified.
- Reproduce a bug before fixing it. If you can't reproduce it, say so instead of fixing blind.

## 6. Test Integrity

**Fix the code, not the test.**

- Never weaken assertions, add mocks, skip, or delete tests just to make them pass.
- Never hardcode expected values to satisfy a test.
- If you believe the test itself is wrong, say so and propose a fix - don't silently change it.
- New code that's hard to test is a design smell. Flag it.

## 7. Don't Mask Errors

**Errors should surface, not disappear.**

- No empty catch blocks. No `catch (e) {}`, no bare `except: pass`.
- No silent fallbacks or default returns that swallow failures.
- Don't log-and-continue on errors that should halt execution.
- If defensive handling is genuinely needed, make the failure visible: log with context, propagate, or fail fast.

## 8. When Blocked

**Two or three failed attempts = stop and report. Not five workarounds.**

- If the same problem persists after 2-3 different attempts, stop.
- Report: what you tried, what happened, your best hypothesis.
- Don't cascade workarounds (disabling checks, broad exception handling, commenting out code) to force progress.
- A clear "I'm stuck because X" beats a broken "solution".

## 9. Dangerous Operations

**Ask before anything destructive or hard to reverse.**

Never without explicit confirmation:
- `git push --force`, history rewrites, branch deletion
- Deleting files or data, `rm -rf`
- Database migrations or schema changes
- Changes to CI/CD pipelines, deployment or infra config
- Bulk renames/moves across the codebase

When in doubt whether something is destructive: ask.

## 10. Dependencies

**Prefer what's already there.**

- No new packages without asking. Check the standard library and existing dependencies first.
- Use the project's existing utilities/helpers instead of writing parallel ones.
- If a new dependency is genuinely justified, present it: what, why, alternatives considered.

## 11. Project Commands

**Fill in per project. These are the verification tools for §4 and §5.**

```
Build:      [command]
Test:       [command]
Lint:       [command]
Typecheck:  [command]
Run:        [command]
```

If these are missing or broken, flag it before starting work.

## 12. Task Report

**End every non-trivial task with a short summary:**

- **Changed:** files touched and why (one line each)
- **Verified:** what was run, what passed
- **Not verified:** what couldn't be checked and why
- **Open:** known issues, TODOs, decisions needed

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, clarifying questions come before implementation rather than after mistakes - and "done" always means verified.
