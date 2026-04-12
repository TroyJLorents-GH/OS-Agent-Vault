---
title: Mixture of Experts
type: concept
created: 2026-04-10
updated: 2026-04-10
sources: ["S — The Big LLM Architecture Comparison"]
tags: [architecture, llm, compute, inference, training, "2025", "2026"]
---

# Mixture of Experts (MoE)

The dominant architectural trend in LLMs as of 2025-2026. MoE replaces each FeedForward module in a transformer block with **multiple expert FeedForward modules**, but only activates a small subset per token via a learned router. This dramatically increases total model capacity (knowledge uptake during training) while keeping inference cost manageable.

## How It Works

```
Standard:  Input → [Single FeedForward] → Output
MoE:       Input → Router → [Expert 1, Expert 5, Expert 12] → Output
                           (only 3 of 256 experts activated)
```

- **Total parameters** = large (all experts combined)
- **Active parameters** = small (only the selected experts per token)
- **Router** selects which experts handle each token

Example: [[DeepSeek]] V3 has 671B total parameters but only 37B active per inference step (256 experts, 9 active: 1 shared + 8 routed).

## Key Design Decisions

### More Small Experts vs. Fewer Large Experts

The trend favors **more, smaller experts** for better specialization:

| Model | Total Experts | Active | Expert Hidden Size |
|-------|--------------|--------|-------------------|
| DeepSeek V3 | 256 | 9 | 2,048 |
| Qwen3 235B | 128 | 8 | small |
| [[Kimi K2]] | 384 | 9 | — |
| MiniMax-M2 | 128 | 8 | — |
| [[GPT-OSS]] 20B | 32 | 4 | 2,880 (large) |
| Grok 2.5 | 8 | — | large (older style) |

DeepSeekMoE paper showed finer-grained experts improve performance at constant total parameter count.

### Shared Experts

An always-active expert that handles common patterns, freeing routed experts to specialize. Introduced by DeepSeekMoE (2024).

- **Use shared expert:** DeepSeek V3, GLM-4.5/5, Grok 2.5, Kimi K2, Qwen3-Next
- **Dropped shared expert:** Qwen3, MiniMax-M2, GPT-OSS

Qwen3 developer: "We did not find significant enough improvement on shared expert and we were worrying about the optimization for inference."

### Dense Layers Before MoE

GLM-4.5/5 and DeepSeek V3 use 3 dense layers before MoE blocks. Rationale: early layers need to form stable low-level representations before routing decisions shape higher-level processing. MoE routing instability in early layers can interfere with syntactic/semantic feature extraction.

## Dense vs. MoE Tradeoffs

| Dimension | Dense | MoE |
|-----------|-------|-----|
| Fine-tuning | Simpler, more robust | More complex |
| Deployment | Standard hardware | Requires expert parallelism |
| Inference cost | Proportional to total params | Proportional to active params |
| Knowledge capacity | Limited by param count | Much larger at same inference cost |
| Optimization | Well-understood | Router stability is tricky |

Qwen3 releases both dense and MoE variants to serve different use cases.

## Connections

- Central architectural feature in [[S — The Big LLM Architecture Comparison]]
- [[DeepSeek]]'s MoE design (shared experts, many small experts) is becoming the reference
- Complements [[Multi-Head Latent Attention]] for inference efficiency
- [[Small language models]] can now use MoE (Qwen3 0.6B is dense, but Qwen3 30B-A3B is MoE at small active size)
- Relevant to [[fine-tuning]] — dense models are preferred for customization (per [[S — The Big LLM Architecture Comparison]])
- Nemotron 3 combines MoE with Mamba-2 hybrid for extreme efficiency

(Source: [[S — The Big LLM Architecture Comparison]])
