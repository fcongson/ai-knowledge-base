---
type: video-summary
source: https://www.youtube.com/watch?v=sU9MW8Ycq2M
channel: Switch Dimension
date: 2026-11-24
duration: ~09:45
tags:
  - knowledge
  - ai
  - agent-skills
  - claude-code
  - spec-driven-development
  - software-engineering
---

# Pocock vs Pstack vs Osmani: Which Skill Pack Wins?

> Rob O'Shaughnessy of Switch Dimension breaks down Addy Osmani's agent-skills repository, which passed 100K GitHub stars, and compares it with Lauren Tan's pstack (from Cursor) and Matt Pocock's skills. Each pack solves a different problem, so the video explains when to use each one. His main argument is that you should not run every skill on every project: match the process to the size of the task, learn the engineering practices inside the skills, and write your own.

<iframe width="560" height="315" src="https://www.youtube.com/embed/sU9MW8Ycq2M" frameborder="0" allowfullscreen></iframe>

---

## Addy Osmani's six-stage lifecycle

Osmani is a long-standing JavaScript figure. He wrote *Learning JavaScript Design Patterns* and led Chrome user experience and web performance work at Google, which produced Lighthouse and Core Web Vitals. He has since moved to Anthropic. Rob's point is that his skills put an experienced engineer's judgement into markdown, so reading them is like studying the practices of a top professional instead of reading a stack of O'Reilly books.

The approach is a traditional software development lifecycle: define, plan, build, test, review, and release. Each stage has its own slash command. Unlike Pocock ("grilling", "wayfinder", "fog of war") or pstack ("potato mode", "arenas"), there is no new vocabulary to learn. Rob thinks this makes it the best fit for an existing team or a large company.

- **Spec** produces a proper PRD covering goals, structure, code style, testing, and boundaries before any code is written.
- **Plan** breaks the work into small, atomic tasks with acceptance criteria.
- **Build** implements one thin vertical slice at a time, with tests, review, and an independent commit for each.
- **`/build auto`** lets you approve the plan once, then runs each task autonomously. Each task is still tested and committed on its own, and the run stops if something fails.

Other commands include `/constraints` (an interview about your quality bar), a web performance audit, and `/code simplify` for code that works but that nobody wants to touch. In total there are 25 skills plus four reviewer roles: staff engineer, test engineer, security auditor, and web performance auditor.

## Inside the skill files

Rob says the skill files, not the slash commands, are the interesting part. Each skill has an **anti-rationalization table**: a list of the excuses an agent produces to skip a stage ("this is too simple to test", "I tested this manually"), each paired with a rebuttal. Anyone who has worked with agents or junior engineers has heard these excuses, and writing them down in advance is a smart move.

Another idea is **doubt-driven development**. For any important decision, the system starts a fresh context whose only job is to question the claim (statement, deduction, doubt, agreement, stop). This works like a devil's advocate review during the build, not just at the end.

The skills also carry well-known engineering principles:

- Hyrum's Law in the API design skill: someone will come to depend on every observable behaviour of your API.
- The Beyoncé Rule in the testing skill: if you like it, you should put a test on it.
- Chesterton's Fence in code simplification: do not remove something until you know why it is there.
- Trunk-based development and small, atomic commits.

Rob's view is that reading these skills is a better software engineering course than most courses, even if you never install them.

## Sponsor: Neon

The sponsor segment covers running several agents on separate feature branches. A code branch alone is not enough, because the database, storage, and other resources also need to be isolated. Neon is now a full platform (database, storage, functions, authentication, and an AI gateway), and an agent can use the CLI to branch all of it, so each agent gets its own copy.

## Pocock vs pstack vs Osmani

The three packs each ask a different question.

- **Pocock's skills** ask whether you and the agent agree on what you are building. His best-known skill is an "interrogation" in which the agent questions you before writing anything. His other tools include a shared glossary, architecture decision records, specs, and tickets. He is openly against heavy frameworks, so his skills are small, modular, and meant to be adapted.
- **Lauren Tan's pstack** asks whether you can prove it works. It deliberately has no planning skills, on the view that the best specification is the code itself. The emphasis is on research, verification, and multimodal checks after the work is done. A successful build does not count as proof.
- **Osmani's skills** ask whether the whole process was followed. They are the only one of the three that covers the full lifecycle, including CI/CD, observability, deprecation, and release. They install on about 70 different agents, which makes them the most team-friendly and portable.

Rob combines all three at different stages instead of using them together. He suggests:

- Reach for **Pocock** when the task is unclear or you are working in a long-lived codebase whose architecture you care about. Interrogation is the skill to install first.
- Reach for **Osmani** when a team needs a predictable process that everyone understands and a full set of quality gates they do not have to build themselves. Rob's own approach with the teams he trains is closest to this one.
- Reach for **pstack** when things get messy: a bug you cannot reproduce, a migration, or long-running agents working overnight that you need to trust by morning. It also works well as a Cursor plugin.

