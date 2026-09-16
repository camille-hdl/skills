---
date: 2026-09-16
---

# Tableau de recommandation

Relevé le **2026-09-16** à partir de benchmarks et de documentations **publiés** ; aucun benchmark n'a été lancé pour l'écrire. Il couvre sept modèles : GPT-6 Astra, GPT-5.6 Sol, Terra et Luna (OpenAI), Claude Opus 5 et Fable 5.1 (Anthropic), Grok 4.6 (SpaceXAI, servi par Cursor). Les autres modèles n'y ont pas de rang.

## Niveaux de preuve

- **[T]** mesure d'un tiers indépendant. Pèse le plus.
- **[É]** déclaration d'un éditeur : son harnais, effort rarement précisé, pas de réplication. Vaut indice, pas mesure.
- **[I]** inférence : le raisonnement est donné, aucune source ne l'affirme.
- **‡ forfait** : l'ordre de la ligne dépend du forfait de l'utilisateur ; voir « Coût : le forfait décide de l'ordre ».

## Catalogue

| Modèle | Éditeur | Codex | Claude Code | Cursor | Effort par défaut |
| --- | --- | --- | --- | --- | --- |
| Astra | OpenAI | `gpt-6-astra` | — | — | medium |
| Sol | OpenAI | `gpt-5.6-sol` | — | oui | **low** |
| Terra | OpenAI | `gpt-5.6-terra` | — | oui | medium |
| Luna | OpenAI | `gpt-5.6-luna` | — | oui | medium |
| Opus 5 | Anthropic | — | `opus` | oui | — |
| Fable 5.1 | Anthropic | — | `fable` | oui, **sans conservation zéro** | high |
| Grok 4.6 | SpaceXAI / Cursor | — | — | `cursor-grok-4.6-<effort>` | high |

Efforts : `low`, `medium`, `high`, `xhigh`, `max`. Les défauts diffèrent d'un modèle à l'autre : passe toujours l'effort explicitement. Dans Cursor, l'effort fait partie de l'identifiant (voir `harnais.md`).

## Complexité et impact

Complexité, de la plus simple à la plus dure :

- **mécanique** : extraction, renommage, classement, transformation, sans décision à prendre ;
- **plan prêt** : les décisions sont prises, il reste à exécuter une tâche courte ;
- **longue et autonome** : plan prêt, mais beaucoup d'étapes sans supervision ;
- **sans plan** : l'agent doit choisir l'approche.

Impact :

- **faible** : l'erreur se voit vite et se répare sans dommage ;
- **moyen** : l'erreur coûte du temps de reprise ;
- **fort** : l'erreur touche la production, des données, la sécurité, ou une décision coûteuse à défaire.

L'impact ne vient d'aucun benchmark. Il règle la revue : plus il est fort, plus la revue est indépendante — autre éditeur, modèle fort.

## Recommandations

Forme de la commande : la section du harnais dans `harnais.md`, avec l'identifiant du catalogue et l'effort de la ligne (dans Cursor, l'effort fait partie de l'identifiant).

