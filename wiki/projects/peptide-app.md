---
title: peptide-app
type: project
created: 2026-06-05
updated: 2026-06-05
sources: []
tags: [peptide-app, projects, health, y2026]
---

# peptide-app

Troy's **deployed** app for tracking peptide concentration, dosing schedule, and goals.

> **Status: deployed.** Live build. This page tracks architecture + live decisions; append changes to the changelog as the app evolves.

## Problem + who for

People running peptide protocols need to track **concentration** (reconstitution math — mg per vial, dilution, dose volume), **timing** (a scheduler so doses aren't missed), and **goals** (what the protocol targets). peptide-app combines all three in one tool — for self-quantifying health/fitness users managing their own regimen.

## Stack / architecture

| Layer | Tech |
|-------|------|
| Frontend | TypeScript + Vite |
| Backend / DB / auth | Supabase |

**Architecture note:** Supabase (Postgres + auth + realtime) holds user protocols, dose logs, and schedule state; TS+Vite frontend. Core logic is **concentration math + a scheduler**, not AI — honest framing: this is the least AI-centric of the three projects. AI is a *potential* layer (see open decisions), not a current dependency.

## Open decisions

- **Add an AI layer?** Candidate uses: natural-language dose logging, protocol suggestions, anomaly flagging. Would move it toward [[domain-specific-ai]] (health). Decide whether that's in scope or scope creep.
- **Notifications** — does the scheduler push reminders (Supabase + web push / Edge Functions), or passive in-app only?
- **Regulatory caution** — health dosing tool. Any AI suggestion feature inherits medical-advice liability + [[AI Regulation]] exposure. Keep informational, not prescriptive.

## Wiki connections

- [[domain-specific-ai]] — the health vertical it could specialize into (if AI added)
- [[job-nexus]], [[automateflows]], [[agent-os]] — sibling projects
- [[AI Regulation]] — relevant if/when dosing guidance gets AI-generated

## Changelog

- **2026-06-05** — page created from Troy's spec. Status: deployed.
