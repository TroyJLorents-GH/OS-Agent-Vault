---
title: "Part I: AI for scientific research: The power of small language models"
source: "https://www.redhat.com/en/blog/ai-scientific-research-power-small-language-models"
author:
  - "[[Daniel Domkowski]]"
  - "[[O'Neill Joseph]]"
published: 2026-03-30
created: 2026-04-08
description: "Discover how small language models (SLMs) and a unified AI platform accelerate AI in scientific research by overcoming compute silos and data privacy challenges, and how Red Hat AI enables research institutions to build domain-specific, reproducible models that transform complex workflows."
tags:
  - clippings
  - llm
  - slm
  - fine-tuning
  - compute
  - training
  - inference
  - red-hat
  - scientific-research
  - domain-specific-ai
---
Scientific research has a compute problem. Not a shortage of ideas, but a shortage of infrastructure that can keep up with them. It also has a platform problem—how can we deliver [generative AI](https://www.redhat.com/en/topics/ai/what-is-generative-ai) (gen AI) capabilities through the right architecture and operating model so institutions can provide access without handing every user unrestricted access to expensive models and runaway spend.

## What are small language models?

[Small language models](https://www.redhat.com/en/topics/ai/llm-vs-slm) (SLMs) are usually domain-specific AI models developed with significantly fewer parameters than their massive counterparts, typically ranging from 1 billion to 10 billion parameters. While [large language models](https://www.redhat.com/en/topics/ai/what-are-large-language-models) (LLMs) function like vast, general-purpose libraries, SLMs are specialized models trained on high-quality, curated datasets to excel at specific tasks. This reduced scale allows them to run efficiently on local devices or edge infrastructure, offering a cost-effective way to improve data privacy and reduce latency. By focusing on narrow domains rather than the entire internet, these models provide a strategic pathway for enterprises to deploy gen AI without the massive computational overhead of traditional models.

## Using AI for scientific research

The modern research workflow spans an enormous range of compute demands. Training a domain-specific language model on clinical data looks nothing like running a molecular dynamics simulation, which looks nothing like serving a fine-tuned model to a team of researchers in real time. These workloads live in different paradigms—traditional high-performance computing (HPC) for the heavy batch jobs, cloud-native Kubernetes for [containerized services and MLOps](https://www.redhat.com/en/resources/mlops-architecture-openshift-infographic), and an emerging middle layer where gen AI is accelerating every phase of the scientific loop. For years, researchers and platform engineers have juggled these worlds separately—different clusters, different schedulers, different teams.

The case for a unified AI platform is no longer theoretical, it's operational. The combination of Red Hat OpenShift, [Red Hat AI](https://www.redhat.com/en/products/ai/enterprise), NVIDIA, and the emerging capabilities around [Slurm-on-Kubernetes](https://slurm.schedmd.com/kubernetes.html) is finally making that platform real for research institutions across universities, federally funded research and development centers (FFRDCs), national labs, medical centers, and research-intensive industries.

Here we'll lay out how those pieces fit together, and why domain-specific model customization is the capability that transforms the platform from useful to indispensable.

## Why research can no longer afford siloed infrastructure

Most research institutions operate 2 largely separate compute environments. On one side, an HPC cluster running Slurm, which is purpose-built for large-scale, long-running batch jobs—such as training runs, simulations, or data synthesis at scale. On the other side, there's a growing cloud-native footprint for containerized workflows, reproducible pipelines, and AI-driven applications. These environments share physical hardware, but almost nothing else—they have different schedulers, different job submission interfaces, different resource accounting, and different operational teams.

The result is fragmentation that costs time, money, and reproducibility. GPU clusters sit idle between large simulation jobs because there's no mechanism to dynamically schedule smaller inference workloads against unused capacity. Experiment pipelines that depend on moving artifacts between the HPC environment and the Kubernetes environment require manual intervention or brittle glue scripts. Fine-tuned models sit on a researcher's workstation rather than being served as a shared resource. And when a collaborating institution wants to reproduce a result, they're rebuilding an environment from scratch rather than pulling a container image.

As [I've written previously on this topic](https://medium.com/@dan.domkowski/the-ai-first-research-platform-merging-hpc-cloud-native-to-deliver-a-unified-research-foundation-cab1f9054974), the pace, scale, and complexity of modern AI-first research demand infrastructure that is powerful, flexible, reproducible, and shareable all at once. Neither HPC alone nor Kubernetes alone delivers that. Only a converged platform does.

Gen AI has accelerated the urgency. Language models are now accelerating the slowest parts of the scientific cycle—reading and synthesizing literature, generating and debugging analysis code, designing experiments, and interacting with instruments. National laboratories describe LLM-based agents as tools that expand the pace and scope of discovery in ways that compound over time. But deploying those models in research environments (tuning them, serving them, governing them, and making them available to teams who aren't machine learning (ML) engineers) requires infrastructure that most research institutions haven't yet built.

That is the gap Red Hat AI is designed to close.

## 3 benefits of SLMs for scientific research

Before getting into platform architecture, it's worth spending time on what makes AI useful in research contexts specifically because this shapes every infrastructure decision that follows.

The temptation in any new AI deployment is to start with a general-purpose frontier model. GPT-4, Llama 4 Maverick, or a comparable large model from a cloud API. The reasoning is intuitive—these models know a lot, they're capable of broad reasoning, and they require minimal setup. For exploratory work or general productivity, that reasoning holds.

It breaks down the moment the work becomes domain-specific, sensitive, or high-stakes. And in research, it almost always becomes all 3. So, what are the benefits of SLMs?

### 1\. SLMs are more focused and predictable

Consider a clinical AI assistant built to guide health counseling in underserved communities—a real use case we've been working on with researchers in a university school of medicine. A general-purpose model can hold a conversation. It can answer broad health questions. What it cannot reliably do is apply the CDC Medical Eligibility Criteria correctly across hundreds of contraindication edge cases, maintain an appropriate therapeutic communication style across a multi-turn conversation, flag crisis scenarios accurately, and refuse to provide guidance outside its clinical scope, all at once, at the accuracy thresholds that patient safety requires.

The problem is not that the model is too small. The problem is that the model's knowledge is too diffuse, and its behavior too unpredictable, for the mission it's being asked to serve. General competence is not the same as domain expertise. In clinical AI, that distinction is not academic. It's a patient safety issue.

### 2\. SLMs can be trained on limited, higher quality, data

Another advantage of domain-specific models is how effectively they learn from limited data. Many research domains simply do not have massive labeled datasets available due to privacy constraints, regulatory limits, or the rarity of the phenomena being studied. Smaller or more focused base models can often adapt more efficiently from carefully curated datasets, allowing the training signal to concentrate on the terminology, reasoning patterns, and edge cases that matter most. The result is higher accuracy on specialized tasks with significantly lower compute and data requirements. This is a critical advantage for research institutions where both GPU capacity and labeled data are scarce.

This pattern repeats across research domains. In financial services research, a general model doesn't carry the regulatory context needed to reason accurately about risk classification. In oil and gas, it doesn't understand the operational semantics of subsurface data well enough to add real value to reservoir modeling. In [cybersecurity research](https://www.redhat.com/en/blog/4-use-cases-ai-cyber-security), a model that has been trained on the open internet carries biases and knowledge gaps that can actively mislead analysis. In drug discovery, the difference between a model that understands protein folding literature deeply and one that knows a little about everything is the difference between a useful research accelerant and an expensive distraction.

### 3\. SLMs are more controllable and deterministic

Research also has a reproducibility problem. Results must be verifiable, repeatable, and attributable to a specific methodology. When using external APIs, the underlying model can change without notice, making it difficult or impossible to reproduce the same output over time. Running models on [Red Hat OpenShift AI](https://www.redhat.com/en/products/ai/openshift-ai) gives research teams complete control over model versions, training artifacts, and serving configurations. A specific model checkpoint can be versioned, deployed, and revisited months later with the same behavior and performance characteristics.  
  

This control is fundamental to scientific integrity. Open models, versioned pipelines, and containerized execution environments allow institutions to move from best effort replication to true reproducibility, a requirement in serious research.

"Good enough" without domain expertise is not good enough for research. The researchers who are going to get the most out of language models are those who have models that actually know their field, not at a survey level, but at the level of a trained expert.

This is why an AI platform needs to support model customization in addition to model serving.

## Red Hat AI model customization: Building your domain expert

Red Hat AI provides a modular, scalable approach to model customization that is purpose-built for exactly this challenge. As detailed in [the building blocks for scalable and repeatable model customization](https://www.redhat.com/en/blog/red-hat-ai-modular-building-blocks-scalable-repeatable-model-customization), it includes the full pipeline from data preparation through fine-tuning, to serving and evaluation, all within the platform.

Effective model customization is not just about adding knowledge to a model, it's also about encoding behavioral alignment and domain reasoning patterns into model weights. This could include things like a clinical communication rubric, the structured reasoning pattern of an epidemiological analysis, or the schema of a geophysical dataset. These are not things you can prompt into a model reliably, they're things you train it to do.

Red Hat AI's approach to this is built around several key capabilities:

### Retrieval-augmented generation (RAG)

Not every problem requires training knowledge into model weights. In many research workflows, the most relevant information is dynamic, evolving, and stored across structured and unstructured datasets. This is where retrieval becomes a critical complement to fine-tuning. The platform supports [retrieval-augmented approaches](https://www.redhat.com/en/topics/ai/what-is-retrieval-augmented-generation) that allow models to access domain-specific knowledge at inference time, grounding responses in the latest research artifacts, documents, and datasets without requiring constant retraining. In practice, fine-tuning and retrieval are not competing approaches, they are complementary. Fine-tuning encodes domain reasoning and behavior, while retrieval injects current, contextual knowledge. Together, they form a more complete and practical system for research environments.

### InstructLab and synthetic data generation

Before you can fine-tune, you need data, and in many research domains, labeled training data is scarce. [InstructLab](https://www.redhat.com/en/topics/ai/what-is-instructlab), developed through the open source community and integrated into Red Hat AI, provides a framework for synthetic data generation that allows researchers to expand their training datasets from small golden datasets. For clinical research, where privacy constraints limit the availability of real patient conversations, synthetic generation from a curated set of expert-rated examples is not just convenient, but often the only viable path.

### LoRA and QLoRA for efficient fine-tuning

Full fine-tuning of large models is computationally expensive and often unnecessary. Low-rank adaptation techniques like [low-rank adaptation (LoRA) and its quantized variant QLoRA](https://www.redhat.com/en/topics/ai/lora-vs-qlora) allow researchers to adapt the behavioral properties of a base model on domain-specific data with a fraction of the compute cost of full fine-tuning. In a shared GPU environment where training jobs compete for resources, this efficiency difference can be operationally significant.

### Training Hub library

The orchestration of fine-tuning jobs (such as data ingestion, training run management, checkpoint management, evaluation) is managed through the [Training Hub library](https://github.com/Red-Hat-AI-Innovation-Team/training_hub) available for OpenShift AI. This provides a reproducible, auditable training pipeline that platform engineers can operate and researchers can use without needing to manage infrastructure. Training jobs become first-class workloads on the cluster, subject to the same scheduling, resource accounting, and namespace governance as inference workloads.

### Evaluation and iteration

Red Hat AI's model evaluation capabilities allow research teams to run their fine-tuned models against domain-specific test sets and behavioral rubrics before using them in production. For clinical applications where a specific accuracy threshold against safety criteria is a go/no-go condition, this evaluation step is non-negotiable.

The result of this pipeline is a fully customized model that belongs to your research team, not a cloud provider. A model that can be versioned, audited, and updated as domain knowledge evolves, that can run on-premises in environments where sending sensitive data to an external API is not acceptable, and that performs at the level the research demands.

As I've argued in [The Case for Fine-Tuning](https://medium.com/@dan.domkowski/the-case-for-fine-tuning-why-smaller-smarter-models-are-winning-in-mission-critical-ai-dfdca7bba93a): Frontier models are extraordinary reasoning engines. Fine-tuned models are mission instruments. In scientific research, the mission is specific. The instrument needs to match it.

## Closing thoughts

In the coming decade, the institutions that will move fastest will not simply adopt LLMs, they will build platforms to train smaller, more focused models to become true domain experts that can be integrated directly into the research workflow. This requires infrastructure that can bridge traditional HPC and modern cloud-native AI, provide governance over how models are trained and served, and allow researchers to iterate quickly without sacrificing reproducibility or cost control. This is the architectural shift currently underway, and platforms built on Red Hat OpenShift and [Red Hat AI](https://www.redhat.com/en/products/ai) are making it practical for research organizations to operate in this new model.

In our next article, we'll look at the other half of the equation—how these customized models are operationalized at scale. Model serving, resource scheduling across Slurm and Kubernetes, and the emerging concept of shared institutional AI services are what turn customized models from isolated research artifacts into a platform capability that accelerates discovery across an entire institution.