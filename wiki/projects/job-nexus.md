---
title: job-nexus
type: project
created: 2026-06-05
updated: 2026-06-05
sources: []
tags:
  - job-nexus
  - projects
  - domain-specific-ai
  - code-gen
  - y2026
---

# job-nexus

Troy's **shipped** app that compares a resume against a job description to surface fit, gaps, and tailoring opportunities.

> **Status: shipped.** Live build. This page tracks architecture + the live decisions; append changes to the changelog as the app evolves.

## Problem + who for

Job seekers can't tell how well their resume matches a given posting, or where the gaps are. job-nexus does the resume↔JD comparison automatically — surfaces alignment and missing keywords/skills so the user tailors per application instead of guessing.

This is a direct instance of [[AI as equalizer]] — democratizing the kind of resume-matching insight that paid career coaches and ATS-optimization services gate behind a fee.

## Stack / architecture

| Layer | Tech |
|-------|------|
| Frontend | TypeScript + Vite |
| Datastore | Azure Cosmos DB |
| Search / matching | Azure AI Search |
| Auth / hosting | Firebase |

**Architecture note:** [Azure AI Search](https://learn.microsoft.com/en-us/azure/search/) is the engine doing the resume↔JD matching — almost certainly vector/semantic search over embedded resume + posting text. That makes job-nexus a **retrieval/semantic-similarity** app in the [[retrieval-augmented-generation]] family (matching, not generation), and a concrete [[domain-specific-ai]] build (HR/recruiting domain). Cosmos DB holds resumes/postings/results; Firebase fronts auth + hosting.

## Open decisions

- **LLM in the loop?** Is matching pure Azure AI Search vector similarity, or is a generative model writing the gap analysis / rewrite suggestions? Determines whether this is a RAG app or a search app.
- **Indeed integration?** The [[Indeed]] MCP (live in this environment) could pull postings directly — auto-fetch JD instead of paste. Natural next feature.
- **Scoring transparency** — does it show *why* a match scored low (which [[AI Regulation]] explainability trend rewards)?

## Wiki connections

- [[AI as equalizer]] — the equity thesis this app embodies
- [[domain-specific-ai]] — recruiting/HR specialization over a general model
- [[retrieval-augmented-generation]] — semantic-search matching pattern
- [[Indeed]] — candidate posting source (MCP available)
- [[agent-os]] — sibling project; could become a managed agent under it
- [[automateflows]], [[peptide-app]] — sibling builds (shared TS+Vite stack)

## Changelog

- **2026-06-05** — page created from Troy's spec. Status: shipped.
