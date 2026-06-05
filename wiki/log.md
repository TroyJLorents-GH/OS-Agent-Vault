# Compiler Log

_Chronological record of ingests, queries, and lint passes._

- **2026-04-07 14:35 UTC** — ingest: 'techcrunch.com' from https://techcrunch.com/2026/04/07/adobe-launches-acrobat-spaces-a-free-ai-powered-study-tool-for-students/ — 20 wiki pages

## [2026-04-08] ingest | Part I: AI for Scientific Research — The Power of Small Language Models

**Source:** Red Hat Blog by Daniel Domkowski (2026-03-30)

**Pages created (11):**
- `sources/redhat-slms-scientific-research-2026-03-30` — full source summary
- `entities/red-hat-ai` — Red Hat's enterprise AI platform
- `entities/instructlab` — open-source synthetic data generation tool
- `entities/daniel-domkowski` — author, AI infrastructure thought leader
- `concepts/small-language-models` — 1-10B param domain-specific models
- `concepts/fine-tuning` — LoRA/QLoRA and the case for weight adaptation
- `concepts/retrieval-augmented-generation` — RAG as complement to fine-tuning
- `concepts/domain-specific-ai` — the overarching thesis of specialization over generality
- `concepts/synthetic-data-generation` — solving data scarcity with golden datasets
- `concepts/model-reproducibility` — versioned models for scientific integrity
- `concepts/hpc-cloud-convergence` — merging HPC and cloud-native infrastructure
- `concepts/ai-for-scientific-research` — applying LLMs to the scientific cycle

**Key finding:** The article makes a strong case that domain-specific SLMs (1-10B params), fine-tuned via LoRA/QLoRA on synthetic data from small golden datasets, outperform frontier models for specialized research tasks. Fine-tuning and RAG are framed as complementary — fine-tuning encodes reasoning behavior, RAG provides current knowledge. Unresolved wikilinks created for: NVIDIA, OpenShift AI, LoRA, QLoRA, Training Hub, scaling laws, agent-os, job-nexus, peptide-app.
- **2026-04-09 22:21 UTC** — ingest: 'anthropic.com' from https://www.anthropic.com/features/81k-interviews — 20 wiki pages
- **2026-04-09 22:45 UTC** — lint: 2 orphans, 44 missing, 2 unindexed

## [2026-04-09] ingest | What 81,000 People Want from AI (deep ingest)

**Source:** Anthropic (2026-03-18), by Saffron Huang et al.

**Pages created (7):**
- `sources/anthropic-81k-interviews-2026-03-18` — comprehensive source summary with full data tables
- `concepts/light-and-shade-of-ai` — framework: AI benefits and harms are entangled within the same person
- `concepts/cognitive-atrophy` — skill loss from AI overreliance; worst in institutional settings
- `concepts/ai-emotional-support` — AI filling emotional gaps; most entangled tension (3x co-occurrence)
- `concepts/ai-and-economic-displacement` — job displacement vs empowerment; strongest sentiment predictor
- `concepts/ai-as-equalizer` — AI democratizing access in developing world
- `concepts/sycophancy` — AI being too agreeable, reinforcing delusions

**Pages updated (2):**
- `entities/anthropic` — enriched with 81K study details, research initiatives
- `entities/claude` — rewritten with user experience patterns, known issues from study

**Key finding:** The "light and shade" framework — same AI capabilities produce both benefits and harms, entangled within the same person. Emotional support is the most entangled (3x co-occurrence); economic displacement is the least (divides into camps). Cognitive atrophy is worst in institutional settings but minimal when learning is volitional.

## [2026-04-10] ingest | The Big LLM Architecture Comparison

**Source:** Sebastian Raschka's Substack (2025-07-19, updated 2026-04-02)

