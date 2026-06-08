---
title: Overview
type: overview
created: 2026-06-04
updated: 2026-06-04
sources: []
tags: [overview, llm, agents, compute, y2026]
---

# Wiki Overview

High-level synthesis of the whole vault as of mid-2026. Every bold theme links out to the pages that carry the detail. Updated when a source materially shifts the big picture.

## The one-sentence state of AI (mid-2026)

Raw model capability is **converging and commoditizing**, so the action has moved to three layers around the model: the **harness** that turns a model into an agent, the **inference economics** that decide what's affordable to run, and the **org/labor reorganization** as agents start doing real work. Underneath it all, a **capital supercycle** is building the compute — and a **public backlash** is starting to push back.

## 1. The model landscape is converging

Frontier models (Claude, GPT-5.x, [[Gemini]]) and open weights are reaching rough parity on raw capability. See [[AI Industry Landscape April 2026]] and [[Open-Source AI]].

- **Architecture has stabilized** around the [[Transformer Architecture]] with incremental refinements: [[Mixture of Experts]] (sparse routing, single-GPU frontier inference), [[Multi-Head Latent Attention]], [[Sliding Window Attention]], [[Multi-Token Prediction]]. Documented in [[S — The Big LLM Architecture Comparison]].
- **Open weights hit parity** — [[Gemma]] 4, Qwen, GLM-5, gpt-oss, Mistral under Apache 2.0/MIT. License liberation is as important as the weights.
- **Tiering by economics** — [[Gemini]]'s sub-quarterly Flash cadence shows models are now continuous software products, with cheap tiers optimized for the high-volume workloads that dominate real usage.
- **Implication:** when models converge, *what wraps them* decides the winner → section 2.

## 2. The harness era: agents = model + harness

The single most important reframing in the wiki: **Agent = Model + Harness** (model ≠ harness ≠ product). As models converge, the harness is the differentiator. Core pages: [[Agent Harness and Scaffolding]], [[Context Engineering]], [[Coding Agent Architecture]], [[Agentic AI]], [[Autonomous Agent Workflows]].

- "A lot of apparent model quality is really context quality" — [[Context Engineering]] and the 6-component [[Coding Agent Architecture]].
- [[Claude Code]] is the canonical "agentic harness around Claude" — and the commercial proof ($2.5B/yr).
- Execution patterns are maturing: [[Autonomous Agent Workflows]] (`/goal`, `/loop`, Stop hooks, evaluator-loop), bounded sub-agents, orchestrators.
- Tooling standard: MCP at 97M installs ([[Agentic AI]]).

## 3. Inference economics + the capex supercycle

The cost center shifted from training to **serving**. See [[Inference Economics]] — the frame underneath almost everything.

- This drives MoE adoption, the [[AI Operating System]] stack (Kubernetes + vLLM + llm-d), pricing collapse, and cheap model tiers.
- **Capital is treating AI infra as strategic infrastructure, not software** — [[AI Capex Buildout]]: [[Cerebras]] IPO (~$95B), [[NVIDIA]] (~$5.5T), memory/data-center deals. Utility-style capital, not SaaS multiples.
- **Constraints tightening:** memory bandwidth, energy, land/permits, labor (Samsung strike), and sovereign chip access (Huawei/GLM-5 zero-Nvidia training).

## 4. AI as a workforce — the labor reorganization

Agents are moving from "draft, human executes" to **doing end-to-end work**. See [[AI Workforce]] and its product instance [[Henry]].

- **System of action vs system of record** — AI executes across ERP/CRM/ITSM while those stay the source of truth.
- **Labor + tech budgets merge** — CFOs ask "humans or agents?" financially.
- **The tension:** vendors frame this as "jobs reshape, not reduce"; the 81K study found job/economy fear is the *strongest* predictor of negative AI sentiment. Same trend, opposite valence — flagged on [[AI and Economic Displacement]] and [[AI as equalizer]].

## 5. The human dimension (the 81K study)

Anthropic's 80K-person study ([[S — anthropic-81k-interviews-2026-03-18|81K study]]) grounds how real people experience AI:

- **[[light and shade of AI]]** — benefits and harms are entangled within the same person, not split across camps.
- **[[sycophancy]]** (too agreeable), **[[cognitive atrophy]]** (skill loss, worst in institutional settings), **[[ai-emotional-support]]** (most entangled tension).
- **[[AI as equalizer]]** — disproportionate empowerment in the developing world and for people with disabilities.

## 6. Safety, governance, geopolitics

- **[[alignment]]** is the throughline of [[Anthropic]]'s work; user-reported [[sycophancy]] and overrestriction are alignment problems in the wild.
- **[[AI Regulation]]** — EU AI Act (Aug 2026), US state laws, explainability as a product feature.
- **[[AI in Warfare]]** — frontier models named warfare-grade (Anthropic Mythos); dual-use tension with the safety mission.
- **[[AI Data Center Backlash]]** — 71% of US adults oppose local data centers; trust/permitting is now a binding constraint.
- **Litigation/power** — Musk v. OpenAI; OpenAI–Apple platform friction (see [[OpenAI]], [[Apple]], [[Elon Musk]]).

## 7. The infrastructure & memory layer

- [[AI Operating System]] — the standardized inference layer (the "Linux of AI inference").
- [[AI Memory Systems]] — store-and-retrieve vs compile-and-maintain; [[MemPalace]] as the high-scoring reference; long-term memory ties into [[Context Engineering]].
- [[Physical AI]] — the next compute-demand cycle (robotics, AV, NVIDIA Isaac/Alpamayo).
- [[domain-specific-ai]] + [[small language models]] + [[Fine-Tuning]] ([[LoRA]]/[[QLoRA]]) — the specialization stack.

## 8. Troy's projects (applied lens)

- [[agent-os]] — OS-style layer for agents (scaffold; needs spec). Closest external analog: [[AI Workforce]]/[[Henry]].
- [[job-nexus]] — resume↔JD matching (shipped); Azure AI Search semantic matching → [[domain-specific-ai]] + [[AI as equalizer]] + [[retrieval-augmented-generation]].
- [[peptide-app]] — health dosing tracker/scheduler (deployed); least AI-centric, candidate [[domain-specific-ai]] health layer.
- [[automateflows]] — Troy's **company** selling AI/automation implementation (deployed); the services edge of [[AI Workforce]], likely [[n8n]]-delivered. Closest analog: [[Henry]] at the SMB end.

## Open threads to watch

- ✅ **Post-I/O reconciliation (resolved 2026-06-04)** — the leaked "3.2 Flash" shipped as **Gemini 3.5 Flash** at I/O; "Flash beats Pro" confirmed on real benchmarks. See [[Gemini]].
- ✅ **Musk v. OpenAI (resolved 2026-05-18)** — all claims dismissed on statute of limitations; [[OpenAI]] cleared, Musk appealing. Restructuring path toward a rumored $1T IPO is open.
- ✅ **Samsung strike (resolved 2026-05-20)** — averted via government-mediated deal (~74% approval); memory-supply risk contained, pay tensions persist.
- **Who owns the enterprise agent orchestration layer** ([[AI Workforce]])?
- **Reliability gap** — agent success rates (20%→77.3%) vs the "end-to-end autonomous" promise.
- **Gemini 3.5 Pro** GA (~June 2026) — does the Pro tier reclaim a clear lead, or has Flash permanently compressed the ladder?
- **Pre-release leak calibration** — the 3.2→3.5 miss is a useful datapoint on weighting AI leaks (right thesis, wrong specifics).
