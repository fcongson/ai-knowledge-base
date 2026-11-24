---
tags:
  - knowledge
  - ai
  - agent-skills
  - claude-code
  - tooling
created: 2026-11-24
---

# Agent Skill Packs: Pocock, Osmani, and pstack

A comparison of three popular skill packs for coding agents. For a video take on the same three packs, see [[Pocock vs Pstack vs Osmani - Which Skill Pack Wins]].

## Why skill packs exist

A coding agent has general ability but no knowledge of how you want work done. Left alone, it takes the shortest path: it skips specs, writes code before the design is agreed, and calls work done without proof. A skill is a Markdown file that tells the agent how to handle one kind of task. A pack bundles many skills into a shared workflow.

- **Consistency:** the agent follows the same process every time.
- **Reuse:** write the process once instead of re-explaining it in each chat.
- **Context efficiency:** only a short header loads at first, and the full instructions load when needed.

Good for planning, debugging, code review, testing, and shipping. Poor fit for one-off questions.

## The three packs

| | mattpocock/skills | addyosmani/agent-skills | Cursor pstack |
|---|---|---|---|
| Core idea | Agree on what to build before any work starts | Senior-engineer discipline across the full lifecycle | "Go deep first": write less code of higher quality |
| Size | About 25 small skills | 26 skills, 10 commands, 5 agent personas, 7 checklists | 22 playbooks, 23 principles, workflow skills |
| Stars (Nov 2026) | 329.3k | 119.8k | About 14.7k (third-party listing) |
| Works best in | Any agent | Any agent | Cursor first |
| Author | Matt Pocock | Addy Osmani | Lauren Tan |

### mattpocock/skills
- Philosophy: align before building, use a shared language, give the agent feedback, design to prevent mud.
- Signature skill: `grill-me` interviews you about a plan until every branch of the design is resolved.
- Keeps a shared glossary (`GLOSSARY.md`) so you and the agent use the same terms.
- Chain: `to-spec`, then `to-tickets`, then `implement` (uses `tdd`), then `code-review`.
- Unique: `wayfinder` (maps very large work as decision tickets), `handoff` (continue in another agent), `retro` (improve the agent's environment), `improve-codebase-architecture` (deep modules with small interfaces).
- Small, editable, and composable. Avoids heavy process frameworks.
- Install: Claude Code plugin from the `claude-plugins-official` marketplace, or `npx skills@latest add mattpocock/skills`. Run `/setup-matt-pocock-skills` once per repo. Install by one method only, or every skill appears twice.

### addyosmani/agent-skills
- Lifecycle: Define, Plan, Build, Verify, Review, Ship. Each phase has a slash command (`/spec`, `/plan`, `/build`, `/test`, `/review`, `/ship`, and others).
- Every skill has the same layout: Overview, When to Use, Process, Rationalizations, Red Flags, Verification.
- "Rationalizations" lists the excuses an agent gives for skipping a step, with a rebuttal for each.
- Every skill requires evidence, such as passing tests or build output.
- Widest coverage: security, performance, observability, CI/CD, deprecation, ADRs.
- Includes `accessibility-engineering` (WCAG 2.2 AA, axe-core, pa11y), an accessibility-auditor persona, and the `/a11y` command.
- Install: `npx skills add addyosmani/agent-skills`, or `/plugin marketplace add addyosmani/agent-skills`.
- In Claude Code, `/review` clashes with a built-in command, so use `/agent-skills:review`.

### Cursor pstack
- Entry point: `poteto-mode` reads the request, matches it to one of 22 playbooks (bug fix, feature, refactoring, prototype, autonomous run, shipping, and others), and copies it into the task list.
- Multi-model features: `/arena` runs one task on several models in separate worktrees and a judge scores the results. `/interrogate` sends one diff to several models for review.
- Other skills: `/how`, `/why` (finds historical intent in git, PRs, tickets), `/teach`, `/recall`, `/architect`, `/swarm`, `/reflect`, `unslop`, `blast-radius`.
- `/setup-pstack` assigns models to roles (implementation, investigation, judgment, review).
- Install: `/add-plugin pstack` in Cursor. In Claude Code: `/plugin marketplace add cursor/plugins`, then `/plugin install pstack@cursor-plugins`. Commands get a `pstack:` prefix there.
- Limits: outside Cursor you lose per-subagent model assignment and `/loop`. Several frontier models cost a lot. The full process is too heavy for small changes.
- Caveat: GitHub blocked a direct read of the pstack page, so these details come from search results and a third-party deep dive (Flavio Copes). Check the repo for the current state.

## Which to use

| Situation | Start with |
|---|---|
| The agent builds the wrong thing, or requirements are vague | Pocock: `grill-me` |
| You want one consistent process from spec to launch, or need security, performance, or accessibility checks | Osmani |
| You work in Cursor, run big or risky changes, and can pay for several models | pstack |
| Small bug fix or quick script | None of them |

## Cautions

- Start with one pack and one skill. Do not install all three.
- Every installed skill adds description text to the agent's context.
- The packs overlap (`tdd`, code review, spec writing), so several packs can give the agent conflicting instructions.
- Trial: use one skill on a side project for a week, then check whether the output improved enough to justify the extra steps. Remove it if not.
- Read the `SKILL.md` files before installing. They are short, and you can copy the parts you like into your own skills.

## Sources

- https://github.com/mattpocock/skills
- https://github.com/addyosmani/agent-skills
- https://github.com/cursor/plugins/tree/main/pstack
- https://flaviocopes.com/pstack/
- https://deepwiki.com/cursor/plugins/3.4-pstack-plugin
- https://atlasnote.ai/en/skills/pstack
