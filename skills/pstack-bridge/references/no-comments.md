# Run no-comments

Use this workflow only when the user requests `/no-comments`. It runs between
implementation and independent review and does not replace that review. Pilot on
small projects. Before launching or editing, check the user's instructions and
the target project's policy. Refuse the pass if either excludes it. If the
policy's applicability is uncertain, ask before proceeding. Exclusion lists
belong in user or project configuration, outside this generic skill.

## Read the current upstream source

Locate the installed `no-comments` skill through the catalog when available.
Use its associated pstack source only if it contains both
`skills/no-comments/SKILL.md` and `agents/comment-sicko.md`. The skills CLI
installs `skills/`, not `agents/`, so a standalone installed skill is insufficient.
Otherwise use the active Cursor pstack plugin under
`~/.cursor/plugins/cache/cursor-public/pstack/`, then a `cursor/plugins` checkout
with both files under `pstack/`. If several versions exist and the active source
cannot be determined, ask which source to use. Read the workflow and agent from
that same source and revision, replacing any catalog workflow already loaded.
Record both paths and their shared version or commit. Do not mix revisions.

If no complete local source is available, fetch both files from `cursor/plugins` on
`main` at runtime, using GitHub's API or raw content endpoint. Resolve the commit
first and fetch from that commit so the recorded revision identifies the bytes
read. Resolve the workflow and required references from the same revision when
using this fallback. Read the whole agent file, including its frontmatter, and
pass it unchanged with the upstream scope. A temporary run file is transport
input, not an installed agent. Keep no maintained copy in this bridge or in
native agent registries. If resolution, retrieval, or reading fails, stop before
dispatch and report the failure. Do not reconstruct the prompt from memory.

Compute the SHA-256 of both files and compare them with the reviewed fingerprints
below. On a mismatch, compare the current files with those at the reviewed commit,
retrieved at runtime. Continue only if their contract is unchanged: scoped file or
diff input, comment-only seat writes, the report fields, and the parent's
acceptance, retry, fix, and approval phases. If the contract changes or comparison
is impossible, stop before dispatch and ask the user how to adapt the bridge.
Record both hashes, the comparison, and any changes in the run report.

After a successful comparison, the bridge maintainer updates this reference's
reviewed commit, date, and both fingerprints through a reviewed bridge change.
Until that change lands, compare again on each run. A run does not silently
overwrite the baseline or rewrite upstream rules.

Last reviewed on 2026-10-01:

- Source: `cursor/plugins`, commit `c47b12849e43f18d5c374c7069c744cc55b0ea00`.
  The installed Cursor plugin has identical bytes for both files.
- Agent `pstack/agents/comment-sicko.md`, SHA-256:
  `c0fd0383008da45fc78cfac17b9007d62c42f87ad1c8d5c2fb658b1fd01f7c82`.
- Workflow `pstack/skills/no-comments/SKILL.md`, SHA-256:
  `5c5b0882297d704c3a9720c52b7a793c68b013eaf717989f0945624efdfe2b05`.

Read the upstream `no-comments` workflow and its required principle skills,
including `principle-fix-root-causes` and
`principle-redesign-from-first-principles`. Resolve `how` and `why` for the
parent's investigations. Required skills can come from the installed pstack
source. Report missing dependencies before launching.
Resolve `architect` and its references only if a reshape is approved.

## Prepare Comment Sicko's seat

Use the caller's files or diff. Otherwise use the current diff against the base
branch, default `main`, including the working tree. Record the selected base,
allowed paths, and current uncommitted changes. By default, copy the scoped files
before dispatch into a unique run directory outside the repository. Preserve
relative paths, bytes, file modes, and symlinks, and record absent paths. Save
the input diff there too. Pass the absolute snapshot path in the brief. Restore
only rejected edits against this snapshot, preserving pre-existing uncommitted work.

Identify the model provider that wrote the diff from the task context. If unknown,
ask before dispatch. Use delegate's live inventory and task heuristic to choose
Comment Sicko's model and effort, requiring a different provider from that author.
Compare against the author, who may differ from the current parent. This
requirement overrides the rule that gives capability priority over provider
diversity and the single-provider fallback in this bridge and delegate. Choose
the best accessible combination from another provider even if its performance
tier is lower. Report any capability shortfall or unmeasured tier without
claiming equivalence. A different model from the same
provider does not qualify. If no other provider is accessible, stop the pass.