**Pages created (8):**
- `sources/S — The Big LLM Architecture Comparison` — comprehensive survey of 23+ architectures
- `entities/Sebastian Raschka` — AI researcher, educator, LLM architecture expert
- `entities/DeepSeek` — Chinese AI lab whose architecture became the open-weight reference standard
- `concepts/Transformer Architecture` — foundational architecture, persisting with incremental refinements
- `concepts/Mixture of Experts` — dominant 2025 trend, many-small-experts design
- `concepts/Multi-Head Latent Attention` — DeepSeek's KV compression, outperforms GQA and MHA
- `concepts/Sliding Window Attention` — local attention windows for efficiency
- `concepts/Linear Attention` — 2025 revival, MiniMax retreat, Kimi refinement
- `concepts/Multi-Token Prediction` — multi-token training signal + speculative decoding

**Key findings:** (1) MoE is the dominant architectural trend — nearly every major model adopted it. (2) DeepSeek V3's architecture is being copied wholesale by Kimi K2, Mistral 3, and GLM-5. (3) Linear attention had a revival then partial retreat when MiniMax found it failed on reasoning tasks. (4) Architecture is converging — "the secret sauce is in the training pipeline." (5) MLA outperforms both GQA and MHA while saving memory.
- **2026-04-11 17:40 UTC** — query: 'Whats new in AI?' — 0 sources, filed=queries/whats-new-in-ai.md
- **2026-04-11 17:41 UTC** — lint: 2 orphans, 52 missing, 2 unindexed
- **2026-04-11 17:41 UTC** — query: 'Llm models' — 0 sources, filed=no

## [2026-04-11] ingest | Developing a Standard AI OS

**Source:** Red Hat Blog by Brian Stevens (2025-08-14)

**Pages created (3):**
- `sources/S — Developing a Standard AI OS` — full source summary: AI OS = Kubernetes + vLLM + llm-d
- `concepts/AI Operating System` — standardized AI inference layer, Linux analogy, three-layer architecture
- `entities/Brian Stevens` — Red Hat Blog author, coopetition advocate

**Key finding:** Enterprise AI needs a standard AI OS analogous to Linux — not a new OS from scratch, but an emergent layer of open-source projects (Kubernetes for orchestration, vLLM as inference kernel, llm-d for distributed inference). The "train once, infer repeatedly" principle makes inference optimization the central challenge. Red Hat positions its products (AI Inference Server, RHEL AI, OpenShift AI) as the commercial layer atop this open-source stack.

## [2026-04-11] ingest | Components of A Coding Agent

**Source:** Sebastian Raschka's Substack (2026-04-04)

**Pages created (3):**
- `sources/S — Components of A Coding Agent` — full source summary of the 6-component coding agent framework
- `concepts/Coding Agent Architecture` — concept page: LLM + harness = coding agent, 6 components, harness as differentiator
- `concepts/Prompt Caching` — concept page: stable prefix vs changing state, cache reuse across turns

**Pages updated (2):**
- `entities/Sebastian Raschka` — added Components of A Coding Agent to key contributions
- `wiki/index.md` — added new source and concept entries

**Key finding:** The agent harness — not the model — is increasingly the differentiator in coding agent performance. Raschka identifies six components (repo context, prompt caching, tool use, context compaction, session memory, subagent delegation) and argues that dropping an open-weight model like GLM-5 into a comparable harness could match GPT-5.4 in Codex or Opus 4.6 in Claude Code. Core insight: "A lot of apparent 'model quality' is really context quality."

## [2026-04-11] ingest | MemPalace

**Source:** GitHub README by Milla Jovovich & Ben Sigman (~2026-04-08)

**Pages created (3):**
- `sources/S — MemPalace` — full source summary of the highest-scoring open-source AI memory system
- `entities/MemPalace` — entity page: open-source memory system, 96.6% R@5, local-only, MCP server
- `concepts/AI Memory Systems` — concept page: store-and-retrieve vs. compile-and-maintain, 4-layer stack, raw beats compressed

