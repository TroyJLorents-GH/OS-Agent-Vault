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
