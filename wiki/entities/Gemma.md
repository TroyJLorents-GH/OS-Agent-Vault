---
title: Gemma
type: entity
created: 2026-06-03
updated: 2026-06-03
sources: ["S — Open-Source AI Landscape April 2026", "S — The Big LLM Architecture Comparison", "Gemini 3.2 Flash What We Know Before Google IO 2026"]
tags: [google-deepmind, llm, multimodal, open-source, product, y2026]
---

# Gemma

[[Google]]'s **open-weights** model family — the open counterpart to the closed [[Gemini]] line. Edge-to-server lineup, natively multimodal (vision + audio). The current generation is **Gemma 4**.

## Gemma 4 family

| Variant | Total / Active | Context | License | Type |
|---------|----------------|---------|---------|------|
| Gemma 4 31B | 31B / 31B | 256K | Apache 2.0 | Dense |
| Gemma 4 26B-A4B | 26B / 4B | 256K | Apache 2.0 | MoE |
| Gemma 4 E4B | 4B / 4B | 128K | Apache 2.0 | Dense (edge) |
| Gemma 4 E2B | 2B / 2B | 128K | Apache 2.0 | Dense (edge) |

(Source: [[S — Open-Source AI Landscape April 2026]])

- **Apache 2.0** — first Gemma under an OSI-approved license, a deliberate strategic shift away from Google's earlier custom "Gemma terms." Now sits alongside gpt-oss as the strictest-licensing-friendly frontier open weights. See [[Open-Source AI]].
- **Cheapest frontier-class inference** — Gemma 4 31B fits on an A100 40GB (~$1.50/hr).
- **Edge SLMs are real** — E2B (2B) and E4B (4B) show frontier-quality at phone scale. See [[Small language models]].
- **Local on consumer GPUs** — [[NVIDIA]] ships optimized Gemma 4 inference on RTX hardware, enabling local agentic AI.

## Architecture notes

From the architecture survey ([[S — The Big LLM Architecture Comparison]]): Gemma 4 uses **p-RoPE** (RoPE applied to 25% of frequency pairs), **reuses keys as values in global layers**, **Pre+Post-Norm**, and the **[[Sliding Window Attention]]** 5:1 local-to-global ratio (1024-token windows) that Gemma 3 pioneered. Like most 2026 models it uses GQA rather than [[Multi-Head Latent Attention]].

## Figure discrepancy (lint note)

The [[S — Gemini 3.2 Flash Before Google IO 2026]] blog describes the I/O 2026 Gemma 4 release as a **"27B variant with 4-bit quantization."** The detailed [[S — Open-Source AI Landscape April 2026]] lists the dense flagship at **31B**. Treat 31B (dense, full precision) as canonical; the "27B 4-bit" is likely an approximate/quantized framing from the leak-stage blog. Reconcile after Google's official I/O release notes.

## Connections

- [[Google]] — vendor
- [[Gemini]] — closed sibling line
- [[Open-Source AI]] — license liberation, MoE single-GPU inference
- [[Small language models]] — E2B/E4B edge variants
- [[Sliding Window Attention]] — Gemma-pioneered efficiency technique
- [[Multi-Head Latent Attention]] — contrast (Gemma uses GQA)
- [[NVIDIA]] — RTX local inference
- [[S — Open-Source AI Landscape April 2026]] — primary spec source
- [[S — The Big LLM Architecture Comparison]] — architecture details