The three overlap heavily. Rob puts that down to engineers reaching the same conclusions at the same time, not to copying.

## You don't need all of it

Rob's main point is that running every skill on every project is overkill. Agents are now capable enough that trimming your `agents.md` file and existing skills is often the best thing to do. Many skills reflect their author's working style more than they teach the agent anything new. Very long skill files also overload and confuse the context window, and every installed skill is something the agent has to consider, so skills can trigger when you do not want them.

He ties the amount of process to the size of the task:

- **Tiny edit** (changing a button colour): make the change and look at it. No PRD is needed.
- **Visual work or prototype:** iterate with the agent and check as you go.
- **Small feature:** a short discussion to agree the approach, then build it with tests.
- **Large or unclear feature:** write a spec and a staged plan, with tests at each stage.
- **Production, security, or irreversible changes:** run the full audit, including doubt-driven development.

Osmani gives the same advice for his own skills: roll them out gradually, starting with testing in your existing codebase, and do not install all 25 at once.

## Build your own skills

The lasting value is in the practices: test-driven development, small vertical slices, agreeing requirements before building, recording the reasons for decisions, and proving that something works with a real example. A green test is not proof that the app works. None of these ideas is new. Pocock draws on *The Pragmatic Programmer* and object-oriented design, Osmani on Google's engineering practices, and Tan on years of React and Meta experience. The skills package those ideas in a form an agent can follow.

Rob suggests treating the packs as textbooks: install them, read them, take what works, and build your own on top. When your agent makes a mistake, do not get angry; update the skill with what you learned, which is how all three packs were created. Share the results with your team. He closes by promoting his Switch Dimension course and community, and asks viewers which skill packs they use.

---

## Key Takeaways

- **The three packs answer different questions** — Pocock checks that you and the agent agree, pstack checks that the work is proven, and Osmani checks that the whole process was followed.
- **Osmani's pack is the most traditional and portable** — it follows the standard software development lifecycle and installs on about 70 agents, so it suits teams and larger companies.
- **Anti-rationalization tables are worth copying** — listing the excuses an agent uses to skip steps, with a rebuttal for each, prevents shortcuts before they happen.
- **Doubt-driven development adds review during the build** — a fresh context challenges important decisions as they are made, not only at the end.
- **More skills do not make a smarter agent** — long skill files and many skills fill the context window and can trigger when unwanted.
- **Match process to risk** — a button colour needs no PRD, while production or irreversible changes justify a full audit.
- **A passing build or green test is not proof** — verify the behaviour with a real example.
- **Learn the practices, then write your own skills** — treat the packs as textbooks, and fix your own skills each time the agent makes a mistake.

---

## Notable Quotes

> "More skills do not necessarily mean a smarter agent."

— **Rob O'Shaughnessy** (~[08:30](https://www.youtube.com/watch?v=sU9MW8Ycq2M&t=510))

> "The formalities should match the significance of what you are working on."

— **Rob O'Shaughnessy** (~[08:15](https://www.youtube.com/watch?v=sU9MW8Ycq2M&t=495))

> "Just because you see a green test light doesn't mean your app is working."

— **Rob O'Shaughnessy** (~[09:10](https://www.youtube.com/watch?v=sU9MW8Ycq2M&t=550))

> "Don't treat any of these packages like religion. Treat them like an O'Reilly textbook."

— **Rob O'Shaughnessy** (~[09:25](https://www.youtube.com/watch?v=sU9MW8Ycq2M&t=565))

---

## Chapters

| Time | Topic |
|------|-------|
| 00:00 | Intro |
| 00:45 | Who is Addy Osmani |
| 01:30 | The six-stage lifecycle |
| 03:00 | Inside the skills |
| 04:30 | Sponsor |
| 05:15 | Pocock vs Addy vs pstack |
| 07:00 | The $87 head-to-head |
| 08:00 | You don't need all of this |
| 09:00 | Build your own skills |
| 09:45 | Outro |

---

## Resources

- [Addy Osmani agent-skills](https://github.com/addyosmani/agent-skills) — the 25-skill, six-stage lifecycle pack covered in the video
- [Matt Pocock skills](https://github.com/mattpocock/skills) — small, modular skills built around interrogation and a shared glossary
- [pstack](https://github.com/cursor/plugins/tree/main/pstack) — Lauren Tan's verification-focused skills, packaged as a Cursor plugin
- [Neon](https://get.neon.com/VKIr4Dc) — the sponsor: a Postgres platform with branching for agent workflows
- [Switch Dimension course and community](https://switchdim.s.gy/yt-addy-osmani-agent-skills) — the creator's course on building your own skills and agent workflows
