---
title: Agent OS
type: project
created: 2026-06-03
updated: 2026-06-03
sources: []
tags: [agent-os, agents, projects, "2026"]
---

# Agent OS

Troy's project exploring an **operating-system-style layer for AI agents**. This page is a scaffold assembled from how the rest of the wiki already references `agent-os` — the concrete spec, scope, and current status need Troy's direction (the wiki maintainer doesn't invent project details).

> **Status: scaffold / needs Troy input.** Filling the gaps below converts this from a hub of inbound links into a real project page.

## What the wiki already connects to Agent OS

Existing pages tie `agent-os` to four threads:

1. **Coding-agent patterns** — could integrate the harness/scaffold techniques from [[Coding Agent Architecture]] and [[Agent Harness and Scaffolding]] (model vs scaffold vs harness, context engineering, bounded sub-agents). (Ref: [[AI Coding Tools]])
2. **Workflow orchestration** — [[n8n]] floated as the glue layer between agents and external services. Maps to the **orchestrator** role and the enterprise "orchestration as new middleware" idea in [[AI Workforce]].
3. **Domain-specific model switching** — could the framework route between fine-tuned domain models? (Ref: [[domain-specific-ai]], [[small language models]])
4. **Inference infrastructure** — any agent-OS deployment benefits from the serving-stack thinking in [[AI Operating System]] and [[Inference Economics]] (vLLM, KV cache, quantization → viability and margins).

## Reference points (external)

- **[[Henry]] / [[AI Workforce]]** — a shipped instance of "agent as a labor layer that executes across 5–15 systems." Closest real-world analog to what Agent OS appears to aim at: system-of-action over systems-of-record, skills-not-monolithic-workflows, governed orchestration.
- **[[Claude Code]]** — reference harness design (`/goal`, Stop hooks, sub-agents, auto mode); see [[Autonomous Agent Workflows]].
- **[[AI Operating System]]** — the enterprise/infra meaning of "AI OS" (Kubernetes + vLLM + llm-d). Worth deciding whether Agent OS is *that* layer or sits above it.

## Open questions (for Troy)

- **Scope:** personal agent runtime, a product, or a framework/library? Single-user or multi-agent orchestration?
- **Relationship to this vault:** the repo is literally "OS Agent Vault" — is Agent OS the system that *operates on* this second brain, or a separate build?
- **Build vs assemble:** custom harness, or orchestrate existing CLIs (Claude Code, Codex) under an n8n/orchestrator layer?
- **Model strategy:** single frontier model, or domain-model routing per [[domain-specific-ai]]?
- **Relation to sibling projects:** how does it connect to `automateflows`, [[job-nexus]], [[peptide-app]]?

## Connections

- [[Agent Harness and Scaffolding]] — core design vocabulary
- [[AI Workforce]] / [[Henry]] — the labor-layer pattern Agent OS resembles
- [[Coding Agent Architecture]] — harness components to borrow
- [[AI Operating System]] — infra layer beneath/around it
- [[n8n]] — candidate orchestration glue
- [[Autonomous Agent Workflows]] — goal/loop/hook execution patterns
