# Typographie française : espaces et signes

Référence de la section 7 de [`SKILL.md`](../SKILL.md). Ces règles portent sur la prose. Le code, les commandes, les identifiants et les citations restent tels quels.

## Espaces avant et après les signes

| Signe | France | Québec (OQLF) | Après le signe |
| --- | --- | --- | --- |
| `.` `,` | aucune espace | aucune espace | espace ordinaire |
| `:` | espace insécable | espace insécable | espace ordinaire |
| `;` | espace insécable | aucune espace (fine insécable admise) | espace ordinaire |
| `!` `?` | espace insécable | aucune espace (fine insécable admise) | espace ordinaire |
| `«` | espace ordinaire avant | espace ordinaire avant | espace insécable |
| `»` | espace insécable avant | espace insécable avant | espace ordinaire |
| `%` | espace insécable | espace insécable | espace ordinaire |
| `€`, `$` | espace insécable | espace insécable | espace ordinaire |
| unités (`Go`, `km`, `°C`) | espace insécable | espace insécable | espace ordinaire |
| heures | `14 h 30` | `14 h 30` | |

Sources : guide de style Microsoft pour le français de France (section « Nonbreaking space ») et tableau de l'OQLF « Espacement avant et après les signes de ponctuation et les symboles ». Pour la France, la référence des imprimeurs est le *Lexique des règles typographiques en usage à l'Imprimerie nationale*, ouvrage payant, non consulté ici.

Mettez aussi une espace insécable :

- entre les chiffres d'un grand nombre : `1 000 000` ;
- entre un nombre et son unité, son symbole ou sa devise : `5 000 €` ;
- entre « chapitre », « annexe », « article » et son numéro : `chapitre 2`.

## Caractères

| Caractère | Unicode | HTML |
| --- | --- | --- |
| espace insécable | U+00A0 | `&nbsp;` |
| espace fine insécable | U+202F | `&#8239;` |
| guillemet ouvrant « | U+00AB | `&laquo;` |
| guillemet fermant » | U+00BB | `&raquo;` |
| apostrophe typographique ’ | U+2019 | `&rsquo;` |
| points de suspension … | U+2026 | `&hellip;` |

## Fichiers sources

Une espace insécable est invisible dans un éditeur et dans une revue de code. Elle peut aussi gêner certains outils de publication : le guide Microsoft déconseille les espaces insécables dans le contenu publié en ligne. Dans un fichier Markdown, un message de commit ou une chaîne de code :

- suivez l'usage du dépôt ;
- si le dépôt n'utilise pas d'espace insécable, mettez une espace ordinaire avant `:` `;` `!` `?` et à l'intérieur des guillemets (variante de France) ;
- n'écrivez jamais un signe collé au mot avant `:` ni à l'intérieur de « ».

L'apostrophe suit la même logique : gardez l'apostrophe droite `'` si le dépôt l'utilise, et ne mélangez pas les deux formes dans un fichier.

## Guillemets

- Guillemets français « » pour les citations et les termes mis en relief.
- Citation dans une citation : “ ” (guide Microsoft).
- Code, chaînes et noms de fichiers : accents graves Markdown (`` ` ``), sans guillemets.

## Majuscules

- Accentuez les capitales : « État », « À partir de », « ÉCHEC ». L'Académie française rappelle que l'accent a pleine valeur orthographique.
- Titres en casse de phrase : majuscule au premier mot et aux noms propres seulement.
- Minuscule aux jours, aux mois, aux noms de langues (« le français ») et aux adjectifs de nationalité.

## Nombres et dates

- Virgule décimale : `3,5`. Point uniquement dans un numéro de version (`version 4.2`) ou dans du code.
- Ordinaux abrégés : `1er`, `1re`, `2e`, `3e`.
- Dates en lettres dans la prose (« 26 octobre 2026 »), ou au format ISO `2026-10-26` dans un tableau ou un nom de fichier.
