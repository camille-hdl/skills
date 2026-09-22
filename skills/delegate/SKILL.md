---
name: delegate
description: Delegate a task to another command-line agent (Codex, Claude Code, Cursor…) through a brief that carries only the necessary context. Use when handing a task or a review to an agent, or when choosing the model and harness for a delegation.
---

# Delegate

The **brief** is the only document the delegated agent receives: it sees neither the conversation nor your reasoning. Everything it must know and cannot find by looking is in it; everything else is not.

The tool, the agent combination, and the fallback are chosen on a **scale**: walk down the rungs in order and stop at the first that applies. These are rules, not suggestions: keep the rung order.

Two reference files, read when a step calls for them:

- [`references/table.md`](references/table.md): recommended models by kind of task, complexity, and impact; performance grids; cost by subscription; sources, evidence levels, and gaps. Dated.
- [`references/harness.md`](references/harness.md): inventory, launch form of each CLI, verified pitfalls, confidentiality.

To ask the user something, write the question in your reply and wait.

## 1. Collect the request

For each item, note “given” (with the value) or “missing”:

- the task, and what completes it;
- the delegation tool (Herdr, a specific CLI…);
- the agent combination — model, effort, harness — for the task and for the review;
- the stated difficulty, and the preference for an expensive or economical model;
- the impact: what an error costs;
- the confidentiality of the data the agent will see;
- the user’s subscriptions (ChatGPT, Claude, Cursor, API key…).

Also look in `AGENTS.md`, `CLAUDE.md`, and accessible project documentation: delegation tool, models, subscriptions.

Done when each item is marked “given” or “missing”.

## 2. Inventory and age of the table

Run, regardless of your shell:

```sh
sh -c 'date +%F; for c in herdr codex claude cursor-agent gemini opencode; do command -v "$c"; done; echo "HERDR_ENV=${HERDR_ENV:-}"'
```

- **Installed harnesses**: the CLIs found. For models that are actually accessible, see “Model inventory” in `references/harness.md`.
- **Herdr available**: `herdr` is found **and** `HERDR_ENV=1`, meaning you are running in a Herdr pane.
- **Age of the table**: compare today’s date with the `date` in the frontmatter of `references/table.md`. If the gap exceeds one month, tell the user, with the table’s date, and recommend updating it from recent benchmarks (the table’s “Updating” section). Then continue with the table as it stands.

Done when you have the list of harnesses, the answer on Herdr, and the age of the table in days.

## 3. Delegation tool — scale

1. The one the user specifies.
2. Otherwise, the one indicated by `AGENTS.md` or other accessible project documentation.
3. Otherwise, **Herdr**, if it is available.
4. Otherwise, **ask the user**, offering the harnesses found in step 2.

Done when the tool is fixed and you know which rung.

## 4. Agent combination — scale

Apply the “Overrides” section of `references/table.md` first: it replaces models of the table, pending benchmarks.

For the task, then for the review if step 5 requires it:

1. The one the user specifies.
2. Otherwise, **chosen from the table**, based on the difficulty the user stated, and on their expensive / economical preference if they stated one.
3. Otherwise, **determined automatically**: estimate the complexity and impact of the task with the table’s definitions, then take the matching row.

**Subscription.** When the chosen row depends on the subscription (the table flags this) and the subscription is missing from the request and from the project documentation, ask the user for it before launching. Then apply the table section “Cost: the subscription decides the order”.

**Confidentiality.** If the agent will see confidential data, keep only models and harnesses that retain zero data: `references/harness.md` says which ones do not.

**Fallback.** When the chosen model or harness is not installed:

1. the same model through another installed harness (the table’s catalog says which ones);
2. otherwise, in the grid for the same kind of task, the installed model at the same performance level with the closest cost;
3. otherwise, the neighboring level, and you tell the user.

A model absent from the table has no rank: place it from a dated public benchmark, with its evidence level, or ask the user.

Done when each agent to launch has an installed model, effort, and harness, and each substitution is noted with its reason.

## 5. Review

A review is required for code, and for any deliverable whose impact is high. It is given to an agent of **equal or higher performance** than the one that did the task, in the grid for the same kind of task, and **preferably from a different vendor**. Choose it with the scale in step 4. If the combination given by the user places the review under the agent that did the task, flag it before launching.

Done when the review is set aside with its reason, or its agent is fixed.

## 6. Write the brief

The brief contains, and nothing else:

- **the objective**: what to produce, in one or two sentences;
- **the done criterion**: a condition the agent can verify on its own;
- **the entry points**: paths, commands, URLs. A pointer is enough for what the agent can read; copy only what it cannot reach;
- **decisions already made** and constraints, with their reason when it prevents an error;
- **the scope**: what it may read, modify, execute; whether it commits; where it stops;
- **the deliverable**: what, in what form, where to write it.

Reread each line: if it serves none of these six points, remove it. Conversation history, discarded hypotheses, and preferences unrelated to the task fail this test.

For a review, the brief points to the task brief, the diff or the files produced, and asks for verified findings.

Write the brief to a file: a temporary file (`mktemp`), or the location provided by the project documentation.

Done when each line serves one of the six points and the agent could start without asking a question.

## 7. Launch

Follow `references/harness.md` for the chosen tool and harness: command form, passing the brief on standard input, permissions granted according to the scope. Launch the review the same way, once the task has been delivered.

Done when each agent has delivered, or has failed with an error you have read.

## 8. Report back

Tell the user:

- the tool and each combination, with the scale rung that fixed them and any override applied;
- the substitutions and their reason;
- the warning on the age of the table, if any;
- the result of the task and of the review, with the path of the deliverables.