**Key finding:** MemPalace achieves 96.6% R@5 on LongMemEval with zero API calls — the highest published score requiring no API. Its hierarchical palace structure (wings, rooms, halls, tunnels, closets, drawers) provides +34% retrieval improvement over flat search. Most striking benchmark result: raw verbatim storage (96.6%) significantly outperforms compressed AAAK format (84.2%), suggesting that for retrieval tasks, keeping originals beats summarizing. The authors publicly corrected overstated claims within hours of launch — rare and credible. Directly relevant to this vault's own design as a complementary memory approach.

## [2026-04-11] lint | Health check and cleanup

**Issues found and fixed:**
- Deleted 8 junk entity pages (country/respondent profiles from shallow 81K ingest: cameroon, honduras, entrepreneur-nigeria, freelancer-usa, healthcare-worker-usa, software-engineer-mexico, claude-powered-classifiers, claudeai)
- Deleted 10 orphan concept pages too granular for the wiki (ai-assisted-productivity, ai-classification, ai-driven-entrepreneurship, ai-enabled-learning, ai-for-personal-growth, conversational-ai-interviewer, open-ended-interviews, qualitative-research, sentiment-analysis, ai-for-societal-challenges)
- Deleted 1 duplicate source page (anthropiccom-2026-04-09, superseded by deep ingest anthropic-81k-interviews-2026-03-18)
- Rewrote entities/claude.md with richer content from deep ingest
- Cleaned index.md — removed all references to deleted pages
- Fixed 68 files with unquoted year tags (2025/2026 → "2025"/"2026")
- Fixed 39 files with code-block frontmatter (```yaml → proper --- delimiters)
- Added taxonomy tags to all 7 raw source files

**Remaining unresolved wikilinks (intentional TODOs):**
- Infrastructure: NVIDIA, AMD, Intel, Hugging Face, vLLM, OpenShift AI, Training Hub, LoRA, QLoRA
- Troy's projects: agent-os, job-nexus, peptide-app

## [2026-04-11] ingest | April 2026: Innovations in AI and Startup Trends Shaping the Future

**Source:** The Tech Edvocate by Matthew Lynch (2026-04-04)

**Pages created (1):**
- `sources/S — April 2026 Innovations in AI and Startup Trends` — source summary

**Pages updated (2):**
- `wiki/index.md` — added new source entry
- `wiki/log.md` — this entry

**Key finding:** General-audience overview confirming the same macro trends seen in deeper sources: frontier model advances (10x processing claim), open-source AI momentum (appealing to resource-constrained startups), and agentic AI frameworks. Also covers startup trends in sustainability, remote work, health tech, and fintech. Low signal density but useful as confirmation of broader themes. No new concept or entity pages warranted.

## [2026-04-11] ingest | AI Trending April 2026: The Top 5 Developments & News

**Source:** BuildEZ Team (2026-04-03)

**Pages created (2):**
- `sources/S — AI Trending April 2026` — $242B Q1 VC funding, agentic AI trend, multimodal, healthcare/finance
- `concepts/Agentic AI` — autonomous AI teammates, MCP at 97M installs, Agentic AI Foundation, $1M agent-run business prediction

**Key findings:** $242B VC invested in AI in Q1 2026 (80% of all global venture funding, up from $59.6B same period 2025). OpenAI valued at $852B, Anthropic at $380B. Agentic AI is the defining trend — agents that perform complex tasks autonomously (Microsoft Copilot Cowork, Anthropic Conway, Salesforce). Noah Labs Vox can detect heart failure from 5-second voice recording. EU AI Act enforcement began 2026.

## [2026-04-11] ingest | New AI Model Releases News April 2026 (Startup Edition)

**Source:** Violetta Bonenkamp at mean.ceo (2026-03-31)

**Pages created (2):**
- `sources/S — New AI Model Releases April 2026 Startup Edition` — densest model landscape snapshot with benchmarks, business numbers, startup strategy
- `concepts/AI Industry Landscape April 2026` — competitive snapshot: frontier models, valuations, pricing collapse, upcoming releases

**Key findings:** The densest model release window in AI history (Feb-April 2026). GPT-5.4 scores 83% GDPVal (matches human experts on economically valuable tasks). Claude Sonnet 4.6 leads GDPval-AA Elo. Gemini 3.1 Pro tops reasoning benchmarks. OpenAI at $25B annualized revenue, possible IPO. Anthropic at $19B. Claude Mythos 5 (10T params) testing internally. Grok 5 (6T MoE) expected Q2. Morgan Stanley warns massive AI breakthrough imminent H1 2026. The shift is from "AI that answers" to "AI that gets things done." Startup advice: build model-agnostic, use multi-model orchestration, match model to task.

## [2026-04-13] ingest | Open-Source AI Landscape April 2026: Complete Guide

**Source:** Digital Applied (2026-04-03)

**Pages created (2):**
- `sources/S — Open-Source AI Landscape April 2026` — complete ecosystem map with model comparison tables, selection framework, deployment economics
- `concepts/Open-Source AI` — the structural shift: 6 families at parity, Apache 2.0 liberation, MoE enabling single-GPU frontier

**Key findings:** (1) 5 of 6 major open models use MoE, enabling single-GPU inference at frontier scale. (2) Apache 2.0/MIT covers 5 of 6 families — only Llama uses custom license. (3) Qwen leads coding benchmarks; Gemma 4 covers edge-to-server; Llama 4 Scout offers 10M context; Mistral Small 4 unifies reasoning/vision/coding in one model. (4) GLM-5 (744B, MIT) was trained entirely on Huawei chips — zero NVIDIA dependency, a geopolitical milestone. (5) Self-hosting crossover at ~50-100M tokens/month; above that, 3-10x savings. (6) "No single model dominates all dimensions" — the landscape is genuinely differentiated.

## [2026-04-13] ingest | Best AI Tools 2026: 100+ Reviewed & Rated

**Source:** AI Weekly by Alexis Gonzalez-del-Valle (2026-03-27)

**Pages created (1):**
- `sources/S — Best AI Tools 2026` — comprehensive tools catalog across 8 categories with pricing, verdicts, and comparison tables

**Key findings:** (1) Two defining 2026 trends: reasoning over retrieval (o3 thinks before responding) and the agentic shift (tools performing work, not just answering). (2) Claude Code: 80.8% SWE-bench, 46% "most loved" among devs, $2.5B/yr revenue for Anthropic — went from zero to #1 in 8 months. (3) Copilot "once revolutionary, now table stakes" — power users migrating to Claude Code and Cursor. (4) OpenAI shut down Sora, redirected to robotics — video gen economically unviable at current compute. (5) n8n highlighted as "power user's Zapier" with AI Agent nodes for self-correcting workflows. (6) Perplexity crossed 1B monthly queries. (7) Tool selection advice: average experienced AI user has 2-3 paid subscriptions, not 15.
- **2026-04-13 16:19 UTC** — query: 'Whats new with multimodal?' — 0 sources, filed=queries/whats-new-with-multimodal.md
- **2026-04-13 16:19 UTC** — query: 'Whats trending in AI in April 2026?' — 0 sources, filed=queries/whats-trending-in-ai-in-april-2026.md
- **2026-04-13 18:07 UTC** — query: 'What are best AI tools?' — 0 sources, filed=no

## [2026-04-13] ingest | Best AI Tools 2026 (continued — entities and concepts)

**Pages created (7):**
- `entities/Cursor` — AI-native IDE, second most-loved coding tool
- `entities/Perplexity` — AI search with citations, 1B queries/month
- `entities/n8n` — open-source automation with AI Agent nodes
- `entities/Midjourney` — leading AI image generator
- `entities/ElevenLabs` — leading AI voice platform
- `entities/Runway` — leading AI video generation
- `concepts/AI Coding Tools` — competitive landscape, terminal agents vs AI-native IDEs, vibe coding

**Key connection:** The coding tools landscape directly demonstrates the thesis from Raschka's coding agent article — the harness matters as much as the model. Claude Code's dominance (80.8% SWE-bench, $2.5B/yr) validates the 6-component framework. n8n applies the same agent loop pattern to business workflow automation.

## [2026-04-15] ingest | AI Technology Trends 2026: Key Developments You Need to Know

**Source:** BuildEZ Team (2026-04-14)

**Pages created (5):**
- `sources/S — AI Technology Trends 2026 Key Developments` — source summary covering the trillion-dollar pivot, agentic AI breakthrough, multimodal integration, physical AI, and regulation wave
- `concepts/Inference Economics` — the 2026 shift from training costs to serving costs; the frame that unifies AI OS, MoE adoption, Sora shutdown
- `concepts/AI Regulation` — EU AI Act, CA/CO laws, XAI demand; compliance as product feature
- `concepts/Physical AI` — AI in robots, autonomous vehicles, smart machines
- `entities/NVIDIA` — finally fills one of the longest-unresolved wikilinks; covers Isaac GR00T, Alpamayo, partnerships, and the Huawei challenge to training monopoly

**Key findings:** (1) Global AI spending projected at $2.52T in 2026 (+44% YoY per Gartner), driven almost entirely by inference/deployment not training. (2) "Inference Economics" is the unifying frame — explains MoE dominance, AI OS stack, Sora shutdown, pricing collapse. (3) Agent success on real-world tasks jumped from 20% (2025) to 77.3% (April 2026) per Terminal-Bench — a staggering 12-month delta. (4) 2026 is the enforcement year for AI regulation — EU AI Act Aug 2, CA laws Jan 1, CO law June 30. XAI demand rising. (5) Physical AI is the next frontier — Sora shutdown redirected resources to robotics; NVIDIA GTC 2026 dominated by agentic deployments and physical AI. (6) "Great Divergence" — manufacturing/logistics prioritize AI to solve labor gaps; content sectors face "Crisis of Distinctiveness."
- **2026-04-13 19:14 UTC** — query: 'Where are my gaps?' — 0 sources, filed=queries/where-are-my-gaps.md
- **2026-04-13 19:15 UTC** — query: 'What are the best AI   tools for coding?' — 0 sources, filed=queries/what-are-the-best-ai-tools-for-coding.md
- **2026-04-13 21:47 UTC** — query: 'Where are my gaps?' — 4 sources, filed=queries/where-are-my-gaps.md
- **2026-04-15 19:17 UTC** — query: 'what projects are opensource?' — 5 sources, filed=queries/what-projects-are-opensource.md
- **2026-04-22 22:16 UTC** — query: 'OpportunityScan' — 0 sources, filed=queries/opportunityscan.md
- **2026-04-22 22:16 UTC** — query: 'Opportunity' — 5 sources, filed=queries/opportunity.md

## [2026-05-16] ingest | Keep Claude Working Toward a Goal

**Source:** Anthropic Claude Code docs — code.claude.com/docs/en/goal (raw dated 2026-05-15)

**Pages created (3):**
- `sources/S — Keep Claude Working Toward a Goal` — full source summary, architecture, conditions, gotchas
- `entities/Claude Code` — Anthropic's terminal coding agent, 80.8% SWE-bench, $2.5B/yr
- `concepts/Autonomous Agent Workflows` — `/goal` vs `/loop` vs Stop hooks vs auto mode; evaluator-loop pattern

**Pages updated (1):**
- `entities/anthropic` — added Claude Code section, business numbers, Mythos cross-reference

**Key finding:** `/goal` introduces the **evaluator-loop pattern** — a separate small fast model (Haiku) judges each turn's completion against a user-set condition. The evaluator cannot call tools, only judges conversation contents, which forces the worker model to demonstrate completion in the transcript. Mechanically `/goal` is a session-scoped prompt-based Stop hook. Open question: does the evaluator inherit [[sycophancy]] from training? Empirical test worth running.

## [2026-05-16] ingest | Top Tech News May 15, 2026

**Source:** techstartups.com daily roundup by Nickie Louise (2026-05-15)

**Pages created (10):**
- `sources/S — Top Tech News May 15 2026` — synthesized roundup of 17 stories across 5 themes
- `entities/Cerebras` — wafer-scale chipmaker, May 15 IPO at ~$95B close
- `entities/OpenAI` — overdue entity; GPT-5.4, Codex, Musk litigation
- `entities/Apple` — Siri/ChatGPT friction; backs Google in EU fight
- `entities/Sam Altman` — OpenAI CEO; named in Musk suit
- `entities/Elon Musk` — $150B litigant against OpenAI
- `entities/Samsung` — 45K-worker strike over AI bonus disparity
- `entities/Microsoft` — OpenAI partner named in Musk suit; Exchange zero-day
- `concepts/AI Data Center Backlash` — Gallup 71% opposition; new constraint on capex pace
- `concepts/AI Capex Buildout` — 2026 strategic-infra capital cycle
- `concepts/AI in Warfare` — Pentagon Mythos comment; dual-use tension with Anthropic safety framing

**Pages updated (2):**
- `entities/NVIDIA` — $5.5T intraday cap, Cerebras as first public competitor, EU Android fight
- `entities/anthropic` — added Mythos section with warfare framing tension

**Key findings:**
1. **AI capex looks like infrastructure, not software** — Cerebras IPO ($95B/+68%), Nvidia $5.5T cap, Argentum $2.5B, Kioxia $8.2B Q1 — public markets pricing pure-play AI chip + data center bets at infrastructure multiples
2. **Supply-side fragility is real** — Samsung 18-day strike (May 21) over 607% memory-division bonuses vs 50-100% logic threatens $14-21B operating profit and global memory supply for AI data centers
3. **71% of Americans oppose local AI data centers** (48% strongly) — first concrete signal that local trust/permitting is a binding constraint on buildout
4. **Mythos framing tension** — Anthropic positions Mythos under safety; Pentagon cyber official names it as warfare-grade. Same model, opposing narratives. Will shape regulation and commercial positioning
5. **Musk v. OpenAI closes** — $150B damages claim, Altman accused of lying; jury deliberates Monday. Could force restructuring before $1T IPO
6. **OpenAI vs Apple cracking** — OpenAI exploring legal options over Siri partnership; the platform-vs-model-provider fight is now litigation-grade
7. **Career ladder compression** — Class of 2026 entering a labor market where entry-level tech roles are automated. Troy's career strategy implication: leverage AI directly rather than wait for traditional onramps

## [2026-06-03] ingest | Gemini 3.2 Flash: What We Know Before Google I/O 2026

**Source:** Build Fast with AI by Satvik Paramkusam (2026-05-18) — pre-release leak analysis

**Pages created (1):**
- `sources/S — Gemini 3.2 Flash Before Google IO 2026` — full source summary
- `entities/Gemini` — Google's model family (Pro/Flash/Flash-Lite), 2026 lineage table

**Pages updated (1):**
- `entities/google` — major expansion: AI position, Gemini cadence, I/O 2026 lineup, regulatory

**Key findings:**
1. **Flash eating Pro** — leaked Gemini 3.2 Flash matched/exceeded 3.1 Pro on creative coding (SVG, Three.js) at ~1/6 input cost in blind Arena evals. If real, compresses the whole tier ladder
2. **Pure Inference Economics** — leaked $0.25/$2.00 pricing tuned for query-heavy/response-moderate workloads (search, assistant). Cheap high-volume tier optimized for what dominates real usage
3. **Sub-quarterly cadence** — 3.0 Flash (Dec 25) → 3.1 Flash-Lite (Mar) → 3.2 Flash (May). Flash treated as continuous software product. Lesson: version-pinned, provider-agnostic infra
4. **Caveat** — Arena evals skewed to creative coding; page written pre-I/O. Needs a post-I/O reconciliation pass to mark confirmed vs wrong

## [2026-06-03] ingest | Harness, Scaffold, and the AI Agent Terms Worth Getting Right

**Source:** Hugging Face Blog by Sergio Paniego & Aritra Roy Gosthipaty (2026-05-24) — glossary

**Pages created (2):**
- `sources/S — Harness Scaffold and Agent Terms` — full source summary
- `concepts/Agent Harness and Scaffolding` — model vs scaffold vs harness; orchestrator/skills/sub-agents; RL training terms
- `concepts/Context Engineering` — context-window design; short/long-term memory; training vs inference cost asymmetry

**Pages updated (3):**
- `concepts/Agentic AI` — added precise "Agent = Model + Harness" definition section
- `concepts/Coding Agent Architecture` — vocabulary note splitting scaffold vs harness
- `entities/Claude Code` — "agentic harness around Claude" canonical example

**Key findings:**
1. **Agent = Model + Harness** — the one equation. model ≠ harness ≠ product; two products on the same model differ by harness choices
2. **Scaffold vs harness** — scaffold = what the model works from (prompt, tools, parsing, memory); harness = the execution loop (calls model, handles tools, decides when to stop). Distinction matters most in training pipelines
3. **Vocabulary backbone** — grounds everything agent-related already in the wiki; cleanly separates capabilities the wiki had been blurring
4. **RL training loop** — environment → trainer → reward → updated policy; rollout/trajectory, verifiable vs learned reward, rubrics

## [2026-06-03] ingest | Henry: The AI Worker That Does Real IT Work (9 Enterprise Predictions)

**Source:** ai.work blog by Maor Ezer, CEO (2026-05-28) — vendor thesis

**Pages created (2):**
- `sources/S — Henry AI Worker Enterprise Predictions 2026` — full source summary
- `entities/Henry` — ai.work's AI IT worker product
- `concepts/AI Workforce` — agents as enterprise labor layer; system-of-action vs system-of-record

**Pages updated (1):**
- `concepts/AI and Economic Displacement` — added "reshape not reduce" counter-narrative + tension

**Key findings:**
1. **AI as workforce, not feature** — "AI stops being a tool and becomes the operating model." Agents behave like employees across 5–15 systems per workflow
2. **System of action vs system of record** — clean architectural split: records (ERP/CRM/ITSM) stay source of truth; AI executes across them. Mirrors compute/storage, microservices/monolith
3. **Labor + tech budgets merge** — CFOs ask "humans vs agents?" financially. The displacement pathway stated in plain accounting terms
4. **Tension flagged** — vendor's optimistic "jobs reshape not reduce" sits against 81K data where job fear was the strongest negative-sentiment predictor. Same trend, opposite valence — noted on both pages
5. **Orchestration as new middleware** — dozens of agents per enterprise → demand for a horizontal governance/identity/logging/rollback layer

## [2026-06-03] lint | Health check (post 3-source ingest; first since 2026-04-11)

**Scope:** ~95 wiki pages. Triggered after Gemini/Agent-glossary/Henry ingest (+ prior May 16 batch).

**Issues found + fixes applied:**
1. **Naming inconsistency (FIXED)** — new pages used `[[Agent OS]]`; vault convention is lowercase `[[agent-os]]` (used by 6 existing pages). Standardized refs in `Henry`, `AI Workforce`.
2. **High-reference missing page: Gemma (FIXED)** — referenced 15+ times (Open-Source AI, architecture pages, Gemini, google, NVIDIA) with no entity page. Created `entities/Gemma`.
3. **High-reference missing page: agent-os (FIXED)** — referenced from 6+ pages, no page. Created scaffold `projects/agent-os` (first Projects entry); flagged for Troy's spec.
4. **Data discrepancy (RECONCILED)** — Gemini 3.2 blog cites Gemma 4 "27B 4-bit"; Open-Source Landscape lists 31B dense. Noted on `Gemma` page; 31B treated canonical pending I/O notes.

**No orphans** found in the new entity/concept cluster — all inbound-linked.

**Open gaps (NOT auto-fixed — need Troy or web lookup):**
- **`overview.md` missing entirely** — CLAUDE.md specifies a high-level synthesis page; never created. ~95 pages now exist with no top-level synthesis. Biggest structural gap.
- **Unresolved project links:** `job-nexus`, `peptide-app`, `automateflows` — referenced across many pages, no pages (same situation agent-os was in).
- **Unresolved concept/entity links:** `alignment`, `Anthropic Interviewer`, `Claude.ai`, `LoRA`, `QLoRA`, `scaling laws`, Anthropic `Conway` — referenced but no pages.
- **Stale-pending (time-sensitive, need refresh):** Musk v. OpenAI verdict (was "jury deliberates Monday" ~May 18 — likely decided by now); Samsung 18-day strike (started May 21 — resolution status?); Gemini 3.2 Flash page is pre-I/O (May 18) and needs post-I/O reconciliation (I/O was May 19–20).

## [2026-06-04] maintain | overview.md + gap-fill (lint follow-up)

Acted on the 2026-06-03 lint's open gaps.

**Pages created (5):**
- `overview.md` — **the missing top-level synthesis** (8 themes: model convergence → harness era → inference economics/capex → AI workforce → human dimension/81K → safety/governance → infra/memory → Troy's projects). Resolves the biggest structural gap. Linked from `index` top.
- `concepts/alignment` — resolves a long-standing unresolved link; ties Anthropic mission to in-the-wild sycophancy/overrestriction and agent-era stakes
- `concepts/scaling laws` — predictability + compute-optimal, then 2026 qualifications (architecture gains, inference-time scaling, data wall, economics flip)
- `concepts/LoRA` — extends (not duplicates) `Fine-Tuning`: adapter mechanics, rank, multi-adapter serving, merge-vs-keep
- `concepts/QLoRA` — 4-bit-base extension; training-memory quantization vs inference quantization distinction

**Index updated:** added `[[overview]]` pointer at top; 4 new concepts listed.

**Note on method:** LoRA/QLoRA were already substantively covered inside `Fine-Tuning`; created compact dedicated pages that extend rather than duplicate (per "prefer updating / one-thing-per-page / compound knowledge"). Did NOT auto-create `job-nexus`/`peptide-app`/`automateflows` (need Troy's specs).

## [2026-06-04] maintain | Web reconciliation of 3 stale-pending items

Resolved the lint's time-sensitive items via live web search (US web, current as of June 2026).

**1. Gemini 3.2 Flash leak → shipped as Gemini 3.5 Flash (I/O, May 19).** The leak's *thesis* held ("Flash beats Pro") but the *version number was wrong* (3.2 → 3.5). Real benchmarks: Terminal-Bench 2.1 76.2%, GDPval-AA 1656 Elo, MCP Atlas 83.6%, CharXiv 84.2%; ~4× faster output; GA via Google Antigravity + Gemini API; 3.5 Pro in testing (~June). Unconfirmed: $0.25/$2.00 pricing, Liquid Glass UI.
- Updated: `entities/Gemini` (lineage + reconciliation section), `sources/S — Gemini 3.2 Flash Before Google IO 2026` (post-I/O callout), `entities/google` (what-shipped).

**2. Musk v. OpenAI → dismissed (May 18).** Unanimous jury, <2 hrs, on a 3-year statute of limitations; merits never reached. Altman/Brockman/OpenAI cleared; Musk appealing. Clears restructuring path toward rumored $1T IPO.
- Updated: `entities/OpenAI`, `entities/Elon Musk`, `entities/Sam Altman`, `sources/S — Top Tech News May 15 2026`.

**3. Samsung strike → averted (May 20).** Government-mediated wage deal, ~74% union approval, ended a 5-month dispute; some chip bonuses >~$340K. Supply risk contained; chip/non-chip pay gap persists.
- Updated: `entities/Samsung`, `concepts/AI Capex Buildout`, `sources/S — Top Tech News May 15 2026`.

**Also updated:** `overview.md` open-threads (3 items marked resolved; added Gemini 3.5 Pro GA + leak-calibration as new watch items).

**Method note:** web facts cited inline as markdown links (not raw/ sources). Original predictions preserved with outcomes appended (per "note the evolution, don't silently overwrite"). The pre-I/O Gemini page is **kept** as a deliberate leak-vs-reality calibration record.
