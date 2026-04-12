---
title: "Coding Agent Architecture"
type: concept
created: 2026-04-10
updated: 2026-04-10
sources: ["S — Components of A Coding Agent"]
tags: [agents, code-gen, llm, architecture, technique, "2026"]
---

# Coding Agent Architecture

## Definition

A **coding agent** is an LLM wrapped in an agent harness optimized for software engineering tasks. It is not just a model that can write code — it is a system that navigates repositories, manages context, uses tools, maintains memory, and iterates on feedback loops to produce working software changes.

(Source: [[S — Components of A Coding Agent]])

## The Hierarchy

The relationship between components follows a layered model:

1. **LLM** — The raw next-token engine. Can generate code but lacks environmental awareness.
2. **Reasoning Model** — A beefed-up engine. Still an LLM but trained to spend more inference-time compute on intermediate reasoning, verification, and search. More powerful but more expensive.
3. **Agent Harness** — The software scaffold that helps us use the model. Manages context, tools, prompts, state, and control flow. This is where most of the practical capability difference comes from.

The analogy: the LLM is the engine, the reasoning model is a beefed-up engine, and the agent harness is the vehicle that lets us drive it. The harness turns raw model capability into usable software engineering performance.

## The 6 Components

[[Sebastian Raschka]] identifies six core building blocks of a coding agent:

1. **Live Repo Context** — Workspace summary gathered upfront (git branch, status, project docs). The agent doesn't start from zero.
2. **Prompt Shape and Cache Reuse** — Split prompt into stable prefix (instructions, tools, workspace) and changing state (memory, transcript, request). Stable prefix is cached. See [[Prompt Caching]].
3. **Tool Access and Use** — Pre-defined named tools with validation, approval gating, and path checking. Less freedom = more reliability.
4. **Minimizing Context Bloat** — Clipping long outputs, transcript compression, deduplication of older file reads. The underrated key to agent quality.
5. **Structured Session Memory** — Two layers: working memory (distilled state for task continuity) and full transcript (durable record of everything).
6. **Delegation with Bounded Subagents** — Spawn subtasks with inherited context but tighter boundaries (read-only, depth limits).

## The Harness Is the Differentiator

A central insight: vanilla LLMs today have very similar capabilities. GPT-5.4, Claude Opus 4.6, GLM-5 — the raw models are converging. The harness is often the distinguishing factor that makes one system work better than another. This aligns with the architectural convergence documented in [[S — The Big LLM Architecture Comparison]].

> "A lot of apparent 'model quality' is really context quality." (Source: [[S — Components of A Coding Agent]])

This means that improving coding agent performance is increasingly about better context management, smarter tool design, and more sophisticated memory — not just training bigger models.

## Two Memory Layers

Coding agents maintain at least two layers of state:

- **Working memory:** A small, explicitly maintained summary of what currently matters — current task, important files, recent notes. Modified and compacted over time, not just appended to. Used for task continuity across turns.
- **Full transcript:** The complete record of all user requests, tool outputs, and LLM responses. Stored as JSON on disk. Resumable across sessions.

These serve different purposes: working memory keeps the agent oriented on its task; the transcript provides a durable record and enables session resumption.

## Context Management as the Underrated Key

Context bloat is arguably the biggest practical challenge in coding agents. Multi-turn coding sessions generate massive context from repeated file reads, tool outputs, and logs. Effective harnesses use:

- **Clipping** — preventing any single output from dominating the prompt budget
- **Transcript compression** — keeping recent events rich, compressing older events aggressively
- **Deduplication** — removing repeated file reads from the context

This is "boring" infrastructure work, but it directly determines how capable the agent feels to the user.

## Connections

- [[S — Components of A Coding Agent]] — The primary source for this framework
- [[Sebastian Raschka]] — Author of the source article and Mini Coding Agent reference implementation
- [[Prompt Caching]] — The stable-prefix caching technique (component 2)
- [[Transformer Architecture]] — The foundational model architecture these harnesses wrap
- [[Mixture of Experts]] — Dominant model architecture trend; harness quality matters more as models converge
- [[S — The Big LLM Architecture Comparison]] — Documents the model convergence that makes harness quality the differentiator
