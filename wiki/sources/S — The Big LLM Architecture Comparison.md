---
title: "S — The Big LLM Architecture Comparison"
type: source
created: 2026-04-10
updated: 2026-04-10
sources: ["The Big LLM Architecture Comparison.md"]
tags: [llm, architecture, compute, training, inference, "2025", "2026"]
---

# S — The Big LLM Architecture Comparison

**Source:** https://magazine.sebastianraschka.com/p/the-big-llm-architecture-comparison
**Author:** [[Sebastian Raschka]]
**Published:** 2025-07-19 (last updated 2026-04-02, adding Gemma 4)
**Publisher:** Sebastian Raschka's Substack
**Subtitle:** From DeepSeek V3 to GLM-5: A Look At Modern LLM Architecture Design

## Core Thesis

Seven years after GPT, modern LLMs are **structurally more similar than different**. The core [[Transformer Architecture]] persists — what's changed are incremental refinements: RoPE replaced absolute positional embeddings, GQA replaced MHA, SwiGLU replaced GELU. The real differentiation is happening in training pipelines and inference strategies, not architecture. "A lot of the secret sauce these days is in the training pipeline as well as the inference scaling strategies."

## Models Covered (23 architectures)

| Model | Params | Active | Key Architecture Feature |
|-------|--------|--------|--------------------------|
| [[DeepSeek]] V3/R1 | 671B | 37B | [[Multi-Head Latent Attention]] + [[Mixture of Experts]] (256 experts, 9 active) |
| OLMo 2 | 7-32B | dense | Post-Norm placement + QK-Norm for training stability |
| [[Gemma]] 3 | 27B | dense | [[Sliding Window Attention]] (5:1 ratio), Pre+Post-Norm |
| Gemma 3n | ~4B | dense | Per-Layer Embedding for phone-scale efficiency, MatFormer slicing |
| Mistral Small 3.1 | 24B | dense | Standard GQA, abandoned sliding window for better latency |
| [[Llama 4]] Maverick | 400B | 17B | MoE with fewer, larger experts (2 active vs DeepSeek's 9) |
| [[Qwen3]] dense | 0.6-32B | dense | Deeper architecture, smaller hidden layers, QK-Norm |
| Qwen3 MoE | 235B | 22B | Dropped shared expert (unlike DeepSeek), 8 active experts |
| [[SmolLM3]] | 3B | dense | NoPE (No Positional Embedding) in every 4th layer |
| [[Kimi K2]] | 1T | 32B | DeepSeek V3 architecture scaled up — biggest open-weight model |
| Kimi K2 Thinking | 1T | 32B | Same as K2, context extended to 256k |
| [[GPT-OSS]] | 20-120B | 3.6B | OpenAI's first open weights since GPT-2; wider not deeper; attention sinks |
| Grok 2.5 | 270B | MoE | Older-style large experts; shared expert (always-on SwiGLU) |
| GLM-4.5 | 355B | 32B | 3 dense layers before MoE blocks for convergence stability |
| Qwen3-Next | 80B | 3B | [[Gated DeltaNet]] + Gated Attention hybrid (3:1), [[Multi-Token Prediction]] |
| MiniMax-M1 | 456B | 46B | Lightning (linear) attention — later abandoned in M2 |
| MiniMax-M2 | ~235B | 10B | Returned to full attention; per-layer QK-Norm; very sparse (4.37% active) |
| [[Kimi Linear]] | 48B | — | Kimi Delta Attention (refined Gated DeltaNet) + MLA hybrid |
| Olmo 3 | 7-32B | dense | Post-norm, sliding window attention, fully open-source |
| DeepSeek V3.2 | ~671B | 37B | Added sparse attention for efficiency; on par with GPT-5.1 |
| Mistral 3 Large | 675B | 41B | Adopted DeepSeek V3 architecture wholesale; NVIDIA Blackwell optimized |
| Nemotron 3 Nano/Super | 30-120B | 3-12B | Mamba-2 + Transformer hybrid; latent MoE; MTP for speculative decoding |
| Xiaomi MiMo-V2-Flash | 309B | 15B | Aggressive sliding window (128 tokens); matches DeepSeek V3.2 |
| Arcee Trinity Large | 400B | 13B | Gated attention, depth-scaled sandwich norm, NoPE in global layers |
| GLM-5 | 744B | 40B | Adopted DeepSeek's MLA + sparse attention; on par with GPT-5.2, Claude 4.6 Opus |
| Gemma 4 | 31B (+ MoE 26B) | dense/4B | p-RoPE (25% frequency pairs), keys reused as values in global layers |

## Key Architectural Trends

### 1. [[Mixture of Experts]] Is the Dominant Paradigm
Nearly every major 2025-2026 model has adopted MoE. The trend is toward **more, smaller experts** (DeepSeek: 256 experts) rather than fewer, larger ones (GPT-OSS: 32 experts). Shared experts (always-on, handle common patterns) remain debated — DeepSeek, GLM, Grok, and Qwen3-Next use them; Qwen3 and MiniMax-M2 dropped them.

### 2. DeepSeek V3 as Reference Architecture
Three separate teams adopted DeepSeek V3's architecture: **Kimi K2** (scaled up to 1T), **Mistral 3 Large** (adjusted expert ratios), and **GLM-5** (added sparse attention). "Why change what ain't broke?"

### 3. [[Multi-Head Latent Attention]] Over GQA
DeepSeek's MLA compresses KV tensors into lower-dimensional space before caching, then projects back at inference. Ablation studies show MLA **outperforms both GQA and standard MHA** in modeling performance while reducing KV cache memory. Adopted by Kimi K2, GLM-5, Kimi Linear.

### 4. [[Sliding Window Attention]] for Efficiency
Restricts attention to a local window around each token. Gemma 3 pioneered 5:1 local-to-global ratio with 1024-token windows, achieving substantial KV cache savings with "minimal impact on modeling performance." Adopted by Olmo 3, Xiaomi MiMo, GPT-OSS, Trinity Large.

### 5. [[Linear Attention]] Revival — Then Partial Retreat
MiniMax-M1, Qwen3-Next, and DeepSeek V3.2 all adopted linear attention variants. Then **MiniMax retreated**: M2 dropped linear attention because it "had poor accuracy in reasoning and multi-turn tasks." Kimi Linear's refined approach (Kimi Delta Attention) restored confidence — linear attention remains promising but unproven at largest scale.

### 6. Mamba-Transformer Hybrids
Nemotron 3 is the most extreme example: mostly Mamba-2 blocks with only a few attention layers. Qwen3-Next and Kimi Linear use [[Gated DeltaNet]] (conceptually similar to Mamba) in a 3:1 ratio with full attention. Both Gated DeltaNet and Mamba replace attention with gated-state-space updates that scale **linearly** instead of quadratically with sequence length.

### 7. [[Multi-Token Prediction]]
Training LLMs to predict several future tokens per position (typically k=4). Used by DeepSeek V3, Nemotron 3, Qwen3-Next, Xiaomi MiMo. Benefits: richer training signal + enables speculative decoding at inference (the MTP head acts as a built-in draft model).

### 8. Normalization Matters More Than Expected
- **Post-Norm** (OLMo 2): RMSNorm after attention/FF, inside residual — stabilizes training
- **Pre+Post-Norm** (Gemma 3/4): both positions — "a bit of extra normalization can't hurt"
- **QK-Norm**: RMSNorm on queries/keys before RoPE — improves training stability, widely adopted
- **Depth-scaled sandwich norm** (Trinity Large): gain scaled by 1/sqrt(L)

### 9. NoPE (No Positional Embedding)
Removing explicit positional encoding entirely. The causal attention mask provides implicit ordering. SmolLM3 and Trinity Large apply NoPE in a subset of layers. The NoPE paper showed **better length generalization** — model performance degrades less with increasing sequence length.

### 10. Width vs. Depth Tradeoff
GPT-OSS chose wider architecture (fewer layers, larger dimensions) vs. Qwen3's deeper approach. Wider → faster inference (better parallelization) but higher memory. Deeper → more flexibility but harder to train. Gemma 2 ablation: wider was slightly better (52.0 vs 50.8 average).

## Notable Quotes

> "A lot of the secret sauce these days is in the training pipeline as well as the inference scaling strategies."

> "Why change what ain't broke?" — on Mistral 3 adopting DeepSeek V3's architecture

> "Linear attention is tricky in production LLMs. It seemed to work fine with regular prompts, but it had poor accuracy in reasoning and multi-turn tasks." — MiniMax team on why M2 dropped linear attention

## Connections

- **[[Mixture of Experts]]** — the dominant trend; central concept page created from this source
- **[[Multi-Head Latent Attention]]** — DeepSeek's key innovation, now spreading
- **[[Sliding Window Attention]]** — efficiency technique with proven minimal quality impact
- **[[Linear Attention]]** — the revival story with MiniMax's cautionary retreat
- **[[Multi-Token Prediction]]** — emerging technique spanning training and inference
- **[[Small language models]]** — Qwen3 0.6B, SmolLM3 3B show small models can be architecturally sophisticated
- **[[Fine-tuning]]** — dense models noted as "more straightforward to fine-tune" vs. MoE
- **[[DeepSeek]]** — their architecture is becoming the reference standard for open-weight LLMs
- **[[Sebastian Raschka]]** — prolific AI educator, author of "Build a Large Language Model (From Scratch)"

## Open Questions

- Will [[Linear Attention]] succeed at truly large scale (>100B), or is MiniMax's retreat the canary?
- When will someone combine MoE + sliding window attention + MLA in one architecture?
- Is the trend toward more, smaller experts universal, or will some domains favor fewer, larger experts?
- DeepSeek V4 hasn't dropped yet — will it introduce a genuinely new architectural paradigm, or continue incremental refinement?
- How much of benchmark performance is actually architecture vs. training data vs. training recipe?

(Source: [The Big LLM Architecture Comparison](../raw/The%20Big%20LLM%20Architecture%20Comparison.md))
