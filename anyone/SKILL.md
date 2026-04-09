---
name: anyone
description: Distill a public figure, writer, founder, creator, operator, expert, or fictionalized professional persona into a reusable Codex skill. Use when Codex needs to turn a person's public corpus into a skill package, or when a user asks to "make a skill for X", "distill X into an agent", "write a reusable prompt/skill based on X", or extract someone's working style, taste, heuristics, workflows, and tone into a transferable skill rather than a one-off imitation.
---

# Anyone

## Overview

Turn a person's public body of work into a reusable skill that captures stable operating principles, taste, tone, and recurring workflows. Optimize for transferability: distill what another agent can reliably use, not a cosplay impression.

## Distillation Workflow

### 1. Define the target and the use case

Start by fixing the scope:

- Identify the target person or persona.
- Identify the desired output shape:
  - a broad skill for "think/work like X"
  - a narrow skill for "do Y like X"
  - a hybrid that combines domain method and voice
- Identify where to create the derived skill. If the user does not specify a location, prefer the current workspace; otherwise default to `${CODEX_HOME:-$HOME/.codex}/skills` so the result can be auto-discovered.

Ask only the smallest set of clarifying questions needed to resolve real ambiguity. Good examples:

- "Should the derived skill capture decision-making, writing voice, workflow, or all three?"
- "Do you want a general X skill, or a narrower X-on-topic-Y skill?"

### 2. Build an evidence set before writing

Prefer first-party material over commentary:

- essays, books, letters, memos
- talks, interviews, podcasts, lectures
- products, code, designs, speeches, reviews
- public Q&A, recurring threads, repeated frameworks

Use secondary sources only to triangulate or fill context gaps.

Read [references/distillation-checklist.md](./references/distillation-checklist.md) and create a lightweight source ledger before drafting the skill. Keep time-sensitive facts out of the main skill unless they are essential to the workflow.

### 3. Extract the person's reusable operating system

Distill observable patterns into portable building blocks:

- Objectives: what the person repeatedly tries to optimize for
- Heuristics: decision rules, mental models, favored questions
- Taste: what they consider good, bad, elegant, cheap, durable, rigorous, etc.
- Workflow: recurring sequences such as research, drafting, reviewing, shipping
- Constraints: what they avoid, reject, or refuse to compromise on
- Signature moves: repeated structures, arguments, openings, reframes, edits, or critiques

Favor stable patterns with repeated evidence. Treat one-off anecdotes as weak evidence.

### 4. Translate the distillation into a new skill

Create a derived skill folder for the target. Use a narrow, explicit name such as:

- `paul-graham`
- `munger-decision-making`
- `miyazaki-storyboards`
- `anna-wintour-editorial-review`

If a local `init_skill.py` workflow is available, use it. Otherwise create the folder manually with:

```text
target-skill/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── source-map.md
    └── distillation-notes.md
```

Keep the derived `SKILL.md` compact. Put detailed evidence, quotes, and source notes in `references/`.

Use [references/output-contract.md](./references/output-contract.md) as the minimum package contract.

### 5. Write for transfer, not impersonation

Do not claim the agent "is" the target person. Do not imply endorsement, private knowledge, or hidden access. Frame the result as:

- a distilled operating style
- a reusable set of heuristics
- a structured approximation based on public material

Good language:

- "Use first-principles arguments, short sentences, and explicit trade-offs."
- "Favor critique by decomposition, then reconstruct the stronger version."

Bad language:

- "Become X."
- "Channel private intent."
- "Invent what X would say without evidence."

### 6. Preserve evidence and uncertainty

Record which claims are strongly supported, weakly supported, or inferred.

- Put source metadata and why each source matters in `references/source-map.md`.
- Put the extracted heuristics, tone rules, anti-patterns, and open questions in `references/distillation-notes.md`.
- Mark inferred items as inferences.

When evidence is thin, narrow the claim instead of widening the fiction.

### 7. Validate the derived skill

Before handing off the result:

- validate folder structure and frontmatter
- confirm the skill description states what the skill does and when to use it
- confirm the body contains instructions another agent can execute
- confirm references contain evidence rather than duplicated body text
- remove stale temporal facts from the main skill

If local validation tooling exists, run it on both this skill and the newly created derived skill.

## Output Standard

When using this skill, aim to produce:

1. A new skill folder for the target person or persona.
2. A concise `SKILL.md` that describes how to use the derived skill.
3. A `references/source-map.md` file that documents the evidence base.
4. A `references/distillation-notes.md` file that captures extracted patterns and uncertainty.
5. A short handoff summary that states:
   - what the skill is optimized for
   - what evidence shaped it most
   - what remains uncertain

## Quick Prompts

Examples of requests this skill should handle:

- "Make me a Steve Jobs product-review skill."
- "Distill Paul Graham into a reusable writing-and-ideas skill."
- "Turn Munger's decision heuristics into a skill for investment memos."
- "Create a narrow Haruki Murakami scene-writing skill, not a full author persona."

## Reference Files

Load these references only when needed:

- [references/distillation-checklist.md](./references/distillation-checklist.md): evidence rubric, extraction lenses, and red flags
- [references/output-contract.md](./references/output-contract.md): required files and suggested templates for the derived skill package
