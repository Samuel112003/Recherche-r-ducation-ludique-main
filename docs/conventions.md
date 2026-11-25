# Conventions de travail

## Organisation du dépôt

```
sources/                      PDF des sources
  INDEX.md                    tableau des sources : type, thèmes, usage dans la synthèse
  1 - Revues systematiques/
  2 - Etudes cliniques/
  3 - Theses et modeles cliniques/
  4 - Documents institutionnels/
  5 - Etudes techniques et jeux de donnees/
  <dossiers temporaires>      parfois créés pour déposer de nouvelles sources avant tri
syntheses/                    synthèses rédigées (PDF)
  src/                        sources HTML des synthèses (à partir de la v3)
docs/                         cette documentation
```

## Règles de classement des sources

Détail complet dans [`sources/INDEX.md`](../sources/INDEX.md). En résumé :

- **Un dossier = la nature de la source** : revue, étude clinique, thèse ou modèle, document institutionnel, étude technique. Chaque source est dans un seul dossier. Les **thèmes** sont des étiquettes dans `INDEX.md`, et une source peut en avoir plusieurs.
- **Nommage :** `Auteur Année - Titre court.pdf`. Deux auteurs : `Auteur1 Auteur2`. Trois et plus : premier auteur seul.
- Toute source ajoutée dans un dossier classé doit avoir sa ligne dans `INDEX.md`.
- Une source citée dans une autre mais pas encore téléchargée va dans la table « Sources à récupérer » de `INDEX.md`.
- Un dossier sans numéro contient de nouvelles sources déposées par l'équipe. Les trier seulement quand l'équipe le demande : supprimer les doublons, renommer, classer dans 1 à 5, ajouter une ligne dans `INDEX.md`.
- L'équipe préfère des dossiers **intuitifs** plutôt qu'une classification rigide (décision du 25/11/2026). On peut créer, renommer ou fusionner un dossier si une source ne trouve pas de place naturelle. Il faut alors mettre à jour le tableau « Organisation » de `INDEX.md` et ce fichier.
- Règle de partage entre 2 et 5 : une étude **sur des patients** va dans `2 - Etudes cliniques`, même si elle utilise des capteurs (ex. Liu 2022). Une étude technique **sur des sujets sains** ou un jeu de données va dans `5 - Etudes techniques et jeux de donnees`.

## Règles de rédaction des synthèses

Elles découlent des synthèses v2 et v3 :

- Chaque affirmation renvoie à une source **du corpus**, avec son type de preuve.
- Ce que le corpus ne permet pas d'établir est **signalé explicitement**, pas comblé par des connaissances générales.
- Une référence seulement citée par une autre source (« cité dans ») est signalée comme telle. Il faut la récupérer avant de la citer en première main.
- Pas de chiffre sans source vérifiée. Exemple : le « 40 à 70 % d'abandon » de la v1 a été retiré, faute de source dans le corpus. Une fois Jack et al. (2010) récupéré, on a constaté que la revue ne fait que **citer** « jusqu'à 70 % » d'après Sluijs et al. (1993). Essery et al. (2017) reprend le même chiffre, de la même source : un chiffre souvent répété n'est pas pour autant mieux établi. Il faut donc toujours lire la source avant de lui attribuer un chiffre.
- Rédaction en français, fluide et concise : une synthèse ne traite que les idées de son étape, et renvoie le reste à l'étape concernée.

## Produire une synthèse en PDF

Les synthèses sont écrites en HTML dans `syntheses/src/`, puis imprimées en PDF avec Edge en mode headless (aucun outil LaTeX ou pandoc n'est installé) :

```bash
cd syntheses
"/c/Program Files (x86)/Microsoft/Edge/Application/msedge.exe" --headless --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="$(cygpath -w "$PWD")\\Synthèse et ancrage scientifique v3.pdf" \
  "file:///$(cygpath -m "$PWD")/src/synthese-v3.html"
```

Après une modification de la source, regénérer le PDF et vérifier les sauts de page (`pdftotext -f N -l N`).

## Git

- Messages de commit en français, première ligne courte, puis le détail.
- Les gros PDF sont versionnés directement (pas de Git LFS).

## Notes techniques pour une instance Claude (Windows, Git Bash)

- `pdftotext` est disponible (`pdftotext -layout fichier.pdf -` pour sortir sur stdout). Les accents s'affichent mal dans le terminal mais le texte est exploitable.
- `pdfinfo` et `pdftoppm` ne sont **pas** installés : l'outil Read ne peut donc pas afficher les pages de PDF. PyMuPDF (`fitz`) et `pypdf` ne sont pas installés non plus.
- Pour un PDF scanné sans texte (ex. `Nunez-Cortes 2026…`), on peut extraire l'image de la page en PNG avec un petit script Python (zlib + struct) puis la lire avec l'outil Read.
- Vérifier les doublons avec `md5sum` avant d'ajouter une source : deux fichiers déposés le 25/11/2026 étaient des copies de sources déjà classées. Vérifier aussi l'auteur et le sujet, et pas seulement le nom : un premier « Jack 2010 » était un homonyme hors sujet.
- Cochrane et PubMed Central bloquent le téléchargement direct des PDF par `curl` (erreur 412, page anti-robot). Pour un article présent sur PMC, on imprime la page de l'article en PDF avec Edge headless (`--virtual-time-budget=15000 --print-to-pdf=... https://pmc.ncbi.nlm.nih.gov/articles/PMCxxxx/`). L'API Europe PMC (`ebi.ac.uk/europepmc/webservices/rest/search?query=DOI:"..."`) donne l'identifiant PMC.
- La thèse Collis 2022 fait environ 30 Mo et plusieurs centaines de pages : la lire par plages de pages (`pdftotext -f N -l M`).
