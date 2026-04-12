---
title: "S — Components of A Coding Agent"
type: source
created: 2026-04-10
updated: 2026-04-10
sources: ["Components of A Coding Agent.md"]
tags: [llm, agents, code-gen, architecture, technique, "2026"]
---

# S — Components of A Coding Agent

## Source Metadata

- **Author:** [[Sebastian Raschka]]
- **Published:** 2026-04-04
- **URL:** [Components of a Coding Agent](https://magazine.sebastianraschka.com/p/components-of-a-coding-agent)
- **Raw:** [Components of A Coding Agent.md](../../raw/Components%20of%20A%20Coding%20Agent.md)

## Core Thesis

The agent harness — the surrounding system that wraps an LLM — matters as much as the model itself for coding performance. **"A lot of apparent 'model quality' is really context quality."** Systems like Claude Code and Codex feel dramatically more capable than the same models in a plain chat interface because the harness handles repo context, tool management, prompt caching, memory, and context compaction.

## Key Definitions

- **LLM:** The raw next-token model — the engine.
- **Reasoning Model:** An LLM trained/prompted to spend more inference-time compute on intermediate reasoning, verification, or search. A beefed-up engine — more powerful but more expensive.
- **Agent:** A control loop around the model. Given a goal, the agent decides what to inspect, which tools to call, how to update state, and when to stop.
- **Agent Harness:** The software scaffold that manages context, tool use, prompts, state, and control flow around an agent.
- **Coding Harness:** A task-specific agent harness for software engineering — manages code context, tools, execution, and iterative feedback. Claude Code and Codex are coding harnesses.

## The 6 Components of a Coding Agent

### 1. Live Repo Context

A workspace summary gathered upfront before the model does any work. Includes git branch, status, recent commits, project docs (README, AGENTS.md), and repo layout. The agent collects these "stable facts" so it is not starting from zero on every prompt. This is critical because instructions like "fix the tests" are not self-contained — the agent needs project context to act correctly.

### 2. Prompt Shape and Cache Reuse

The prompt is split into a **stable prefix** (general instructions, tool descriptions, workspace summary) and **changing state** (short-term memory, recent transcript, latest user request). Smart runtimes reuse the stable prefix across turns instead of rebuilding everything from scratch, saving compute and latency. This is a key reason why Claude Code and Codex feel faster than plain chat. See [[Prompt Caching]] for more detail.

### 3. Tool Access and Use

The harness provides a pre-defined list of named tools with clear inputs and boundaries (list files, read file, search, run shell command, write file, etc.). When the model emits a structured action, the harness validates it through programmatic checks:
- Is this a known tool?
- Are the arguments valid?
- Does this need user approval?
- Is the requested path inside the workspace?

Only after checks pass does anything execute. **Less freedom = more reliability.** The harness constrains the model but improves usability. Approval gating and path checking add safety without eliminating capability.

### 4. Minimizing Context Bloat

One of the underrated, boring parts of good coding-agent design. Multi-turn coding sessions generate massive amounts of context from repeated file reads, tool outputs, and logs. The harness uses at least two compaction strategies:
- **Clipping:** Shortening long document snippets, tool outputs, memory notes, and transcript entries so no single piece dominates the prompt budget.
- **Transcript reduction/summarization:** Compressing the full session history into a smaller promptable summary. Recent events are kept richer (more likely to matter); older events are compressed more aggressively. Older file reads are deduplicated.

### 5. Structured Session Memory

Two distinct layers of state:
- **Working memory:** A small, distilled, explicitly maintained summary of what matters across turns — current task, important files, recent notes. Used for task continuity.
- **Full transcript:** The complete durable record of all user requests, tool outputs, and LLM responses. Stored as JSON on disk. Resumable if the agent is closed.

The compact transcript (for prompt reconstruction) and working memory (for task continuity) have different jobs. See [[Coding Agent Architecture]] for the conceptual framework.

### 6. Delegation with Bounded Subagents

The agent can spawn subtasks with inherited context but tighter boundaries. Subagents are useful for parallelizing side questions (which file defines a symbol, what a config says, why a test fails) without forcing the main loop to carry every thread.

The design challenge is **binding** the subagent: it inherits enough context to be useful but is constrained (e.g., read-only access, restricted recursion depth). Claude Code has supported subagents for a long time; Codex added them more recently. Codex subagents inherit the main agent's sandbox and approval setup rather than forcing read-only mode — the boundary is more about task scoping, context, and depth.

## Key Insight

> "Since, in my view, the vanilla versions of LLMs nowadays have very similar capabilities (e.g., the vanilla versions of GPT-5.4, Opus 4.6, and GLM-5 or so), the harness can often be the distinguishing factor that makes one LLM work better than another."

> "This is speculative, but I suspect that if we dropped one of the latest, most capable open-weight LLMs, such as GLM-5, into a similar harness, it could likely perform on par with GPT-5.4 in Codex or Claude Opus 4.6 in Claude Code."

This supports the thesis that **architecture convergence** (see [[S — The Big LLM Architecture Comparison]]) extends into the product layer: if models are converging, harness quality becomes the primary differentiator.

## Comparison to OpenClaw

OpenClaw is a local, general agent platform that can also code — not a specialized terminal coding assistant. Overlaps with coding harnesses include prompt/instruction files (AGENTS.md, SOUL.md, TOOLS.md), JSONL session files with transcript compaction, and subagent spawning. But OpenClaw is optimized for running many long-lived local agents across chats, channels, and workspaces, with coding as one workload among several. Coding agents like Claude Code and Codex are optimized for a person working in a repository asking a coding assistant to inspect, edit, and execute.

## Notable Quotes

- "A lot of apparent 'model quality' is really context quality."
- "The harness can often be the distinguishing factor that makes one LLM work better than another."
- "If we dropped one of the latest open-weight LLMs like GLM-5 into a similar harness, it could likely perform on par with GPT-5.4 in Codex or Claude Opus 4.6 in Claude Code."
- "This is one of the underrated, boring parts of good coding-agent design."
- "Less freedom [for the model] also improves the usability."

## Connections

- [[Sebastian Raschka]] — Author; also wrote [[S — The Big LLM Architecture Comparison]]
- [[Coding Agent Architecture]] — Concept page synthesizing the 6-component framework
- [[Prompt Caching]] — Concept page on the stable-prefix caching technique
- [[Transformer Architecture]] — The foundational model architecture these harnesses wrap
- [[Mixture of Experts]] — Architectural trend discussed in Raschka's other survey
- [[Anthropic]] — Developer of Claude Code, one of the primary examples in this article
- [[claude]] — Claude models used in Claude Code

## Open Questions

- How much harness-specific post-training actually matters? Raschka notes OpenAI maintains separate Codex variants — is this a significant factor or marginal?
- Could an open-weight model in an equivalent harness truly match proprietary systems, or do API-level optimizations (custom caching infrastructure, specialized fine-tuning data) create a moat?
- How do the 6 components interact with multi-agent orchestration at scale (e.g., teams of coding agents working on different parts of a codebase)?
- What is the performance ceiling for context compaction? At what point does aggressive compression lose critical information?
