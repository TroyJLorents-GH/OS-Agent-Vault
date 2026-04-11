---
title: Retrieval-Augmented Generation (RAG)
type: concept
created: 2026-04-08
updated: 2026-04-08
sources: ["redhat-slms-scientific-research-2026-03-30"]
tags: [technique, inference, llm, rag, 2026]
---

# Retrieval-Augmented Generation (RAG)

A technique where a language model retrieves relevant information from external knowledge sources at inference time and uses it to ground its responses. Rather than relying solely on knowledge baked into model weights during training, RAG pulls in current, contextual data from structured and unstructured datasets.

## When to Use RAG vs. Fine-Tuning

| Dimension | RAG | [[Fine-tuning]] |
|-----------|-----|------------|
| What it changes | What the model *knows right now* | How the model *thinks and behaves* |
| Knowledge type | Dynamic, evolving, factual | Stable reasoning patterns, behavioral norms |
| Persistence | Ephemeral (per-query) | Permanent (in weights) |
| Data requirements | A retrievable corpus | Curated training examples |
| Compute cost | Low (inference-time retrieval) | Higher (training run required) |

## The Complementarity Thesis

[[Red Hat AI]] frames RAG and fine-tuning as complementary, not competing:

> "Fine-tuning encodes domain reasoning and behavior, while retrieval injects current, contextual knowledge. Together, they form a more complete and practical system for research environments."

This is a significant architectural insight. Many teams default to "just use RAG" because it's simpler than fine-tuning. The counterargument: RAG can tell a model *what*, but it can't teach it *how to reason* about that information in domain-appropriate ways. A clinical AI needs both the latest drug interaction data (RAG) and the ability to reason through contraindication logic (fine-tuning).

## Connections

- Complements [[fine-tuning]] — different layers of the same system
- Relevant to [[domain-specific AI]] as one of two essential components
- [[Small language models]] benefit especially from RAG because their smaller weight capacity means they can't store as much knowledge — retrieval compensates
- Troy's wiki system (this vault) is itself a form of manually-curated RAG: structured knowledge that an LLM retrieves and reasons over

(Source: [[redhat-slms-scientific-research-2026-03-30]])
