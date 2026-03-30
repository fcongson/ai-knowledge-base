---
type: video-summary
source: https://youtu.be/fcFOYzMeG7U?si=K9m4lbcmzLrdfQEz
channel: How I AI
date: 2026-01-28
duration: 55:47
tags:
  - ai
  - agents
  - clawdbot
  - moltbot
  - autonomous-agents
  - security
---

# My Honest Experience with Clawdbot (now Moltbot) — Claire Vo

> Claire Vo gives an unfiltered, first-person account of installing and testing Clawdbot (now renamed Moltbot) — a viral open-source autonomous AI agent that can run code, spin up sub-agents, join video calls, and take real actions on your machine. The episode opens with her actually inviting it onto the podcast via Telegram.

<iframe width="560" height="315" src="https://www.youtube.com/embed/fcFOYzMeG7U" frameborder="0" allowfullscreen></iframe>

> **Note on naming:** The tool was called Clawdbot at the time of recording. It has since been renamed **Moltbot**.

---

## What is Clawdbot / Moltbot?

An open-source autonomous AI agent that runs locally on your machine. Unlike chat-based AI tools, it can:
- Execute code and take real actions on your computer
- Spin up sub-agents to parallelise tasks
- Join video calls
- Access your files, messaging apps, and accounts
- Be controlled via Telegram (including voice messages)

---

## Installation: Not as Simple as Advertised

The "one-liner" install is misleading. Claire walks through:
- Dependency chaos and setup friction
- Hardware requirements worth knowing before starting
- Security warnings that should not be dismissed
- Why you should create **separate accounts** (e.g. a dedicated Google Workspace account) before granting access — not your primary accounts

---

## Security: The Real Conversation

This is the core tension of the episode. Giving an autonomous agent access to your machine, calendar, email, and messaging apps is genuinely risky. Claire's framework:

- **Separate accounts** — create a sandboxed Google/email account specifically for the agent
- **Scoped permissions** — only grant OAuth access to what you actually need it to do
- **Telegram as the control layer** — using a messaging app as the interface adds a deliberate friction point between you and the agent's actions
- **Model choice matters** — different models have different cost and capability trade-offs for agentic tasks (Claude Sonnet 4.5 referenced)
- Security concerns don't go away — she revisits them at the end of the episode

---

## Where It Was Great

### Research Tasks
- Clawdbot excels at autonomous research — e.g. Reddit analysis for market research
- Can browse, aggregate, and synthesise information across sources without hand-holding

### Voice Messaging Workflow
- Sending voice messages via Telegram to trigger agent tasks works surprisingly well
- Useful for on-the-go delegation without needing to type detailed prompts

### Building a Next.js App
- Claire used it to build a Next.js app to display her Clawdbot chat history
- Deployed via Vercel
- A good example of the agent completing a real, multi-step development task end-to-end

---

## Where It Struggled

### Time & Scheduling
- Clawdbot has poor awareness of basic time concepts
- Family calendar management went noticeably wrong during testing

### Speed / Latency
- Latency is one of the biggest friction points for autonomous agents
- The gap between sending a request and getting a result breaks the "assistant" feel

### Email & Impersonation
- Email mishaps during testing — the agent sent things it shouldn't have
- Highlights why prompting matters more than ever with autonomous agents: vague instructions lead to unintended real-world actions

### Prompting Overhead
- Autonomous agents require more precise prompting than chat tools
- The cost of a bad prompt is higher when the agent takes real actions

---

## Product Perspective

Claire steps back from user to product thinker:
- The current open-source version is powerful but rough — installation, security setup, and reliability are all barriers for mainstream users
- The consumer-friendly version of this (polished UX, safe defaults, managed permissions) hasn't been built yet — and whoever builds it will have a significant product opportunity
- Compares the space to Devin for coding agents

---

## Key Takeaways

- **Autonomous agents are real and available now** — but they require deliberate setup and security thinking
- **Separate accounts before you start** — don't grant access to your primary email, calendar, or accounts
- **Prompting stakes are higher** — with an agent that takes real actions, vague prompts have real consequences
- **Latency is the UX problem** — speed is what separates a useful agent from a frustrating one
- **Research > scheduling** — async, research-heavy tasks are where current agents shine; real-time, time-aware tasks are still weak

---

## Chapters

| Time | Topic |
|------|-------|
| 00:00 | Introduction — inviting Clawdbot to join the podcast via Telegram |
| 02:07 | What Clawdbot is and how it works |
| 03:50 | Installation process and hardware requirements |
| 07:26 | Security considerations and creating separate accounts |
| 08:03 | Setting up Telegram integration |
| 10:02 | Use case: Clawdbot as an EA |
| 13:08 | Configuring the AI agent |
| 14:31 | Granting Google Calendar access |
| 18:03 | Testing Clawdbot as a personal assistant |
| 23:16 | Speed frustrations |
| 23:54 | Email mishaps and impersonation issues |
| 26:33 | Why prompting matters more than ever with autonomous agents |
| 27:32 | Quick recap and family calendar management gone wrong |
| 32:11 | Using voice messaging with Clawdbot |
| 36:14 | Product thoughts |
| 37:06 | Building a Next.js app to show chat history |
| 42:29 | Research capabilities and Reddit analysis |
| 46:10 | Final thoughts on security concerns |
| 48:00 | The future of AI assistants and who will build them |
