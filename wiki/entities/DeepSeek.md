---
title: DeepSeek
type: entity
created: 2026-04-10
updated: 2026-04-10
sources: ["S — The Big LLM Architecture Comparison"]
tags: [openai, llm, architecture, compute, training, inference, "2025", "2026"]
---

# DeepSeek

Chinese AI lab whose architecture has become the **reference standard for open-weight LLMs** in 2025-2026. DeepSeek R1's January 2025 release made a major impact; by late 2025, three separate teams had adopted the DeepSeek V3 architecture wholesale.

## Architecture Innovations

### [[Multi-Head Latent Attention]] (MLA)
Compresses KV tensors into lower-dimensional space, reducing KV cache memory while **outperforming** both standard MHA and GQA in modeling performance. Introduced in DeepSeek V2, refined in V3.

### [[Mixture of Experts]] Design
- 256 experts per MoE module, 9 active (1 shared + 8 routed)
- 671B total parameters, only 37B active per inference step
- Shared expert handles common patterns; routed experts specialize
- MoE layers in every transformer block except the first 3 (dense layers first for convergence stability)

### Sparse Attention (V3.2)
DeepSeek V3.2 added sparse attention for further efficiency. V3.2 is on par with GPT-5.1 and Gemini 3.0 Pro.

## Model Timeline

| Model | Date | Total Params | Active | Key Change |
|-------|------|-------------|--------|------------|
| DeepSeek V2 | May 2024 | — | — | Introduced MLA |
| DeepSeek V3 | Dec 2024 | 671B | 37B | MLA + MoE at scale |
| DeepSeek R1 | Jan 2025 | 671B | 37B | Reasoning model on V3 architecture |
| DeepSeek V3.1 | — | 671B | 37B | Incremental |
| DeepSeek V3.2 | Dec 2025 | ~671B | 37B | Added sparse attention; GPT-5.1 competitive |

## Architecture Adoption

Three teams adopted DeepSeek V3's full architecture:
1. **[[Kimi K2]]** — scaled up to 1 trillion parameters (biggest open-weight model)
2. **Mistral 3 Large** — same architecture, adjusted expert size ratio, added vision encoder
3. **GLM-5** — added DeepSeek's MLA + sparse attention; on par with Claude 4.6 Opus

> "Why change what ain't broke?" — [[Sebastian Raschka]]

## Connections

- Architecture innovations: [[Multi-Head Latent Attention]], [[Mixture of Experts]]
- Covered extensively in [[S — The Big LLM Architecture Comparison]]
- [[Multi-Token Prediction]] used in V3 training
- Contrast with [[Small language models]] approach from [[S — redhat-slms-scientific-research-2026-03-30]] — DeepSeek represents the "scale up with efficiency tricks" path, while SLMs represent the "scale down with domain focus" path

(Source: [[S — The Big LLM Architecture Comparison]])
