---
title: Domain-Specific AI
type: concept
created: 2026-04-08
updated: 2026-04-08
sources: ["redhat-slms-scientific-research-2026-03-30"]
tags: [llm, slm, fine-tuning, technique, strategy, "2026"]
---

# Domain-Specific AI

The practice of building AI systems that are specialized for a particular domain rather than relying on general-purpose frontier models. The core thesis: **general competence is not domain expertise**, and for mission-critical applications, the model needs to know the field at the level of a trained expert.

## The Argument Against Defaulting to Frontier Models

The temptation in any new AI deployment is to start with a general-purpose frontier model (GPT-4, Llama 4, etc.). For exploratory work or general productivity, this reasoning holds. It breaks down the moment the work becomes:
1. **Domain-specific** — the model needs deep, specialized knowledge
2. **Sensitive** — data can't leave the institution
3. **High-stakes** — errors have real consequences

In research, the work almost always becomes all three.

## Implementation Path

1. Start with a base model (open weights, 1-10B parameters — a [[small language models|small language model]])
2. Generate training data via [[synthetic data generation]] ([[InstructLab]])
3. [[Fine-tuning|Fine-tune]] with [[LoRA]]/[[QLoRA]] on curated domain data
4. Augment with [[retrieval-augmented generation]] for dynamic knowledge
5. Evaluate against domain-specific benchmarks and behavioral rubrics
6. Deploy on versioned, governed infrastructure ([[Red Hat AI]])

## Domains Where This Pattern Applies

- **Clinical AI** — health counseling, drug interactions, diagnostic support
- **Drug discovery** — protein folding literature, molecular modeling
- **Financial services** — regulatory reasoning, risk classification
- **Oil & gas** — subsurface data, reservoir modeling
- **Cybersecurity** — threat analysis without internet-trained biases
- **Legal** — regulatory compliance, case law reasoning

## Strategic Implications

The institutions and companies that will move fastest are those that **train domain experts, not adopt general assistants.** This has implications for Troy's projects:
- [[agent-os]] — could the agent framework support domain-specific model switching?
- [[job-nexus]] — a career domain AI needs fine-tuned understanding of job markets, resume patterns, and hiring dynamics
- [[peptide-app]] — health/peptide domain knowledge requires expert-level precision

## Connections

- Implemented via [[small language models]] + [[fine-tuning]] + [[retrieval-augmented generation]]
- [[Model reproducibility]] is essential for domain-specific deployments in research
- [[InstructLab]] solves the data scarcity problem for niche domains
- Relates to the broader [[scaling laws]] debate — when does scale matter vs. specialization?

(Source: [[redhat-slms-scientific-research-2026-03-30]])
