---
title: LoRA (Low-Rank Adaptation)
type: concept
created: 2026-06-04
updated: 2026-06-04
sources: ["redhat-slms-scientific-research-2026-03-30"]
tags: [technique, training, fine-tuning, llm, y2026]
---

# LoRA (Low-Rank Adaptation)

A parameter-efficient fine-tuning (PEFT) method: instead of updating a model's full weight matrices, LoRA freezes them and trains small **low-rank adapter matrices** injected alongside. The detailed role of LoRA in the customization pipeline lives on [[Fine-Tuning]]; this page covers the technique-specific mechanics and serving implications not captured there.

## How it works (mechanics)

- For a frozen weight matrix `W`, LoRA learns a low-rank update `ΔW = B·A`, where `A` and `B` are much smaller (rank `r`, typically 8–64). Only `A` and `B` train.
- **Trainable parameters drop by ~10,000×** for large models — the gradient/optimizer state, which dominates fine-tuning memory, shrinks proportionally.
- **Rank `r` is the main knob:** higher rank = more capacity to adapt, more memory; low rank often suffices because task-specific adaptation is itself low-dimensional.

## Why it matters beyond cost

- **Adapters are composable and swappable** — a single frozen base model can host *many* LoRA adapters, one per domain/task, swapped at load time. This is the operational basis for serving many specialized behaviors from one base (relevant to [[domain-specific-ai]] and any [[agent-os]]-style model-routing layer).
- **Merge or keep separate** — adapters can be **merged** back into base weights for zero inference overhead, or **kept separate** to preserve swappability and auditability. Keeping them separate supports [[model-reproducibility]] (versioned adapters over opaque full checkpoints).
- **Shared-GPU friendliness** — in contended training environments, LoRA's small footprint is operationally decisive (Source: [[redhat-slms-scientific-research-2026-03-30]]).

## Relationship to QLoRA

[[QLoRA]] = LoRA on top of a **quantized** (4-bit) base, pushing fine-tuning onto consumer GPUs. LoRA is the adapter idea; QLoRA is the memory-quantization extension.

## Connections

- [[Fine-Tuning]] — parent technique and full pipeline context
- [[QLoRA]] — the quantized extension
- [[small language models]] — LoRA makes domain SLMs practical
- [[domain-specific-ai]] — multi-adapter serving from one base
- [[model-reproducibility]] — versioned adapters
- [[InstructLab]] — generates the synthetic data LoRA trains on

(Source: [[redhat-slms-scientific-research-2026-03-30]])
