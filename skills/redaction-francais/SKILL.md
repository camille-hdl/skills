---
name: redaction-francais
description: Rédaction technique en français, en langage clair (plain language, ISO 24495-1) et selon la typographie française. À utiliser pour écrire ou relire en français une documentation, un README, un guide, une note de décision, une description de PR, un message de commit ou un message d'erreur, ou quand un skill ou l'utilisateur demande `redaction-francais`.
---

# Rédaction en français

Un texte est en **langage clair** quand son lecteur y trouve ce dont il a besoin, le comprend à la première lecture et peut s'en servir. « Langage clair » est le terme français pour *plain language*. La norme ISO 24495-1:2023 en fixe les principes au niveau international, et la norme canadienne CAN-ASC-3.1:2025 en donne une version française gratuite. Ce skill applique cette démarche au français technique.

Il suffit seul pour un texte en français. Une fois le texte écrit, passez `unslop` (par `unslop-agent` si l'agent ne peut pas l'invoquer), qui retire les tics d'écriture d'IA. Ses règles visent l'anglais, donc appliquez leur équivalent français. Sa règle 19 (guillemets droits) ne vaut pas pour le français : gardez « ».

Ne modifiez jamais le code, les commandes, les chemins, les identifiants, les URL, les messages d'erreur cités ni les citations. Corrigez la prose autour.

Les conventions écrites du dépôt ou de l'organisation l'emportent sur ce skill : glossaire, tutoiement, écriture inclusive, variante régionale, espaces insécables. Cherchez-les avant d'écrire (`AGENTS.md`, `CONTRIBUTING.md`, charte éditoriale, textes voisins).

## 1. Situer le lecteur

Avant d'écrire, répondez à trois questions :

- Qui lit ? Une personne qui développe le projet, qui l'exploite, qui l'utilise, qui relit une PR ?
- Que sait-elle déjà ? Le vocabulaire du domaine, le code, rien ?
- Que doit-elle faire ou savoir après la lecture ?

Un document sert un usage principal : faire agir (installer, corriger, déployer) ou faire comprendre (expliquer un choix, décrire une API). Quand un texte mélange les deux, séparez-les en sections ou en documents liés. Une procédure n'explique pas le pourquoi en cours de route. Elle renvoie à l'explication.

Si le public est inconnu et que le choix change le texte, demandez-le.

L'étape est finie quand vous pouvez écrire en une phrase : « [lecteur] lit ce texte pour [action ou savoir] ».

## 2. Mettre l'essentiel d'abord

- Ouvrez le document, la section et le paragraphe par ce que le lecteur doit retenir ou faire. Le contexte, les détails et les exceptions viennent après (pyramide inversée).
- Un titre dit ce que contient la section : « Sauvegarder la base avant la migration », pas « Remarques ». Écrivez-le en casse de phrase : seule la première lettre et les noms propres prennent une majuscule.
- Trois niveaux de titres au plus.
- Un thème par paragraphe.
- Étapes ordonnées : liste numérotée. Éléments sans ordre : liste à puces. Données à comparer : tableau. Les éléments d'une liste ont la même forme grammaticale.

## 3. Écrire des phrases claires

- **Une idée par phrase.** Au-delà de 20 mots, cherchez à couper. Une phrase plus longue reste si elle porte une seule idée et se lit d'une traite.
- **Sujet, verbe, complément.** Rapprochez le sujet du verbe. Une incise longue entre les deux devient une autre phrase.
- **Nommez qui agit.** « Le script supprime les fichiers temporaires », pas « Les fichiers temporaires sont supprimés ». Le passif reste possible quand l'acteur est inconnu ou sans importance.
- **Le verbe plutôt que le nom.** Le français administratif empile les noms tirés de verbes : « procéder à la vérification de » devient « vérifier », « effectuer la mise à jour de » devient « mettre à jour ». Méfiez-vous de « permettre de », « faire l'objet de », « être en mesure de ».
- **Pas de chaîne de compléments.** « La mise à jour de la configuration du serveur de production » se lit mal. Écrivez « mettre à jour la configuration du serveur de production », ou coupez.
- **Pas de participe présent en remorque.** « …, permettant ainsi de réduire les coûts » devient une phrase qui a son propre sujet : « Le cache réduit les coûts. »
- **Affirmez ce qui est sûr.** Le conditionnel de prudence (« devrait », « pourrait », « il conviendrait de ») rend chaque phrase incertaine. Écrivez le fait au présent. Pour une incertitude réelle, dites ce qui est inconnu : « La cause n'est pas encore identifiée. »
- **La forme affirmative.** « Gardez la clé secrète » plutôt que « Ne divulguez pas la clé ». Réservez la négation aux interdictions qui ont des conséquences graves. Évitez la double négation.
- **Lisez « ne… pas que » deux fois.** « Le script ne lit pas que les fichiers JSON » peut vouloir dire « il lit aussi d'autres fichiers » ou « il ne lit pas les fichiers JSON ». Écrivez celle des deux qui est vraie.
- **Un pronom, un antécédent évident.** « Celui-ci », « ce dernier », « cela », « ce qui » renvoient souvent à deux candidats. Répétez le nom.
- **Le sujet nommé plutôt que « on ».** « On » ne dit pas qui agit. Écrivez « vous », « nous », « l'équipe », « le serveur ».
- **Des liens logiques explicites.** « parce que », « donc », « si », « avant », « après » disent la relation que le lecteur devrait sinon deviner.

