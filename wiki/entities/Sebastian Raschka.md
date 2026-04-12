---
title: Sebastian Raschka
type: entity
created: 2026-04-10
updated: 2026-04-10
sources:
  - S — The Big LLM Architecture Comparison
  - S — Components of A Coding Agent
tags:
  - person
  - llm
  - architecture
  - training
---

# Sebastian Raschka

AI researcher, educator, and author. PhD. Writes one of the most comprehensive and technically precise newsletters on LLM architectures and training. Publishes on Substack (magazine.sebastianraschka.com) and maintains open-source from-scratch implementations of major LLM architectures.

## Key Contributions

- **"The Big LLM Architecture Comparison"** — the most comprehensive survey of modern LLM architectures (DeepSeek V3 through GLM-5), covering 23+ models with side-by-side structural comparisons. See [[S — The Big LLM Architecture Comparison]].
- **"Components of a Coding Agent"** — breakdown of the six core building blocks of coding harnesses (repo context, prompt caching, tool use, context compaction, session memory, subagent delegation). Argues the harness matters as much as the model. See [[S — Components of A Coding Agent]].
- **"Build a Large Language Model (From Scratch)"** — book on LLM internals
- **"Build a Reasoning Model (From Scratch)"** — follow-up book (Early Access at Manning)
- **From-scratch implementations:** PyTorch implementations of Qwen3, OLMo 3, and other models without external LLM library dependencies
- **LLM Architecture Gallery** — visual overview of all covered architectures at sebastianraschka.com/llm-architecture-gallery/

## Key Observations

- Architecture is converging: "A lot of the secret sauce these days is in the training pipeline as well as the inference scaling strategies"
- DeepSeek V3's architecture is becoming the reference standard — adopted by Kimi K2, Mistral 3 Large, GLM-5
- Predicted shared experts and higher expert counts as future directions before Qwen3-Next confirmed them

## Why He Matters for the Wiki

Raschka's work is a primary source for understanding LLM architecture decisions. His side-by-side comparisons cut through marketing to show what's actually different between models. His from-scratch implementations verify architectural claims against actual code.

(Source: [[S — The Big LLM Architecture Comparison]])
