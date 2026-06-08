---
title: "S — Harness, Scaffold, and the AI Agent Terms Worth Getting Right"
type: source
created: 2026-06-03
updated: 2026-06-03
sources: ["Harness, Scaffold, and the AI Agent Terms Worth Getting Right"]
tags: [agents, llm, technique, rl, training, reference, y2026]
---

# S — Harness, Scaffold, and the AI Agent Terms Worth Getting Right

**Authors:** Sergio Paniego, Aritra Roy Gosthipaty · **Publisher:** Hugging Face Blog · **Published:** 2026-05-24 · **Type:** Glossary / mental model
[Source article](../../raw/Harness,%20Scaffold,%20and%20the%20AI%20Agent%20Terms%20Worth%20Getting%20Right.md) · Original URL: huggingface.co/blog/agent-glossary

## Why it exists

Agent vocabulary is evolving faster than shared understanding. After ICLR 2026, co-author @ariG23498 asked why no one could converge on what "harness" and "scaffold" mean. This glossary grounds the terms that keep getting mixed up. It does not claim canonical definitions — different frameworks use the same word differently — it offers a **practical mental model**. Primary source for [[Agent Harness and Scaffolding]] and [[Context Engineering]].

## The core decomposition

**Agent = Model + Harness.** "If you're not the model, you're the harness."

- **Model** — the LLM. Text in, text out. No memory between calls, no loop. Can *express* intent to call a tool but can't execute it. Answers one prompt and stops.
- **Scaffolding** — the behavior-defining layer: system prompt, tool descriptions, response parsing, what's remembered across steps. Shapes how the model *sees* the world and acts in it.
- **Harness** — the execution layer: calls the model, handles tool calls, decides when to stop. What makes the agent *run*.

The key nuance: **harness vs scaffold** is where most confusion lives. Products (Claude Code, Codex, Antigravity CLI) loosely call *everything that isn't the model* "the harness." Claude Code's own docs: *"Claude Code serves as the agentic harness around Claude."* The finer scaffold/harness split matters most when you reason about them separately — e.g. in a training pipeline. "Scaffold" also gets used broadly for any supporting infra: hooks, runtime config, even directory structure.

**Coupling varies:** Claude Code and Codex are tightly bound to their provider's models. Antigravity CLI and Hermes Agent are model-agnostic — plug in any model.

## Inference-time terms

- **Harness engineering** — designing the execution layer well: when to stop, how errors are handled, what guardrails keep the agent on track. (Addy Osmani; OpenAI's Codex account.)
- **Eval harness** — same pattern at evaluation time: run fixed scenarios at a checkpoint, record metrics, don't update weights. (e.g. EleutherAI lm-evaluation-harness.)
- **Orchestrator** — a higher-level controller coordinating *multiple* agents as units, each running its own harness. A harness drives one model's loop; an orchestrator manages agents.
- **Agent** — RL origin: a function mapping observation → action, looping with an environment. In LLM terms: a model plus everything that lets it *act*, not just respond.
- **Context Engineering** — designing what enters the context window at each step (system prompt, tool descriptions, history, retrieved knowledge); the harness actively manages this throughout the run. See [[Context Engineering]].
  - **Short-term memory** — what stays in-context during a single run.
  - **Long-term memory** — persists across sessions, stored externally, retrieved + injected on demand.
- **Policy** — the behavior an agent follows (probability of each action given a situation). Partly learned in weights, partly determined by scaffold + harness. **A policy is not an agent** — wrap a checkpoint in scaffold + harness and deploy, and its behavior *is* the policy.
- **Tool Use** — how agents reach outside themselves (APIs, code interpreters, DBs, web, filesystem). Model emits structured intent; harness routes it; result feeds back into context.
- **Skills** — reusable, structured packages of knowledge for multi-step tasks. A *tool* is an action ("run this command"); a *skill* bundles everything to accomplish a goal ("investigate this bug, hypothesize, write a fix"). Portable, loaded on demand.
- **Sub-agents** — an agent called by another to handle a subtask; has its own model + scaffold, reasons independently, returns a result. What separates it from a tool (function call) or skill (packaged knowledge): a sub-agent can itself reason, use tools, and call further sub-agents. The caller is sometimes the **orchestrator**.

## Training-specific terms (the RL pipeline)

Every RL training system for LLMs is the same loop: **environment → trainer → reward → updated policy.**

- **RL Environment** — a stateful object: takes an action (usually a tool call), updates state, returns an observation. (`touch foo.txt` → file created → new file listing.)
- **Trainer** — runs many agent episodes, scores results, updates the inner model's weights. (TRL's GRPOTrainer.)
- **Rollout** — one full agent run start to finish (also *trajectory* / *trace*). The raw data RL learns from.
- **Reward** — the score telling the algorithm if the model is improving. *Verifiable* (tests pass) vs *learned* (human prefs, LLM-as-judge); *sparse* (one end-of-episode score) vs *dense* (per-step).
  - **Rubrics** — break reward into explicit weighted dimensions instead of one number (OpenEnv, Verifiers: `WeightedSum`, `Sequential`, `Gate`).

## Why it matters for this wiki

This is the **vocabulary backbone** for everything agent-related already filed: [[Coding Agent Architecture]], [[Agentic AI]], [[Autonomous Agent Workflows]], [[Claude Code]]. It cleanly separates three things the wiki had been blurring: **model ≠ harness ≠ product**. Two products on the same model feel different because their harnesses make different choices; swap a better model into the same harness and the experience also changes.

Community thread also flagged finer terms: **Agent CLI** (the command-line app launching/managing instances), **Agent Definition** (a Markdown/JSON blueprint — "class"), **Agent Instance** (a running process — "object"), and where **MCP** fits (a standardization protocol making the Tool-Use → Harness connection interoperable across vendors).

## Connections

- [[Agent Harness and Scaffolding]] — primary concept page distilled from this source
- [[Context Engineering]] — the context-window discipline defined here
- [[Coding Agent Architecture]] — Raschka's 6-component harness, now grounded in shared vocabulary
- [[Agentic AI]] — "Agent = Model + Harness" sharpens the definition
- [[Claude Code]] — cited example; "agentic harness around Claude"
- [[Autonomous Agent Workflows]] — stop conditions are harness-engineering decisions
- [[Mixture of Experts]] / [[S — The Big LLM Architecture Comparison]] — model convergence is why the harness is the differentiator

## Open questions / tensions

- **No canonical definitions yet** — the post explicitly declines to enforce one vocabulary. Useful but unstable; expect drift.
- **"Agent" is overloaded** — a commenter notes the popular meaning shifts yearly (autonomy-centric last year, model+harness this year). Prefer specific terms (CLI / Definition / Instance).
- Where exactly **skills** end and **sub-agents** begin is framework-dependent — the line moves.
