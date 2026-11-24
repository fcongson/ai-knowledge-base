---
type: video-summary
source: https://www.youtube.com/watch?v=MN9dGgmLyso
channel: Matt Pocock
date: 2026-10-02
duration: ~01:05:36
tags:
  - ai
  - ai-agents
  - agentic-engineering
  - claude-skills
  - verification
  - software-factory
  - media
---

# LIVE: Poteto (creator of pstack) on shipping 1,000's of PR's a month at SpaceX

> Matt Pocock interviews Lauren Tan (poteto), a former Meta React engineer who now works on Cursor's agents window and Grokbot at SpaceX AI, about her talk on shipping about 2,500 pull requests in one month. She explains how she built trust in coding agents step by step, why verification is the most important skill, how a constrained codebase keeps agents on track, and how she connects outside signals such as bug reports to coordinator agents that merge their own work overnight.

<iframe width="560" height="315" src="https://www.youtube.com/embed/MN9dGgmLyso" frameborder="0" allowfullscreen></iframe>

---

## The Trust Ladder and Distilling Your Own Expertise

Lauren describes her path as a ladder of trust in agents. After leaving Meta, she spent a month on a side project and noticed she was spending many hours micromanaging a single agent. She wrote early skills to teach the agent to work more like her, but she could not measure whether those skills helped. That early work became the basis of her skill library, pstack, even though she did not know it at the time.

When she joined Cursor in March and worked on performance problems in the agents window, she saw the same limit again. She was the "meat proxy" between her agent and Chrome DevTools. The skill that moved her up the ladder was not a writing or planning skill. It was a verification skill that let the agent run the app and see the result of its own work.

Matt and Lauren also agree that domain expertise matters more as models improve. In Lauren's view, the bottleneck is no longer the agent. The bottleneck is how clearly a person can state intent and goals. A doctor or lawyer who is a little technical, and who has a clear vision, can build strong products because they can express that vision precisely. They connect this to language: choosing precise words (such as "tautological tests" or "TDD") gives the agent a compressed set of meaning to work from.

## The Michelin Kitchen Metaphor

Lauren does not like the term "software factory" because factories suggest volume, not quality or craft. She prefers a Michelin kitchen. A home cook does everything alone. When a whole family crowds into the kitchen, the work becomes stressful unless it is divided well. A head chef does not cook every dish but organizes the whole kitchen, orders ingredients, and stays responsible for the outcome and the restaurant's reputation.

The parallel for engineers is direct. You may no longer write every line, but your name stays on the result. How you set up your skills, environment, and codebase are the new ingredients. Lauren extends the metaphor: once one kitchen works well, you can open a second and third restaurant, with each large project acting as its own restaurant that you visit in turn.

## Verification and the Environment

Verification is, in Lauren's words, the most important skill in any toolkit. It gives the agent "hands and eyes": it can run the code, use it like a person would, and take traces and snapshots. This is what turns a set of prompts into a real loop, because the agent can judge its own work and iterate. It also enables hill climbing, where an agent keeps improving something against a score or rubric. Every app at Cursor and SpaceX AI now has an auto-maintained verification skill.

### Deterministic parts go into a CLI

Lauren built a CLI inside her verification skill that wraps Playwright and the Chrome DevTools protocol. Without it, each agent rebuilt the same verification scripts differently, which wasted time and context. Her principle is to move the deterministic parts of a task into code and leave only the parts that need judgment to the agent. The same idea applies to migrations, where code mods that walk the abstract syntax tree can do mechanical changes more reliably than an agent.

### Constrain the codebase

Matt and Lauren agree that the engineer's new job is mostly to improve the environment. Lauren compares it to sharpening knives. If you never invest in tools, everything is slow and you are stuck micromanaging. She also links this to TypeScript type narrowing: you shrink the space of valid code until there is only one obvious way to do things. Her team's internal Electron framework, Dune, uses strict lint rules and conventions such as one directory per feature. This came from early versions of Grokbot that had eight god files of 10,000 lines or more. Whenever she sees an agent make a mistake, she asks how to turn it into a lint rule or structure so the mistake cannot happen again.

## Scaling to Thousands of PRs

The prerequisite for high PR volume is the environment above. Lauren then separates an inner loop (agents writing code toward an intent) from an outer loop (external information such as Slack messages, Linear tickets, X posts, and emails). If she has to carry that information to the agent herself, she is the bottleneck. Grokbot routines watch those sources and pass context to Cursor Projects, which are cloud coordinator agents that delegate to sub-agents. Grokbot is her outer loop and Cursor Projects are her inner loop.

A coordinator also sees patterns across many reports. A burst of related bug reports about slow performance, for example, can reveal one underlying cause that separate agents would each patch differently or duplicate. Lauren sometimes has a routine append findings to a document instead of fixing them at once. She reviews that buffer every few days and groups related items, which prevents pure execution mode from hiding the larger picture. Much of the PR volume is also "gardening": small, continuous improvements, not 2,500 new features. She runs more than ten coordinators, each owning an area such as app performance, user-reported bugs, or an experimental rewrite.

