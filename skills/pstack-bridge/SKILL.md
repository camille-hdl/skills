---
name: pstack-bridge
description: Run pstack why, how, arena, blast-radius, reflect, and manually requested no-comments outside Cursor. Use alongside a pstack invocation in Claude Code or Codex to translate Task calls into delegate, Herdr, or compatible native agents.
metadata:
  source: https://github.com/cursor/plugins/tree/main/pstack/skills
---

# Pstack bridge

Load this skill alongside the requested pstack skill. Keep that skill's prompts,
phases, evidence rules, and output format. This bridge replaces its Cursor
`Task` transport and model selection for the current run. Leave installed pstack
files untouched so `npx skills update` can maintain them.

Requires `delegate`; install it globally with this repository's skills.

Explicit invocation works even when automatic discovery does not:

- Claude Code: `/pstack-bridge`, then `/why <question>` or `/arena <task>`.
- Codex: `$pstack-bridge` alongside `$why` or `$arena` in the same request.
- Either: "Use pstack-bridge with how" or "Use pstack-bridge with blast-radius".
- Session reflection: `/pstack-bridge`, then `/reflect` in Claude Code,
  or `$pstack-bridge $reflect` in Codex.
- Comment cleanup: `/pstack-bridge`, then `/no-comments <scope>` in Claude Code,
  or `$pstack-bridge $no-comments <scope>` in Codex.

When invoked alone, acknowledge loading and wait for the pstack request.
The bridge is an instruction adapter, not a registered `Task` tool or a hook.
Keep it active for the selected workflow, including an `arena` called by
`blast-radius`. Load each upstream skill and its required references explicitly.

## Prepare the run

1. For `no-comments`, first follow [no-comments.md](references/no-comments.md)
   to resolve its workflow, agent, and dependencies from one pstack source.
   Its absence from the installed skill catalog alone does not stop resolution.
   For other workflows, find the installed pstack skill through the skill catalog
   or `~/.agents/skills/`. Find `delegate` there too. A repository checkout can
   use `skills/delegate/`.
   Read `delegate/SKILL.md`, `references/harness.md`, and `references/table.md`.
   For `reflect`, also read [reflect.md](references/reflect.md) to resolve the
   active session input, structural principle, and skill-authoring route.
   If a required skill is missing, report the paths searched and stop before
   launching.
2. Follow delegate's request collection, live inventory, table age, tool scale,
   subscription rules, confidentiality checks, and model overrides. Inventory
   accessible models as well as installed CLIs. A CLI's presence alone does not
   establish access to its models or the parent's MCPs.
3. Read `~/.cursor/rules/pstack-models.mdc` if present. For each role, use its
   configured value, or the upstream default when the file or line is absent.
   Translate that value into the intentions below. An absent rule needs no new
   configuration file. `auto` and `inherit-parent` request the parent's actual
   combination, subject to the role's capabilities and permissions.

### Translate intentions, then choose a combination

| Upstream input | Intention passed to delegate |
| --- | --- |
| `model` identifier | Requested family and capability, inferred from the live catalog and delegate table. Defaults are preferences, not user-pinned models. |
| Effort or speed suffix | Desired depth or latency. Delegate chooses supported effort and subscription cost. The same suffix does not imply equal performance across models. |
| Multiple runner families | Preserve the requested seat count and seek distinct available families suited to the task. |
| Cross-judge pool | Prefer a vendor different from the parent's, at equal or higher performance than every candidate being judged. |
| Unknown identifier or family | Record that it is unmapped. Select by the role through delegate, rather than inventing a replacement slug. |

Pass upstream effort into delegate step 1 as stated difficulty. A suffix asking
for high or maximum depth also supplies an `expensive` preference. For that
high-depth request, step 4 uses the demanding or complex row for the role before
an automatic estimate of the task's complexity. A speed suffix supplies a
latency preference only.

