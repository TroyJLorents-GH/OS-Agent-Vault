---
title: AI Memory Systems
type: concept
created: 2026-04-10
updated: 2026-04-10
sources: ["S — MemPalace", "S — Components of A Coding Agent"]
tags: [agents, llm, technique, "2026"]
---

# AI Memory Systems

## The Problem

AI conversations evaporate. Every session starts from zero. Six months of daily AI use generates roughly 19.5 million tokens — all gone when the session ends. Users lose accumulated context, preferences, project knowledge, and relationship continuity.

This is not just an inconvenience — it is an architectural limitation that caps the usefulness of AI assistants. Without memory, every interaction is a cold start.

## Two Approaches to AI Memory

### 1. Store-and-Retrieve

**Example:** [[MemPalace]]

Keep everything verbatim. Use structure (hierarchical palace) and search (vector similarity, knowledge graph) to find relevant memories on demand.

- **Pro:** Nothing is lost. The full record exists.
- **Con:** Retrieval quality depends on structure and search. Raw storage grows without bound.
- **Benchmark evidence:** MemPalace achieves 96.6% R@5 on LongMemEval with raw verbatim storage (Source: [[S — MemPalace]])

### 2. Compile-and-Maintain

**Example:** This vault (OS Agent Vault / LLM Wiki pattern)

An LLM incrementally builds structured, cross-referenced knowledge pages. Each ingestion creates summaries, entity pages, concept pages, and connections.

- **Pro:** Pre-synthesized, navigable, cross-referenced. Knowledge compounds over time.
- **Con:** Lossy — the LLM decides what matters. Original nuance may be lost in summarization.

These two approaches are **complementary**, not competing. A complete memory architecture might use verbatim storage for recall fidelity and compiled knowledge for navigability and synthesis.

## Coding Agent Memory

From [[Sebastian Raschka]]'s analysis of coding agent architecture (Source: [[S — Components of A Coding Agent]]):

Coding agents need two distinct memory layers:

1. **Working memory** — a distilled state summary that fits in the context window. Updated as the task progresses. Analogous to MemPalace's L0 + L1 layers.
2. **Full transcript** — the durable record of everything that happened. Used for reconstruction after context compaction. Analogous to MemPalace's L3 drawers.

The distinction matters because context windows are finite. Working memory must be compact enough to leave room for code, tool outputs, and reasoning. The full transcript is a fallback, not a primary context source.

## The MemPalace Stack

[[MemPalace]] implements a 4-layer memory architecture:

| Layer | Purpose | Size | Load Strategy |
|-------|---------|------|--------------|
| L0 — Identity | Who the user is | ~50 tokens | Always loaded |
| L1 — Critical Facts | Essential facts (AAAK format) | ~120 tokens | Always loaded |
| L2 — Room Recall | Topic-specific retrieval | Variable | On demand |
| L3 — Deep Search | Full search across all drawers | Variable | On demand |

Cold start cost: ~170 tokens (L0 + L1 only). This is a design insight — the system wakes up knowing *who you are* and *what matters most*, then loads deeper context only when needed.

## Key Insight: Raw Beats Compressed

MemPalace's benchmarks reveal a striking result: raw verbatim storage (96.6% R@5) significantly outperforms their AAAK compressed format (84.2% R@5) — a 12.4 percentage point gap.

This suggests that for **retrieval tasks**, keeping the original text is better than compressing it, even when compression saves tokens. The information lost during compression hurts retrieval more than the token savings help. This has implications for any system that summarizes or compresses memories before storing them.

The open question is whether this applies universally or only to current embedding/retrieval technology. Better compression schemes or better retrieval over compressed text could change this calculus.

## Connections

- [[Retrieval-Augmented Generation]] — AI memory systems are a form of RAG where the retrieval corpus is the user's own conversation history
- [[Coding Agent Architecture]] — memory is one of the six core components of a coding agent harness
- [[MemPalace]] — the highest-scoring open-source implementation
- [[S — MemPalace]] — full source analysis
- [[S — Components of A Coding Agent]] — memory layers in coding agents
- [[AI emotional support]] — memory persistence is critical for emotional continuity with AI
- [[cognitive-atrophy]] — if AI memory enables deeper reliance on AI, the atrophy question becomes more acute
