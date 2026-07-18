---

type: video-summary 
source: https://www.youtube.com/watch?v=pUHA_jNwuYE 
channel: How I AI (Claire Vo) 
date: 2026-05-20 
duration: ~45:21 
tags:

- knowledge
- ai-engineering
- spec-driven-development
- notion-ai
- coding-agents
- ci-cd
- engineering-management
- codex
- workflow-automation

---

# Spec-driven development: the AI engineering workflow at Notion | Ryan Nystrom

> Ryan Nystrom, engineering manager and hands-on builder at Notion, joins host Claire Vo to walk through three concrete AI-powered workflows that have fundamentally changed how his team operates. Across a 45-minute conversation, Ryan demonstrates how a custom Notion AI agent auto-generates daily standup pre-reads, how Notion's internal "Boxy" system lets engineers @mention Codex from a task comment and receive a full pull request in 20 minutes, and how spec-first development — dictating ideas into Whisper, converting them to structured markdown specs, and letting agents implement and verify features autonomously — has become his model for the future of software engineering. The episode is a rare look inside a team that has fully operationalised AI agents rather than merely experimenting with them.

<iframe width="560" height="315" src="https://www.youtube.com/embed/pUHA_jNwuYE" frameborder="0" allowfullscreen></iframe>

---

## Project Afterburner and the Joy of Tinkering Again

Ryan joined Notion in December 2024 after the acquisition of Campsite, the team communication tool he co-founded. He now manages a team of six to seven engineers while still writing code himself — a deliberate choice he argues every engineering manager, director, and even CTO should make in this moment. Despite more than 20 years in software, he describes the past year as the most energising of his career: he has changed IDEs, terminals, and tools more than ten times, and wakes up every day excited to build.

The anchor project he demonstrates throughout the episode is "Afterburner" — an internal push to cut Notion's CI pipeline time to a quarter of its current duration. Ryan was given the project not because he is an infrastructure expert, but precisely because he isn't: his team's reputation for speed and AI-first thinking made them the right group to bring fresh eyes and "puppy dog energy" to a slow CI problem. The project hub in Notion captures metrics, decisions, bug logs, and meeting notes, and it is this infrastructure that sets up the three workflow demonstrations.

---

## Automated Standup Pre-reads with a Custom Notion AI Agent

Ryan's team runs a daily standup, but they long ago abandoned the hollow ritual of going around the room reciting task lists. Instead, a custom Notion AI agent — internally nicknamed the "Hot Potato agent" — runs at 9:00 a.m. every morning, 24 hours of activity and compiling a rich pre-read document before anyone joins the call.

The agent fans out across multiple sources simultaneously using sub-agents (a feature Ryan notes is powerful but not widely promoted yet): it reads the project's Slack channel, queries the Honeycomb observability platform via MCP to pull the latest CI metrics, looks up recently closed Notion tasks and merged pull requests, and reads yesterday's meeting transcript. It then structures all of this into a formatted briefing — CI speed trends, decisions made, progress on sub-goals, bugs, open questions, and risks — and posts a link to Slack before the meeting starts.

The agent's instructions are written in plain natural language and specify output format, data sources, tone (brief and fun), and write permissions carefully: it is allowed to edit only the meetings database, not the broader task or project databases that the whole company uses. Ryan even used the agent to help configure its own Honeycomb MCP integration — he screenshot the observability query and told the agent to OCR it and update its own instructions.

The practical outcome is that Ryan can code up until the moment the standup begins. The meeting itself becomes a conversation about decisions, discoveries, and problems rather than a status recitation. Ryan observes that the automated surfacing of every engineer's contributions — regardless of how vocal or quiet they are — democratises visibility and draws out insights from engineers who would never have volunteered them unprompted.

---

## Background Agents and the "Boxy" System

The second workflow centres on Notion's internal VM-based system, called "Boxy," which allows engineers to invoke Codex (or Claude Code) directly from a Notion task comment using an @mention. Rather than switching to a terminal, writing a prompt, and waiting, an engineer can describe a feature request or bug fix in a few sentences inside the task where the work is already tracked, tag the agent, and walk away.

