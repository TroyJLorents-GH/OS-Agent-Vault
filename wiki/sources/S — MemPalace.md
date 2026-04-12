---
title: "S — MemPalace"
type: source
created: 2026-04-10
updated: 2026-04-10
sources: ["milla-jovovichmempalace The highest-scoring AI memory system ever benchmarked. And it's free.md"]
tags: [llm, agents, technique, benchmark, "2026"]
---

# S — MemPalace

## Source Metadata

- **Authors:** Milla Jovovich & Ben Sigman
- **Clipped:** ~2026-04-08
- **URL:** [MemPalace on GitHub](https://github.com/milla-jovovich/mempalace)
- **Publisher:** GitHub README

## Core Pitch

AI conversations disappear when sessions end. Six months of daily AI use generates roughly 19.5 million tokens — all of it lost. [[MemPalace]] stores everything and makes it findable, combining verbatim raw storage with a hierarchical structure for retrieval.

The system is open-source, local-only, and free. No cloud dependency, no subscription.

## The Palace Metaphor

Inspired by the ancient Greek method of loci (memory palaces), MemPalace organizes memories into a spatial hierarchy:

- **Wings** — a person or project (top-level namespace)
- **Rooms** — specific topics within a wing
- **Halls** — memory-type corridors (facts, events, discoveries, preferences, advice)
- **Tunnels** — cross-wing connections linking the same room topic across different wings
- **Closets** — summaries pointing to originals (compressed references)
- **Drawers** — verbatim original files (the source of truth)

This structure is not just metaphorical — it directly impacts retrieval quality. Wing+room filtering gives a **+34% retrieval improvement** over searching all closets (though the authors later corrected this claim; see Honesty section below).

## 4-Layer Memory Stack

| Layer | Purpose | Size |
|-------|---------|------|
| L0 — Identity | Who the user is | ~50 tokens |
| L1 — Critical Facts | Essential facts in [[AAAK Dialect]] format | ~120 tokens |
| L2 — Room Recall | On-demand retrieval from specific rooms | Variable |
| L3 — Deep Search | Full search across all drawers | Variable |

The system wakes up with only ~170 tokens (L0 + L1), keeping cold-start costs minimal. Deeper layers are loaded on demand.

## AAAK Dialect (Experimental)

AAAK is a lossy abbreviation system designed for token compression. It is readable by any LLM without a decoder ring.

**HONEST STATUS:** AAAK regresses LongMemEval retrieval from 96.6% to 84.2% — a 12.4 percentage point gap. The authors publicly acknowledge this. Default storage mode is raw verbatim, not AAAK. The question remains whether AAAK can improve enough to close this gap.

## Benchmarks

- **96.6% R@5 on LongMemEval** (raw mode, zero API calls) — highest published score requiring no API
- **100% with Haiku rerank** — perfect score when adding a lightweight reranking step
- **+34% retrieval improvement** from palace structure (wing+room filtering vs. searching all closets)

### Competitive Comparison

| System | Score | Cost | API Required |
|--------|-------|------|-------------|
| [[MemPalace]] | 96.6% R@5 | Free | No |
| Mastra | 94.87% | API costs | Yes |
| Mem0 | ~85% | $19-249/mo | Yes |
| Zep | ~85% | $25/mo+ | Yes |

## Knowledge Graph

MemPalace includes temporal entity-relationship triples stored in SQLite — conceptually similar to Zep's Graphiti but entirely local and free. This enables relationship-aware queries beyond simple vector similarity.

## Specialist Agents

Each specialist agent gets its own wing and diary, written in AAAK. This allows multiple AI personas or project-specific agents to maintain separate memory spaces within the same palace.

## MCP Server

Ships with an MCP server exposing 19 tools, enabling integration with [[Claude]], ChatGPT, Cursor, and Gemini. This positions MemPalace as a universal memory layer across AI interfaces.

## Auto-Save Hooks

Includes auto-save hooks for Claude Code:
- Save every N messages
- Emergency save before context compaction

This addresses the critical failure mode where a long coding session's context is lost during compaction.

## The Honesty Section

The authors publicly corrected overstated claims within hours of launch:

1. **AAAK compression** — initially presented as the default; corrected to show raw verbatim outperforms AAAK by 12.4 points
2. **"+34% palace boost"** — clarified the conditions under which this improvement applies
3. **Contradiction detection** — walked back overstated capabilities

Their stated principle: *"We'd rather be right than impressive."*

This level of public self-correction is rare in AI tooling and worth noting as a positive signal for project credibility.

## Open Questions

- Will AAAK improve enough to close the 12.4 percentage point gap vs. raw storage?
- How does the palace structure scale beyond 22K memories?
- Can the hierarchical structure be auto-generated, or does it require manual wing/room design?
- How does MemPalace interact with context compaction in tools like Claude Code?

## Connections

- [[Coding Agent Architecture]] — memory is one of the core components of a coding agent harness
- [[Retrieval-Augmented Generation]] — the palace is fundamentally a structured retrieval system, with the hierarchy acting as a pre-filter before vector search
- [[AI emotional support]] — memory persistence matters for emotional continuity; users who form relationships with AI lose context every session
- [[AI Memory Systems]] — MemPalace exemplifies the "store-and-retrieve" approach to AI memory
- [[S — Components of A Coding Agent]] — Sebastian Raschka identifies memory (working memory + full transcript) as a key agent component; MemPalace is a concrete implementation of the "full transcript" layer
