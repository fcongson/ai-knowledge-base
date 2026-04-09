---

type: video-summary 
source: https://www.youtube.com/watch?v=7huCP6RkcY4 
channel: Cole Medin 
date: 2026-04-10 
duration: ~18:35 
tags:

- claude-code
- llm-knowledge-base
- obsidian
- second-brain
- ai-agents
- memory-system
- karpathy

---

# I Built Self-Evolving Claude Code Memory w/ Karpathy's LLM Knowledge Bases

> Cole Medin walks through Andrej Karpathy's viral framework for building personal LLM knowledge bases — using a compiler analogy to explain how raw content flows into an interconnected wiki — then pivots to his own extension of the idea: a self-evolving memory system for Claude Code that captures internal session conversations rather than external articles, automatically growing smarter with every coding session.

<iframe width="560" height="315" src="https://www.youtube.com/embed/7huCP6RkcY4" frameborder="0" allowfullscreen></iframe>

---

## Karpathy's LLM Knowledge Base Architecture

Andrej Karpathy's viral tweet described a workflow for building personal knowledge bases using LLMs. The core insight is simple: instead of relying on an AI to retrieve information from the open web, you ingest curated external content — articles, papers, research — into your own structured system where an agent can query it on demand. Karpathy's tool of choice is Obsidian, which Cole also uses as his "canvas" for second-brain work.

Karpathy structures the entire system around a **compiler analogy**, making the architecture intuitive for developers:

- **Source code** → Raw input. Articles and papers dumped into a `/raw` folder as unprocessed markdown.
- **Compiler** → An LLM that processes the raw content: writing summaries, creating cross-references, and organising knowledge into structured articles.
- **Executable / Wiki** → The compiled, queryable output. Obsidian's graph view visualises how documents link together, letting an agent traverse connections to produce richer answers.
- **Test suite / Linting** → Health checks that find gaps in coverage, stale data, items sitting in `/raw` that haven't been promoted yet, and broken internal links.
- **Runtime** → The agent actively querying the wiki to answer questions.

One of the most interesting details Karpathy shares is that he doesn't need fancy RAG or a vector database. The LLM is good enough at maintaining an `index.md` file — a high-level map of all folders and resources — that the agent can navigate the knowledge base through simple file reads and backlink traversal. This keeps the whole system beautifully lean.

---

## Adapting the Architecture for Internal Data

Cole's key contribution is recognising that the most valuable "raw" data isn't external articles — it's the conversations you're already having with your coding agent. Every Claude Code session produces decisions made, gotchas discovered, and patterns identified. Currently, all of that context evaporates when the session ends or the context window compacts.

His system, [claude-memory-compiler](https://github.com/coleam00/claude-memory-compiler), mirrors Karpathy's architecture exactly but swaps the data source:

|Karpathy (external)|Cole (internal)|
|---|---|
|Articles / papers in `/raw`|Claude Code session logs in `/daily-logs`|
|LLM compiles to wiki|Claude Agent SDK extracts concepts & connections|
|Obsidian graph for querying|Same Obsidian vault, same graph view|
|Manual ingestion via Web Clipper|Automatic capture via Claude Code hooks|

The result is a codebase-specific knowledge base that compounds over time. Every project gets its own memory. The agent remembers architectural decisions, learns which patterns to avoid, and surfaces that context instantly at the start of each new session — without needing to scan git logs or spin up sub-agents to analyse the codebase.

---

## Claude Code Hooks: How the System Actually Runs

The entire mechanism is driven by three Claude Code hooks configured in `settings.json` — no additional integrations or installs required.

### Session Start Hook

When a new Claude Code session begins, a lightweight Python script loads two files into the agent's context: `agents.md` (a global rules file explaining the entire memory system to the agent so it understands what it's been "dropped into") and `knowledge/index.md` (the actively maintained index of all wiki articles). With these two files, the agent immediately knows where to look for relevant prior knowledge.

### Pre-Compact and Session End Hooks

Both hooks do the same thing: whenever context is about to be lost — through a manual session close or an automatic memory compaction — the latest messages from the conversation are sent to the **Claude Agent SDK** running as a separate process. That process summarises the conversation into a structured daily log entry covering decisions made, lessons learned, and action items. This is the equivalent of the raw folder in Karpathy's system.

### The Flush Process

