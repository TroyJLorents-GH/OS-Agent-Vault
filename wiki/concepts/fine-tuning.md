---
title: Fine-Tuning
type: concept
created: 2026-04-08
updated: 2026-04-08
sources: ["redhat-slms-scientific-research-2026-03-30"]
tags: [technique, training, llm, slm, fine-tuning, "2026"]
---

# Fine-Tuning

The process of adapting a pre-trained model's weights on domain-specific data to encode specialized knowledge, behavioral alignment, and reasoning patterns. Fine-tuning is distinct from prompting — it changes what the model *is*, not just what it's told to do.

## What Fine-Tuning Encodes

Fine-tuning doesn't just add knowledge — it encodes **behavioral alignment and domain reasoning patterns** into model weights:
- A clinical communication rubric
- The structured reasoning pattern of an epidemiological analysis
- The schema of a geophysical dataset

> "These are not things you can prompt into a model reliably. They're things you train it to do."

This is the key distinction from [[retrieval-augmented generation]]: RAG injects knowledge at inference time, fine-tuning changes the model's reasoning behavior permanently.

## Efficient Methods

### LoRA (Low-Rank Adaptation)
Adapts a base model by training small low-rank matrices instead of updating all weights. Dramatically reduces compute cost compared to full fine-tuning while preserving most of the performance gains.

### QLoRA (Quantized LoRA)
Combines LoRA with model quantization — the base model is loaded in reduced precision (4-bit), and only the LoRA adapters are trained in full precision. Even more compute-efficient, enabling fine-tuning on consumer-grade GPUs.

### Why Not Full Fine-Tuning?
Full fine-tuning of large models is computationally expensive and often unnecessary. In shared GPU environments where training jobs compete for resources, the efficiency difference between LoRA/QLoRA and full fine-tuning can be operationally significant.

## Fine-Tuning + RAG: Complementary, Not Competing

A nuanced position from [[Red Hat AI]]:
- **Fine-tuning** encodes domain reasoning and behavior
- **[[Retrieval-augmented generation]]** injects current, contextual knowledge

Together they form a more complete system. This challenges the common framing where RAG is positioned as the "simpler alternative" to fine-tuning. The argument is that you need both — fine-tuning for *how* the model thinks, RAG for *what* it knows right now.

## The Full Pipeline

On [[Red Hat AI]], the customization pipeline is:
1. Data preparation (curated domain data)
2. [[Synthetic data generation]] via [[InstructLab]] (expand from small golden datasets)
3. Fine-tuning via LoRA/QLoRA
4. Evaluation against domain-specific test sets and behavioral rubrics
5. Versioned deployment on [[OpenShift AI]]

## Connections

- Core enabler of [[small language models]] — makes SLMs practical for domain tasks
- Complementary to [[retrieval-augmented generation]] — different roles in the stack
- [[InstructLab]] solves the data scarcity problem that would otherwise block fine-tuning
- [[Model reproducibility]] depends on versioned fine-tuned checkpoints, not API calls
- Relevant to Troy's projects: any project deploying AI for a specific domain should consider fine-tuning vs. prompting vs. RAG

(Source: [[redhat-slms-scientific-research-2026-03-30]])
