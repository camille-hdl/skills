# Run no-comments

Use this workflow only when the user requests `/no-comments`. It runs between
implementation and independent review and does not replace that review. Pilot on
small projects. Publication and Gestion/SIA are excluded because the cleanup is
too disruptive. Check the target project before launching or editing.

## Read the current upstream source

Resolve `no-comments/SKILL.md` through the installed skill catalog, then look for
`agents/comment-sicko.md` in the associated pstack source root. The skills CLI
installs `skills/`, not `agents/`. An installed skill alone is insufficient.
Check the active Cursor pstack plugin under
`~/.cursor/plugins/cache/cursor-public/pstack/` or a `cursor/plugins` checkout
containing `pstack/agents/comment-sicko.md`. Select the active source explicitly
when several versions exist. Record its path and version or commit.

If no associated source is available, fetch the file from `cursor/plugins` on
`main` at runtime, using GitHub's API or raw content endpoint. Resolve the commit
first and fetch from that commit so the recorded revision identifies the bytes
read. Resolve the workflow and required references from the same revision when
using this fallback. Read the whole agent file, including its frontmatter, and
pass it unchanged with the upstream scope. A temporary run file is transport
input, not an installed agent. Keep no maintained copy in this bridge or in
native agent registries. If resolution, retrieval, or reading fails, stop before
dispatch and report the failure. Do not reconstruct the prompt from memory.

Compute the SHA-256 of the agent bytes and compare it with the last reviewed
fingerprint below. Report a mismatch and inspect the current agent and workflow
before dispatch. Record the source, fingerprint, and contract changes in the run
report. A changed hash is not permission to rewrite upstream rules.

Last reviewed on 2026-10-01:

- Source: `cursor/plugins`, commit `c47b12849e43f18d5c374c7069c744cc55b0ea00`,
  `pstack/agents/comment-sicko.md`. The installed Cursor plugin has identical bytes.
- SHA-256: `c0fd0383008da45fc78cfac17b9007d62c42f87ad1c8d5c2fb658b1fd01f7c82`.

Read the upstream `no-comments` workflow and its required principle skills,
including `principle-fix-root-causes` and
`principle-redesign-from-first-principles`. Resolve `how` and `why` for any
investigation the agent or parent needs. Required skills can come from the
installed pstack source. Report missing dependencies before launching.
Resolve `architect` and its references only if a reshape is approved.

## Prepare Comment Sicko's seat

Use the caller's files or diff. Otherwise use the upstream default, the current
diff against `main`, including the working tree. Record the base, allowed paths,
and current uncommitted changes. Preserve a before-pass snapshot so rejecting
the seat's edits cannot overwrite the user's existing work.

Identify the model family that wrote the diff from the task context. If unknown,
ask before dispatch. Use delegate's live inventory and task heuristic to choose
Comment Sicko's model and effort, requiring a different family from that author.
Compare against the author, who may differ from the current parent. This
requirement overrides the bridge's generic fallback that continues with one
provider. If no suitable different family is available, report the pass blocked.

Follow [execution.md](execution.md) for transport, handles, and result collection.
Honor explicit tool choices and prefer Herdr when available. Start the seat in
the project's repository or worktree, with writes limited to the allowed scope.
A native transport must express the selected family and permissions. The brief
contains the unchanged agent file, scope, snapshot location, deliverable, and the
annotation context below. When executing from clanker, begin with the mandated
executor instruction that disables additional agents and tabs. Permit additional
investigation only when the upstream `/how` or `/why` phase requires it.

Include this repository context separately from the upstream prompt:

> Tool-readable annotations are executable input. Never delete `// @flow`,
> `$FlowFixMe`, PHPDoc types such as `@param`, `@return`, `@var`, and generics such
> as `array<…>` or `list<…>`, `# noqa`, `ansible_managed`, or similar pragmas read
> by type checkers, linters, generators, or build tools. Preserve an entire mixed
> block if removing its prose would damage its annotation. List these as skips.
> If a protected suppression masks a correctness bug, name the symbol and the
> root cause as `MUST KILL` while leaving the annotation intact. The parent
> applies the same protection when inspecting and fixing findings.

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

Fix trivial accepted flags in scope under the upstream principle skills. A
`MUST KILL` requiring a new shape remains open until the user explicitly approves
`/architect` for that accepted set. Requesting `/no-comments` alone grants no
such approval. Do not launch architect, its grounding seats, or its arena while
approval is absent. Report the symbol, reason, and required reshape instead.

With explicit approval, load the upstream `architect` skill and references.
Adapt its `how`, `why`, and arena calls through this bridge, honoring the
`architect runners` model intentions. Run it once for the accepted set and stop
at the sketch, as `no-comments` requires. The parent then implements the smallest
root-cause fix in scope. Report out-of-scope causes as open work. Preserve the
upstream approval requirement for constraint encodings too.

Verify the final diff and run the project's relevant checks for affected tool
annotations and any parent code fixes. Report upstream deletion counts,
restorations, reruns, sketch, fixes, encoding offers, and open constraints.
Include protected skips, source and hash changes, author and cleaner families,
delegate's actual selection, transport, and verification limits. A completed
cleanup with open reshapes must identify that work as open.

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
