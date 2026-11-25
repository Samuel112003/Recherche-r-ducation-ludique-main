# Plan de recherche et état d'avancement

Le travail est découpé en étapes. Chaque étape donne lieu à une recherche de sources puis à une synthèse dans `syntheses/`.

Dernière mise à jour : 25/11/2026.

## Étape 1 — Ancrage clinique

- Les troubles de la main : post-opératoire, blessures, TMS
- Enjeux et défis de la rééducation de la main

**État : terminée.** Synthèse à jour : `syntheses/Synthèse et ancrage scientifique v3.pdf` (4 pages de texte et 2 de références). Elle intègre le chiffrage et les causes de la mauvaise observance (Jordan 2010, Jack 2010, Essery 2017, Then 2020) et justifie le choix des pathologies « cas d'école ». Les parties de la v2 qui relevaient de l'étape 2 en ont été retirées : le plaisir (Jones & Zenko) et le détail de la comparaison activités/exercices. Elles sont à reprendre dans la synthèse de l'étape 2.

## Étape 2 — Ludification et motivation

- L'impact de la ludification sur la motivation à faire une activité douloureuse ou pénible (jeu, gamification)
- Qu'est-ce qui pousse à faire une activité appréciée malgré sa pénibilité ou la douleur ?
- La ludification du renforcement et de la rééducation de la main

**État :** collecte commencée, pas encore de synthèse dédiée. La synthèse v2 (§2.4 et §2.5), retirée du dossier mais disponible dans l'historique git, contient déjà des éléments à reprendre : les témoignages de Collis 2021 sur les activités appréciées, la comparaison activités/exercices de Collis 2022 et le plaisir pendant l'effort (Jones & Zenko 2023).

| Point | Sources | Couverture |
|---|---|---|
| Impact de la ludification sur la motivation face à une activité pénible | Jones & Zenko 2023, Then 2020, Liu 2022, Koutsiana 2020, Doumas 2021 | Correcte, mais preuves fragiles : petits effectifs, AVC, sujets sains |
| Ce qui fait tenir malgré la douleur ou la pénibilité | Collis 2021 (qualitative, dans la thèse), Jack 2010 (obstacles à l'observance), Jordan 2010 (leviers), Núñez-Cortés 2026 (distraction) | Correcte |
| Ludification de la rééducation **de la main** | Then 2020, Liu 2022 | Faible : deux petites études seulement |

## Étape 3 — Exercices, ressenti et capteurs

- La ludification des renforcements musculaires et de la rééducation
- Exercices de renforcement et de rééducation de la main (pouce, doigts, poignet…)
- Impact de l'appréciation des exercices sur la qualité de la rééducation
- Le ressenti des exercices de renforcement et de rééducation de la main
- Capteurs physiologiques dans la réhabilitation de la main

**État :** collecte commencée.

| Point | Sources | Couverture |
|---|---|---|
| Ludification du renforcement et de la rééducation | Koutsiana 2020, Doumas 2021 (membre supérieur, AVC) ; Then 2020, Liu 2022 (main) | Correcte pour le membre supérieur, faible pour la main |
| Exercices pouce, doigts, poignet | Groth 2004 (tendons), Collis 2022 (poignet) | Partielle, pas de source dédiée |
| Impact de l'appréciation sur la qualité de la rééducation | Collis 2022 (activités choisies), Jones & Zenko 2023 | Partielle |
| Ressenti des exercices | Collis 2021 (qualitative, dans la thèse), Liu 2022 (questionnaire) | Faible |
| Capteurs physiologiques en rééducation de la main | Liu 2022 seulement. Baghernezhad, Al-Timemy et Pradhan portent sur des sujets sains, hors rééducation | Faible |

## Étape bonus (envisagée) — Valider un mouvement par capteurs

Question : comment vérifier qu'un mouvement est **bien exécuté** (conforme et réellement fait) avec un suivi EMG et/ou accéléromètres ?

**Constat actuel :** aucune source trouvée qui donne des **résultats** de validation d'un mouvement de rééducation de la main suivi par EMG ou accéléromètre. Le corpus contient seulement une mesure objective par **électrogoniométrie** à domicile (Collis et al., 2022, dans la thèse Collis), qui montre que la mesure est faisable, sans valider de critère « bon mouvement ».

Sources ajoutées le 25/11/2026 (Baghernezhad 2025, Al-Timemy 2022, Pradhan 2022, Liu 2022) : elles montrent qu'on peut **reconnaître quel geste** est fait (environ 88–89 % chez des sujets sains) et **détecter une activation musculaire** même faible chez des patients. Aucune ne valide encore qu'un geste de rééducation est **bien exécuté** (amplitude, force, compensations) chez des patients. La question bonus reste donc ouverte.

Pistes de recherche à explorer : reconnaissance d'activités par IMU au poignet, comparaison IMU vs goniométrie, EMG de surface de l'avant-bras pour la force de préhension, validation de capteurs dans les gants instrumentés.

Ce point est directement lié à l'exigence « vérifier l'engagement et la conformité au protocole » du sujet.
