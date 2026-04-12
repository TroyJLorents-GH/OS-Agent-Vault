---
title: Multi-Token Prediction
type: concept
created: 2026-04-10
updated: 2026-04-10
sources: ["S — The Big LLM Architecture Comparison"]
tags: [architecture, technique, training, inference, llm, "2025"]
---

# Multi-Token Prediction (MTP)

A training technique where the LLM predicts several future tokens at each position (typically k=4) instead of just the next one. Small extra prediction heads output logits for positions t+1 through t+k, and losses are summed across all offsets.

## Dual Benefits

### 1. Better Training Signal
Predicting multiple tokens forces the model to build richer internal representations — it must understand not just the immediate next token but the trajectory of the sequence. This speeds up training convergence.

### 2. Built-in Speculative Decoding
At inference time, the MTP heads can act as a **native draft model** for speculative decoding — proposing candidate token sequences that the main model then verifies. This reduces inference latency without needing a separate, smaller draft model.

Nemotron 3 Super explicitly uses this: the shared-weight MTP head acts as an internal draft model, and multi-step training maintains consistency between training and inference.

## Adoption

| Model | MTP at Training | MTP at Inference |
|-------|----------------|-----------------|
| DeepSeek V3/V3.2 | Yes | — |
| Qwen3-Next | Yes | Yes (speculative decoding) |
| GLM-4.5 | Yes | — |
| MiniMax-M2 | Yes | — |
| Nemotron 3 Super | Yes | Yes (native speculative decoding) |
| Xiaomi MiMo-V2-Flash | Yes | — |

## Connections

- Covered in [[S — The Big LLM Architecture Comparison]] across multiple model sections
- Complements [[Mixture of Experts]] and [[Sliding Window Attention]] as an efficiency technique — but operates on a different axis (predicting more tokens per step vs. reducing per-token cost)
- Originally proposed in the MTP paper (2024), recommended k=4

(Source: [[S — The Big LLM Architecture Comparison]])
