---
title: Red Hat AI
type: entity
created: 2026-04-08
updated: 2026-04-08
sources: ["redhat-slms-scientific-research-2026-03-30"]
tags: [product, red-hat, training, inference, fine-tuning, compute, "2026"]
---

# Red Hat AI

Red Hat's enterprise AI platform, built on [[OpenShift AI]] and designed to provide the full model lifecycle — from data preparation through [[fine-tuning]], serving, and evaluation — on-premises or in hybrid environments.

## Key Capabilities

- **Model customization pipeline:** data ingestion → [[synthetic data generation]] (via [[InstructLab]]) → [[fine-tuning]] (via [[LoRA]]/[[QLoRA]]) → evaluation → serving
- **[[Retrieval-augmented generation]]** for dynamic knowledge injection at inference time
- **[[Training Hub]]** library for orchestrated, reproducible training jobs on OpenShift AI
- **Model versioning and governance:** full control over model checkpoints, training artifacts, and serving configurations — critical for [[model reproducibility]]
- **[[HPC-cloud convergence]]:** bridges traditional Slurm-based HPC clusters with Kubernetes-native AI workloads via Slurm-on-Kubernetes

## Strategic Position

Red Hat AI is positioned as the platform that closes the gap between "researchers want to use AI" and "institutions have the infrastructure to support it." The pitch is that research institutions need more than model serving — they need the ability to customize, version, evaluate, and govern [[domain-specific AI]] models on their own infrastructure.

Partners: [[NVIDIA]] (GPU infrastructure), open source community ([[InstructLab]])

## Relevance

For Troy's projects: Red Hat AI's architecture — the full customization pipeline with versioned models, evaluation gates, and on-prem serving — is a reference pattern for how [[domain-specific AI]] tools could be built and deployed. The emphasis on making fine-tuning accessible to non-ML-engineers is a design principle worth carrying forward.

(Source: [[redhat-slms-scientific-research-2026-03-30]])