## Review, Dark Factories, and One-Way Doors

Lauren does not read every PR. She samples, as a quality supervisor would, and corrects the environment when several agents repeat the same shortcut. Her "full autopilot" mode in pstack spawns several verifier agents per PR. They fuzz the running app, click through it, look for regressions, fix what they find, and repeat before the PR lands. It uses many tokens, and she tunes the number of verifiers. She reviews the commit history in the morning and reverts or adds lint rules if needed. She says the first night was frightening, and that she now sleeps better.

Matt notes that this differs from the original "vibe coding" idea, where the code is ignored. Here the code and environment are essential. They agree a dimmer switch is a better picture than a fully dark factory, and Lauren's restaurateur analogy fits: the owner still visits and tastes the food sometimes.

On one-way-door changes that cannot be undone, such as data loss, Lauren says the answer depends on how verifiable the domain is. Software is often verifiable, and she admits she does not have a full answer for domains that are hard to verify. She expects new agent-oriented languages, mentioning Bend, that combine programming with proofs.

## Skills as Encoded Workflows

Skills are, at the end of the day, markdown and process written as language. Lauren and Matt describe their libraries (pstack and Matt's skills) as complementary and encourage people to combine them. Everyone should keep their own set of knives. Lauren recommends mining past chat transcripts for the places where you had to correct or intervene, then turning those patterns into skills or lint rules. She built a pstack skill called Recall to carry context from one chat into the next. As models improve, she expects skills to shrink and focus on workflow steps instead of implementation details.

---

## Key Takeaways

- **Verification is the most important skill** — an agent that can run and observe its own work removes you as the proxy and makes true loops possible.
- **Trust comes before scale** — running many agents works only after one agent is reliable enough to leave alone.
- **Change the environment, not just the prompt** — every repeated agent mistake should become a lint rule, a convention, or a structural constraint.
- **Put deterministic work in code** — wrap repeatable steps in a CLI or script and keep agent judgment for the parts that need it.
- **Connect the outer loop to the inner loop** — let routines pull bug reports and requests into coordinator agents so you stop ferrying context.
- **Use coordinators to see patterns** — grouping related reports prevents duplicate fixes and exposes root causes; a buffer document helps you see the big picture.
- **Sample instead of reviewing everything** — scrutinize a subset of PRs, and fix the environment when several agents repeat the same problem.
- **Domain expertise gains value** — clear intent and precise language are now the bottleneck, which favors people who know their field deeply.
- **Verifiability limits autonomy** — one-way-door domains are harder to automate unless agents can truly verify the work.

---

## Notable Quotes

> "the bottleneck is no longer the agent, right? It becomes your ability to express your intent in your goals in a clear way"

— **Lauren Tan** (~[06:34](https://www.youtube.com/watch?v=MN9dGgmLyso&t=394))

> "how do I make the easy thing the right thing?"

— **Lauren Tan** (~[04:22](https://www.youtube.com/watch?v=MN9dGgmLyso&t=262))

> "how do I turn this into a lint rule?"

— **Lauren Tan** (~[32:49](https://www.youtube.com/watch?v=MN9dGgmLyso&t=1969))

> "It's just language."

— **Lauren Tan** (~[63:26](https://www.youtube.com/watch?v=MN9dGgmLyso&t=3806))

---

## Chapters

The video description has no chapter markers, so these timestamps are approximate and inferred from the transcript.

| Time | Topic |
|------|-------|
| 00:00 | Introduction and the 2,500 PR talk |
| ~02:11 | The trust ladder and Lauren's path to Cursor |
| ~06:34 | Why domain expertise and precise language matter |
| ~13:07 | The Michelin kitchen metaphor |
| ~20:46 | Verification as the key skill |
| ~26:15 | The verification CLI and determinism |
| ~32:49 | Constraining the codebase (Dune, lint rules) |
| ~40:28 | Inner and outer loops, scaling to 2,500 PRs |
| ~47:02 | Coordinator agents, Grokbot, and Cursor Projects |
| ~54:41 | Reviewing by sampling and full autopilot |
| ~60:10 | One-way doors and verifiable domains |
| ~63:26 | Skills as workflows, combining pstack with other skills |

---

## Resources

- Re-upload: this conversation also appears as "Lauren Tan Reveals How 30+ AI Agents Ship PRs While You Sleep" at https://www.youtube.com/watch?v=6hxp0SpGxz8 (probably a third-party repost; the channel was not checked).
- Lauren Tan's early skills repo — an open-source repo on her GitHub that she names aloud as "potato slash noodle"; the exact URL is not in the description, so find it manually.
- pstack — Lauren's skill library for agent workflows, including verification, full autopilot, and Recall.
- Grokbot — SpaceX AI's personal agent with connectors and routines, used as the outer loop.
- Cursor Projects — cloud coordinator agents that delegate to sub-agents.
- Bend — an agent-oriented language that combines programming with proofs.