| Nature | Complexité · impact | Modèle + effort | Harnais | Preuve | Remarque |
| --- | --- | --- | --- | --- | --- |
| Code | mécanique | Luna `low` ou `medium` | Codex ; Cursor | OpenAI oriente Luna vers « extraction, classification, transformation » [É] | aucune donnée tierce sur l'effort bas en code |
| Code | plan prêt · faible | Luna `high` | Codex ; Cursor | SWE-Bench Pro 62,7 % contre Sol 64,6 % [É] ; ARC-AGI-2 : 7,4 % en `medium`, 29,3 % en `high` [T] | [I] l'effort `high` vaut son surcoût |
| Code | longue et autonome · moyen | Opus 5 `high` | Claude Code | Terminal-Bench 4.0 : 51,8 %, contre Sol 37,3 % et Luna 17,3 % [T] | très verbeux ; dans Claude Code, un advisor Fable 5.1 est possible, son apport n'est pas mesuré |
| Code | sans plan, ou impact fort | Astra `high` ou Fable 5.1 `high` ‡ forfait | Codex / Claude Code | Terminal-Bench 4.0 : 58,2 % et 57,9 %, chacun dans son harnais [T] | revue par l'autre |
| Planification | complexe · fort | Fable 5.1 `high` ou Astra `high` ‡ forfait ; contre-lecture du plan par l'autre | Claude Code / Codex | Astra 1er sur tous les proxys : Intelligence Index 53, ECI 166, ARC-AGI-2 92,1 % en `high`, ARC-AGI-3 62,7 % [T] ; Fable 5.1 au même niveau : Intelligence Index 53, ECI 164 [T] | Astra est le moins verbeux des modèles forts [T] |
| Planification | moyenne | Opus 5 `high` | Claude Code | Intelligence Index 51, ECI 162, ARC-AGI-3 30,2 % contre Sol 7,8 % [T] | |
| Recherche web | enjeu faible, coût bas | Luna `high` | Codex, web activé ; Cursor | BrowseComp 83,3 % [É] ; seule option bon marché avec une donnée | Grok 4.6 coûte moins encore sur Cursor, mais sans aucune donnée : à essayer, pas à recommander |
| Recherche web | enjeu fort, synthèse qui décide | Sol `xhigh` | Codex, web activé | seul signal tiers : 1er d'Arena Search, en `xhigh`, au 2026-08-24 [T] ; BrowseComp 90,4 % [É] | Astra, Opus 5 et Fable 5.1 étaient absents d'Arena Search. Sans Codex : Opus 5 avec outils web, BrowseComp 90,8 % [É, lecture incertaine] |
| Revue de code | toute implémentation | l'autre éditeur parmi Astra `high`, Fable 5.1 `high`, Opus 5 `high` | Codex / Claude Code | les trois premiers de Terminal-Bench 4.0 [T] | égal ou supérieur à l'auteur, dans la grille Code |
| Prose pour humains | relecture, simplification | Grok 4.6 `high` | Cursor | aucun benchmark de reformulation trouvé | choix d'usage de l'auteur de la skill, non mesuré |

Lignes absentes :

- **Planification simple** : aucune ligne. [I] Prends le modèle le moins coûteux au niveau « Bonne » ou plus de la grille Planification.
- **Terra : aucune case.** [I] Elle coûte 10 fois Luna en crédits Codex, pour un Terminal-Bench 4.0 dans les intervalles de confiance de Luna (21,5 ± 3,3 contre 17,3 ± 2,8) et un BrowseComp à 4 points [É].

## Grilles de performance

Pour le repli et le choix du relecteur : un niveau par ligne, du plus fort au plus faible. « Coût » suit l'ordre de quota [I] de la section suivante ; entre Opus 5, Astra et Fable 5.1, il dépend du forfait.

### Planification

Aucun benchmark ne mesure la planification. Proxys : raisonnement sur problèmes fermés.

| Niveau | Modèles | Coût | Preuve |
| --- | --- | --- | --- |
| Haute | Astra, Fable 5.1 ; Opus 5 un cran dessous | élevé ‡ | Intelligence Index 53 / 53 / 51 ; ECI 166 / 164 / 162 ; ARC-AGI-3 : Astra 62,7 %, Opus 5 30,2 %, Fable 5.1 non publié [T] |
| Bonne | Sol | moyen | Intelligence Index 47, ECI 162, ARC-AGI-2 92,5 % en `max`, mais ARC-AGI-3 7,8 % [T] |
| Moyenne | Grok 4.6 ; Terra | faible ; moyen | Intelligence Index 44 / 42 ; ARC-AGI-2 67,1 % en `xhigh` / 83,9 % en `max` [T] |
| Faible | Luna | faible | Intelligence Index 38 ; ARC-AGI-2 59,5 % en `max`, 7,4 % en `medium` [T] |

### Code

