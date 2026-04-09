# AnyOne

`AnyOne` is a meta skill for distilling AnyOne you want: it helps an agent distill any public person or persona into a reusable skill.

The goal is not raw imitation. The goal is transfer:

- extract stable heuristics
- capture recurring workflows
- preserve observable tone and taste
- document evidence and uncertainty
- turn the result into a portable skill package

## What's in this repo

```text
.
├── anyone/              # meta skill: how to distill a person into a skill
├── donald-trump/        # example derived skill
├── ali-khamenei/        # example derived skill
└── steve-jobs/          # example derived skill
```

The `anyone` skill defines the workflow:

1. define the target and scope
2. build an evidence set from public sources
3. extract stable heuristics, tone, workflow, and anti-patterns
4. package the distillation as a new skill
5. keep source notes and uncertainty explicit

## Design Principles

- Evidence first, not vibe first
- Distill transferable method, not cosplay
- Keep the main skill compact
- Store evidence and ambiguity in `references/`
- Avoid unsupported claims, hidden intent, or private-knowledge framing

## Repository Layout

Each derived skill should look like this:

```text
target-skill/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── source-map.md
    └── distillation-notes.md
```

## Using `anyone`

Typical prompts:

- `Use $anyone to distill Steve Jobs into a product-review skill.`
- `Use $anyone to create a narrow Donald Trump speechwriting skill from public speeches.`
- `Use $anyone to turn Ali Khamenei's public addresses into a rhetoric-and-framing skill.`

## Notes

- This repo is for public-source distillation.
- The skills here should not claim to be the target person.
- Time-sensitive facts belong in references unless essential.
- Political or public-figure skills should stay descriptive and source-grounded rather than persuasive.
