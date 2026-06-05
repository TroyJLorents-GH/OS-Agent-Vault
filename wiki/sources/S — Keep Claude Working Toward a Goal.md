---
title: "S — Keep Claude Working Toward a Goal"
type: source
created: 2026-05-16
updated: 2026-05-16
sources: ["Keep Claude working toward a goal.md"]
tags: [agents, claude-code, technique, "2026"]
---

# Keep Claude Working Toward a Goal

**Source:** [code.claude.com/docs/en/goal](https://code.claude.com/docs/en/goal) (Anthropic official docs)
**Ingested:** 2026-05-16
**Requires:** Claude Code v2.1.139+
**Raw file:** [Keep Claude working toward a goal](../../raw/Keep%20Claude%20working%20toward%20a%20goal.md)

## Summary

`/goal` is a Claude Code command that sets a completion condition. After each turn, a small fast model (defaults to Haiku) evaluates whether the condition holds. If not, [[Claude Code]] starts another turn automatically. Goal clears when met. Session-scoped — one goal active at a time.

Use case: substantial work with a **verifiable end state** — module migration until tests pass, design doc until acceptance criteria hold, splitting files until size budget, working through issue backlog until queue empty.

## Architecture

`/goal` is a wrapper around a **session-scoped prompt-based Stop hook**. Each turn end → condition + conversation sent to evaluator → yes/no + reason returned. "No" feeds reason back as guidance. "Yes" clears the goal.

The evaluator **does not call tools**. Only judges what Claude has surfaced in the conversation. Write conditions Claude's own output can demonstrate.

## Comparison to Other Autonomous Workflows

See [[Autonomous Agent Workflows]] for full breakdown. Quick table:

| Approach | Next turn starts when | Stops when |
| --- | --- | --- |
| `/goal` | Previous turn finishes | Model confirms condition met |
| `/loop` | Time interval elapses | User stops, or Claude decides done |
| Stop hook | Previous turn finishes | User script/prompt decides |

`/goal` and Stop hooks both fire after every turn. `/goal` is session-scoped shorthand; Stop hook is settings-file persistent across all sessions in scope. [Auto mode](https://code.claude.com/docs/en/auto-mode-config) approves tools within a turn but doesn't start new ones — complementary to `/goal`.

## Writing Effective Conditions

A condition that survives many turns has:

- **One measurable end state** — test result, build exit code, file count, empty queue
- **A stated check** — how Claude proves it, e.g. `npm test exits 0` or `git status is clean`
- **Constraints that matter** — what must not change, e.g. "no other test file modified"

Max 4000 chars. Bound runtime with clauses like `or stop after 20 turns`.

## Key Commands

```text
/goal all tests in test/auth pass and lint is clean   # set
/goal                                                  # check status
/goal clear                                            # cancel (aliases: stop, off, reset, none, cancel)
```

Non-interactive:
```shellscript
claude -p "/goal CHANGELOG.md has an entry for every PR merged this week"
```

`--resume`/`--continue` restores active goals but resets turn count/timer/token baseline.

## Requirements & Gotchas

- Workspace must have trust dialog accepted (hooks system requirement)
- Unavailable if `disableAllHooks` set at any settings level
- Unavailable if `allowManagedHooksOnly` set in managed settings
- Evaluator tokens billed on small fast model — typically negligible vs main-turn spend

## Connections

- [[Claude Code]] — the harness that hosts `/goal`
- [[Autonomous Agent Workflows]] — `/goal` vs `/loop` vs Stop hooks vs auto mode
- [[Coding Agent Architecture]] — `/goal` extends the loop component of Raschka's 6-component framework
- [[Agentic AI]] — `/goal` is a concrete primitive for the agentic AI trend
- [[entities/anthropic]] — Anthropic ships `/goal` as a Claude Code feature

## Open Questions / Tensions

- Evaluator can only see what's surfaced in conversation — what if Claude runs work that doesn't echo full output? Goal may stall or false-pass.
- Sycophancy risk: evaluator is just another LLM. Does it succumb to the same "yes-bias" patterns documented in [[sycophancy]]?
- Token cost compounds across long-running goals — claimed "negligible" but unverified for multi-hour goals
- Resume resets token baseline but conditions can re-trigger expensive work — no built-in idempotency
