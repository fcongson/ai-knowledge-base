---

type: video-summary 
source: https://www.youtube.com/watch?v=38t5UBCa4OI 
channel: Simon Scrapes 
date: 2026-04-08 
duration: ~17:00 
tags:

- claude-code
- agentic-ai
- developer-tools
- llm-workflows
- ai-automation
- multi-agent-systems

---

# Every Claude Code Workflow Explained (& When to Use Each)

> Simon Scrapes walks through the five core agentic patterns built into Claude Code — from basic sequential conversations all the way to fully autonomous headless execution. The video is aimed at developers who are only using Claude Code one conversation at a time and want to unlock parallelisation, sub-agents, and scheduled automation. Understanding these patterns means the difference between using Claude as a chatbot and running it as a coordinated, largely self-managing team.

<iframe width="560" height="315" src="https://www.youtube.com/embed/38t5UBCa4OI" frameborder="0" allowfullscreen></iframe>

---

## The Built-in Sub-Agents You Didn't Know About

Before getting into the five patterns, there's an important foundation: Claude Code already runs sub-agents automatically, even in a plain single-conversation session. There are three baked in by default.

**Explore** is a fast, read-only scout that runs on Haiku — Anthropic's lightest model. When you ask something like "how does my authentication flow work?", Claude will often spin up Explore in the background to read through your file structure and return a summary, keeping your main conversation's context window uncluttered.

**Plan** activates specifically when you enter plan mode (via `/plan` or Shift-Tab twice). It researches your codebase in its own isolated context window before presenting a strategy, again without bloating the main thread.

**General Purpose** is the workhorse. It runs on Sonnet, has full read-write tool access, and handles complex multi-step tasks that require both reading the codebase and making changes across multiple files.

The key insight is that Claude is routing work to these agents automatically based on task complexity — you don't instruct it to. Each sub-agent gets its own context window, so the main conversation stays clean regardless of how much file-reading is happening behind the scenes.

---

## Pattern 1 — Sequential Flow

Sequential flow is the default mode most people use: one terminal, one Claude Code session, tasks building on each other. You assign task one, wait for the result, then give task two — and because everything lives in the same context window, the output of each step feeds naturally into the next.

A typical example might be: "build me a landing page" → "add a hero image" → "add a contact form." Each instruction is informed by everything that came before it.

The ceiling of sequential flow is the context window, shown as a green bar at the bottom of the terminal. As the session grows longer, Claude starts to lose track of earlier details — a phenomenon Simon calls **context rot**. Two tools help push that ceiling back: `/clear` wipes the history while keeping you in the session, and `/compact` condenses the conversation into a rolling summary. Well-structured `claude.md` files and modular skills also help, because Claude can load specific reference material when it's needed and discard it when it's not.

Sequential flow is the right choice for linear, iterative work where each task genuinely depends on the last. But when tasks are independent of each other, or when context rot becomes unavoidable, it's time to move to pattern two.

---

## Pattern 2 — The Operator

In the operator pattern, _you_ act as the orchestrator. Instead of one terminal, you open multiple — each running its own Claude Code instance with its own isolated context window and, using the new `-w` flag (worktrees), its own isolated copy of the project on a separate branch.

The example given is a SaaS app with three simultaneous workstreams: building a new onboarding flow, fixing a checkout bug, and redesigning the user settings page. None of these depend on each other, so they can run in parallel without any risk of one session polluting another's context. You'd open three terminals:

```
claude -w "new onboarding flow"
claude -w "fix checkout bug"
claude -w "redesign user settings"
```

Each spawns a dedicated worktree — a clean branch with its own workspace — and drops straight into a Claude Code session. You check in on each terminal periodically, copy findings between windows when needed, and decide when each branch is ready to merge back into main. When you close a worktree session, Claude handles cleanup automatically: if there's no work to keep it removes the workspace; if there is, it prompts you for next steps.

The operator pattern is ideal when you want maximum control and have a handful of parallel, independent tasks. Its limit is human attention — managing more than four or five terminals simultaneously becomes unwieldy.

---

## Pattern 3 — Split & Merge

Split and merge moves the parallelisation _inside_ a single Claude Code session. Rather than you manually opening multiple terminals, Claude itself fans work out to multiple sub-agents, runs them simultaneously, and then synthesises the results back into the main conversation.

The practical example from the video is competitive research: instead of researching five competitors one by one (sequential flow), you ask Claude to research all five and it spins up five sub-agents — one per competitor — all running at the same time. Each returns its findings to the main agent, which then synthesises them into a single report.

Claude can run up to **10 sub-agents concurrently**, queuing any additional tasks until a slot opens. Beyond the three built-in sub-agents (Explore, Plan, General Purpose), you can define custom agents in your `.claude` folder with a name, a description, and a defined set of tools — Claude reads those descriptions and decides when to delegate to them automatically, or you can invoke a specific agent by name.

One powerful application of this pattern is a **builder-validator chain**: one sub-agent builds something, passes the result back to the main agent, which then routes it to a second sub-agent for review. You get a built-in quality check without doing the reviewing yourself.

The hard limitation of split and merge is that **sub-agents cannot communicate with each other** — everything must funnel through the main agent in a hub-and-spoke topology. For tasks where agents genuinely need to coordinate with one another, that's a bottleneck that requires the next pattern.

---

## Pattern 4 — Agent Teams

Agent teams are Claude Code's newest and most advanced coordination mode, released as a research preview alongside Opus. Rather than sub-agents reporting only to a central hub, teammates in an agent team share a **common task list** and can send messages directly to one another. Agent one knows what agent two is working on and vice versa.

