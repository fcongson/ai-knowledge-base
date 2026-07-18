---
type: video-summary
source: https://youtu.be/MZZCW179nKM?si=Y4nOiIDrFN2mxFiG
channel: How I AI
date: 2025-10-22
duration: 27:23
tags:
  - knowledge
  - ai
  - claude
  - claude-code
  - claude-skills
  - workflows
  - automation
---

# Claude Skills Explained: How to Create Reusable AI Workflows — Claire Vo

> A practical breakdown of Claude Skills — Anthropic's feature for creating reusable, on-demand AI workflows — covering what they are, how to structure them, and how to build them using Claude Code and Cursor.

<iframe width="560" height="315" src="https://www.youtube.com/embed/MZZCW179nKM" frameborder="0" allowfullscreen></iframe>

---

## What Are Claude Skills?

Claude Skills are **markdown files with task-specific instructions, metadata, and optionally linked files** that can be called on demand inside Claude Code, the Claude web app, or the desktop app.

They solve the reusable workflow problem: if you find yourself copying and pasting the same prompts over and over, Claude Skills give you a structured, repeatable way to invoke those workflows without the manual overhead.

### How They Differ from Claude Projects and Custom GPTs

| | Claude Projects / Custom GPTs | Claude Skills |
|---|---|---|
| Context | Always loaded for every chat in that project | Called on demand, only when needed |
| Scope | General-purpose context for a variety of tasks | Task-specific instructions |
| Flexibility | Static per project | Dynamic — invoke any skill in any conversation |

Skills are not a replacement for Projects — they're complementary. Projects give you persistent context; Skills give you portable, reusable task definitions.

---

## Anatomy of a Claude Skill

A Skill is a **folder** containing:

1. **A markdown file** — the core skill definition with:
   - Metadata (name, description, trigger)
   - Step-by-step instructions in natural language
2. **Linked files** (optional) — referenced from the markdown:
   - Example inputs/outputs
   - Templates
   - Additional instructions
3. **Python scripts** (optional) — for validation or consistent code execution, rather than relying on the LLM to generate the script each time

> Claire's take: natural language definition is a feature, not a limitation. If models are great at natural language, workflows should be defined that way — not as rigid if/then automations.

---

## How to Create Skills

### Option 1: Claude's Built-in Skill Creator
- Use Claude's web interface to generate the skill file
- Good for getting started quickly
- Demonstrated from scratch in the episode

### Option 2: Cursor (More Efficient)
- Claire's preferred workflow for building and iterating on skills
- Faster to edit, version, and validate multiple skills
- Use Python validation scripts to test skills before uploading

### Uploading
- Skills are uploaded via the Claude web interface
- Once uploaded, they're available across Claude Code, web, and desktop

---

## Example Skills Built in the Episode

- **Changelog → Newsletter** — takes a product changelog and formats it into a reader-friendly newsletter
- **Demo Notes → Follow-up Email** — turns raw notes from a sales or product demo into a structured follow-up email
- **PRD Generation** — a recurring use case for product managers (referenced as a core ChatPRD workflow)

---

## Key Takeaways

- **Skills replace prompt libraries** — if you have a Google Doc or GitHub repo full of saved prompts you paste in manually, Skills are the structured version of that
- **Task-specific > general-purpose** — the more precisely scoped a Skill is, the more reliably it performs
- **Linked files extend context intelligently** — examples and templates bundled with a Skill help Claude produce more consistent output without bloating every conversation
- **Python scripts add determinism** — for analytical or technical tasks, bundling a script eliminates LLM variability in how the code is generated each time
- **Natural language is the interface** — Skills are just markdown; no workflow builder, no node graphs, no code required to define them

---

## Chapters

| Time | Topic |
|------|-------|
| 00:00 | Introduction |
| 01:39 | What are Claude Skills and how do they work? |
| 08:30 | The structure of Claude Skills files |
| 11:00 | Demo: creating Skills using Claude's built-in skill creator |
| 16:08 | A more efficient workflow: creating Skills with Cursor |
| 17:42 | Using Python validation scripts |
| 18:37 | Testing Skills with Claude Code |
| 20:52 | Creating a changelog-to-newsletter Skill |
| 22:16 | Creating a demo-to-follow-up-email Skill |
| 23:45 | Uploading Skills to the Claude web interface |
| 26:04 | Conclusion and summary |
