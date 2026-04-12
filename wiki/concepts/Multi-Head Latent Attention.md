---
title: Multi-Head Latent Attention
type: concept
created: 2026-04-10
updated: 2026-04-10
sources: ["S — The Big LLM Architecture Comparison"]
tags: [architecture, llm, inference, compute, "2025"]
---

# Multi-Head Latent Attention (MLA)

An attention mechanism introduced by [[DeepSeek]] (V2, then V3) that compresses key and value tensors into a lower-dimensional latent space before storing them in the KV cache, then projects them back to full size at inference time.

## How It Differs from GQA

| Mechanism | Strategy | KV Cache Savings | Performance |
|-----------|----------|-----------------|-------------|
| MHA (standard) | Separate K,V per head | None (baseline) | Baseline |
| GQA | Share K,V across head groups | Good | Comparable to MHA |
| **MLA** | Compress K,V into latent space | Good | **Better than MHA** |

The key insight: GQA is a computational workaround that performs "comparably" to MHA. MLA actually **outperforms** MHA in modeling performance (per DeepSeek V2 ablation studies) while also reducing KV cache memory. It's strictly better on both dimensions.

## Why It's Not Universal Yet

MLA is more complex to implement and adds an extra matrix multiplication during inference. Most models (Llama 4, Qwen3, Gemma 3/4, GPT-OSS) still use GQA, likely because GQA is simpler, well-optimized in existing frameworks (FlashAttention), and "good enough."

## Adoption

- **Use MLA:** DeepSeek V3/V3.2/R1, [[Kimi K2]], Kimi Linear (with gating), GLM-5, Mistral 3 Large
- **Use GQA:** Llama 4, Qwen3, Gemma 3/4, GPT-OSS, OLMo 2/3, MiniMax-M2

The fact that three major architectures (Kimi K2, Mistral 3, GLM-5) adopted DeepSeek's full architecture — including MLA — suggests MLA's advantages are real enough to copy.

## Connections

- Key component of [[DeepSeek]]'s architecture alongside [[Mixture of Experts]]
- Alternative approach to [[Sliding Window Attention]] for KV cache reduction
- Covered in detail in [[S — The Big LLM Architecture Comparison]]

(Source: [[S — The Big LLM Architecture Comparison]])
