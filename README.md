# Camille's skills

Collection de skills installables avec la CLI [`skills`](https://skills.sh/).

## Installer les skills

Depuis le projet dans lequel les skills doivent être disponibles :

```bash
npx skills add camille-hdl/skills
```

Pour voir la liste sans installer :

```bash
npx skills add camille-hdl/skills --list
```

Pour installer un skill précis :

```bash
npx skills add camille-hdl/skills --skill nom-du-skill
```

Ajouter `-g` pour une installation globale, ou `-a codex` (et éventuellement
d'autres agents) pour cibler un agent précis. Les mises à jour se font avec
`npx skills update`.

## Ajouter un skill

Chaque skill doit vivre dans son propre sous-répertoire de `skills/` et
contenir un fichier `SKILL.md` avec un frontmatter YAML comprenant au minimum
`name` et `description` :

```text
skills/
└── mon-skill/
    └── SKILL.md
```

Un modèle est disponible dans [`templates/SKILL.md.example`](templates/SKILL.md.example).