| Niveau | Modèles | Coût | Preuve |
| --- | --- | --- | --- |
| Haute | Astra, Fable 5.1 | élevé ‡ | Terminal-Bench 4.0 : 58,2 %, 57,9 % [T] |
| Bonne | Opus 5 | élevé ‡ | Terminal-Bench 4.0 : 51,8 % [T] ; CursorBench 70,0 % [É] |
| Moyenne | Sol | moyen | Terminal-Bench 4.0 : 37,3 % [T] ; SWE-Bench Pro 64,6 % [É] |
| Faible sur tâches longues, proche sur tâches cadrées | Terra, Grok 4.6, Luna | moyen ; faible ; faible | Terminal-Bench 4.0 : 21,5 %, 20,3 % (dans Grok Build), 17,3 % [T] ; SWE-Bench Pro Luna 62,7 % [É] ; CursorBench Grok 4.6 69,9 % [É, Cursor co-entraîne Grok] |

[I] L'écart entre SWE-Bench Pro [É] et Terminal-Bench 4.0 [T] suggère qu'un petit modèle suffit quand la tâche est découpée, et décroche sur de longues tâches autonomes.

### Recherche web

Aucun benchmark tiers de recherche agentique. Le seul signal indépendant est Arena Search.

| Niveau | Modèles | Coût | Preuve |
| --- | --- | --- | --- |
| Haute | Sol ; Astra, Opus 5, Fable 5.1 | moyen ; élevé ‡ | Sol 1er d'Arena Search [T] ; BrowseComp Astra 91,5 %, Sol 90,4 %, Opus 5 90,8 % [É] ; HLE avec outils Fable 5.1 65,0 %, Opus 5 63,6 % [É] |
| Bonne | Terra ; Luna | moyen ; faible | BrowseComp 87,5 % ; 83,3 % [É] |
| Inconnue | Grok 4.6 | faible | aucune donnée |

## Coût : le forfait décide de l'ordre

Le coût qui compte n'est pas le prix au jeton, mais ce que la délégation consomme **du forfait de l'utilisateur** : un quota rare, des crédits payants, ou de l'argent sur une clé d'API. Le même modèle peut passer par deux réserves : Sol, Terra et Luna par Codex ou Cursor ; Opus 5 et Fable 5.1 par Claude Code ou Cursor. Quand une réserve est basse, l'autre prend le relais.

### Repères indépendants du forfait

| Modèle | Crédits Codex par M de sortie [É] | Jetons de sortie pour l'Intelligence Index [T] | Prix API, $ par M, entrée → sortie [É] | Coût d'un run Terminal-Bench 4.0 [T] |
| --- | --- | --- | --- | --- |
| Luna | 30 (×1) | 150 M | 0,20 → 1,20 | 0,3 k$ |
| Terra | 300 (×10) | 120 M | 2 → 12 | 1,7 k$ |
| Sol | 500 (×17) | 90 M | 4 → 20, promotion annoncée au moins jusqu'au 21 novembre 2026 | 2,5 k$ |
| Astra | 1 250 (×42) | **60 M**, le plus concis | 10 → 50 | 3,3 k$ |
| Grok 4.6 | — | 94 M | 2 → 6 | 3,6 k$ (dans Grok Build) |
| Opus 5 | — | 140 M | 5 → 25 | 6,0 k$ |
| Fable 5.1 | — | 190 M, le plus verbeux | 10 → 50 | 6,2 k$ |

- Contradiction [É] : l'annonce GPT-5.6 donne Sol 5 → 30, Terra 2,50 → 15, Luna 1 → 6.
- Les jetons ne se comparent pas un pour un entre éditeurs : le tokenizer d'Anthropic produit « approximately 30% more tokens for the same text » [É].
- [T] Astra coûte 2,5 fois Sol au jeton, mais en consomme trois fois moins : son run Terminal-Bench 4.0 coûte 1,3 fois celui de Sol, pour 58,2 % contre 37,3 %.

### Selon le forfait

