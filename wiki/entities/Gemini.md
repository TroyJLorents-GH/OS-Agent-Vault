---
title: Gemini
type: entity
created: 2026-06-03
updated: 2026-06-04
sources: ["Gemini 3.2 Flash What We Know Before Google IO 2026", "S — New AI Model Releases April 2026 Startup Edition"]
tags: [google-deepmind, llm, multimodal, product, "2026"]
---

# Gemini

[[Google]] DeepMind's frontier model family — natively multimodal (text, image, audio, video). Competes with [[Claude]], GPT, and open-weight families. Tiered into **Pro** (max capability), **Flash** (efficiency), and **Flash-Lite** (cheapest).

## 2026 lineage

Google is treating Flash as a **continuous software product** rather than discrete releases — a sub-quarterly cadence:

| Version | Released | Notes |
|---------|----------|-------|
| Gemini 3 Flash | Dec 2025 | First Gemini 3-family Flash |
| Gemini 3.1 Pro | Feb 19, 2026 | 94.3% GPQA Diamond; strong SVG/design |
| Gemini 3.1 Flash-Lite | Mar 2026 | Cost-sensitive tier |
| ~~Gemini 3.2 Flash~~ | (pre-release codename / leak) | **Shipped as 3.5 Flash** — see reconciliation |
| **Gemini 3.5 Flash** | **I/O 2026 (May 19), GA** | Beats 3.1 Pro on coding/agentic/multimodal; 4× faster output |
| Gemini 3.5 Pro | In testing at I/O; GA ~June 2026 | Advanced reasoning/coding |

(Sources: [[S — Gemini 3.2 Flash Before Google IO 2026]]; [Google I/O 2026 announcements](https://blog.google/innovation-and-ai/technology/ai/google-io-2026-all-our-announcements/))

## Gemini 3.5 Flash (shipped) — reconciliation of the "3.2 Flash" leak

The pre-I/O leak tracked on [[S — Gemini 3.2 Flash Before Google IO 2026]] called the model **"3.2 Flash."** At Google I/O (May 19, 2026), the model that actually shipped is **Gemini 3.5 Flash** — the **version number in the leak was wrong, the thesis was right.**

**Confirmed at launch** ([9to5Google](https://9to5google.com/2026/05/19/google-io-2026-news/), [Google](https://blog.google/innovation-and-ai/technology/ai/google-io-2026-all-our-announcements/)):
- **"Flash beats Pro" — confirmed with real benchmarks.** 3.5 Flash outperforms Gemini 3.1 Pro on coding/agentic/multimodal: **Terminal-Bench 2.1 76.2%, GDPval-AA 1656 Elo, MCP Atlas 83.6%, CharXiv 84.2%**.
- **~4× faster output** tokens/sec than other frontier models — the Flash speed promise held.
- **GA day one** via **Google Antigravity**, the Gemini API in **Google AI Studio** and **Android Studio**.
- **Gemini 3.5 Pro** in testing, slated for ~June 2026.

**What the leak got wrong:** the version number (3.2 → 3.5), and "creative-coding-only" framing — real benchmarks show broad coding/agentic/multimodal gains, not just SVG/Three.js cherry-picks. The leaked $0.25/$2.00 pricing and "Liquid Glass" UI are not confirmed in these results and remain to verify.

## Strategic read

- **Flash eating Pro** — a Flash model approaching Pro quality at a fraction of the cost compresses the whole tier ladder and pressures Pro-tier pricing. Pure [[Inference Economics]] play: optimize the cheap, high-volume tier for the workloads that dominate real usage (search, assistant, AI Overviews).
- **Multimodal moat at Flash price** — closest-priced rival DeepSeek V4 Flash is text-only; Gemini 3.2 Flash carries the full multimodal stack. See [[DeepSeek]].
- **Distribution advantage** — deploys across Search, Maps, YouTube, Docs, Gmail, Chrome at Google scale on day one. No other lab has that surface.

## Related Google AI (I/O 2026)

[[Gemma]] 4 open weights (27B, Apache 2.0), Android 17 AI Core, Project Astra, Google Antigravity agentic dev platform, Gemini Live voices. Collected on the [[Google]] entity page.

## Connections

- [[Google]] — vendor
- [[S — Gemini 3.2 Flash Before Google IO 2026]] — primary source
- [[Inference Economics]] — Flash-tier economics thesis
- [[DeepSeek]] — efficiency-tier competitor
- [[Claude]] — frontier rival
- [[AI Industry Landscape April 2026]] — leaderboard context
- [[AI Coding Tools]] — creative-coding capability competes with coding agents
