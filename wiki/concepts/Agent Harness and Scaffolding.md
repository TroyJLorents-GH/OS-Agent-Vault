---
title: "Agent Harness and Scaffolding"
type: concept
created: 2026-06-03
updated: 2026-06-03
sources: ["Harness, Scaffold, and the AI Agent Terms Worth Getting Right", "S — Components of A Coding Agent"]
tags: [agents, llm, technique, rl, reference, "2026"]
---

# Agent Harness and Scaffolding

The shared vocabulary for talking about agents precisely. After ICLR 2026, practitioners couldn't converge on what "harness" and "scaffold" mean; this is the practical mental model that grounds them (Source: [[S — Harness Scaffold and Agent Terms]]). No definitions are fully canonical — frameworks differ — but this separation makes discussion tractable.

## The one equation

> **Agent = Model + Harness.** "If you're not the model, you're the harness."

Three things people constantly blur — **model ≠ harness ≠ product**:

| Layer | What it is | Role |
|-------|-----------|------|
| **Model** | The LLM. Text in → text out. No memory, no loop. Can express tool intent, can't execute. | Raw capability |
| **Scaffolding** | System prompt, tool descriptions, response parsing, cross-step memory. | What the model *works from* — how it sees the world |
| **Harness** | Calls the model, handles tool calls, decides when to stop. | What makes the agent *run* |

Two products on the same model feel different because their **harnesses make different choices**. Swap a better model into the same harness — the experience also changes. The model, the harness, and the product are three different things.

### Harness vs scaffold (the confusing part)

Loosely, products call *everything that isn't the model* "the harness." Claude Code's docs: *"Claude Code serves as the agentic harness around Claude."* The finer split — scaffold = what the model works from; harness = the execution loop — matters most when you reason about them **separately**, as in a training pipeline. "Scaffold" is also used broadly for supporting infra: hooks, runtime config, even directory structure.

## Key terms (inference side)

- **Harness engineering** — designing the execution layer well: stop conditions, error handling, guardrails. Applies at training *and* inference. (Closely tied to [[Autonomous Agent Workflows]] — a `/goal` completion condition is a harness-engineering decision.)
- **Eval harness** — runs fixed scenarios at a checkpoint, records metrics, doesn't update weights.
- **Orchestrator** — coordinates *multiple* agents as units, each running its own harness. A harness drives one model's loop; an orchestrator manages agents.
- **Context Engineering** — designing what enters the context window each step. Big enough for its own page: [[Context Engineering]].
- **Policy** — the behavior an agent follows (action probabilities given a situation); partly in weights, partly from scaffold + harness. A policy is *not* an agent — deploy a checkpoint in scaffold + harness and its behavior *is* the policy.
- **Tool Use** — structured intent emitted by the model, routed by the harness, result fed back into context.
- **Skills** — portable, on-demand packages of knowledge for multi-step tasks. Tool = an action; skill = everything needed to accomplish a goal. (Matches the enterprise "AI executes skills, not monolithic workflows" framing in [[AI Workforce]].)
- **Sub-agents** — an agent called by another: own model + scaffold, reasons independently, returns a result. Unlike a tool (function) or skill (knowledge), a sub-agent can reason, use tools, and call further sub-agents.

## Key terms (training side — the RL loop)

**Environment → Trainer → Reward → updated policy.**

- **RL Environment** — stateful object: action in (usually a tool call) → state update → observation out.
- **Trainer** — runs many episodes, scores them, updates the inner model's weights (e.g. TRL GRPOTrainer).
- **Rollout** — one full agent run start-to-finish (a.k.a. trajectory / trace); the raw data RL learns from.
- **Reward** — verifiable (tests pass) vs learned (human prefs, LLM-as-judge); sparse (end-of-episode) vs dense (per-step). **Rubrics** split reward into weighted dimensions.

## Why it matters

As raw models converge (GPT-5.4, Claude Opus, GLM-5 — see [[S — The Big LLM Architecture Comparison]] and [[Mixture of Experts]]), **the harness is increasingly the differentiator.** This is the same insight as [[Coding Agent Architecture]] ("a lot of apparent model quality is really context quality"), now generalized beyond coding and given precise vocabulary.

## Related fine-grained terms (community)

- **Agent CLI** — the command-line app that launches/manages agent instances (Claude Code, Codex, Gemini CLI, Opencode).
- **Agent Definition** — a Markdown/JSON blueprint of behavior (a "class").
- **Agent Instance** — a running process from a definition (an "object").
- **MCP** — standardization protocol making the Tool-Use → Harness connection interoperable across vendors. See [[Agentic AI]] (MCP at 97M installs).

## Connections

- [[S — Harness Scaffold and Agent Terms]] — primary source
- [[Context Engineering]] — the context-window sub-discipline
- [[Coding Agent Architecture]] — the 6-component harness, a concrete instance
- [[Agentic AI]] — "Agent = Model + Harness" sharpens the definition
- [[Autonomous Agent Workflows]] — stop conditions as harness engineering
- [[Claude Code]] — canonical "agentic harness around Claude"
- [[AI Workforce]] — enterprise "skills not workflows" + orchestrator at scale
- [[AI Memory Systems]] — short-term vs long-term memory map onto store-and-retrieve approaches
