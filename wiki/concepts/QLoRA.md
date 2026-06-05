---
title: QLoRA (Quantized LoRA)
type: concept
created: 2026-06-04
updated: 2026-06-04
sources: ["redhat-slms-scientific-research-2026-03-30"]
tags: [technique, training, fine-tuning, inference, llm, "2026"]
---

# QLoRA (Quantized LoRA)

A memory-extreme variant of [[LoRA]]: the frozen base model is loaded in **4-bit precision** while small LoRA adapters train in full precision. This collapses the memory needed to fine-tune large models, enabling it on a **single consumer-grade GPU**. Introduced in the [[Fine-Tuning]] pipeline; this page covers what's distinct from plain LoRA.

## What QLoRA adds over LoRA

- **4-bit base, full-precision adapters** — the large frozen weights (the memory bottleneck) sit in 4-bit; gradients flow only through the small high-precision adapters. You get most of full fine-tuning quality at a fraction of the VRAM.
- **Democratization** — fine-tuning a model that previously required multiple datacenter GPUs becomes possible on one prosumer card. This is the technique behind much of the open-weights [[Fine-Tuning]] community.
- **Quantization is for *training* memory** — note the parallel but separate use of 4-bit at *inference* (e.g. [[Gemma]] 4 quantized for edge/RTX). Same tool (low precision), two different goals: QLoRA shrinks training memory; inference quantization shrinks serving cost ([[Inference Economics]]).

## Trade-offs

- **Slight quality/precision cost** vs full-precision LoRA, usually small and worth it for the memory savings.
- **Slower per-step** than non-quantized training (dequantization overhead), but feasible where full fine-tuning is simply impossible.
- Adapters can still be **merged** into a dequantized base or **kept swappable** (see [[LoRA]]).

## Connections

- [[LoRA]] — the base technique QLoRA quantizes
- [[Fine-Tuning]] — parent pipeline; fine-tuning vs RAG vs prompting
- [[small language models]] — QLoRA makes domain SLMs trainable cheaply
- [[Inference Economics]] — contrast: quantization for serving cost, not training memory
- [[Gemma]] — 4-bit quantization at inference time (the other use of low precision)

(Source: [[redhat-slms-scientific-research-2026-03-30]])