Follow [execution.md](execution.md) for transport, handles, and result collection.
Honor explicit tool choices and prefer Herdr when available. Start the seat in
the project's repository or worktree, with writes limited to the allowed scope.
A native transport must express the selected provider and permissions. The brief
contains the unchanged agent file, scope, snapshot location, deliverable, and the
annotation and investigation context below. The seat executes its brief itself,
with no additional agents or tabs.

Include this transport adaptation separately from the unchanged upstream prompt:

> The parent owns `/how` and `/why`. Never launch either workflow or delegate
> another seat. When a comment's claim needs investigation beyond nearby code,
> leave it pending and report its path, symbol, claim, and requested investigation.
> Defer its deletion or keep decision to the parent. This overrides the upstream
> agent's instruction to run those workflows itself.

Include this repository context separately from the upstream prompt:

> Tool-readable annotations are executable input. Never delete `// @flow`,
> `$FlowFixMe`, PHPDoc types such as `@param`, `@return`, `@var`, and generics such
> as `array<…>` or `list<…>`, `# noqa`, `ansible_managed`, or similar pragmas read
> by type checkers, linters, generators, or build tools. Preserve an entire mixed
> block if removing its prose would damage its annotation. List these as skips.
> If a protected suppression masks a correctness bug, name the symbol and the
> root cause as `MUST KILL` while leaving the annotation intact. Only the parent
> can remove an annotation under the verified root-cause-fix rule below.

This context identifies tool input. It does not add a prose exception to
Comment Sicko's keep list or restate that list. The seat edits comments and
reports refactor targets. Application-code fixes belong to the parent.

## Inspect the pass and act on accepted findings

Wait for the full report and inspect the actual diff against the snapshot.
Apply upstream acceptance, restoration, and retry rules. Reject application-code
edits, scope escapes, and deletions of protected annotations as well as the
upstream rejection cases. Restore rejected hunks against the before-pass state,
preserving unrelated work. Rerun one rejected pass with the failure named. If
the second report is rejected, fail `/no-comments` and report the work open.
Check missed suppressions and thin constraint claims as upstream requires.
For pending claims and thin `IMPORTANT` or `do not remove` decisions, the parent
launches `/how` or `/why` through this bridge before accepting a kill or keep.
Read the required skills and references in the parent's session, and apply the
upstream decision rules to the resulting evidence. If user or project constraints
prevent an investigation, report that finding open rather than accept it.

The parent may remove a protected annotation only when it fixes that annotation's
cause in the same pass and the responsible tool confirms it is no longer needed.
Check the corrected code with that tool and verify it passes without the
annotation. Record the fix, tool result, and removal. If the cause remains, the
tool is unavailable, or verification fails, keep the annotation and report the
unverified removal open. The seat never removes protected annotations.

Fix trivial accepted flags in scope under the upstream principle skills. A
`MUST KILL` requiring a new shape remains open until the user explicitly approves
`/architect` for that accepted set. Requesting `/no-comments` alone grants no
such approval. Do not launch architect, its grounding seats, or its arena while
approval is absent. Report the symbol, reason, and required reshape instead.
In an interactive session, offer `/architect` approval at the end of the pass;
leave the reshape open until the user explicitly agrees. In unattended runs,
report it open unless the caller explicitly approved it in advance.

With explicit approval, load the upstream `architect` skill and references.
Adapt its `how`, `why`, and arena calls through this bridge, honoring the
`architect runners` model intentions. Run it once for the accepted set and stop
at the sketch, as `no-comments` requires. The parent then implements the smallest
root-cause fix in scope. Report out-of-scope causes as open work. Preserve the
upstream approval requirement for constraint encodings too.

Verify the final diff and run the project's relevant checks for affected tool
annotations and any parent code fixes. Report upstream deletion counts,
restorations, reruns, sketch, fixes, encoding offers, and open constraints.
Include protected skips, pending investigations, verified annotation removals,
source and hash changes, author and cleaner providers, delegate's actual
selection, transport, and verification limits. A completed cleanup with open
reshapes must identify that work as open.

## Make the skills discoverable outside Cursor

Install upstream skills globally, unchanged, when the target agent cannot
discover them. `no-comments` is the entrypoint. `principle-fix-root-causes` is
required for its fixes. `architect` is needed only for explicitly approved
reshapes. Installation never grants that approval.

```bash
npx skills add cursor/plugins -g --skill no-comments principle-fix-root-causes
npx skills add cursor/plugins -g --skill architect
```

Keep `how`, `why`, and `principle-redesign-from-first-principles` available too.
Install or update this bridge and `delegate` from `camille-hdl/skills`. The
upstream agent still resolves at runtime, since these commands do not install
`agents/comment-sicko.md`.
