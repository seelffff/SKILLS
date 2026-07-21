# claude skills

five skills i actually run every day. a skill is just a folder with a `SKILL.md` -
claude loads it only when the task needs it. no plugins, no config, no cloud.

drop any of these into your skills folder and claude picks them up automatically.

## the five

| skill | what it does | replaces |
|---|---|---|
| **deck-builder** | csv/notes -> a clean dark `.pptx`, not a text blob | a paid docs api + hours of formatting |
| **web-research** | searches, fetches, answers with citations | tavily / serpapi ($30-70/mo) |
| **code-review** | runs a severity-graded review on your diff | a $19/mo review bot |
| **csv-cleaning** | messy csv in -> clean, typed, deduped out | 40 min of manual excel |
| **skill-forge** | turns your own repeated task into a SKILL.md | re-explaining the same thing forever |

## how skills work

a `SKILL.md` has two parts:

```
---
name: deck-builder
description: when to trigger this skill...   <- claude reads only this to decide
---

# instructions claude follows once the skill loads
```

claude keeps the short descriptions in context, and pulls the full instructions
in only when a task matches. that's the whole trick - a folder of these = a claude
that stops chatting and starts doing.

## use

1. clone this repo
2. copy any skill folder into your claude skills directory
3. give claude a matching task - it loads the skill on its own

## structure

```
claude-skills/
  deck-builder/SKILL.md
  web-research/SKILL.md
  code-review/SKILL.md
  csv-cleaning/SKILL.md
  skill-forge/SKILL.md
```

mit. take them, fork them, write your own with skill-forge.
