---
name: technical-writing-agent
description: Technical-writing pass on docs, RFCs, READMEs, PR descriptions, or commit messages, by running pstack's user-invoked `technical-writing` standard from its installed SKILL.md. Use when you write or review one of them, or when a skill or the user asks for `technical-writing`.
---

# Technical writing (agent relay)

pstack's `technical-writing` sets `disable-model-invocation: true`, so the Skill tool refuses it. Reading its `SKILL.md` is the invocation. This relay carries no rules of its own and follows every `npx skills update` of pstack.

1. Read the first of these files that exists:
   - `~/.agents/skills/technical-writing/SKILL.md` (global install)
   - `.agents/skills/technical-writing/SKILL.md` in the current project
   - `.claude/skills/technical-writing/SKILL.md` in the current project

   If none exists, deliver the text and say that the technical-writing pass did not run because `technical-writing` is not installed.
2. Apply all of its layers and rules to the text. Where it says to apply `unslop`, run `unslop-agent`. The step is done when the text you deliver is the revised one, not when you have listed findings.
3. When you hand the text back, add one line outside the text itself: "technical-writing pass applied", plus anything the skill asks you to report.
