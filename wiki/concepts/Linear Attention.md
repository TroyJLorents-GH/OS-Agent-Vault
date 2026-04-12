---
title: Linear Attention
type: concept
created: 2026-04-10
updated: 2026-04-10
sources: ["S — The Big LLM Architecture Comparison"]
tags: [architecture, llm, inference, compute, "2025", "2026"]
---

# Linear Attention

Attention variants that reduce the quadratic O(n²) cost of standard attention to linear O(n) by avoiding explicit computation of the n×n attention matrix. A long-sought efficiency goal that experienced a **revival in 2025 — followed by a partial retreat**.

## The Promise

Standard attention computes QK^T, producing an n×n matrix — quadratic in sequence length. Linear attention approximates this via kernel functions or state-space updates, scaling linearly. This matters enormously for long-context scenarios (128k+ tokens).

## The 2025 Revival

Three major models adopted linear attention variants:

1. **MiniMax-M1** (June 2025) — "lightning attention" (456B, 46B active)
2. **Qwen3-Next** (Sept 2025) — [[Gated DeltaNet]] + Gated Attention hybrid (3:1 ratio)
3. **DeepSeek V3.2** (Dec 2025) — sparse attention variant

## The Retreat

**MiniMax-M2 dropped linear attention**, returning to full quadratic attention. The team stated:

> "Linear attention is tricky in production LLMs. It seemed to work fine with regular prompts, but it had poor accuracy in reasoning and multi-turn tasks."

This is significant — reasoning and multi-turn are precisely the capabilities driving value in modern AI (agentic applications, coding, analysis). If linear attention degrades exactly where it matters most, its efficiency gains may not be worth the tradeoff.

## The Counter-Revival

**Kimi Linear** (Oct 2025) refined the approach with Kimi Delta Attention (channel-wise gating instead of scalar gating) and restored competitive performance. It's as fast as Gated DeltaNet while matching MLA on long-context and reasoning benchmarks.

The verdict: linear attention **can** work, but requires careful engineering. The naive approaches degrade quality; the refined approaches (Kimi Delta Attention, Gated DeltaNet) are promising but unproven at the largest scale (Kimi Linear is 48B, 20x smaller than Kimi K2).

## Gated DeltaNet

The leading linear attention variant, used by Qwen3-Next and Kimi Linear. Conceptually similar to Mamba-2 — both maintain a running hidden state with gated updates instead of computing full attention. The key difference: DeltaNet uses a "delta rule" fast-weight update; Mamba uses a learned state-space filter.

## Connections

- Hybrid approach with full attention in [[S — The Big LLM Architecture Comparison]] — 3:1 ratio of linear:full is the current standard
- Mamba-Transformer hybrids (Nemotron 3) are a related approach to the same efficiency problem
- The retreat-and-return pattern is a lesson in AI development: first attempts often fail on edge cases, refinements succeed
- [[Sliding Window Attention]] is the "safe" efficiency technique; linear attention is the "ambitious" one

(Source: [[S — The Big LLM Architecture Comparison]])