Ryan demonstrates this with a real example from the morning of recording: a friend texted him asking if Notion's tab block could support "copy link to tab." Ryan opened the task, wrote three or four sentences describing the feature (including an edge case about tab-switching on fresh page loads), dropped in a screenshot showing where the button should live, noticed the delete button's hover state wasn't turning red, and added that to the notes too. He then @mentioned Codex. Eleven minutes later, Codex replied with a pull request link, a preview environment URL, and screenshots it had taken of its own UI verification. When a type-check failure surfaced in CI, Ryan replied in plain English — "I don't know what's going on here" — and Codex explained its reasoning and fixed the types.

Ryan is explicit that Boxy is the result of Notion building real internal developer tooling rather than just using off-the-shelf agent UIs. The boxes are VMs with Codex and Claude Code pre-installed, triggered from within the product rather than from a separate tool. He argues that any large engineering organisation that does not yet have a VM strategy and background agent strategy is leaving significant AI adoption velocity on the table.

---

## Spec-First Development: The Workflow Ryan Calls the Future

The third and most conceptually substantial workflow is spec-driven development — a pattern Ryan's team arrived at while rebuilding Notion AI's agent harness after reaching what he describes as "tool and instruction fatigue" with an over-bloated system prompt.

The process starts not with code but with a voice memo. Ryan opens Whisper and talks through how a feature should work — what he calls a "yap session." He feeds the transcript to Codex, points it at the team's existing spec library so it can learn the format, and asks it to produce a structured markdown spec. After a few revisions, that spec is committed directly to the codebase in an `agent-specs/` subfolder alongside the source code it describes.

The spec is comprehensive: it includes behavioural descriptions, pointers to relevant code locations, and — critically — a verification section that describes exactly how the feature should be tested. When Ryan is ready to implement, he opens Codex again, points it at the spec file, and says "build it." Because the spec is so complete, Codex one-shotted the first feature he tried this on, returning several thousand lines of code after a couple of hours. Ryan reviewed, played with it, confirmed it was correct, and merged.

What makes this model powerful beyond the initial build is version control. The spec file has its own git history. When requirements change, Ryan updates the spec first and then asks the agent to align the implementation — the spec is the source of truth, not the code. Claire notes that the plain English spec is also readable by non-engineers, making it a useful asset for marketing, documentation, or cross-functional alignment in a way that code alone never could be.

Ryan's broader thesis is that engineers are evolving into systems thinkers and architects. The most important skill is no longer writing the implementation but designing the verification loop: if you can give an agent a way to run itself, test itself, and confirm correctness, you can go arbitrarily deep on autonomous implementation. He observes, wryly, that technical design documents and spec writing are not new — teams have always written them — but previously those docs sat waiting for a calendar slot and a review meeting. Now they get built the moment they are ready.

---

## Key Takeaways

- **Spec-first development turns plain English into a source of truth** — writing the spec before the code gives agents the full context to one-shot implementations and gives the team a version-controlled changelog for how features actually work.
- **Custom agents are most powerful when given precise, scoped permissions** — restricting what databases an agent can write to prevents accidents while still letting it do meaningful work.
- **CI speed is a mathematical multiplier on AI output** — a slow pipeline is a hard ceiling on how many agent-generated PRs can actually ship; improving CI compounds across every human and agent on the team.
- **Background agents should be triggered from inside your existing workflow** — embedding agent invocation in task comments (rather than a separate tool) reduces friction and keeps context in one place.
- **Meeting prep is a form of toil that AI should fully absorb** — offloading standup compilation protects engineers' deep work time and reduces a key burnout vector for managers.
- **Engineering managers should keep writing code** — the current era rewards hard technical skills; managers who stay hands-on are better equipped to guide teams and evaluate AI output.
- **Verify sycophancy by demanding a cited counter-argument** — asking the model to defend its reasoning under pushback is more reliable than asking "are you sure?", which tends to produce capitulation rather than genuine reconsideration.
- **Automated context democratises team visibility** — surfacing every engineer's contributions equally, regardless of their communication style, brings out insights that would otherwise stay quiet.

---

## Notable Quotes

> "I didn't start with writing code. I didn't start with anything. I just started with an empty markdown document. I actually just opened up Whisper and started yapping about how this feature should work."