| Forfait | Limites publiques | Effet sur l'ordre |
| --- | --- | --- |
| ChatGPT Plus (Codex) | messages locaux par fenêtre de 5 h : Astra 5–45, Sol 10–100, Terra 25–200, Luna 250–2 000 ; « Weekly limits may also apply » [É] | **Astra est rare** : réserve-le à la planification ou au code à impact fort, et préfère Fable 5.1 si le forfait Claude l'inclut. Luna est la bête de somme |
| ChatGPT Pro 5x / Pro 20x | Astra 25–225 / 100–900 ; Luna 1 250–10 000 / 5 000–40 000 [É] | Astra devient un premier recours pour le code sans plan et la planification lourde |
| Mode Fast de Codex | Astra : « 2.5x multiplier » ; autres modèles non publiés [É] | à éviter quand le quota compte |
| Claude Pro | Opus 5 inclus, « strongest model on Claude Pro » ; Fable 5.1 **uniquement par crédits payants** [É] | Fable 5.1 coûte de l'argent : Astra ou Opus 5 d'abord, Fable 5.1 en dernier, advisor compris |
| Claude Max | Fable 5.1 inclus jusqu'à « 50% of your weekly usage limits », consommé plus vite que les autres modèles Claude, sans multiplicateur publié ; limites absolues non publiées [É] | **Fable 5.1 devient le premier recours** en planification lourde et en code sans plan ; Astra reste la réserve. Un advisor Fable consomme du quota, pas de l'argent |
| Cursor, forfaits payants | deux réserves mensuelles : « Cursor Models », avec « significantly more included usage » pour Grok 4.6 ; « Other Models » (GPT-5.6, Opus 5, Fable 5.1) décomptés au prix API ; Astra absent ; montants non publiés [É] | Grok 4.6 est le moins cher. Cursor sert de réserve de secours pour Luna, Sol, Opus 5 et Fable 5.1 quand Codex ou Claude sont épuisés, hors données confidentielles pour Fable 5.1 |
| Clé d'API seule | prix au jeton | ordre par coût de run [T] : Luna < Terra < Sol < Astra < Grok 4.6 < Opus 5 ≈ Fable 5.1 |

Contradiction [É] : le centre d'aide ChatGPT réserve Astra aux forfaits Pro et supérieurs, le tableau de Codex lui donne un quota sur Plus. Vérifie avec la liste des modèles de Codex (`harnais.md`).

**Forfait inconnu.** Ordre de quota [I], du moins cher au plus cher : Grok 4.6 (réserve Cursor dédiée) · Luna · Terra · Sol · puis Opus 5, Astra et Fable 5.1, **sans ordre entre eux**. Quand le choix tombe entre ces trois-là, le forfait décide : demande-le.

## Trous

Rien de fiable n'est publié sur ces points. Dis-le plutôt que de combler.

- **Planification** : aucun benchmark. Les proxys mesurent le raisonnement sur des problèmes fermés, pas le découpage, les arbitrages ni la lisibilité d'un plan sur un dépôt réel.
- **Combinaisons** — advisor, contre-lecture, revue croisée : aucun benchmark.
- **Harnais** : Terminal-Bench 4.0 mesure un couple modèle + harnais de l'éditeur (Codex, Claude Code, Grok Build). Rien ne mesure ces modèles dans Cursor.
- **Grok 4.6** : aucune donnée en recherche web ; en code, le tiers (Terminal-Bench 4.0, dans Grok Build) et l'éditeur (CursorBench) se contredisent. Rien n'établit que Grok 4.6 dans Cursor et dans l'API SpaceXAI ont les mêmes poids.
- **SWE-bench indépendant** : aucune ligne lisible pour ces modèles. SWE-bench Verified est écarté : OpenAI ne le publie plus, pour contamination et tests défectueux. Les SWE-Bench Pro de Fable 5.1 (81,2 %) et d'Opus 5 (79,2 %) ne viennent que d'agrégateurs.
- **Fable 5.1** : ni BrowseComp, ni ARC-AGI-3.
- **ARC-AGI-3** : les 99,9 % d'Astra annoncés par OpenAI viennent d'un harnais propre (« Provider Adapter ») ; seul le harnais « Standard », à 62,7 %, se compare aux autres.
- **Index agrégés** : les éditeurs citent l'Intelligence Index en v4.1, le site d'Artificial Analysis est en v4.3. Les classements diffèrent ; ne mélange pas les versions.
- **Recherche agentique indépendante** (GAIA, DeepResearch Bench) et **METR time horizon** : rien pour ces modèles.
- **Quotas** : montants inclus des réserves Cursor, limites absolues de Claude, multiplicateur de Fable, multiplicateurs Fast de Codex hors Astra : non publiés.

