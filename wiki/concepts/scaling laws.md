---
title: Scaling Laws
type: concept
created: 2026-06-04
updated: 2026-06-04
sources: ["S — The Big LLM Architecture Comparison", "S — AI Technology Trends 2026 Key Developments"]
tags: [scaling-laws, training, compute, theory, llm, y2026]
---

# Scaling Laws

The empirical finding that model performance improves **predictably** with increases in three quantities — model parameters, training data, and compute — typically as smooth power laws. Scaling laws are why the field spent 2020–2025 betting on "bigger," and the reasons that bet is now being qualified are central to the mid-2026 picture.

## The core claim

Loss falls as a power law in compute, parameters, and data. Two practical consequences:
- **Predictability** — you can forecast a larger model's loss before training it, making capital allocation a quantitative decision.
- **Compute-optimal allocation** — for a fixed compute budget, there is an optimal split between model size and data (the "Chinchilla" insight): many early large models were *undertrained* relative to their size.

This underwrites the [[bitter lesson|bitter-lesson]] intuition that general methods leveraging more compute beat hand-crafted cleverness over time.

## Where the simple story breaks (2026 view)

The wiki's architecture and economics pages document the qualifications:

- **Architecture convergence, not just size** — gains in 2025–2026 came heavily from architecture/efficiency ([[Mixture of Experts]], [[Multi-Head Latent Attention]], [[Sliding Window Attention]]) rather than raw parameter count. See [[S — The Big LLM Architecture Comparison]]. Models are *converging* in capability, which a pure "scale wins" view didn't predict.
- **Inference-time scaling** — a new axis: spend more compute *at inference* (reasoning models, search, longer chains) instead of only at training. Capability now scales with test-time compute, not just model size.
- **Data wall** — high-quality human text is finite; [[synthetic data generation]] and curation increasingly substitute for raw scale.
- **Economics flips the objective** — [[Inference Economics]]: once serving cost dominates, the goal is the *smallest* model that clears the bar, not the largest. [[Small language models]] and [[Fine-Tuning]] are the practical answer; [[Gemma]] E2B/E4B show frontier-quality at 2–4B.

## Why it still matters

Even qualified, scaling laws remain the planning backbone of the [[AI Capex Buildout]] — multi-year compute commitments are bets that more compute reliably buys more capability. The forecast of **$2.52T global AI spending** ([[S — AI Technology Trends 2026 Key Developments]]) is a scaling-laws bet at civilization scale. The open question is whether the returns curve bends before the capital does.

## Connections

- [[Mixture of Experts]] — efficiency gains that complicate pure parameter scaling
- [[Inference Economics]] — the economic counterforce: smallest-sufficient, not largest
- [[AI Capex Buildout]] — scaling laws as the capital-allocation thesis
- [[Small language models]] — the "scale down" response
- [[synthetic-data-generation]] — addressing the data wall
- [[S — The Big LLM Architecture Comparison]] — architecture convergence evidence

## Open questions

- Are we on the flat part of the curve for pretraining, with inference-time compute the new frontier?
- Does the [[AI Capex Buildout]] over-index on a training-scaling story while the actual gains shift to harness + inference?