Resolve each seat with delegate's model scale and fallback order. Apply delegate's
overrides first and infer the requested capability level from the upstream model
in the task's performance grid. Keep the requested family when an accessible
model in it meets that level, even if the selected row recommends another family.
For a seat retained by family, use the selected row's effort if specified,
otherwise the catalog's default effort. Verify that the selected model and
transport support it.
Concrete model IDs, providers, efforts, and prices belong to delegate's inventory
and table, not to this bridge. A user's explicit combination takes precedence.
For reviews and judges, capability outranks vendor diversity. If equal-tier review
is unavailable, report the shortfall instead of claiming an equivalent review.
For Comment Sicko's seat, the different-provider requirement in
[no-comments.md](references/no-comments.md) takes precedence over this capability
rule and the single-provider fallback below.

If the family is unavailable or cannot meet the requested level, substitute through
delegate. Report every departure from the requested family or capability level
as a substitution with its reason. An unranked model cannot establish equivalence;
record that gap instead of assuming it meets the level.
With one provider, keep independent seats and report that provider diversity was
impossible. Continue with available combinations and state any performance loss.

## Adapt each Task call

Use this mapping after selecting the combination. Read
[execution.md](references/execution.md) for the chosen transport and for `arena`
isolation before launching.

| Task field or operation | Replacement |
| --- | --- |
| `prompt`, `description` | A delegate brief with the complete upstream prompt, reachable reference paths, seed context, scope, done criterion, and deliverable. Use the description as a seat label. |
| `subagent_type: generalPurpose` | An agent able to run the whole brief with the required tools. Adapt the type to the native tool's actual schema. |
| `subagent_type: "Comment Sicko"` | Read the upstream `agents/comment-sicko.md` at runtime and pass it unchanged to a delegate-selected seat from a different provider than the diff's author. The seat reports investigation needs to the parent. Follow [no-comments.md](references/no-comments.md). |
| `model` | The installed combination selected above. Pass only model and effort options the chosen transport supports. |
| `readonly: true` | Enforced read-only permissions or a native read-only type. Return findings through the response or transport capture. |
| `readonly: false` | Tool-capable mode within the brief's scope. This flag alone grants no permission to edit. |
| `run_in_background: true` | Start the seat without waiting for its result. Retain its handle, working directory, and result location. |
| Parallel calls | Dispatch independent seats before waiting. Respect available concurrency limits and record any batching. |
| Await or read Task output | Wait on retained handles, read each complete response or designated artifact, and inspect errors and partial output. A launch acknowledgement is not a result. |

Preserve these workflow boundaries:

- `how`: read-only explorers, then the explainer after all findings arrive.
  The simple path has only one explainer.
- `why`: investigators and synthesizer need MCP-capable mode, despite producing
  no edits. Discover tools in the current session rather than Cursor's `mcps/`
  directory. Assign each investigator one source. Confirm that source is reachable
  from its selected transport. Record unavailable categories as coverage gaps.
  Synthesize after collecting every finding, null result, and justified skip.
- `arena`: candidates write to separate locations. Start the read-only cross-judge
  only after all candidates have finished or failed, while the parent reads them.
  Keep pick, graft, verification, and the synthesis note in the upstream order.
- `blast-radius`: perform its proof against real code. A wide investigation uses
  the same adapted `arena`; model substitution does not replace the proof.
- `reflect`: three tool-capable reviewers, then the synthesizer with their full
  outputs. Follow [reflect.md](references/reflect.md) for session boundaries,
  approval before skill edits, backlog handling, and `create-skill` adaptation.
- `no-comments`: run only on a manual request, after implementation and before
  independent review. Read [no-comments.md](references/no-comments.md) for source
  resolution, protected annotations, report inspection, and the explicit approval
  required for `/architect`. Refuse the pass if user or project policy excludes
  it. If applicability is uncertain, ask before launching. Pilot on small projects.

## Finish the run

Present the upstream result and delegate's selection report. Include original
intentions, actual tool/model/effort combinations, substitutions, diversity or
performance shortfalls, coverage gaps, dropouts, and verification limits.
Apply delegate's review rule to the final deliverable. A judge of pre-graft
candidates does not review later edits. Completion requires the upstream final
artifact and every launched seat to have delivered or failed with an inspected
error. Preserve incomplete work for inspection.
