---
title: Transformer Architecture
type: concept
created: 2026-04-10
updated: 2026-04-10
sources: ["S — The Big LLM Architecture Comparison"]
tags: [architecture, llm, training, inference, "2025", "2026"]
---

# Transformer Architecture

The foundational architecture for modern LLMs, introduced in "Attention is All You Need" (2017). Seven years later, the core structure persists with remarkable stability — most innovations are **refinements within the same framework**, not replacements of it.

## The Base Components (as of 2025-2026)

A modern transformer block typically contains:
1. **Normalization** (RMSNorm, replacing LayerNorm)
2. **Attention** (GQA, MLA, or sliding window variant, replacing standard MHA)
3. **FeedForward / MoE** (SwiGLU activation, replacing GELU; optionally multiple experts)
4. **Positional encoding** (RoPE, replacing absolute embeddings; sometimes NoPE)
5. **Residual connections** (unchanged from original)

## What Changed (Incremental Refinements)

| Component | Original (2017-2019) | Modern (2025-2026) | Why |
|-----------|----------------------|---------------------|-----|
| Normalization | LayerNorm, Post-Norm | RMSNorm, Pre-Norm or both | Simpler, more stable training |
| Attention | Multi-Head | GQA, [[Multi-Head Latent Attention]], [[Sliding Window Attention]] | KV cache efficiency |
| FeedForward | Single block | [[Mixture of Experts]] | More capacity at same inference cost |
| Activation | GELU | SwiGLU | Better performance |
| Position | Absolute embeddings | RoPE (or NoPE) | Better length generalization |
| Attention stability | — | QK-Norm | Prevents training instability |

## What Hasn't Changed

- The core attention mechanism (scaled dot-product) remains standard
- Residual connections (skip connections) are universal
- Decoder-only autoregressive architecture dominates
- The transformer block is repeated many times (61x in DeepSeek V3, 78x in GLM-5)

## Emerging Challenges

### [[Linear Attention]] and Mamba Hybrids
The quadratic cost of standard attention drives exploration of alternatives. Mamba-2 (Nemotron 3), [[Gated DeltaNet]] (Qwen3-Next, Kimi Linear), and lightning attention (MiniMax-M1) all attempt linear-time replacements. But MiniMax's retreat from linear attention in M2 shows that full attention's quality advantage remains significant for reasoning tasks.

### The Architecture vs. Training Debate
[[Sebastian Raschka]]'s observation: "A lot of the secret sauce these days is in the training pipeline as well as the inference scaling strategies." Architecture is converging; differentiation increasingly comes from training data, training recipes, and post-training (RLHF, DPO, etc.).

## Connections

- All models in [[S — The Big LLM Architecture Comparison]] are transformer-based (or transformer-hybrid)
- [[Mixture of Experts]] is the biggest structural change to the FeedForward component
- [[Multi-Head Latent Attention]] and [[Sliding Window Attention]] are the main attention refinements
- [[Multi-Token Prediction]] changes the training objective but not the architecture itself
- [[Small language models]] use the same architecture at smaller scale (Qwen3 0.6B, SmolLM3 3B)

(Source: [[S — The Big LLM Architecture Comparison]])
