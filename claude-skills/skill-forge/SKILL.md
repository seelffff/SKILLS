---
name: skill-forge
description: Use when the user wants to create their own Claude skill, turn a repeated task or SOP into a reusable SKILL.md, or asks "make a skill for X / how do I write a skill". Produces a clean, well-scoped SKILL.md following best practices. The meta-skill that builds skills.
---

# Skill Forge

Turn a repeated task into a reusable skill. A skill is a folder with a `SKILL.md`
(and optional scripts/templates) that Claude loads only when the task calls for it.

## Anatomy of a good SKILL.md

```
---
name: kebab-case-name
description: One or two sentences. WHAT it does + WHEN to trigger it. This is the
             only part Claude reads to decide whether to load the skill - make it precise.
---

# Title

Short intent line.

## Rules        <- the non-negotiables
## Steps        <- the procedure, in order
## Output       <- exactly what to hand back
```

## Rules for writing skills

1. **The description is everything.** It's the trigger. Include concrete phrases the user
   would actually say. Vague description = skill never loads.
2. **One job per skill.** If it does three unrelated things, make three skills.
3. **Instructions, not essays.** Numbered steps, hard rules, a defined output shape.
4. **Encode judgment, not just steps** - the "don't do X", the quality bar, the edge cases.
5. **Keep it short.** A page. Push heavy code into a script the skill calls, not into prose.

## Steps

1. Ask (or infer) the repeated task and what "done right" looks like.
2. Draft the `description` first - nail the trigger phrases.
3. Write Rules -> Steps -> Output.
4. Add a `scripts/` file if the task needs real code.
5. Save as `<skill-name>/SKILL.md` and tell the user how to drop it into their skills folder.

## Output

A ready-to-use `SKILL.md` (plus scripts if needed), scoped to one job, with a trigger-precise description.
