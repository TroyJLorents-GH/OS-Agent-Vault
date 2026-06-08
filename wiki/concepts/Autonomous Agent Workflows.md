---
title: "Autonomous Agent Workflows"
type: concept
created: 2026-05-16
updated: 2026-05-16
sources: ["S — Keep Claude Working Toward a Goal"]
tags: [agents, claude-code, technique, y2026]
---

# Autonomous Agent Workflows

Patterns for keeping a coding agent running across turns without per-step prompting. The question for each pattern: **what starts the next turn, and what stops the loop?**

## The Four Primitives (Claude Code reference)

| Approach | Next turn starts when | Stops when | Scope |
| --- | --- | --- | --- |
| `/goal` | Previous turn finishes | Evaluator model confirms condition | Session |
| `/loop` | Time interval elapses | User stops or Claude decides done | Session |
| Stop hook | Previous turn finishes | User script or prompt decides | Settings file |
| Auto mode | (per-tool, within a turn) | Claude judges work done | Setting |

`/goal` and a Stop hook are mechanically the same — `/goal` is a session-scoped shorthand for a prompt-based Stop hook. Auto mode is orthogonal: it removes per-tool prompts within a turn, while `/goal` removes per-turn prompts. Stack them together for fully unattended runs.

## Evaluator-Loop Pattern

`/goal` introduces the **evaluator-loop pattern**: a separate small fast model judges whether the work is done at each turn boundary, independent of the model doing the work. Why this matters:

- **Fresh perspective** — the doing model can convince itself it's done; an outside evaluator is harder to fool
- **Cheap** — runs on Haiku-class models; tokens negligible vs main-turn spend
- **Conversation-only** — evaluator cannot call tools; only judges what's been surfaced. Forces the worker to **demonstrate** completion in the transcript.

## Effective Conditions

A condition that survives many turns:
- One measurable end state (test result, exit code, file count, empty queue)
- A stated check ("npm test exits 0", "git status clean")
- Constraints that must not change ("no other test file modified")
- A runtime bound clause ("or stop after 20 turns")

## Scheduling vs Persistence

The four primitives above keep the **current session** running. Independent of session, scheduling primitives exist for nightly/morning workloads: cloud routines and desktop scheduled tasks. Different problem — different tools.

## Connections

- [[Claude Code]] — the harness exposing these primitives
- [[Coding Agent Architecture]] — extends Raschka's 6-component framework (loop control)
- [[Agentic AI]] — these primitives are the building blocks of the agentic shift
- [[Prompt Caching]] — long-running goals amplify the value of cache reuse
- [[sources/S — Keep Claude Working Toward a Goal]] — source

## Open Questions

- Does the evaluator model inherit [[sycophancy]] patterns from training? Empirical test would be: run `/goal` with a deliberately false-confident "done" message in the transcript and see if Haiku rubber-stamps it.
- When evaluator-judged completion is wrong, how do you tell? (No ground truth in conversation alone.)
- Should evaluator be a *different family* of model than the worker, to reduce shared blind spots?
