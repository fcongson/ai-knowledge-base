---

type: video-summary 
source: https://www.youtube.com/watch?v=fD4ktSkNCw4 
channel: How I AI 
date: 2026-04-03 
duration: ~37:00 
tags:

- ai
- cursor
- vibe-coding
- prd
- task-management
- context-management
- mcp
- solo-founder
- agentic-workflows

---

# Ryan Carson's 3-Step Playbook — Structured AI Development in Cursor

> Ryan Carson, five-time founder with 20 years of experience, shares his structured playbook for turning "vibe coding" into a scalable process using PRDs, task lists, and custom Cursor rules — making sure he's not just building fast, but building the right things.

<iframe width="560" height="315" src="https://www.youtube.com/embed/fD4ktSkNCw4" frameborder="0" allowfullscreen></iframe>

---

## The Core Problem with Vibe Coding

2025 is the year of the vibe coder — but you can't always vibe your way to a scalable, maintainable product. The most common mistake:

> _"I think the biggest mistake that I do — that everyone does — is they try to rush through the context where you just don't have the patience to tell the AI what it actually needs to know to solve your problem."_

The fix is slowing down at the start. A clear PRD and task list speeds everything up downstream.

---

## The 3-Step System

Ryan uses three custom Cursor Rules files stored in a `.cursor/rules` folder. All three are open-sourced and work with Cursor, Claude Code, Windsurf, Lovable, Roo, and others.

> 📦 **Open-source repo:** [github.com/snarktank/ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks)

---

### Step 1 — Generate a PRD (`create-prd.mdc`)

A **Product Requirements Document** defines what you're building, for whom, and why — before any code is written.

**How to use:**

```
@create-prd.mdc
Here's the feature I want to build: [describe your feature]
Reference these files: [optional: @file1.py @file2.ts]
```

**Key design decisions in the rule:**

- Asks clarifying questions in **dot notation** (e.g. 2.1, 2.2) to prevent the AI bundling multiple questions into one bullet
- Frames output as suitable for **"a junior developer to understand and implement"** — keeps the AI grounded and avoids over-engineering
- Use **MAX mode** in Cursor for more thorough generation on complex features

The AI saves the PRD as a markdown file (e.g. `MyFeature-PRD.md`) in a `tasks/` folder. You can tweak it manually before proceeding.

---

### Step 2 — Generate a Task List (`generate-tasks.mdc`)

Converts the PRD into a detailed, checkbox-based implementation plan.

**How to use:**

```
@generate-tasks.mdc
Now take @MyFeature-PRD.md and create tasks
```

The AI confirms the high-level outline and waits for a "go" before generating subtasks — giving you a checkpoint to course-correct early.

**Output format:**

- Parent tasks (like epics) numbered 1, 2, 3…
- Subtasks numbered 1.1, 1.2, 1.3…
- Sub-subtasks where needed
- Markdown checkboxes `[ ]` for visual progress tracking

---

### Step 3 — Work Through the Task List (`process-task-list.mdc`)

Rules for iterating through tasks **one subtask at a time**, with human approval at each step.

**How to use:**

```
@process-task-list.mdc
Let's start @tasks/MyFeature-tasks.md
```

**Key behaviours enforced:**

- Tackle **one subtask at a time** — never the whole list at once
- Mark each subtask complete immediately after finishing
- **Stop and wait** for user approval (`y` is enough) before proceeding
- Keeps you in the loop to catch linter errors and small regressions before they compound

**Ryan's git strategy:** Commit after completing a parent task if the app is in a working state; hold off otherwise until all tasks are done.

---

## MCP Servers in Cursor

MCPs give Cursor's AI the ability to interact directly with external tools — no manual API calls, no extra tabs.

|MCP|Use Case|
|---|---|
|**Postgres**|Query the database in plain language — no SQL required. Ryan's most-used MCP daily.|
|**BrowserBase**|Control a headless browser in the cloud from Cursor — automates frontend testing and UI bug reproduction.|
|**Stagehand**|Another browser automation MCP.|
|**Prisma / SQLite**|Schema and database management for local/dev projects.|

