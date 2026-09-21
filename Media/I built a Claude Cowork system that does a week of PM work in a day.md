---
type: video-summary
source: https://www.youtube.com/watch?v=p2qmX6TM0kw
channel: How I AI
date: 2026-09-21
duration: ~44:00
tags:
  - claude-cowork
  - product-management
  - ai-productivity
  - personal-ai-system
  - automation
  - self-improving-systems
  - notion
  - onboarding-plugins
---

# I built a Claude Cowork system that does a week of PM work in a day

> Claire Vo interviews Daniel Blum, a product manager at Melio (a B2B payments company), who has built a Claude Cowork-based productivity system that runs a weekly prep, a daily morning brief, and weekly self-improvement loops, with Notion as a read-only dashboard. He claims it lets him do in a day what used to take a week, and he has scaled the approach across Melio through a "Workstation" onboarding plugin. It matters because it is a concrete, reproducible pattern for turning an AI assistant into a self-maintaining operating system for knowledge work.

<iframe width="560" height="315" src="https://www.youtube.com/embed/p2qmX6TM0kw" frameborder="0" allowfullscreen></iframe>

---

## The problem: PM overhead and the two rules of a powerful system

Daniel frames the problem as the coordination overhead of product management: endless tasks arising from Slack, meetings and action items, all competing with the in-depth work and focus time he actually wants. Earlier tools such as Gemini Gems improved specs and research, but did nothing for the chaos of day-to-day coordination. Cowork was the unlock, though he stresses the tool itself is not the point, and says Codex or ChatGPT's work mode could serve too.

What matters, in his view, are two rules. First, the system must be able to rewrite its own core files, so it keeps improving. Second, it needs connections and integrations into as much of your ecosystem as possible. He also makes the point that this is doable under the constraints of an average PM: limited tokens, budgets and company-mandated tools (Melio moved from Gemini Enterprise to Claude Enterprise and Cowork only a few months earlier).

## Notion as a read-only dashboard, and how context is built

His Notion board has three sections: Top of Mind (large initiatives), This Week (current priorities) and Inbox (items surfaced from Slack, email and calendar). Cowork built the board itself, replacing a messy Google Doc, and manages it on his behalf. Daniel now treats Notion as essentially read-only: he looks at it for focus and occasionally marks something done, but Claude does the maintenance.

The board works because Claude knows him well. He built a scalable context structure with a file for every topic, area of work, goal and colleague, seeded through links, decks and lots of Whisper dictation, then kept fresh by a recurring update every few weeks. As a demonstration, a "demo" skill let him anonymise his real environment in one prompt, swapping his manager's name for "your manager" and his top initiative for "headline feature", which showed how much context the system holds.

## Weekly prep and the morning brief

The weekly prep is a recurring task composed of several skills. Each Sunday it pulls from Notion, calendar, Slack and Granola meeting transcripts, recommends what to focus on, proposes adding, removing or finishing items across Top of Mind, This Week and Inbox, and then walks through upcoming meetings asking how much prep each needs (a full prep task, a quick reminder, or none). The system also knows he is inbox-zero on Slack and email, so an item that has disappeared is likely done or read.

The daily morning brief summarises yesterday's meetings from Granola transcripts with a one-liner and any action items, then does something distinctive: it scans recent Slack, email and notes for context it does not understand, such as an unknown term, file, milestone or goal, and asks him about it. In the live demo it flagged the term "settlement cap", explained what it inferred from the thread, and offered to save the definition to context. Claire calls this genuinely new, since company jargon is not in a model's training data and proactively asking for definitions keeps the context clear.

## Return on investment and daily use

Daniel runs roughly 70 to 80% of his computer time through Cowork, because anything done outside it is context the system does not capture. He started with Chrome browser use heavily but leans on connectors and MCPs as more become available, keeping Chrome for tools without integrations. On ROI, he is candid that the early weeks are frictionful and trust is low, but the value compounds if you contextualise ruthlessly and centralise work in the harness. His headline claim is that he can do a week of work in a day, and, more importantly, do deeper, more data-backed research and competitive analysis than he could when moving fast on hunches. Claire adds that the system forces people to learn how to work with Cowork, which matters for anyone building products that may be used through Claude.

## The self-improvement loop

A weekly scheduled task with several skills has Claude help improve the system with minimal effort from Daniel. It has four parts:

- **How my drafts landed:** compares drafts Claude wrote with what he actually sent, and learns from the gap.
- **Skills worth building:** spots recurring activities and suggests turning them into skills (many of his skills originated here, for example a design handoff skill between Cowork and a prototyping tool).
- **Fixes to existing setup:** every skill and recurring task logs feedback and friction, and the loop surfaces the top frictions each week for fixes.
- **Improve:** a critical auditor skill to which he sends tips, posts and articles (often via a Slack channel from his phone), asking whether the idea is real, powerful and needed. Run against Claire's loops episode, it concluded his scheduled tasks were already loops but that he lacked goal loops, which he could adopt.

Claire highlights building telemetry and feedback capture directly into skills as an approach she wishes more people used.

## Scaling to the team with the Workstation plugin

Melio's "Workstation" is an operating-system-style plugin, started for PMs and expanded to all employees, built with several colleagues in Cowork rather than Claude Code. Early attempts had PMs spending days installing dependencies through the terminal, so they insisted on a simple UX built into the chat. The onboarding takes about 15 minutes: it connects tools, confirms role, maps colleagues and management, reads calendar and Slack, creates the user's writing voice, and captures goals. It is distributed as a shared plugin.

Daniel traces the lesson back to "Spectacular", a spec-writing Gem he built a year earlier. Watching other PMs struggle with a tool tailored to how he works taught him that even internal tools need guided, accessible onboarding. Claire's advice: every company should build a "bootstrap my personal AI" skill or plugin so everyone starts from the same page.

