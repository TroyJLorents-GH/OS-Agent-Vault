---
title: automateflows
type: project
created: 2026-06-05
updated: 2026-06-05
sources: []
tags:
  - automateflows
  - projects
  - business
  - agents
  - strategy
  - y2026
---

# automateflows

Troy's **company** — helps businesses with automation and AI implementation. Deployed (site live).

> **Status: deployed / operating.** This is a company, not just an app — it has a business dimension as well as a build. This page tracks both; consider a sibling page in `wiki/business/` if the revenue/GTM side grows enough to warrant its own.

## Problem + who for

Businesses know they should adopt AI/automation but lack the in-house skill to scope, build, and integrate it. automateflows is the **implementation partner** — Troy's company doing the automation + AI buildout for them. This is the consulting/services edge of the exact trend the wiki tracks: the [[AI Workforce]] shift and "automation as the new middleware."

## Stack / architecture

| Layer | Tech |
|-------|------|
| Frontend | React + Vite + Tailwind |
| Hosting | Netlify |

**Architecture note:** Site is React + Vite + Tailwind on Netlify — the marketing/client-facing surface. The *delivery* side (what gets built for clients) is the real engine: almost certainly [[n8n]]-style workflow orchestration + agent integrations. Worth documenting the actual delivery stack/playbook separately from the website stack.

## Open decisions

- **Delivery stack** — what tooling does automateflows actually deliver with? [[n8n]]? Custom agents? Claude/GPT API wrappers? This is the IP; document it.
- **Productize vs bespoke** — pure services (per-client builds) or repeatable products/templates? Determines margin + scale (services don't scale, products do).
- **Positioning vs the field** — competes/overlaps with the [[AI Workforce]] vendors ([[Henry]]/ai.work) at the SMB/implementation end. What's the wedge — local/SMB focus, hands-on integration, vertical specialization?
- **Relation to [[agent-os]]** — is Agent OS the internal framework automateflows delivers *with*? Natural synergy.

## Wiki connections

- [[AI Workforce]] — the macro trend automateflows sells into (agents as labor layer)
- [[n8n]] — likely core delivery/orchestration tool
- [[Autonomous Agent Workflows]] — execution patterns relevant to client builds
- [[agent-os]] — candidate internal framework / sibling project
- [[Henry]] — enterprise-end analog of the same "AI does the work" pitch
- [[job-nexus]], [[peptide-app]] — sibling builds

## Changelog

- **2026-06-05** — page created from Troy's spec. Status: deployed / operating as a company.
