# Harnais

Comment lancer un agent délégué depuis n'importe quel harnais : tout passe par des commandes shell. La `--help` du CLI installé fait foi ; ce fichier en garde ce qu'elle ne dit pas.

Marqué **✔** : exécuté le 2026-09-16 avec codex-cli 0.154.0, Claude Code 2.1.273 et cursor-agent 2026.09.10. Le reste est une forme à vérifier avant usage.

## Inventaire des modèles

- **Codex** : `codex debug models`.
- **Cursor** : `cursor-agent --list-models`. Les modèles sans conservation zéro des données y portent la mention « (NO ZDR) ».
- **Claude Code** : alias `opus` et `fable` pour `--model`.
- **Tout CLI** : un prompt trivial (« Réponds uniquement PONG ») avec le modèle et l'effort voulus confirme l'accès pour quelques jetons.

## Forme commune

Écris le mandat dans un fichier et passe-le **par l'entrée standard** (`< mandat.md`). Les trois CLI ci-dessous le lisent ainsi ✔, et cela évite de citer un long texte dans le shell.

Accorde les droits du **périmètre** du mandat, pas davantage : lecture seule pour une recherche, une planification ou une revue ; écriture pour une implémentation.

Pour une tâche longue, lance la commande en arrière-plan si ton harnais le permet, ou redirige sa sortie vers un fichier que tu liras.

## Codex

```sh
codex exec --ephemeral -s read-only -m gpt-5.6-luna -c model_reasoning_effort="low" - < mandat.md
```

✔ tel quel. Variantes :

- **écriture** : `-s workspace-write` ;
- **hors dépôt git** : `--skip-git-repo-check` ;
- **web** : `--search`, ou `web_search = "live"` dans la configuration de Codex ([doc](https://developers.openai.com/codex/config-basic)) ✔ ;
- **dernier message dans un fichier** : `-o <fichier>`.

## Claude Code

```sh
claude -p --model opus --effort low < mandat.md
```

✔ tel quel. Variantes :

- **web** : `--allowedTools "WebSearch,WebFetch"` ✔. Cette option est **variadique** : elle avale un prompt placé après elle. Le mandat passe donc par l'entrée standard, jamais en argument.
- **écriture et shell** : `--permission-mode` et `--allowedTools` règlent les droits ; vérifie les valeurs dans `claude --help`.

## Cursor

```sh
cursor-agent -p --trust --mode ask --model cursor-grok-4.6-low --output-format text < mandat.md
```

✔ tel quel, en lecture seule. Variantes :

- **shell ou web** : `-f --sandbox enabled` ✔. Sans `-f`, l'agent en mode `-p` se voit refuser le shell et la recherche web, **même dans un répertoire de confiance**. `--sandbox enabled` borne ce que `-f` ouvre.
- **écriture** : retire `--mode ask`.
- **modèle** : l'effort fait partie de l'identifiant (`gpt-5.6-luna-high`, `cursor-grok-4.6-high`) ; prends l'identifiant exact dans `cursor-agent --list-models`.

## Herdr

Herdr lance l'agent dans un pane, où l'utilisateur peut le suivre. Si une skill `herdr` est installée, suis-la ; `herdr --help` et `herdr agent` font foi.

1. Trouve ou crée un pane shell libre (`herdr pane`).
2. Démarre l'agent avec ses options de modèle et d'effort :
   ```sh
   herdr agent start <nom> --kind codex --pane <id> -- --model gpt-5.6-luna -c model_reasoning_effort="high"
   ```
   `--kind` accepte aussi `claude`, `cursor` et d'autres ; les options après `--` sont celles du CLI interactif.
3. Envoie-lui un pointeur vers le mandat :
   ```sh
   herdr agent prompt <nom> "Lis et exécute le mandat du fichier <chemin>." --wait
   ```
4. Lis son rendu avec `herdr agent read <nom>`, ou dans les fichiers que le mandat désigne.

## Autres CLI

Gemini CLI, OpenCode et les autres : dans leur `--help`, trouve le mode non interactif, le choix du modèle et de l'effort, la lecture de l'entrée standard et les droits. Vérifie la forme avec un prompt trivial avant d'envoyer le mandat.

## Confidentialité

Pour des données confidentielles, retiens un modèle et un harnais qui conservent zéro donnée :

- **Cursor** : écarte les modèles marqués « (NO ZDR) » dans `cursor-agent --list-models`. Le 2026-09-16, c'était le cas de tous les `claude-fable-5-1-*`.
- **Anthropic** : les modèles Fable imposent 30 jours de rétention par défaut ([support Claude](https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan)).
- Pour les autres, la politique de conservation du fournisseur et le contrat de l'utilisateur font foi ; dans le doute, demande.
