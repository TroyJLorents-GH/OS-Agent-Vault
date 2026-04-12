---
title: Sliding Window Attention
type: concept
created: 2026-04-10
updated: 2026-04-10
sources: ["S — The Big LLM Architecture Comparison"]
tags: [architecture, llm, inference, compute, "2025"]
---

# Sliding Window Attention

An efficiency technique that restricts each token's attention to a local window of nearby tokens instead of the full sequence. Introduced in the LongFormer (2020), now widely adopted.

## Global vs. Local Attention

- **Global (standard):** each token attends to every other token — O(n²) cost
- **Local (sliding window):** each token attends only to a fixed window around its position — O(n·w) cost where w is window size

In practice, models use a **hybrid** of both. The ratio and window size vary:

| Model | Local:Global Ratio | Window Size |
|-------|-------------------|-------------|
| Gemma 2 | 1:1 | 4,096 |
| Gemma 3/4 | 5:1 | 1,024 |
| GPT-OSS | 1:1 (every other) | — |
| Olmo 3 | similar to Gemma 3 | — |
| Xiaomi MiMo-V2-Flash | 5:1 | 128 (very aggressive) |
| Trinity Large | 3:1 | 4,096 |

## Key Finding

Gemma 3's ablation study showed sliding window attention has **minimal impact on modeling performance** (measured by perplexity) while substantially reducing KV cache memory. This makes it a "free" efficiency win in most cases.

## Interesting Counterpoint

Mistral abandoned sliding window attention in Mistral Small 3.1 despite using it in earlier models. Possible reason: while sliding window reduces memory, it may not reduce inference latency — and latency was Mistral's priority. Regular attention may also benefit from more optimized implementations (FlashAttention).

## Connections

- Alternative to [[Multi-Head Latent Attention]] for KV cache reduction
- Can combine with GQA (Gemma 3) or MHA (OLMo 3)
- Complements [[Mixture of Experts]] — different efficiency dimensions
- Gemma 3's aggressive 5:1 ratio pioneered the modern hybrid approach

(Source: [[S — The Big LLM Architecture Comparison]])