## 4. Choisir les mots

- Le mot courant : « utiliser », pas « recourir à ». « Avant », pas « préalablement ». « Pour », pas « afin de ».
- Un terme par notion, du début à la fin. Un synonyme fait croire à une autre notion.
- Définissez un terme technique à sa première occurrence, en mots simples ou par un exemple. Développez un sigle à sa première occurrence : « interface de programmation (API) ».
- Le vocabulaire du projet l'emporte. Si le dépôt dit « merge », « déployer », « ticket », gardez ces mots.
- Hors vocabulaire du projet, évitez les faux amis et les calques de l'anglais : « supporter » au sens de *to support* devient « prendre en charge » ou « soutenir », « impacter » devient « affecter » ou « toucher », « librairie » au sens de *library* devient « bibliothèque », « consistant » au sens de *consistent* devient « cohérent ». En cas de doute, cherchez dans FranceTerme, la Vitrine linguistique de l'OQLF ou « Dire, ne pas dire » de l'Académie française.
- Écrivez au sens propre. Une figure de style ou une expression familière échappe au lecteur qui lit en seconde langue ou à travers un outil de traduction.

## 5. Rédiger les consignes

- **Une forme pour tout le document.** L'impératif (« Lancez la commande ») s'adresse au lecteur. L'infinitif (« Lancer la commande ») convient aux modes d'emploi impersonnels et aux consignes très courtes. Les deux sont corrects. Gardez la même forme dans tout le document, et la forme déjà employée par le dépôt s'il en a une.
- **Le but ou la condition d'abord.** « Pour restaurer la base, lancez `make restore`. » « Si la commande échoue, relancez-la avec `--verbose`. » Le lecteur saute ce qui ne le concerne pas.
- **Une action par étape.** Ajoutez ce que le lecteur doit voir quand l'étape a réussi : la sortie attendue, le fichier créé, le message affiché.
- **L'avertissement avant l'étape qu'il protège**, jamais après.

## 6. S'adresser au lecteur

