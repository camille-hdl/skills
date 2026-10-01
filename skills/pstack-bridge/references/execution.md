# Execute adapted pstack calls

## Choose the transport

Honor delegate's user and project tool choices, then prefer Herdr when available.
Herdr is available only when its CLI exists and `HERDR_ENV=1`. Follow delegate's
Herdr procedure and the installed Herdr skill when using it. When none of these
rungs selects a tool, this bridge permits the compatible native option below
before delegate's question rung.

In Claude Code, a seat can use native `Agent` when no higher-priority tool choice
requires Herdr or a CLI, and all these conditions hold:

- Delegate selected a combination the native tool can express. The seat needs
  neither a different provider nor a distinct working directory or isolation.
- Its type has every required tool and can enforce the requested permissions.
- Its actual model and effort match the selection, including inherited settings.

For `readonly: true`, use `Explore` or an available read-only type suited to the
brief. Inspect its restrictions rather than assuming it has MCP or shell access.
For `why`, use a tool-capable type with the assigned MCP and a no-edits scope.
Check the current `Agent` schema for background, model, and effort support. Use an
existing compatible type or delegate's CLI route when a setting is unavailable.
The [Claude Code subagent documentation](https://code.claude.com/docs/en/sub-agents)
describes types and their permission boundaries.

In Codex, use native agent tools only if the session exposes them and can express
the selected combination, scope, and isolation. A prose request to be read-only
does not establish a sandbox. Otherwise use delegate's selected CLI through the
shell. This bridge supplies no fixed native model enum.

Without Herdr or a compatible native route, follow delegate's CLI launch forms.
If its tool scale reaches the question rung, ask which installed CLI to use before
launching. Missing subscription information is handled by delegate as well.
Installing the bridge does not install or authenticate another provider.

## Dispatch, wait, and collect

Write one brief per seat with absolute paths. Start each agent in the target
repository or its own worktree. The brief includes the upstream templates and
constraints, not just a request to invoke the bridge again. Have each seat perform
its assigned work itself, with no additional delegation unless the upstream phase
explicitly requires it.

With Herdr, retain the actual pane and agent handles returned at creation. Start
the selected CLI with delegate's permissions, model, and effort options. Send the
brief pointer using `herdr agent prompt` without `--wait` for a background seat.
Check `herdr agent get` and `herdr agent read` to confirm submission and progress.
Wait in bounded intervals with `herdr agent wait`, accepting `idle`, `done`, and
`blocked`. Inspect a blocked state or error. An idle pane without the required
deliverable is incomplete. Read the full result file when terminal output is cut.

With native tools, retain each returned handle and use the session's completion
notification, wait, resume, or output-reading mechanism. Forward the full prompt
and attach any context the child cannot read. Verify required tools survived the
chosen background mode before relying on that route.

With a CLI, pass the brief on standard input as delegate specifies. For background
work, capture stdout, stderr, exit status, and a process or job handle separately
per seat. Read the capture after completion. A zero exit without the promised
artifact, or a response explicitly cut short, is incomplete. Grant read-only
seats no workspace writes merely to store transport logs. The parent captures
those logs outside the reviewed tree.

If the transport cannot run seats concurrently, use bounded batches and report
the scheduling change. Preserve the dependency barriers between candidates and
judge, or investigators and synthesizer.

## Isolate arena candidates

Before dispatch, record one common base commit and the grounding artifacts.
Account for relevant uncommitted input in the grounding so every candidate sees
the same starting task. Give each code candidate its own worktree and branch from
that base. For artifacts outside Git, use separate candidate directories under a
unique run directory. No candidates share writable files, branches, or outputs.

Set the candidate's working directory to that worktree and restrict writes to its
assigned location. Check permissions for shared Git metadata if its brief needs
Git writes. Give the read-only judge access to every finished candidate path and
the rubric. Do not give candidates the rubric that upstream reserves for judging.

Freeze candidate outputs when their agents finish. Read every successful artifact
and record failures before launching the cross-judge. If none delivered, report
the failed arena without selecting a base. Choose the judge's performance tier
using delegate's grid for the task being judged. Equal or higher performance than
the strongest candidate comes before a different vendor from the parent.

The parent picks and grafts into the designated final location. Retain candidates
until verification and the synthesis note are complete. Follow user or project
policy for commits, cleanup, and publication. Finish or stop owned agents before
releasing their workspaces, and preserve unrelated user panes and files.
