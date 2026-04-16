---
title: "S — Open-Source AI Landscape April 2026"
type: source
created: 2026-04-13
updated: 2026-04-13
sources: ["Open-Source AI Landscape April 2026 Complete Guide.md"]
tags: [llm, architecture, benchmark, product, strategy, open-source, google-deepmind, meta-ai, openai, mistral, "2026"]
---

# S — Open-Source AI Landscape April 2026

**Source:** https://www.digitalapplied.com/blog/open-source-ai-landscape-april-2026-gemma-qwen-llama
**Author:** Digital Applied
**Published:** 2026-04-03
**Publisher:** Digital Applied Blog

## Core Finding

The open-source AI landscape in April 2026 bears little resemblance to a year ago. Six distinct model families from six organizations now ship competitive open-weight models that match or exceed proprietary alternatives on targeted benchmarks. The question is no longer "should we consider open-weight?" but "which open-weight model matches our specific requirements?"

## Three Structural Shifts

1. **[[Mixture of Experts]] is the default architecture** — 5 of 6 major open models use MoE. Active parameter counts range from 5.1B (gpt-oss) to 40B (GLM-5), enabling single-GPU inference for models with 100B-744B total parameters.
2. **License liberation** — Apache 2.0 and MIT now cover the majority of leading open models (Gemma 4, Qwen 3.6, Mistral Small 4, gpt-oss, GLM-5). Only Llama 4 retains a custom community license.
3. **Open-proprietary gap has closed** — open-weight models are now the rational default for many production workloads, offering control, privacy, and 3-10x cost advantages at scale.

## Complete Model Comparison

| Model | Lab | Total Params | Active Params | Context | License | Architecture |
|-------|-----|-------------|--------------|---------|---------|-------------|
| GLM-5 | Zhipu AI | 744B | 40B | 200K | MIT | MoE |
| Llama 4 Maverick | Meta | 400B | 17B | 1M | Llama 4 Community | 128-expert MoE |
| Mistral Small 4 | Mistral AI | 119B | 6.5B | 256K | Apache 2.0 | 128-expert MoE |
| [[GPT-OSS]] 120b | OpenAI | 117B | 5.1B | 128K | Apache 2.0 | MoE (MXFP4) |
| Llama 4 Scout | Meta | 109B | 17B | 10M | Llama 4 Community | 16-expert MoE |
| Qwen 3.6 Plus | Alibaba | TBD | TBD | 1M | Apache 2.0 | Hybrid MoE + [[Linear Attention]] |
| [[Gemma]] 4 31B | Google | 31B | 31B | 256K | Apache 2.0 | Dense |
| Gemma 4 26B-A4B | Google | 26B | 4B | 256K | Apache 2.0 | MoE |
| Gemma 4 E4B | Google | 4B | 4B | 128K | Apache 2.0 | Dense (edge) |
| Gemma 4 E2B | Google | 2B | 2B | 128K | Apache 2.0 | Dense (edge) |

## Model-by-Model Highlights

### Gemma 4 (Google)
- **Apache 2.0** — first Gemma under OSI-approved license (strategic shift from custom terms)
- Four variants: edge (2B, 4B) to server (26B MoE, 31B Dense), all natively multimodal
- 89.2% AIME 2026, 84.3% GPQA Diamond, 80.0% LiveCodeBench v6
- NVIDIA already ships optimized inference for RTX hardware
- Limitation: 31B max — smaller than Llama 4 (400B) or GLM-5 (744B) for extreme reasoning tasks

### Qwen 3.5/3.6 Plus (Alibaba)
- **Most commercially deployed open-weight family globally** under Apache 2.0
- Widest size range: 0.8B to 397B parameters
- **Leads coding benchmarks** — LiveCodeBench and SWE-bench show clear margins over Llama 4 and Gemma 4
- Qwen 3.6 Plus: hybrid MoE + [[Linear Attention]], 1M context, always-on chain-of-thought
- Aggressive pricing strategy: free preview to drive adoption before pricing kicks in

### Llama 4 Scout/Maverick (Meta)
- Scout: 10M context window (largest), fits single H100, 16-expert MoE
- Maverick: 85.5% MMLU (highest among open models), 128-expert MoE, 400B total
- Llama 4 Community License: free under 700M MAU — non-standard, creates enterprise legal friction vs. Apache 2.0 alternatives