## Sources

Accès du 2026-09-16.

| Source | Nature | Ce qu'elle mesure |
| --- | --- | --- |
| [Terminal-Bench 4.0](https://www.tbench.ai/leaderboard/terminal-bench/4.0) | [T] | tâches en terminal, dans le harnais de l'éditeur ; jetons et coût du run |
| [Artificial Analysis](https://artificialanalysis.ai/models) | [T] | Intelligence Index v4.3 (10 évaluations), jetons de sortie et coût pour le faire tourner |
| [Epoch Capabilities Index](https://epoch.ai/eci) | [T] | agrégat de capacités |
| [ARC Prize](https://arcprize.org/leaderboard) | [T] | ARC-AGI-2 et ARC-AGI-3, par effort, avec coût par tâche |
| [Arena Search](https://arena.ai/leaderboard/search) | [T] | préférence humaine sur des réponses avec recherche ; mise à jour du 2026-08-24 |
| [OpenAI, GPT-6 Astra](https://openai.com/index/gpt-6-astra/) · [GPT-5.6](https://openai.com/index/gpt-5-6/) | [É] | SWE-Bench Pro, DeepSWE, BrowseComp, HLE |
| [Anthropic, Fable 5.1](https://www.anthropic.com/claude-fable-and-mythos-5-1) · [Opus 5](https://www.anthropic.com/news/claude-opus-5) | [É] | HLE, CursorBench, Terminal-Bench |
| [Cursor, Grok 4.6](https://cursor.com/grok) · [x.ai](https://x.ai/news/grok-4-6) | [É] | CursorBench, DeepSWE |
| [OpenAI, SWE-bench Verified](https://openai.com/index/why-we-no-longer-evaluate-swe-bench-verified/) | [É] | raisons de l'abandon |
| [Modèles de l'API OpenAI](https://developers.openai.com/api/docs/models) · [prix](https://developers.openai.com/api/docs/pricing) | [É] | identifiants, efforts, prix |
| [Prix de l'API Anthropic](https://platform.claude.com/docs/en/about-claude/pricing) | [É] | prix, tokenizer |
| [Codex, forfaits](https://learn.chatgpt.com/docs/pricing) · [centre d'aide ChatGPT](https://help.openai.com/en/articles/20001325-a-preview-of-gpt-56-sol-terra-and-luna) | [É] | messages par 5 h, crédits, disponibilité d'Astra |
| [Claude, Fable selon le forfait](https://support.claude.com/en/articles/15424964-claude-fable-models-on-your-plan) · [limites d'usage](https://support.claude.com/en/articles/11647753-how-do-usage-and-length-limits-work) | [É] | Fable sur Pro et Max |
| [Cursor, modèles](https://cursor.com/docs/models) · [prix](https://cursor.com/pricing) | [É] | réserves, décompte au prix API |

## Mettre à jour

1. Relis chaque source ci-dessus ; ajoute les nouveaux modèles des éditeurs couverts, et ceux que l'utilisateur a installés.
2. Garde le niveau de preuve de chaque chiffre ; un chiffre [T] remplace un chiffre [É].
3. Revois les recommandations, les grilles, les effets de forfait et les trous.
4. Change la `date` du frontmatter.
