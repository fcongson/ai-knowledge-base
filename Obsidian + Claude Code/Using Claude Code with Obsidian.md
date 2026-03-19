---
type: guide
created: 2026-03-20
tags:
  - ai
  - obsidian
  - claude-code
  - setup
  - how-to
---

# Using Claude Code with Obsidian

> How to install and actually use it with your notes

## What you're setting up

You're connecting:

- **Obsidian** → where your notes live (your vault = a local folder)
- **Claude Code** → an AI assistant that can read and work with those notes

> Claude works directly on your vault folder

---

## 1. Install Claude Code

These steps assume a typical CLI setup. Choose the method that fits your environment.

### Step 1: Install Node.js (if needed)

Check if you already have it:

```bash
node -v
```

If not:
- Install from: https://nodejs.org (LTS version recommended)
- or (Mac users):

```bash
brew install node
```

### Step 2: Install Claude Code

**Option A — Using npm (recommended default)**

```bash
npm install -g @anthropic-ai/claude-code
```

**Option B — Using Homebrew (Mac)**

If you use Homebrew:

```bash
brew install --cask claude-code
```

Then verify installation:

```bash
claude --version
```

### Step 3: Authenticate

```bash
claude login
```

Follow the browser flow to sign in.

---

## 2. Locate your Obsidian vault

Your vault is just a folder on your computer.

In Obsidian:
- Go to **Settings → Files & Links**
- Find your vault location

OR

- Right-click your vault → "Reveal in Finder"

You'll need this path.

**Example:**
```
/Users/yourname/Documents/Obsidian/Second Brain
```

---

## 3. Open your vault in Claude Code

In your terminal:

```bash
cd /path/to/your/vault
claude
```

Now Claude is operating **inside your notes folder**.

This is the key step.

---

## 4. How Claude interacts with your notes

Once inside your vault, Claude can:
- read `.md` files
- edit notes
- create new notes
- summarize across multiple files
- reorganize content

You are effectively giving AI access to your second brain.

---

## 5. First simple commands to try

Start with low-risk, high-value actions.

**Clean up a messy note**
```bash
claude "Clean up this note into a clear, structured markdown document" file.md
```

**Summarize a meeting note**
```bash
claude "Summarize this into key points, decisions, and next steps" meeting.md
```

**Create a new note from ideas**
```bash
claude "Turn these rough notes into a clear idea document" ideas.md
```

**Work across multiple notes**
```bash
claude "Review these files and identify common themes and insights" *.md
```

---

## 6. Example: Using Claude with your actual workflow

**Step 1 — You write a messy note in Obsidian**

```markdown
# onboarding issues

people confused about setup
docs outdated
too many steps maybe

ideas:
- checklist?
- video?
- simplify env setup
```

**Step 2 — Run Claude on it**

```bash
claude "Turn this into a clear problem summary with suggested solutions" onboarding.md
```

**Step 3 — Claude improves it**

Now your note becomes something like:
- clear problem definition
- structured insights
- actionable next steps

You didn't have to write it perfectly—just capture it.

---

## 7. Editing files safely

Claude can modify files, so a few simple practices help:
- Start by **reviewing outputs before saving changes**
- Use version control (Git) if your team is comfortable
- Or duplicate notes before major changes

**A safe pattern:**
1. "suggest changes" first
2. then apply them

---

## 8. Using Claude across your vault

Once comfortable, you can do more interesting things:

**Find decisions**
```bash
claude "Scan all notes and list key decisions made" *.md
```

**Identify gaps**
```bash
claude "What questions remain unanswered across these notes?" *.md
```

**Create a summary doc**
```bash
claude "Create a summary of this project from these notes" project-*.md
```

---

## 9. When to use Obsidian vs Claude

| Use Obsidian when | Use Claude when |
|---|---|
| capturing thoughts | things are messy |
| writing quickly | you need clarity |
| browsing and linking notes | you want synthesis across notes |
| | you're turning notes into something reusable |

---

## 10. Keep it simple at the start

You don't need advanced workflows. Just do this:

1. Write notes in Obsidian
2. Open your vault in Claude
3. Ask Claude to improve or summarize your notes
4. Save what's useful

That alone is enough to get value.

---

## 11. Common pitfalls

- Trying to automate everything immediately
- Letting AI overwrite notes without review
- Over-structuring your vault early
- Not actually capturing raw notes (this breaks everything)

---

## 12. One habit that makes this work

> Capture first, refine later

If your notes exist, Claude can improve them.
If they don't, AI can't help.

---

## Related

- [[Second Brain Quick Start]]
- [[Thinking with Obsidian + Claude Code]]