> _"It just reduces toil… it puts everything in a single interface that you can seamlessly switch through in natural language."_

---

## Repo Prompt — Precise Context Control

**Tool:** [Repo Prompt](https://repoprompt.com/) (Mac, free tier available)

Cursor does some magic in the background with context — Repo Prompt gives you a "glass box" instead. Use it when you need exact control over what the AI sees.

**How it works:**

1. Open your repo and select specific files/folders — watch the token count live
2. Add a prompt and optionally a stored "architect" meta-prompt
3. Click **Copy** — everything is packaged into clean XML tags (file paths, contents, instructions)
4. Paste directly into any model (o3, Claude, Gemini, etc.)

**Best for:** Architectural reviews, heavy refactors, or any task where incomplete context would send the AI down the wrong path.

---

## Key Takeaways

- **Context is everything** — a well-written PRD is the highest-leverage thing you can do before writing a single line of code
- **One subtask at a time** — human-in-the-loop checkpoints prevent rabbit holes and make bugs easier to catch early
- **Nobody really knows this stuff** — the only way to learn is to get in and experiment; stick with one model until you know its quirks
- **Start simple** — a markdown file beats Asana MCP for most things; add complexity only when you've proven you need it
- **AI as force multiplier** — Ryan runs PM, CTO, and engineering roles solo; not as well as specialists, but well enough to build a company

---

## Notable Quotes

> _"As you code and code and code with AIs, you start to realize that they're like a genius PhD student. But they can't seem to connect these really simple, obvious things that you and I know."_

— **Ryan Carson** (~[5:57](https://www.youtube.com/watch?v=fD4ktSkNCw4&t=357))

> _"Nobody really knows how to do this stuff. The only way you're really going to figure it out is by getting in here and getting your hands dirty and see what works."_

— **Ryan Carson** (~[12:39](https://www.youtube.com/watch?v=fD4ktSkNCw4&t=759))

> _"I literally feel like I'm able to do all of it. Am I able to do it as well as a dedicated product manager? No. Am I able to think as deeply as a CTO? No. But I am able for sure to build this company."_

— **Ryan Carson** (~[32:41](https://www.youtube.com/watch?v=fD4ktSkNCw4&t=1961))

---

## Chapters

|Time|Topic|
|---|---|
|00:00|Intro — what Ryan has been building with AI|
|~04:00|Why structure matters — the case against pure vibe coding|
|~07:00|The three Cursor rules files — overview|
|~10:00|Generating a PRD — live demo (yacht club CRM)|
|~15:00|Generating a task list from the PRD|
|~19:00|Working through the task list one subtask at a time|
|~22:00|MCP servers — Postgres, BrowserBase, Stagehand|
|~28:00|BrowserBase demo — headless browser in the cloud|
|~31:00|Repo Prompt — taking control of context|
|~35:00|Lightning round — AI and the future of founding|

---

## Links

- 📁 **Ryan's rule files (GitHub):** [github.com/snarktank/ai-dev-tasks](https://github.com/snarktank/ai-dev-tasks)
- 🐦 **Ryan on X:** [x.com/ryancarson](https://x.com/ryancarson)
- 🌐 **Ryan's site:** [ryancarson.com](https://ryancarson.com/)
- 🎙️ **How I AI podcast:** [howiaipod.com](https://howiaipod.com/)
- 📝 **Episode write-up (ChatPRD):** [chatprd.ai/how-i-ai/ryan-carsons-3-step-playbook](https://www.chatprd.ai/how-i-ai/ryan-carsons-3-step-playbook-for-structured-ai-development-in-cursor)
- 🤖 **ChatPRD** (sponsor): [chatprd.ai/howiai](https://chatprd.ai/howiai)
- 📝 **Notion** (sponsor): [notion.com/howiai](https://notion.com/howiai)