---
title: MemPalace
type: entity
created: 2026-04-10
updated: 2026-04-10
sources:
  - S — MemPalace
tags:
  - tool
  - agents
  - llm
  - benchmark
---

# MemPalace

Open-source AI memory system by Milla Jovovich & Ben Sigman. Stores verbatim conversation data in ChromaDB with a hierarchical palace structure inspired by the ancient method of loci.

- **Repository:** [github.com/milla-jovovich/mempalace](https://github.com/milla-jovovich/mempalace)
- **License:** Open-source, free
- **Storage:** ChromaDB (vector) + SQLite (knowledge graph)
- **Architecture:** Local-only, no cloud dependency

## Key Capabilities

- **96.6% R@5 on LongMemEval** — highest published score requiring no API calls (Source: [[S — MemPalace]])
- **100% with Haiku rerank** — perfect score with lightweight reranking
- Hierarchical palace structure (wings, rooms, halls, tunnels, closets, drawers)
- 4-layer memory stack waking up with only ~170 tokens
- Knowledge graph with temporal entity-relationship triples
- MCP server with 19 tools for integration with [[Claude]], ChatGPT, Cursor, and Gemini
- Specialist agent support — each agent gets its own wing and diary
- Auto-save hooks for Claude Code (periodic + emergency saves before compaction)

## Competitive Landscape

| System | LongMemEval | Monthly Cost | Cloud Required |
|--------|-------------|-------------|----------------|
| **MemPalace** | **96.6%** | Free | No |
| Mastra | 94.87% | API costs | Yes |
| Mem0 | ~85% | $19-249/mo | Yes |
| Zep | ~85% | $25/mo+ | Yes |

MemPalace's main competitive advantage is the combination of top benchmark scores with zero cost and no cloud dependency. The tradeoff is that users must self-host and manage their own infrastructure.

## The Honesty Correction

Within hours of launch, the authors publicly walked back overstated claims about AAAK compression performance, the "+34% palace boost" metric, and contradiction detection capabilities. Their principle: *"We'd rather be right than impressive."* This kind of public self-correction is uncommon in AI tooling and is a positive credibility signal.

## Relevance to This Vault

This vault (OS Agent Vault) is itself a memory system — an [[AI Memory Systems|AI memory system]]. MemPalace and this wiki represent complementary strategies for knowledge persistence:

- **MemPalace (store-and-retrieve):** Keep everything verbatim, use structure and search to find it. Nothing is lost, but retrieval quality depends on the palace structure.
- **This wiki (compile-and-maintain):** LLM incrementally builds structured, cross-referenced knowledge. Pre-synthesized and navigable, but lossy — the LLM decides what matters.

MemPalace's benchmark data suggests raw verbatim storage (96.6%) outperforms compressed/summarized storage (84.2% with AAAK), which is an important data point for the design of this vault's own processes.

## See Also

- [[S — MemPalace]] — full source summary
- [[AI Memory Systems]] — the broader concept
- [[Retrieval-Augmented Generation]] — MemPalace as a structured RAG system
- [[Coding Agent Architecture]] — memory as a core agent component
- [[S — Components of A Coding Agent]] — memory layers in coding agents
