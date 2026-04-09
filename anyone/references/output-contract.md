# Output Contract

Use this contract when creating the derived skill.

## Required files

```text
target-skill/
├── SKILL.md
├── agents/openai.yaml
└── references/
    ├── source-map.md
    └── distillation-notes.md
```

## Derived `SKILL.md`

Keep the main skill lean.

Recommended structure:

```markdown
---
name: target-skill
description: Distilled skill based on <person>. Use when Codex needs to <do task class> using <core method/tone/workflow>.
---

# <Display Name>

## Overview

State what the skill helps with and what it does not try to do.

## Core Heuristics

List the 5 to 10 decision rules with imperative wording.

## Workflow

Describe the recurring sequence the agent should follow.

## Tone and Style

Describe observable communication rules, not vague adjectives alone.

## Anti-Patterns

Describe what to avoid.

## References

Point to the reference files for evidence and edge cases.
```

## `references/source-map.md`

Use a table or bullet list with:

- source
- type
- date
- importance
- strongest signals extracted from it

Example:

```markdown
| Source | Type | Date | Why it matters | Key signals |
| --- | --- | --- | --- | --- |
| Essay X | Essay | 2013 | Clear first-person explanation of priorities | Prefers clarity over novelty; uses concrete examples before abstraction |
```

## `references/distillation-notes.md`

Organize notes into:

- Stable principles
- Tone markers
- Workflow patterns
- Anti-patterns
- Open questions
- Inferences

Use short bullets and mark inferences explicitly.

## `agents/openai.yaml`

Generate:

- `display_name`: clear human-facing title
- `short_description`: short UI summary
- `default_prompt`: one sentence that explicitly mentions the derived skill as `$skill-name`

Keep UI text faithful to the actual scope of the derived skill.