## What is still missing, and where the time goes

The remaining 20 to 30% comes down to running in the cloud independent of his computer being on. His workaround is a Slack channel that Claude polls, but it still needs to be online. He is also building towards Claude acting on simple tasks itself, by having it infer how tasks get resolved (for example, an answered Slack question means done) so it can eventually handle scheduling, file requests and quick replies. With his reclaimed time he doubles down on in-depth work, customer conversations and research, plus improving the system itself. On frustration with Claude, he admits to "Claude rage", especially when Whisper fails to convey his exclamations.

---

## Key Takeaways

- **The tool matters less than two properties** — a powerful system must be able to rewrite its own core files and integrate with as much of your ecosystem as possible.
- **Contextualise ruthlessly up front** — dictate, share links and decks, and keep per-topic context files updated; early ROI is poor but compounds.
- **Make your dashboard read-only** — let Claude maintain Notion (or equivalent) so you only consult it for focus.
- **Have Claude ask what it does not know** — the morning brief flags unfamiliar terms and goals and saves your answers to context, so internal jargon stops being a blind spot.
- **Centralise your work in one harness** — doing 70 to 80% of work through Cowork means the system captures the context that makes it useful.
- **Build feedback loops into everything** — compare drafts to what you sent, log friction in every skill, and review weekly to spot new skills and fixes.
- **Use a critical auditor for AI tips** — an "Improve" skill filters hype from useful ideas so you adopt what fits without drowning in it.
- **Scale with guided onboarding, not documentation** — a chat-native plugin that sets up connectors, voice and goals in about 15 minutes drove adoption across the company.

---

## Notable Quotes

> "I'm really able to do in a day now what used to take me a week. But more than that, I'll say it's a lot of deeper work."

— **Daniel Blum** (~[22:00](https://www.youtube.com/watch?v=p2qmX6TM0kw&t=1320))

> "You got to go through the pain of switching your systems and it's not going to be as efficient... but if you get to the next level, not only will you have a system that works better for you, but everybody will have more skills."

— **Claire Vo** (~[24:00](https://www.youtube.com/watch?v=p2qmX6TM0kw&t=1440))

> "It's a UX built into the flow into the chat... it basically does everything for you."

— **Daniel Blum** (~[33:00](https://www.youtube.com/watch?v=p2qmX6TM0kw&t=1980))

> "Good UX and simplicity is critical even for internal teams and PMs and technical people."

— **Daniel Blum** (~[36:00](https://www.youtube.com/watch?v=p2qmX6TM0kw&t=2160))

---

## Chapters

| Time | Topic |
|------|-------|
| 00:00 | Daniel's background and the PM overhead problem he needed to solve |
| 03:30 | His AI stack at Melio |
| 05:00 | The two rules that make any AI system genuinely powerful |
| 06:00 | The Notion board Cowork built for him (and manages on his behalf) |
| 07:30 | How he contextualizes Claude with voice memos, links, and recurring updates |
| 09:00 | His weekly prep automation |
| 11:00 | His morning brief |
| 15:00 | How Claude flags unknown internal terms and saves them to context |
| 17:30 | Running 70% to 80% of his workday through Cowork |
| 19:00 | Chrome connector vs. MCPs for tools without integrations |
| 20:00 | The real ROI question: why the early weeks feel slow, and why you push through anyway |
| 25:00 | Scaling the system to the team with the Workstation plugin |
| 26:30 | The self-improvement loop |
| 31:00 | How the Improve skill separates actually useful AI tips from the hype |
| 32:00 | The Workstation onboarding flow, and the UX lesson from distributing "Spectacular" |
| 38:00 | The 20% Claude still can't do, and what changes when it can |
| 41:00 | What Daniel spends his reclaimed time on |
| 42:30 | Claude rage |

---

## Resources

- [PM Co-Pilot repo](https://github.com/IamBlum/pm-copilot) — Daniel's downloadable PM system on GitHub
- [Claude Cowork for PMs: My Self-Improving Productivity System](https://www.chatprd.ai/how-i-ai/claude-cowork-for-pms-my-self-improving-productivity-system) — blog walkthrough of the episode
- [Create a Meta-Workflow to Continuously Improve Your AI Assistant's Performance](https://www.chatprd.ai/how-i-ai/workflows/create-a-meta-workflow-to-continuously-improve-your-ai-assistant-s-performance) — the self-improvement loop workflow
- [Build a Self-Improving AI Morning Brief to Capture Action Items and Learn Company Jargon](https://www.chatprd.ai/how-i-ai/workflows/build-a-self-improving-ai-morning-brief-to-capture-action-items-and-learn-company-jargon) — the morning brief workflow
- [Automate Your Weekly Planning with an AI-Powered PM Assistant](https://www.chatprd.ai/how-i-ai/workflows/automate-your-weekly-planning-with-an-ai-powered-pm-assistant) — the weekly prep workflow
- [How the founder of Morning Brew built a Claude content machine | Alex Lieberman](https://www.lennysnewsletter.com/p/how-the-founder-of-morning-brew-built?utm_source=publication-search) — related self-learning "write like me" loop
- [From a $6.90 newsletter to $3M API: Memelord | Jason Levin](https://www.lennysnewsletter.com/p/from-a-690-newsletter-to-3m-api-how?utm_source=publication-search) — the meme API episode mentioned
- [Daniel Blum on LinkedIn](https://www.linkedin.com/in/blumd/) and [imdanielblum.com](https://www.imdanielblum.com) — where to find Daniel
- [Claire Vo's ChatPRD](https://www.chatprd.ai/) — host's product
