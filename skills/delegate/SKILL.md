---
name: delegate
description: Déléguer une tâche à un autre agent en ligne de commande (Codex, Claude Code, Cursor…) par un mandat qui ne porte que le contexte nécessaire. À utiliser pour confier une tâche ou une revue à un agent, ou pour choisir le modèle et le harnais d'une délégation.
---

# Déléguer

Le **mandat** est le seul document que reçoit l'agent délégué : il ne voit ni la conversation, ni ton raisonnement. Tout ce qu'il doit savoir et ne peut pas trouver en regardant y est ; le reste n'y est pas.

L'outil, la combinaison d'agents et le repli se choisissent sur une **échelle** : on descend les barreaux dans l'ordre et on s'arrête au premier qui s'applique. Ce sont des règles, pas des suggestions : garde l'ordre des barreaux.

Deux fichiers de référence, lus quand une étape les appelle :

- [`references/tableau.md`](references/tableau.md) : modèles recommandés par nature de tâche, complexité et impact ; grilles de performance ; coût selon le forfait ; sources, niveaux de preuve et trous. Daté.
- [`references/harnais.md`](references/harnais.md) : inventaire, forme de lancement de chaque CLI, pièges vérifiés, confidentialité.

Pour demander quelque chose à l'utilisateur, écris la question dans ta réponse et attends.

## 1. Relever la demande

Pour chaque point, note « donné » (avec la valeur) ou « absent » :

- la tâche, et ce qui la termine ;
- l'outil de délégation (Herdr, un CLI précis…) ;
- la combinaison d'agents — modèle, effort, harnais — pour la tâche et pour la revue ;
- la difficulté annoncée, et la préférence pour un modèle cher ou économique ;
- l'impact : ce que coûte une erreur ;
- la confidentialité des données que l'agent verra ;
- les forfaits de l'utilisateur (ChatGPT, Claude, Cursor, clé d'API…).

Cherche aussi dans `AGENTS.md`, `CLAUDE.md` et la documentation accessible du projet : outil de délégation, modèles, forfaits.

Terminé quand chaque point porte « donné » ou « absent ».

## 2. Inventaire et âge du tableau

Lance, quel que soit ton shell :

```sh
sh -c 'date +%F; for c in herdr codex claude cursor-agent gemini opencode; do command -v "$c"; done; echo "HERDR_ENV=${HERDR_ENV:-}"'
```

- **Harnais installés** : les CLI trouvés. Pour les modèles réellement accessibles, voir « Inventaire » dans `references/harnais.md`.
- **Herdr disponible** : `herdr` est trouvé **et** `HERDR_ENV=1`, c'est-à-dire que tu tournes dans un pane Herdr.
- **Âge du tableau** : compare la date du jour à la `date` du frontmatter de `references/tableau.md`. Si l'écart dépasse un mois, dis-le à l'utilisateur, avec la date du tableau, et recommande de le mettre à jour à partir de benchmarks récents (section « Mettre à jour » du tableau). Poursuis ensuite avec le tableau tel qu'il est.

Terminé quand tu as la liste des harnais, la réponse sur Herdr, et l'âge du tableau en jours.

## 3. Outil de délégation — échelle

1. Celui que l'utilisateur précise.
2. Sinon, celui qu'indiquent `AGENTS.md` ou une autre documentation accessible du projet.
3. Sinon, **Herdr**, s'il est disponible.
4. Sinon, **demande à l'utilisateur**, en lui proposant les harnais trouvés à l'étape 2.

Terminé quand l'outil est fixé et que tu sais sur quel barreau.

## 4. Combinaison d'agents — échelle

Pour la tâche, puis pour la revue si l'étape 5 l'exige :

1. Celle que l'utilisateur précise.
2. Sinon, **choisie dans le tableau**, à partir de la difficulté annoncée par l'utilisateur, et de sa préférence cher / économique s'il l'a dite.
3. Sinon, **déterminée automatiquement** : estime la complexité et l'impact de la tâche avec les définitions du tableau, puis prends la ligne correspondante.

**Forfait.** Quand la ligne retenue dépend du forfait (le tableau le signale) et que le forfait est absent de la demande et de la documentation du projet, demande-le à l'utilisateur avant de lancer. Applique ensuite la section « Coût : le forfait décide de l'ordre » du tableau.

**Confidentialité.** Si l'agent verra des données confidentielles, retiens seulement des modèles et des harnais qui conservent zéro donnée : `references/harnais.md` dit lesquels ne le font pas.

**Repli.** Quand le modèle ou le harnais retenu n'est pas installé :

1. le même modèle par un autre harnais installé (le catalogue du tableau dit lesquels) ;
2. sinon, dans la grille de la même nature de tâche, le modèle installé du même niveau de performance au coût le plus proche ;
3. sinon, le niveau voisin, et tu le dis à l'utilisateur.

Un modèle absent du tableau n'a pas de rang : situe-le à partir d'un benchmark public daté, avec son niveau de preuve, ou demande à l'utilisateur.

Terminé quand chaque agent à lancer a un modèle, un effort et un harnais installés, et que chaque substitution est notée avec sa raison.

## 5. Revue

Une revue est nécessaire pour du code, et pour tout livrable dont l'impact est fort. Elle est confiée à un agent **de performance égale ou supérieure** à celui qui a fait la tâche, dans la grille de la même nature de tâche, et **de préférence d'un autre éditeur**. Choisis-le avec l'échelle de l'étape 4. Si la combinaison donnée par l'utilisateur place la revue sous l'agent qui a fait la tâche, signale-le avant de lancer.

Terminé quand la revue est écartée avec sa raison, ou que son agent est fixé.

## 6. Rédiger le mandat

Le mandat contient, et rien d'autre :

- **l'objectif** : ce qu'il faut produire, en une ou deux phrases ;
- **le critère de fin** : une condition que l'agent peut vérifier seul ;
- **les points d'entrée** : chemins, commandes, URL. Un pointeur suffit pour ce que l'agent peut lire ; copie seulement ce qu'il ne peut pas atteindre ;
- **les décisions déjà prises** et les contraintes, avec leur raison quand elle évite une erreur ;
- **le périmètre** : ce qu'il peut lire, modifier, exécuter ; s'il committe ; où il s'arrête ;
- **le rendu** : quoi, sous quelle forme, où l'écrire.

Relis chaque ligne : si elle ne sert aucun de ces six points, retire-la. L'historique de la conversation, tes hypothèses écartées et les préférences sans rapport avec la tâche échouent à ce test.

Pour une revue, le mandat pointe vers le mandat de la tâche, le diff ou les fichiers produits, et demande des constats vérifiés.

Écris le mandat dans un fichier : un fichier temporaire (`mktemp`), ou l'emplacement que prévoit la documentation du projet.

Terminé quand chaque ligne sert l'un des six points et que l'agent pourrait commencer sans poser de question.

## 7. Lancer

Suis `references/harnais.md` pour l'outil et le harnais retenus : forme de la commande, passage du mandat par l'entrée standard, droits accordés selon le périmètre. Lance la revue de la même façon, une fois la tâche rendue.

Terminé quand chaque agent a rendu, ou a échoué avec une erreur que tu as lue.

## 8. Rendre compte

Dis à l'utilisateur :

- l'outil et chaque combinaison, avec le barreau d'échelle qui les a fixés ;
- les substitutions et leur raison ;
- l'avertissement sur l'âge du tableau, s'il y a lieu ;
- le résultat de la tâche et celui de la revue, avec le chemin des livrables.