Once a day, a flush script processes the accumulated daily logs and extracts **concepts** and **connections** from them, promoting the most important insights up into the main wiki. This is the compile step. The agent's primary search target is the wiki, but it can also reach back into the daily logs for full conversation history when needed.

---

## The Compounding Knowledge Loop

The real payoff of this architecture is a self-reinforcing feedback loop. Each question asked of the agent causes it to synthesise across multiple wiki articles and file a new answer — which itself becomes part of the knowledge base. Every new Claude Code session adds more raw material to the daily logs. The flush process periodically enriches the wiki. Over time, the agent's answers get more precise, faster, and more contextually aware of the specific project — without any manual maintenance effort from the developer.

Cole demonstrates this live: after asking a question about what to watch out for in a codebase, the agent answers in roughly 10 seconds by consulting the knowledge base directly, citing specific KB articles. Without the system, the same question would have required scanning git history and spawning sub-agents to analyse source files — a much slower process, especially at scale.

Importantly, the system is also self-documenting and customisable. Because `agents.md` describes the full architecture, Claude Code itself can guide you through customising the prompts used in the flush and compile steps. You can adjust exactly what gets extracted from sessions and how knowledge articles are formatted — and the agent you're customising it with already understands the system it's operating inside.

---

## Key Takeaways

- **Karpathy's compiler analogy maps cleanly to knowledge management** — raw input → LLM compile → queryable wiki → runtime queries is a model any developer can reason about immediately.
- **No vector database needed** — an LLM-maintained index file is sufficient for an agent to navigate a personal knowledge base through plain file reads and backlinks.
- **Internal conversation data is more valuable than external articles** — the decisions and lessons from your own coding sessions are uniquely high-signal and currently thrown away by default.
- **Claude Code hooks are the only infrastructure required** — session start, pre-compact, and session end hooks handle everything automatically with no external services.
- **The Claude Agent SDK runs in the background for free** — it uses your existing Anthropic subscription, so no additional API keys or cost setup is needed.
- **The system is per-codebase and self-improving** — each project gets its own growing memory, and the compounding loop means the agent gets measurably better at answering project-specific questions over time.
- **Full customisability over built-in Claude Code memory** — unlike the native memory system, every prompt and extraction step is editable, and Claude itself can guide the customisation.

---

## Notable Quotes

> "The most valuable raw data isn't external articles. It's your own conversations with your agents."

— **Cole Medin** (~[0:30](https://www.youtube.com/watch?v=7huCP6RkcY4&t=30))

> "I thought I had to reach for fancy RAG, but the large language model has been pretty good about auto-maintaining index files."

— **Cole Medin** (quoting Karpathy) (~[6:30](https://www.youtube.com/watch?v=7huCP6RkcY4&t=390))

> "It's a very self-contained system that can improve itself."

— **Cole Medin** (~[16:20](https://www.youtube.com/watch?v=7huCP6RkcY4&t=980))

> "The questions that we ask our agent are just going to get better and better answers over time."

— **Cole Medin** (~[18:10](https://www.youtube.com/watch?v=7huCP6RkcY4&t=1090))

---

## Chapters

|Time|Topic|
|---|---|
|0:00|Karpathy LLM Knowledge Bases|
|2:32|How it Works|
|6:01|Data Flow and Architecture|
|8:40|My Claude Code Memory System|
|9:19|InsForge (sponsor)|
|10:43|Setting Up the System|
|11:04|Obsidian Setup and Vault Configuration|
|12:16|Claude Code Hooks|
|16:51|The Compounding Knowledge Loop|
|18:35|Outro|

---

## Resources

- [claude-memory-compiler](https://github.com/coleam00/claude-memory-compiler) — Cole's open-source repo; one-shot prompt sets up the full memory system inside any Claude Code project
- [Karpathy's original tweet thread](https://x.com/karpathy/thread/2039805659525644595) — the viral post that inspired this architecture
- [Karpathy's LLM knowledge base gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) — the PRD-style prompt you can send directly to a coding agent to build the full system
- [Dynamous AI Second Brain Bootcamp](https://dynamous.ai/second-brain-bootcamp) — Cole's community and 4-hour workshop covering building a full second brain on Claude Code and the Claude Agent SDK
- [InsForge](https://insforge.dev/) — sponsor; open-source platform bundling database, auth, storage, AI model routing, and hosting for coding agents (promo code: `InsForgePromo`)
- [Obsidian](https://obsidian.md/) — the markdown-based knowledge base app used as the vault and graph viewer throughout the demo (free)