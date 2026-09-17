# Camille's skills

Collection of skills installable with the [`skills`](https://skills.sh/) CLI.

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
