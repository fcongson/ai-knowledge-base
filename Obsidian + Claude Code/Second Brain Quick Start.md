---
type: quick-start
created: 2026-03-20
tags:
  - knowledge
  - ai
  - obsidian
  - claude-code
  - quick-start
  - second-brain
---

# Second Brain Quick Start

> Obsidian + Claude Code — up and running in minutes

---

## What this is

Two tools, one simple idea:

- **Obsidian** — where you write and store notes (just a folder on your computer)
- **Claude Code** — AI that reads and improves those notes

> Capture in Obsidian → Refine with Claude

---

## Get set up

**1. Install Obsidian**

Download from https://obsidian.md, create a vault (just a folder), and write your first note.

**2. Install Claude Code**

```bash
npm install -g @anthropic-ai/claude-code
```

**3. Authenticate**

```bash
claude login
```

**4. Open your vault**

```bash
cd /path/to/your/vault
claude
```

That's it. Claude is now working inside your notes.

---

## Your first 10 minutes

1. Write a rough note about something you're working on right now — don't worry about format
2. Run Claude on it:

```bash
claude "Clean this up into a structured note with key points and next steps" your-note.md
```

3. Review what it produces and save what's useful

That's the whole workflow.

---

## Useful commands to copy-paste

```bash
# Clean up a messy note
claude "Clean this up into a clear, structured markdown document" file.md

# Summarize a meeting note
claude "Summarize this into key points, decisions, and next steps" meeting.md

# Find themes across notes
claude "Review these files and identify common themes and insights" *.md
```

---

## One rule to remember

> Capture first, refine later.

Write messy notes. Claude helps you clean them up.
If you don't capture anything, AI can't help.

---

## Go deeper

- [[Thinking with Obsidian + Claude Code]] — the philosophy behind this approach
- [[Using Claude Code with Obsidian]] — full install options, workflow examples, and safety tips
