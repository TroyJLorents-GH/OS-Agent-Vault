---
title: "Context Engineering"
type: concept
created: 2026-06-03
updated: 2026-06-03
sources: ["Harness, Scaffold, and the AI Agent Terms Worth Getting Right", "S — Components of A Coding Agent"]
tags: [agents, llm, technique, inference, training, "2026"]
---

# Context Engineering

**Designing what goes into the agent's context window at each step** — system prompt, tool descriptions, conversation history, retrieved knowledge. Not a one-time decision: as the agent runs, previous turns shape future calls, and the harness actively manages this throughout the run (Source: [[S — Harness Scaffold and Agent Terms]]).

The slogan from [[Coding Agent Architecture]] captures the stakes: **"A lot of apparent 'model quality' is really context quality."**

## Two layers of memory

- **Short-term memory** — what stays in the context window during a single run: conversation history, tool results, previous reasoning.
- **Long-term memory** — persists across sessions, stored externally, retrieved on demand, then injected back into context when relevant. This is the territory of [[AI Memory Systems]] (store-and-retrieve vs compile-and-maintain; see [[MemPalace]]).

## Training vs inference: same skill, different cost of failure

| | At training | At inference |
|---|-------------|--------------|
| What context shapes | What the model *learns* | What the model *does right now* |
| Cost of getting it wrong | Retrain — expensive, slow | It's just text: change a prompt, redeploy |

This asymmetry is why context engineering is treated as careful, deliberate design in training pipelines and as fast iteration at inference.

## In practice (the coding-agent instantiation)

[[Coding Agent Architecture]] is context engineering made concrete. Its hardest problem — **context bloat** — is a context-engineering problem, solved with:
- **Prompt shape + cache reuse** — stable prefix (instructions, tools, workspace) vs changing state (memory, transcript). See [[Prompt Caching]].
- **Clipping** — no single output dominates the budget.
- **Transcript compression** — recent events rich, older events compressed.
- **Deduplication** — drop repeated file reads.
- **Structured session memory** — working memory (distilled state) vs full transcript (durable record).

## Why it matters

As raw models converge, *what you feed them* — not which model — increasingly determines agent quality. Context engineering is the discipline that turns a capable model into a capable agent. It sits inside the [[Agent Harness and Scaffolding]] picture as the part of the harness that decides, every step, what the model gets to see.

## Connections

- [[Agent Harness and Scaffolding]] — context engineering is the harness's context-management job
- [[Coding Agent Architecture]] — the concrete, battle-tested instantiation
- [[Prompt Caching]] — stable-prefix technique
- [[AI Memory Systems]] — long-term memory approaches
- [[MemPalace]] — high-scoring long-term memory system
- [[S — Harness Scaffold and Agent Terms]] — source definition
- [[S — Components of A Coding Agent]] — the bloat-management toolkit
