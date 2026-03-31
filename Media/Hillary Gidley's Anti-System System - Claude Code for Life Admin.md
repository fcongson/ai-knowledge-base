---
type: video-summary
source: https://www.youtube.com/watch?v=LJ1YZ3Uek3g
channel: How I AI
date: 2026-03-31
duration: ~55:00
tags:
  - ai
  - claude-code
  - productivity
  - personal-ai
  - automation
  - life-admin
  - agentic-workflows
---

# Hillary Gidley's Anti-System System — Claude Code for Life Admin

> Hillary Gidley, entrepreneur and new mum, returns to *How I AI* to share her "anti-system system" for using Claude Code to manage her day, to-do list, and life admin — without the overhead of setting up and maintaining a complex productivity system.

<iframe width="560" height="315" src="https://www.youtube.com/embed/LJ1YZ3Uek3g" frameborder="0" allowfullscreen></iframe>

---

## What is the Anti-System System?

A philosophy for personal AI that prioritises zero setup and zero maintenance cost. The core tenets:

- Start with the simplest (jankiest) version of any workflow and validate it's actually useful before enriching it
- Let the AI observe your real behaviour over time rather than defining preferences upfront
- Complexity must earn its keep — only add integrations after you've proven you'll use them
- Hillary estimates her hit rate on workflows she *thinks* she'll use is about 20%, which is exactly why she doesn't invest heavily upfront

---

## Capturing To-Dos: The Phone Back-Tap

No AI involved at this stage — just a frictionless capture method:

- iPhone back-tap shortcut (double tap) triggers a dictation box
- Voice-dictated task gets saved directly to a reminders inbox file
- Setup via: **Settings → Accessibility → Touch → Back Tap → Double Tap → your Shortcuts shortcut**
- Shortcut itself: add a "Dictate Text" action in the Shortcuts app
- Hillary has shared the full Figma walkthrough at **writerbuilder.com/howai**

---

## Planning the Day with Claude Code

Typing `plan my day` in Claude Code triggers a workflow that pulls from three sources:

### Reminders file
A markdown file Claude maintains by organising captured to-dos into categories. Hillary never edits it directly — Claude does.

### Preferences file
A file Claude has built up by *observing Hillary's behaviour over time*, not by her defining preferences explicitly. It tracks things like when she's most effective, when certain work keeps her up too late, and scheduling constraints (e.g. pumping schedule, childcare coverage). Observed preferences reflect real behaviour rather than aspirational behaviour.

### Calendar
Claude pulls what's already on the calendar for the day and scaffolds around it.

The output is a recommended schedule that breaks big tasks into the smallest possible actionable step — e.g. instead of "do the baby passport", just "book the post office appointment (10 minutes)".

---

## The "Yappers API"

Rather than building integrations to track what she's doing throughout the day, Hillary simply narrates to Claude as she works:

- Claude Code stays open in the right third of the screen all day
- She talks to it about what she's working on, what she finished, what changed
- Claude observes and logs this into a daily note (another markdown file)
- The daily note contains: the planned schedule, a running log of what's actually happening, and a gap analysis between intent and output

This replaces any need for OAuth connections, webhooks, or screen-monitoring — human narration is the integration layer.

---

## End-of-Day Reflection

Claude tracks the delta between what was planned and what actually got done. Hillary can ask it questions like:

- *"What are you observing about the gap between what I'm trying to get done and what I'm actually doing?"*
- *"What patterns are you seeing?"*

Claude surfaces things like: "building is crowding out writing" or "you list three priorities but only number one gets real time."

This feedback loop drives gradual improvement without any deliberate system design — the system evolves from observed reality.

---

## What to Automate: The 10x Framework

For any task, ask: *"If I were 10x better at this, would it have 10x the impact?"*

- **No** → automate it
- **Yes** → invest human time in it

Applies at two levels:
1. Is the task itself worth human time?
2. Within a task, which sub-parts are worth human time?

Example: preparing a talk — ideation and narrative are irreplaceable human work; slide formatting is not. The framework also shifts based on where someone is on a learning curve — moving pixels in PowerPoint is valuable practice early in a career, but not once you've reached saturation.

---

## Building Workflows from First Principles

Hillary demos building a returns-reminder workflow entirely through conversation:

1. Describe the problem to Claude in plain English ("I keep missing return deadlines and I hate dealing with returns")
2. Let Claude ask a few clarifying questions, then tell it to use its judgement
3. Claude proposes solutions, asks what access it would need, and builds the script and skill file itself
4. Result: a `/returns` slash command that checks email for recent purchases, adds return deadlines to reminders, and includes retailer-specific drop-off info

No prior setup, no specialised knowledge, no Python scripting required.

---

## The "Recording On" Skill

A neat solution to demoing personal workflows publicly without doxxing yourself:

- A skill file tells Claude to anonymise any identifying information before displaying it on screen
- Claude still reads from all real files and follows all real workflows
- Consistent anonymisation — if someone is called "Person A" once, they're Person A throughout
- Turned off with `recording off`

Broader application: B2B software demos that need to show production data without exposing customer information.

---

## Key Takeaways

- **Reduce friction at every step** — capture, planning, and review should all be as low-effort as possible
- **Let the AI observe, don't define preferences upfront** — real behaviour beats aspirational behaviour
- **Validate before you invest** — run the janky version for a week before connecting APIs or building complexity
- **The Yappers API beats complex integrations** — narrating your screen is often the right integration strategy
- **Screenshots are underrated** — a screenshot shared with Claude is often faster and more reliable than an integration
- **You don't need to understand the terminal** — start anyway; the power becomes obvious once you're in it
- **One thing a day** — the only way to build the habit of reaching for Claude Code is repetition

---

## Notable Quotes

> "For any possible task, if I were 10 times better at it, would it have 10 times the impact? And if the answer to that is no, then I just automate it. And if the answer to that is yes, those are the things that I want to put more time and effort into."

— **Hillary Gidley** (~[36:14](https://www.youtube.com/watch?v=LJ1YZ3Uek3g&t=2174))

> "The best advice that I have heard and that I try to give to people is just try to do one thing with it every day. You just need to build the muscle memory so that you start to reach for it and you start to have your brain rewired so that you think, 'Oh, the alien that lives in my computer could probably help me with this.' You can intellectually understand it, but you still just need to do it every day and eventually it will start to feel like second nature to you."

— **Hillary Gidley** (~[50:00](https://www.youtube.com/watch?v=LJ1YZ3Uek3g&t=3000))

---

## Chapters

| Time | Topic |
|------|-------|
| 00:00 | Introduction and life updates — new mum, new business |
| ~04:00 | The anti-system philosophy |
| ~08:00 | iPhone back-tap shortcut for capturing to-dos |
| ~12:00 | Plan my day — demo and walkthrough |
| ~18:00 | How preferences are observed and maintained |
| ~22:00 | The Yappers API — narration as integration |
| ~27:00 | End-of-day reflection and gap analysis |
| ~32:00 | What to automate: the 10x framework |
| ~38:00 | Building a returns workflow from scratch |
| ~44:00 | The recording mode skill |
| ~50:00 | Getting started with Claude Code — advice for beginners |
