---
title: "Prompt Caching"
type: concept
created: 2026-04-10
updated: 2026-04-10
sources: ["S — Components of A Coding Agent"]
tags: [technique, inference, llm, agents, "2026"]
---

# Prompt Caching

## Overview

Prompt caching is an optimization technique used by coding agents and LLM runtimes to avoid reprocessing the same prompt content on every turn of a multi-turn session. The core idea is to split the prompt into two parts:

1. **Stable prefix** — Content that rarely changes between turns: system instructions, tool descriptions, workspace summary, and project documentation.
2. **Changing state** — Content that updates on every turn: short-term memory, recent transcript history, and the latest user request.

The stable prefix is cached and reused across turns. Only the changing state needs to be processed fresh on each interaction.

(Source: [[S — Components of A Coding Agent]])

## Why It Matters

In a coding session, the agent's rules, tool definitions, and workspace layout are essentially constant. Without caching, the runtime would rebuild and reprocess the entire prompt — potentially tens of thousands of tokens — on every single turn. This is wasteful in both compute and latency.

By caching the stable prefix, smart runtimes:

- **Reduce latency** — The model does not re-encode the same instructions and tool descriptions every turn
- **Save compute costs** — Cached tokens are cheaper to process than fresh tokens
- **Enable longer sessions** — The saved token budget can be allocated to richer transcript history or working memory

This is one reason why Claude Code and Codex feel faster and more responsive than using the same models through a plain chat interface. The chat interface rebuilds context from scratch; the coding harness reuses what hasn't changed.

## Relation to Coding Agent Design

Prompt caching is Component 2 ("Prompt Shape and Cache Reuse") in [[Sebastian Raschka]]'s framework of [[Coding Agent Architecture]]. It sits between Live Repo Context (Component 1, which gathers the facts that go into the stable prefix) and Tool Access (Component 3, whose tool descriptions are part of the cached prefix).

The effectiveness of prompt caching depends on good prompt design — the more stable content can be pushed into the prefix, the more reuse the runtime achieves.

## Connections

- [[Coding Agent Architecture]] — The broader framework; prompt caching is one of six components
- [[S — Components of A Coding Agent]] — Primary source describing this technique
- [[Sebastian Raschka]] — Author of the source article