### Mistral Small 4
- **Unified model** — instruct + reasoning + vision + coding in one, with adjustable `reasoning_effort` parameter
- 119B total, 6.5B active, 128 experts, 4 active per token
- Outperforms gpt-oss on LiveCodeBench with 20% shorter output — directly translates to lower cost
- 40% faster completion, 3x more requests/second vs. Mistral Small 3

### GPT-OSS 120B (OpenAI)
- **OpenAI's first open-weight model** since GPT-2 — under Apache 2.0
- 117B total, 5.1B active, fits single H100 with MXFP4 quantization
- Trained via RL from OpenAI's most advanced internal models (o3, frontier systems)
- Strategic signal: even OpenAI considers open-weight necessary
- Limitation: text-only, 128K context (smallest among major 2026 open models)

### GLM-5 (Zhipu AI)
- **Largest open-weight model** at 744B total, 40B active
- **Trained entirely on Huawei Ascend chips** — zero NVIDIA dependency. First frontier-class model demonstrating Chinese hardware independence.
- MIT license (most permissive), $1.00/$3.20 per MTok (10x cheaper than Claude Opus 4.6)
- 50.4% on Humanity's Last Exam (exceeding Claude Opus 4.5)
- Uses [[DeepSeek]] Sparse Attention for long-context handling
- Geopolitical implication: future Chinese open models won't be constrained by US export controls

## Selection Framework

| Priority | Best Choice | Runner-Up |
|----------|------------|-----------|
| Coding / development | Qwen 3.5/3.6 | Mistral Small 4 |
| Maximum context window | Llama 4 Scout (10M) | Qwen 3.6 Plus (1M) |
| Edge / mobile | Gemma 4 E2B/E4B | Qwen 3.5 0.8B |
| Strictest licensing | Gemma 4 / gpt-oss (Apache 2.0) | GLM-5 (MIT) |
| Highest benchmarks | Llama 4 Maverick (85.5% MMLU) | GLM-5 (50.4% HLE) |
| Unified single model | Mistral Small 4 | Qwen 3.6 Plus |
| Single-GPU deployment | gpt-oss-120b (5.1B active) | Llama 4 Scout |
| Multimodal | Gemma 4 (vision + audio) | Llama 4 (vision only) |
| Fine-tuning flexibility | Qwen 3.5 family (0.8B-397B) | Gemma 4 |

## Deployment Economics

- **Self-hosting crossover:** ~50-100M tokens/month. Below that, APIs are cheaper. Above, self-hosting saves 3-10x.
- **At 1B+ tokens/month:** 5-10x cost reduction from self-hosting
- **Single-GPU frontier:** MoE enables Llama 4 Scout, gpt-oss, Mistral Small 4 on one H100 (~$2.50/hr cloud)
- **Gemma 4 31B:** fits on A100 40GB (~$1.50/hr) — cheapest frontier-class inference

## Connections

- **[[Mixture of Experts]]** — confirmed as dominant architecture: 5 of 6 families use MoE
- **[[Linear Attention]]** — Qwen 3.6 Plus adopts hybrid MoE + linear attention for 1M context
- **[[DeepSeek]]** — GLM-5 adopts DeepSeek Sparse Attention; architecture influence spreading
- **[[Multi-Head Latent Attention]]** — GLM-5 uses DeepSeek's MLA
- **[[AI Industry Landscape April 2026]]** — this article provides the open-source complement to the proprietary landscape
- **[[Small language models]]** — Gemma 4 E2B (2B) and E4B (4B) show frontier-quality SLMs are now real
- **[[Transformer Architecture]]** — all models remain transformer-based with incremental refinements
- **[[GPT-OSS]]** — OpenAI's strategic entry into open-weight validates the category
- **[[AI as equalizer]]** — Apache 2.0 licensing + single-GPU deployment democratizes frontier AI access

## Open Questions

- Will Qwen 3.6 Plus's hybrid linear attention + MoE become the next architectural standard, or is it a one-off?
- How will GLM-5's Huawei-only training affect Western enterprise adoption (trust/supply chain concerns)?
- Will Meta eventually switch Llama to Apache 2.0, or does the community license serve a strategic purpose?
- At what point does open-source parity with proprietary cause a pricing collapse for API providers?
- Is the "no single model dominates all dimensions" equilibrium stable, or will one family pull ahead?

(Source: [Open-Source AI Landscape April 2026 Complete Guide](../raw/Open-Source%20AI%20Landscape%20April%202026%20Complete%20Guide.md))
