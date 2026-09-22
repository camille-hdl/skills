# Camille's skills

Collection of skills installable with the [`skills`](https://skills.sh/) CLI.

## Skills

| Skill | What it does | When to use it |
| --- | --- | --- |
| [`data-modeling`](skills/data-modeling/SKILL.md) | Helps translate a domain model into a data model, after William Kent's *Data and Reality*, which it borrows from heavily: oneness, sameness, categories, existence, naming scopes, relationships. | Designing classes, entities, attributes, relationships or a database schema from a domain. |
| [`delegate`](skills/delegate/SKILL.md) | Hands a task to another command-line agent (Codex, Claude Code, Cursor…) through a brief, and chooses its model and harness. | Delegating a task or a review to another agent. |
| [`fat-marker-sketch`](skills/fat-marker-sketch/SKILL.md) | Draws very low-fidelity UI concepts as hand-drawn images, several variants side by side. | Exploring UI or UX directions quickly, before wireframes or prototypes. |
| [`hill-chart`](skills/hill-chart/SKILL.md) | Draws the progress of a project's scopes as dots on a hill, Shape Up style: uphill while figuring out what to do, downhill while getting it done. | Showing or updating where the scopes of a project stand. |
| [`pull-request-description`](skills/pull-request-description/SKILL.md) | Writes a short pull request description for human reviewers: what they need to know to run the change in production. | Opening or updating a pull request. |
| [`tactical-programming`](skills/tactical-programming/SKILL.md) | Gives an agent the few well-known design moves for a targeted change to existing code: Shameless Green, Four Rules of Simple Design, Software Vise, Flocking Rules… | Adding code, fixing a bug, refactoring, or changing poorly tested code, in a standalone task or one ticket among others. |

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
