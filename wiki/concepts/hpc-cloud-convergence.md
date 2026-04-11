---
title: HPC-Cloud Convergence
type: concept
created: 2026-04-08
updated: 2026-04-08
sources: ["redhat-slms-scientific-research-2026-03-30"]
tags: [compute, infrastructure, training, inference, scientific-research, 2026]
---

# HPC-Cloud Convergence

The architectural shift toward merging traditional high-performance computing (HPC) infrastructure with modern cloud-native Kubernetes environments into a unified AI platform. Previously theoretical, now becoming operational via technologies like Slurm-on-Kubernetes.

## The Problem: Siloed Infrastructure

Most research institutions operate two separate compute environments:

| Environment | HPC (Slurm) | Cloud-Native (Kubernetes) |
|-------------|-------------|---------------------------|
| Purpose | Large-scale batch jobs — training, simulations | Containerized services, MLOps, inference |
| Scheduler | Slurm | Kubernetes scheduler |
| Strengths | Raw compute power, long-running jobs | Reproducible pipelines, dynamic scaling |
| Weakness | No dynamic scheduling for smaller workloads | Not designed for massive batch jobs |

**Consequences of fragmentation:**
- GPUs sit idle between large simulation jobs (no mechanism to schedule smaller inference workloads on unused capacity)
- Moving artifacts between environments requires manual intervention or brittle glue scripts
- Fine-tuned models sit on researcher workstations instead of being served as shared resources
- Reproducing results at collaborating institutions means rebuilding environments from scratch

## The Convergence

[[Red Hat AI]] + [[OpenShift AI]] + [[NVIDIA]] + Slurm-on-Kubernetes enables:
- Training runs and inference serving on the same cluster
- Dynamic GPU scheduling across workload types
- Containerized, reproducible pipelines that span both paradigms
- Shared model serving as an institutional capability

## Why It Matters Now

Gen AI has accelerated the urgency. Language models are now accelerating every phase of the scientific cycle — literature synthesis, code generation, experiment design, instrument interaction. But deploying these models in research environments (tuning, serving, governing, making them available to non-ML-engineers) requires infrastructure most institutions haven't built yet.

## Connections

- Enables institutional deployment of [[domain-specific AI]] and [[small language models]]
- [[Red Hat AI]] is the platform implementing this convergence
- Part II of the source series will cover the operational details (model serving, resource scheduling)
- The "shared institutional AI services" concept — turning customized models from isolated artifacts into platform capabilities

(Source: [[redhat-slms-scientific-research-2026-03-30]])