To enable it you must add `claude_experimental_agent_teams: 1` as an environment variable in your `settings.json`. You also have to explicitly request an agent team in your prompt — unlike sub-agents, Claude won't choose this mode automatically. Once invoked, Claude determines the team structure, spawns the teammates, and coordinates the work. Inside the terminal you can navigate between teammates with Shift-Up / Shift-Down and message any individual teammate directly, bypassing the team lead entirely if needed.

The cost is significant. Because of the back-and-forth between teammates, the shared task list, and the team lead, token consumption is estimated at **four to seven times** that of a single session. Simon's guidance is clear: agent teams are a last resort, not a default. Reach for them only when the task genuinely requires agents to challenge and adapt to each other — something like a front-end developer, a back-end developer, and a test engineer that all need to coordinate in real time as they build a complex application together.

---

## Pattern 5 — Headless (Autonomous Workflows)

Headless mode is where Claude Code stops being a tool you sit with and becomes a team member that works independently. Using the `-p` flag, you pass a prompt directly on the command line without opening an interactive session. Claude processes the task, executes it with full permissions, and returns the result — no approval prompts, no back-and-forth.

On its own that's useful, but the real power comes from wiring it into your operating system's scheduler (cron on Mac/Linux, Task Scheduler on Windows). A cron job set for 7 a.m. every morning could instruct Claude to read all of yesterday's work, analyse it, and write a summary to `morning-report.md` — ready for you before you've typed a single character. Another example: a script that pulls a video transcript, passes it through Claude with a specific prompt, and writes the resulting social posts to a file for scheduling.

You can also stack guardrails. The `--allowed-tools` flag restricts Claude to specific tool categories (e.g., read-only) if you don't want it making writes autonomously. Members of the community have taken this further with the **RALPH loop** — a pattern that repeatedly feeds the same prompt back in, causing Claude to iteratively refine its own output until it meets a defined standard, sometimes shipping entire projects overnight.

The key constraint is trust and reversibility. Headless works best for tasks where the output is easy to verify and easy to undo. Anything high-stakes or hard to reverse should stay interactive until you've built confidence in Claude's autonomous judgement for that class of task.

---

## Key Takeaways

- **Claude Code is already multi-agent by default** — three built-in sub-agents (Explore, Plan, General Purpose) activate automatically based on task complexity, even in a plain single-conversation session.
- **Sequential flow is powerful but bounded** — context rot is inevitable in long sessions; use `/compact`, `/clear`, and well-structured skills to push the ceiling back.
- **The operator pattern scales you as a human orchestrator** — the `-w` worktree flag makes spinning up isolated parallel sessions fast and clean, with automatic branch management.
- **Split and merge hands parallelisation to Claude** — up to 10 sub-agents can run simultaneously within a single session, ideal for fan-out research or build-then-validate chains.
- **Sub-agents cannot talk to each other** — all coordination must route through the main agent; treat this as an architectural constraint when designing complex workflows.
- **Agent teams enable true cross-agent collaboration** — but at 4–7× the token cost; reserve them for tasks that genuinely require teammates to challenge and adapt to one another.
- **Headless mode turns Claude Code into a scheduled worker** — combine `-p` with cron to run fully automated workflows with no human in the loop.
- **Match the pattern to the task** — most daily work fits sequential flow or the operator pattern; split and merge, agent teams, and headless are progressive power tools for progressively complex needs.

---

## Notable Quotes

> "If you're still using Claude Code one conversation at a time, you're using it wrong."

— **Simon Scrapes** (~[00:04](https://www.youtube.com/watch?v=38t5UBCa4OI&t=4))

> "You'd run teams in parallel, and you'd bring in specialists when required. And Claude Code is built to work exactly like that."

— **Simon Scrapes** (~[00:18](https://www.youtube.com/watch?v=38t5UBCa4OI&t=18))

> "Sub agents can only report back to the main agent — so they can't actually talk to each other. It's a hub-and-spoke methodology."

— **Simon Scrapes** (~[09:45](https://www.youtube.com/watch?v=38t5UBCa4OI&t=585))

> "Agent teams are the most advanced coordination pattern — it is genuinely a game-changer for complex projects, but it should only be used in complex projects because the token usage is extremely high."

— **Simon Scrapes** (~[12:30](https://www.youtube.com/watch?v=38t5UBCa4OI&t=750))

> "This is Claude working without you. You set a task, you walk away, and you come back for the results."

— **Simon Scrapes** (~[16:10](https://www.youtube.com/watch?v=38t5UBCa4OI&t=970))

---

## Chapters

|Time|Topic|
|---|---|
|00:00|Introduction — why single-conversation usage is limiting|
|00:45|Claude's built-in sub-agents (Explore, Plan, General Purpose)|
|02:44|Pattern 1 — Sequential Flow|
|04:38|Pattern 2 — The Operator (multiple terminals + worktrees)|
|07:34|Pattern 3 — Split & Merge (Claude-managed parallelisation)|
|11:50|Pattern 4 — Agent Teams (cross-agent communication)|
|14:22|Pattern 5 — Headless (autonomous scheduled workflows)|

---

## Resources

- [Agentic Academy](https://skool.com/scrapes) — Simon's community with a full Claude Code track covering skills, custom sub-agents, and `claude.md` structure
- [GSD / Get Done by Tash](https://github.com/) — community-mentioned planning framework that splits project briefs into subtasks and executes them; designed for comprehensive projects with a built-in agents folder structure
- [Simon Scrapes YouTube Channel](https://www.youtube.com/@simonscrapes) — follow for future builds and agentic workflow tutorials