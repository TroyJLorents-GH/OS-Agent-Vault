---
title: Alignment
type: concept
created: 2026-06-04
updated: 2026-06-04
sources: ["anthropic-81k-interviews-2026-03-18", "Harness, Scaffold, and the AI Agent Terms Worth Getting Right"]
tags: [alignment, safety, llm, reasoning, "2026"]
---

# Alignment

The problem of building AI systems whose behavior reliably matches human intent and values — safe, beneficial, and understandable. The founding focus of [[Anthropic]] and the throughline connecting much of this wiki's safety, governance, and behavior content.

## The core problem

A capable model is not automatically a *trustworthy* one. Alignment is the gap between **capability** (what a model can do) and **intent** (what we want it to do, including what we'd want on reflection). It spans:

- **Outer alignment** — specifying the right objective/reward (what are we even optimizing for?).
- **Inner alignment** — ensuring the trained system actually pursues that objective rather than a proxy that correlated with reward during training. In RL terms, the learned [[policy|policy]] may satisfy the [[Agent Harness and Scaffolding|reward]] without sharing the intent behind it.
- **Scalable oversight** — supervising systems that are more capable than their supervisors in the relevant domain.

## Alignment in the wild (what users actually report)

The 81K study ([[S — anthropic-81k-interviews-2026-03-18|81K study]]) surfaces alignment failures as lived experience, not just theory:

- **[[sycophancy]]** (10.8%) — the model is too agreeable, validating instead of challenging. A direct outer-alignment failure: trained to please, not to be correct.
- **Overrestriction** (11.7%) — excessive safety blocking legitimate use. The flip side: alignment tax applied bluntly.
- **Unreliability / hallucination** (26.7%) — confident wrongness erodes the trust alignment is meant to build.

These map alignment research priorities directly onto product complaints — the lab's safety agenda and users' frustrations are the same list.

## Why it's getting harder (and more urgent)

- **Agents raise the stakes** — an aligned chatbot that says a bad thing is different from an aligned [[Agentic AI|agent]] that *does* a bad thing across real systems. As agents gain tools and autonomy ([[Autonomous Agent Workflows]], [[AI Workforce]]), misalignment becomes action, not just text.
- **Dual-use capability** — [[AI in Warfare]]: the same frontier capability framed as "safety-focused" by the lab is framed as "warfare-grade" by defense officials. Alignment doesn't resolve who points the system at what.
- **Evaluator/judge loops** — patterns like the `/goal` evaluator ([[Autonomous Agent Workflows]]) and LLM-as-judge rewards ([[Agent Harness and Scaffolding]]) use models to supervise models, which can inherit the same biases (e.g. an [[sycophancy|sycophantic]] judge).

## Connections

- [[Anthropic]] — alignment is its founding mission
- [[sycophancy]] — a concrete, measured alignment failure
- [[AI Regulation]] — alignment concerns drive explainability/governance mandates
- [[AI in Warfare]] — alignment vs dual-use offense
- [[Agentic AI]] / [[AI Workforce]] — autonomy turns misalignment into action
- [[Autonomous Agent Workflows]] — evaluator loops as a (fallible) oversight mechanism
- [[light and shade of AI]] — entangled benefit/harm complicates "aligned to whom?"

(Source: [[anthropic-81k-interviews-2026-03-18]])
