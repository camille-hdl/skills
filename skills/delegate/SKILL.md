---
name: delegate
description: Delegate a task to another command-line agent through a brief that carries only the necessary context. Use when handing a task or review to an agent, choosing its model and harness, or updating recommendations from published benchmarks and local catalogs.
---

# Delegate

The **brief** is the only document the delegated agent receives: it sees neither the conversation nor your reasoning. Everything it must know and cannot find by looking is in it; everything else is not.

The tool, the agent combination, and the fallback are chosen on a **scale**: walk down the rungs in order and stop at the first that applies. These are rules, not suggestions: keep the rung order.

Reference files, read when a step calls for them:

- [`references/table.md`](references/table.md): recommended models by kind of task, complexity, and impact; performance grids; cost by subscription; sources, evidence levels, and gaps. Dated.
- [`references/harness.md`](references/harness.md): inventory, launch form of each CLI, verified pitfalls, confidentiality.
- [`references/benchmark-notes.md`](references/benchmark-notes.md): discovery decisions, recommendation changes, and Fable/Opus comparison. Read when updating the table or assessing that comparison.

To ask the user something, write the question in your reply and wait.

## 1. Collect the request

For each item, note “given” (with the value) or “missing”:

- the task, and what completes it;
- the delegation tool (Herdr, a specific CLI…);
- the agent combination, including model, effort, and harness, for the task and the review;
- the stated difficulty, and the preference for an expensive or economical model;
- the impact: what an error costs;
- the confidentiality of the data the agent will see;
- the user’s subscriptions (ChatGPT, Claude, Cursor, API key…).

Also look in `AGENTS.md`, `CLAUDE.md`, and accessible project documentation: delegation tool, models, subscriptions.

Done when each item is marked “given” or “missing”.

## 2. Inventory and age of the table

Run the executable inventory in `references/harness.md`, regardless of your shell. Read exposed model catalogs without starting agents.

- **Installed harnesses**: the CLIs found. For models that are actually accessible, see “Model inventory” in `references/harness.md`.
- **Herdr available**: `herdr` is found **and** `HERDR_ENV=1`, meaning you are running in a Herdr pane.
- **Age of the table**: compare today’s date with the `date` in the frontmatter of `references/table.md`. If the gap exceeds one month, tell the user, with the table’s date, and recommend updating it from recent benchmarks (the table’s “Updating” section). Then continue with the table as it stands.

When the user requests an update, follow the table's "Updating" procedure: discover new models, versions, and harnesses; give every candidate a disposition; record recommendation changes and dated evidence. An update does not authorize launching agents or testing inference access.

Done when you have the list of harnesses, the answer on Herdr, and the age of the table in days.

## 3. Delegation tool selection

1. The one the user specifies.
2. Otherwise, the one indicated by `AGENTS.md` or other accessible project documentation.
3. Otherwise, **Herdr**, if it is available.
4. Otherwise, **ask the user**, offering the harnesses found in step 2.

Done when the tool is fixed and you know which rung.

## 4. Agent combination selection

Apply the "Overrides" section of `references/table.md` first. User decisions can replace a model or restrict its use for the task, fallback, and review.

For the task, then for the review if step 5 requires it:

1. The one the user specifies.
2. Otherwise, **chosen from the table**, based on the difficulty the user stated, and on their expensive / economical preference if they stated one.
3. Otherwise, **determined automatically**: estimate the complexity and impact of the task with the table’s definitions, then take the matching row.

**Subscription.** When the chosen row depends on the subscription (the table flags this) and the subscription is missing from the request and from the project documentation, ask the user for it before launching. Then apply the table section “Cost: the subscription decides the order”.

**Confidentiality.** If the agent will see confidential data, keep only models and harnesses that retain zero data: `references/harness.md` says which ones do not.

**Fallback.** When the chosen model is unavailable through the selected harness:

1. the same model through another installed harness (the table’s catalog says which ones);
2. otherwise, in the grid for the same kind of task, the installed model at the same performance level with the closest cost;
3. otherwise, the neighboring level, and you tell the user.

A model marked unranked or absent from the table has no task rank: place the exact model/effort/harness from a dated applicable benchmark, with its evidence level, or ask the user. A catalog listing alone confirms neither access nor performance. Do not transfer an older version's score without marking that transfer [I].

Done when each agent has an installed harness and a listed/documented model and effort, access is confirmed under the rule in `references/harness.md` before the full brief is sent, and each substitution is noted with its reason.

## 5. Review

A review is required for code, and for any deliverable whose impact is high. It is given to an agent of **equal or higher performance** than the one that did the task, in the grid for the same kind of task, and **preferably from a different vendor**. Choose it with the scale in step 4. If the combination given by the user places the review under the agent that did the task, flag it before launching.

Use the measured configuration's tier, not the model family's best score. If its exact effort or harness is unmeasured, state the inferred tier [I] and the evidence used. For code, general review transfers the coding grid [I]; a security supplement is not a replacement for the primary reviewer. A same-model review uses an independent session, including Sonnet reviewing Sonnet-authored code. Add the recommended cross-vendor pass when the table calls for it. Commits made after a review are reviewed in turn before the deliverable is declared mergeable. Explicit instructions about whether to delegate still govern.

Done when the review is set aside with its reason, or its agent is fixed.

## 6. Write the brief

The brief contains, and nothing else:

- **the objective**: what to produce, in one or two sentences;
- **the done criterion**: a condition the agent can verify on its own;
- **the entry points**: paths, commands, URLs. A pointer is enough for what the agent can read; copy only what it cannot reach;
- **decisions already made** and constraints, with their reason when it prevents an error. Each constraint names its source: the user, a project rule, or your own assumption. A vague wish becomes a criterion to weigh, never a filter that drops an option the user named. Stop criteria list the exceptions already accepted for the same operation (same diff, same degraded state);
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
