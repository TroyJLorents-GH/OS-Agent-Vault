---
title: "S — Henry: The AI Worker That Does Real IT Work (9 Enterprise AI Predictions for 2026)"
type: source
created: 2026-06-03
updated: 2026-06-03
sources: ["Henry — The AI Worker that does real IT work"]
tags: [agents, product, prediction, strategy, policy, "2026"]
---

# S — Henry: The AI Worker That Does Real IT Work

**Author:** Maor Ezer (Co-Founder & CEO, ai.work) · **Publisher:** ai.work blog · **Created:** 2026-05-28 · **Type:** Vendor thesis / enterprise predictions
[Source article](../../raw/Henry%20%E2%80%94%20The%20AI%20Worker%20that%20does%20real%20IT%20work.md) · Original URL: ai.work/blog/top-enterprise-ai-predictions-for-2026

> Vendor content. ai.work makes **[[Henry]]**, an "AI worker" for IT. Read the predictions as a thesis the company is selling against — directionally useful, but self-interested. Cited for the [[AI Workforce]] framing.

## Core thesis

The gap between what AI *could* do and what it takes to make it work inside an enterprise is finally closing — not because LLMs leapt forward, but because companies now understand AI must be implemented as a **workforce layer that executes work**, not a feature bolted onto tools. The macro trend: **AI stops being a tool and becomes the operating model.** "2026 won't be the year AI replaces jobs. It will be the year AI starts doing real work — reliably, safely, visibly, and at scale."

## The 9 predictions (grouped into 4 shifts)

**The Human Shift**
1. **AI transformation accelerates bottom-up** — practitioners in IT/HR/Finance/Ops/Security start training, supervising, and co-working with AI directly. Compresses timelines from years to quarters.
2. **Skills are redistributed between humans and AI** — jobs reshape, not just reduce. AI takes routine/structured work (approvals, data extraction, system updates, triage, provisioning); humans keep contextual/creative/cross-functional work (architecture, exception handling, policy, security review, governance). See [[AI and Economic Displacement]].

**The Operating Shift**
3. **Labor and technology budgets merge** — CFOs ask "what portion of this workload should be humans vs autonomous agents?" — financially, not philosophically. Trapped labor costs shift into automation/AI-ops budgets; capacity grows without headcount.

**The Architectural Shift**
4. **SaaS + AI gives way to AI-native platforms** — systems designed to reason/act/adapt/learn across environments beat "AI features on legacy architecture." AI must behave like an employee: logging into apps, reading/writing data, handling exceptions, working across **5–15 systems per workflow**.
5. **The system of action breaks free from the system of record** — systems of record (HRIS, ERP, CRM, ITSM) stay the source of truth; AI becomes the **system of action** executing across them. Mirrors compute/storage, microservices/monolith, CDP/CRM separations. Detailed in [[AI Workforce]].
6. **Agent orchestration becomes an organizational priority** — enterprises will run *dozens* of agents by end-2026. Uncoordinated agents bring risk, duplication, audit blind spots, security gaps. Demand for a **horizontal orchestration layer** (cross-agent comms, policy enforcement, identity/access, logging, escalation, rollback) — "the new middleware of the enterprise."
7. **Demand for self-learning, self-evolving systems** — AI that learns from real work/logs, adapts as processes change, self-heals failing sequences, updates skills as tools evolve.

**The Execution Shift**
8. **Autonomous agents handle real end-to-end work** — collect/validate inputs, execute multi-step tasks across systems, handle branching + exceptions, verify completion, update records, escalate only when needed. Two design patterns: **human-in-the-loop becomes purposeful, not protective**; **AI executes skills, not monolithic workflows** (modular, composable).
9. **Internal AI builds slow down** as enterprises face the true cost of DIY AI (fragmented integrations, niche expertise, automation decay, constant refactoring). Shift to **hybrid**: build where it differentiates, buy productized platforms where it accelerates.

## Notable framings worth keeping

- **"System of action" vs "system of record"** — clean architectural vocabulary for where agents sit relative to ERP/CRM. (See [[AI Workforce]].)
- **Labor/tech budget merge** — the financial mechanism behind agent adoption; sharper than generic "AI ROI" talk.
- **"AI executes skills, not monolithic workflows"** — converges with the [[Agent Harness and Scaffolding]] definition of *skills* as portable, on-demand task packages.
- **Orchestration layer as new middleware** — matches the **orchestrator** role in the agent glossary, scaled to the enterprise.

## Connections

- [[Henry]] — the product embodying the thesis
- [[AI Workforce]] — primary concept distilled from this source
- [[AI and Economic Displacement]] — "jobs reshape not reduce," skills redistribution, budget merge
- [[Agentic AI]] — enterprise deployment of autonomous agents at scale
- [[Agent Harness and Scaffolding]] — "skills not workflows," orchestrator, human-in-the-loop
- [[Autonomous Agent Workflows]] — verify-completion / escalation patterns echo evaluator-loop and Stop-hook design
- [[AI Operating System]] — "AI as the operating model" rhymes with the enterprise AI OS layer

## Open questions / tensions

- **Vendor incentive** — every prediction conveniently routes to "buy an AI-native platform like ours." Prediction 9 (DIY AI is too expensive) is the most self-serving. Weigh accordingly.
- **"Reshape not reduce" vs displacement data** — ai.work's optimistic "jobs elevate" framing sits in direct tension with the 81K study, where job/economy concern was the *strongest* predictor of negative AI sentiment (see [[AI and Economic Displacement]]). Same trend, opposite emotional valence. Flagged on both pages.
- **Orchestration standard?** — if every enterprise needs an orchestration layer, who owns it (cloud vendors, ITSM incumbents, startups)? Land-grab in progress.
- **Reliability bar** — "verify completion, escalate only when necessary" assumes agents reliable enough to trust end-to-end. Current agent success rates (20%→77.3% per [[S — AI Technology Trends 2026 Key Developments]]) suggest this is aspirational for many workflows.