- Vouvoyez le lecteur, sauf si le projet tutoie.
- « Nous » désigne les auteurs ou l'équipe, quand c'est utile.
- Écriture inclusive : suivez la convention du projet. Sans convention, préférez les tournures qui ne demandent aucun signe particulier : noms épicènes (« les membres », « le personnel »), noms collectifs (« l'équipe », « la direction »), reformulation (« si vous êtes inscrit » devient « après votre inscription »).

## 7. Appliquer la typographie française

Ces règles portent sur la prose, pas sur le code.

- **Guillemets** « » avec une espace insécable à l'intérieur : « exemple ». Pour une citation dans une citation, “ ”. Le code garde ses guillemets droits.
- **Espaces avant la ponctuation.** Usage de France : espace insécable avant `:` `;` `!` `?`. Usage du Québec : espace insécable avant `:`, aucune espace avant `;` `!` `?`. Suivez la variante du dépôt. À défaut, prenez celle du public visé. Dans un fichier source (Markdown, message de commit), une espace ordinaire remplace l'insécable si le dépôt n'en utilise pas. Une absence d'espace avant `:` n'est correcte dans aucune variante.
- **Majuscules accentuées** : « État », « À noter ». Pas de majuscule aux jours, aux mois ni aux noms de langues.
- **Nombres** : `1 000` (espace insécable entre les milliers), `3,5` (virgule décimale), `10 %`, `20 €`, `14 h 30`, `1er`, `2e`. L'unité suit le nombre, séparée par une espace insécable.
- **Abréviations** : « etc. » termine une liste sans points de suspension. « M. », « Mme ».

Tableau complet par signe, variantes et caractères Unicode : [`references/typographie.md`](references/typographie.md).

## 8. Relire

Relisez le texte entier contre chaque section ci-dessus. Puis vérifiez :

- La première phrase de chaque section dit l'essentiel.
- Chaque phrase de plus de 20 mots a été relue et coupée, ou gardée pour une raison que vous pouvez donner.
- Aucun « on », aucun conditionnel de prudence, aucun participe présent en remorque ne reste sans raison.
- Chaque terme technique est défini ou connu du lecteur, et chaque notion garde un seul nom.
- Les consignes ont toutes la même forme verbale.
- Les guillemets, les espaces avant la ponctuation et les nombres suivent la section 7.
- Le code, les commandes et les citations sont intacts.

Les formules de lisibilité (Flesch et ses adaptations au français) repèrent des phrases longues, mais ne disent pas si le lecteur comprend. Le seul test fiable est un lecteur du public visé. Quand le texte compte (procédure d'exploitation, message à des usagers), proposez de le faire relire par une personne de ce public.

L'étape est finie quand le texte livré est la version corrigée, pas une liste de remarques. Passez ensuite `unslop`.

## Exemple

Avant :

> Afin de procéder à la mise à jour de la configuration, il conviendrait d'effectuer préalablement une sauvegarde de la base, celle-ci pouvant être impactée par la migration, ce qui pourrait entraîner une perte de données.

Après :

> Avant de mettre à jour la configuration, sauvegardez la base de données avec `make backup`. La migration modifie des tables. Si elle échoue sans sauvegarde, les données modifiées sont perdues.

L'action ouvre le texte. Le conditionnel de prudence, les noms tirés de verbes et le pronom ambigu « celle-ci » disparaissent. « Impacter » devient un fait précis : la migration modifie des tables.

## Langage clair, FALC et langue contrôlée

Le langage clair vise tout lecteur. Deux démarches voisines ont d'autres buts :

- Le **FALC** (facile à lire et à comprendre) s'adresse aux personnes qui ont une déficience intellectuelle. Ses règles européennes sont plus strictes, et un texte FALC se relit avec des personnes de ce public. Si le texte vise ce public, dites-le et renvoyez aux règles de l'Unapei.
- Une **langue contrôlée** (ASD-STE100, français rationalisé du GIFAS) restreint le vocabulaire et les temps verbaux pour la maintenance industrielle et la traduction. Ce skill n'impose pas ces restrictions.

## Sources

- ISO 24495-1:2023, *Langage clair et simple — Partie 1 : Principes directeurs et lignes directrices* (payante, non reproduite) : <https://www.iso.org/standard/78907.html>
- CAN-ASC-3.1:2025, *Langage clair*, Normes d'accessibilité Canada (gratuite, en français) : <https://accessibilite.canada.ca/node/985>
- *Guide de rédaction du contenu du site Canada.ca*, section 2 « Langage clair » : <https://conception.canada.ca/guide-redaction/>
- Direction interministérielle de la transformation publique (DITP), « Simplifier le langage et les documents administratifs » : <https://www.modernisation.gouv.fr/simplifier-la-vie-des-usagers-et-des-agents/simplifier-le-langage-et-les-documents-administratifs>
- Office québécois de la langue française, Vitrine linguistique (impératif et infinitif, espacement, emprunts) : <https://vitrinelinguistique.oqlf.gouv.qc.ca/>
- Microsoft, *French (France) Localization Style Guide* : <https://download.microsoft.com/download/c/7/9/c7921dbd-4531-4a4e-8490-e4656d739f3d/fra-fra-StyleGuide.pdf>
- Académie française, accentuation des majuscules et « Dire, ne pas dire » : <https://www.dictionnaire-academie.fr/article/QDL005>
- FranceTerme, termes recommandés au Journal officiel : <https://www.culture.gouv.fr/thematiques/langue-francaise-et-langues-de-france/agir-pour-les-langues/moderniser-et-enrichir-la-langue-francaise/vous-avez-besoin-d-un-terme-francais>
- Unapei, *L'information pour tous*, règles européennes du FALC : <https://www.unapei.org/document/explication-liste-verification-falc/>