— **Ryan Nystrom** (~[32:20](https://www.youtube.com/watch?v=pUHA_jNwuYE&t=1940))

> "Your agent is never going to complain when you ask it to do this five minutes before the meeting starts."

— **Claire Vo** (~[13:30](https://www.youtube.com/watch?v=pUHA_jNwuYE&t=810))

> "It is more relaxing and it's more fun and I feel like I'm getting more done. It's weird to have this like win-win-win."

— **Ryan Nystrom** (~[15:10](https://www.youtube.com/watch?v=pUHA_jNwuYE&t=910))

> "I view our job as engineers evolving into systems thinkers and architects — and most importantly it's the verification loop. If it can't verify correctness, that's the first thing you should go and build."

— **Ryan Nystrom** (~[38:10](https://www.youtube.com/watch?v=pUHA_jNwuYE&t=2290))

> "No more waiting for the meeting. No more waiting for review. Ship it. Have a verification loop. Debated on the merits of it being live and working versus the theoretical merits of it sitting in a document waiting for everybody's calendar to open up."

— **Ryan Nystrom** (~[40:20](https://www.youtube.com/watch?v=pUHA_jNwuYE&t=2420))

---

## Chapters

|Time|Topic|
|---|---|
|00:00|Introduction to Ryan Nystrom|
|02:48|How AI has upended 12+ years of the same working routine|
|04:30|Project Afterburner: Notion's push to cut CI time to a quarter|
|09:00|Why high-frequency, high-quality meetings beat lower-frequency standups|
|11:10|How automated context surfaces every engineer's work equally|
|12:15|Why cutting meeting prep is a burnout protection mechanism|
|14:26|The case for engineering managers writing code|
|16:13|Inside "Boxy": Notion's internal VM-based background agent system|
|20:30|Old World vs. New World code review|
|24:51|Prompting Codex from Notion comments|
|32:00|Spec-first development: writing and checking agent specs into the repo|
|35:10|The spec as changelog: version control for how a feature actually works|
|37:53|How engineers' roles are evolving|
|39:00|Lightning round: why Codex, why CI speed, prompting strategies|
|45:21|Where to find Ryan|

---

## Resources

**Workflow write-ups**

- [Ryan Nystrom's 3 Notion Workflows for Engineering Velocity](https://www.chatprd.ai/how-i-ai/ryan-nystrom-notion-workflows-for-engineering-velocity) — ChatPRD blog post with full workflow walkthroughs
- [Implement Features Using Spec-First Development and an AI Coding Agent](https://www.chatprd.ai/how-i-ai/workflows/implement-features-using-spec-first-development-and-an-ai-coding-agent)
- [From Notion Task to GitHub Pull Request in 20 Minutes with a Coding Agent](https://www.chatprd.ai/how-i-ai/workflows/from-notion-task-to-github-pull-request-in-20-minutes-with-a-coding-agent)
- [Automate Daily Standup Preparation with a Custom Notion AI Agent](https://www.chatprd.ai/how-i-ai/workflows/automate-daily-standup-preparation-with-a-custom-notion-ai-agent)

**Tools**

- [Notion AI](https://www.notion.com/product/ai) — the AI layer embedded in Notion
- [Notion Custom Agents](https://www.notion.com/blog/introducing-custom-agents) — launched February 2026; the feature Ryan uses for the Hot Potato agent
- [Codex (OpenAI)](https://openai.com/codex) — background coding agent Ryan uses for Boxy and spec implementation
- [Claude Code (Anthropic)](https://claude.ai/code) — also installed on Boxy VMs alongside Codex
- [Honeycomb](https://www.honeycomb.io/) — observability platform; queried via MCP by the standup agent for CI metrics
- [Whisper (OpenAI)](https://openai.com/research/whisper) — voice transcription used to capture initial feature "yap sessions"

**Related episode**

- [How Stripe built "minions" — AI coding agents that ship 1,300 PRs weekly | Steve Kaliski](https://www.chatprd.ai/how-i-ai/stripes-ai-minions-ship-1300-prs-weekly-from-a-slack-emoji) — referenced in the CI speed discussion

**Find Ryan**

- X: [@ryannystrom](https://x.com/ryannystrom)
- GitHub: [rnystrom](https://github.com/rnystrom)