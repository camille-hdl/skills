# Camille's skills

Collection of skills installable with the [`skills`](https://skills.sh/) CLI.

## Skills

| Skill | What it does | When to use it |
| --- | --- | --- |
| [`data-modeling`](skills/data-modeling/SKILL.md) | Helps translate a domain model into a data model, after William Kent's *Data and Reality*, which it borrows from heavily: oneness, sameness, categories, existence, naming scopes, relationships. | Designing classes, entities, attributes, relationships or a database schema from a domain. |
| [`delegate`](skills/delegate/SKILL.md) | Hands a task to another command-line agent through a brief; chooses its model, effort, and harness from dated evidence and local catalogs. | Delegating a task or review, choosing a combination, or updating model recommendations. |
| [`fat-marker-sketch`](skills/fat-marker-sketch/SKILL.md) | Draws very low-fidelity UI concepts as hand-drawn images, several variants side by side. | Exploring UI or UX directions quickly, before wireframes or prototypes. |
| [`hill-chart`](skills/hill-chart/SKILL.md) | Draws the progress of a project's scopes as dots on a hill, Shape Up style: uphill while figuring out what to do, downhill while getting it done. | Showing or updating where the scopes of a project stand. |
| [`pstack-bridge`](skills/pstack-bridge/SKILL.md) | Adapts [pstack](https://github.com/cursor/plugins/tree/main/pstack/skills) Task calls and model intentions to delegate, Herdr, or native agents without changing the upstream skills. Requires `delegate`, installed globally with this repository's skills. | Running pstack why, how, arena, blast-radius, reflect, or manually requested no-comments in Claude Code or Codex. |
| [`pull-request-description`](skills/pull-request-description/SKILL.md) | Writes a short pull request description for human reviewers: what they need to know to run the change in production. | Opening or updating a pull request. |
| [`shaping`](skills/shaping/SKILL.md) | Grills the user to turn a raw idea for a change into a pitch, after Ryan Singer's *Shape Up*: the problem, the appetite, the solution (must-haves, nice-to-haves, no-gos), the rabbit holes. Sketches 2 or 3 versions of each screen to choose from. | Before building a new feature or changing one, whether the user is technical or not. |
| [`tactical-programming`](skills/tactical-programming/SKILL.md) | Gives an agent the few well-known design moves for a targeted change to existing code: Shameless Green, Four Rules of Simple Design, Software Vise, Flocking Rules… | Adding code, fixing a bug, refactoring, or changing poorly tested code, in a standalone task or one ticket among others. |

Delegate's [recommendation table](skills/delegate/references/table.md) includes a discovery/update procedure. Its [benchmark notes](skills/delegate/references/benchmark-notes.md) record recommendation changes, candidate dispositions, and the Fable 5.1 / Opus 5.5 comparison.

The bridge's [no-comments workflow](skills/pstack-bridge/references/no-comments.md)
reads Comment Sicko from the pstack source at runtime and chooses a model from a
different provider than the diff's author. The seat preserves tool-readable
annotations and reports investigation needs to the parent. The parent can remove
an annotation only after fixing its cause and confirming with its tool that it
is unnecessary. Invoke the pass manually between implementation and independent
review. Pilot on small projects, subject to user and project exclusions.
`/architect` requires explicit user approval. The workflow lists the global
installation commands for the upstream skills.

The bridge's [reflect workflow](skills/pstack-bridge/references/reflect.md)
uses the active session's transcript or a digest, preserves the three review
lenses and synthesis, and waits for the user's selection before editing skills.
Outside Cursor, substantive edits use the available skill-authoring workflow.

## Install the skills

From the project where the skills should be available:

```bash
npx skills add camille-hdl/skills
```

To see the list without installing:

```bash
npx skills add camille-hdl/skills --list
```

To install a specific skill:

```bash
npx skills add camille-hdl/skills --skill skill-name
```

Add `-g` for a global install, or `-a codex` (and optionally
other agents) to target a specific agent. Updates are done with
`npx skills update`.

## Add a skill

Each skill must live in its own subdirectory of `skills/` and
contain a `SKILL.md` file with YAML frontmatter that includes at least
`name` and `description`:

```text
skills/
└── my-skill/
    └── SKILL.md
```

A template is available in [`templates/SKILL.md.example`](templates/SKILL.md.example).
