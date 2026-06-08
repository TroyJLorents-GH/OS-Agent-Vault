---
title: "Claude Code"
type: entity
created: 2026-05-16
updated: 2026-06-03
sources: ["S — Keep Claude Working Toward a Goal", "S — Best AI Tools 2026", "S — Components of A Coding Agent", "Harness, Scaffold, and the AI Agent Terms Worth Getting Right"]
tags: [product, agents, code-gen, claude-code, anthropic, y2026]
---

# Claude Code

Anthropic's terminal-based coding agent. Distinct from the [[entities/claude]] chat product. Available as CLI, desktop app (Mac/Windows), web app (claude.ai/code), and IDE extensions (VS Code, JetBrains).

## Position

- **80.8% SWE-bench** — top scoring coding agent in 2026
- **46% "most loved"** among devs per Stack Overflow 2026 survey
- **$2.5B/yr** revenue for [[entities/anthropic]] — zero to #1 in 8 months
- Considered the validation case for [[Coding Agent Architecture]] — proof that harness matters as much as model (Source: [[sources/S — Components of A Coding Agent]])
- The canonical example of an **agentic harness**: its own docs state *"Claude Code serves as the agentic harness around Claude"* — cited in the field's agent glossary as the reference for **Agent = Model + Harness**. Tightly coupled to Anthropic's models (vs model-agnostic CLIs like Antigravity / Hermes). See [[Agent Harness and Scaffolding]].

## Notable Features

- **`/goal`** — session-scoped completion condition with evaluator loop (v2.1.139+). See [[sources/S — Keep Claude Working Toward a Goal]] and [[Autonomous Agent Workflows]].
- **`/loop`** — re-run a prompt on a time interval
- **Stop hooks** — script or prompt fired after every turn; `/goal` is a wrapper around a session-scoped prompt-based Stop hook
- **Auto mode** — approves tool calls automatically within a turn
- **Fast mode** — Opus with faster output, toggled via `/fast`
- **Remote Control** — operate sessions remotely

## Models

Default model: Claude (Opus/Sonnet/Haiku). Opus 4.6 and 4.7 support Fast mode. Small-fast-model (Haiku by default) handles evaluator workloads for `/goal`.

## Connections

- [[entities/anthropic]] — vendor
- [[entities/claude]] — model family powering it
- [[Coding Agent Architecture]] — 6-component harness framework
- [[Agent Harness and Scaffolding]] — "agentic harness around Claude"; model vs scaffold vs harness
- [[Autonomous Agent Workflows]] — `/goal`, `/loop`, Stop hooks, auto mode
- [[Prompt Caching]] — stable prefix / changing state for cache reuse
- [[AI Coding Tools]] — competitive landscape (Cursor, Copilot, Codex)
- [[entities/Cursor]] — main competitor on IDE-native side
