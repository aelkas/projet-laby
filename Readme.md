# projet-laby

Représentation, génération, résolution et affichage de labyrinthes en OCaml, avec
export vers des fichiers HTML animés.

<!-- EDIT : une animation ou une capture d'un labyrinthe résolu, placée ici,
     vaut mieux que tout le reste du fichier. Le module Gui les génère déjà. -->

## Ce que fait le projet

Un labyrinthe est une grille de nœuds reliés ou séparés par des murs. À partir de
cette structure, le projet permet de générer des labyrinthes, de les résoudre, de
les lire et de les écrire depuis des fichiers, et de produire un rendu HTML animé
qui montre le déroulement des algorithmes.

<!-- EDIT : nommer ici les algorithmes de génération et de résolution
     effectivement implémentés (par exemple exploration exhaustive, fusion de
     chemins, BFS, DFS...). C'est l'information que cherche un lecteur, et elle
     n'apparaît nulle part pour l'instant. -->

## Architecture

Chaque module suit la même discipline : une interface `.mli`, une implémentation
`.ml`, et un fichier de test dédié.

| Module | Rôle |
|---|---|
| `node` | le type nœud, brique de base du labyrinthe |
| `grid` | le type grille et les fonctions associées |
| `laby` | module principal : labyrinthes, algorithmes de génération et de résolution, entrées/sorties |
| `gui` | génération des fichiers HTML pour l'affichage animé |

Le point d'entrée est `maze.ml`.

Séparer systématiquement interface et implémentation force chaque module à
exposer un contrat minimal : `laby` ne connaît de `grid` que sa signature, ce qui
permet de faire évoluer les implémentations sans casser le reste.

## Compilation et exécution

```shell
dune build
./maze.exe [arguments]
```

Pour nettoyer les fichiers produits par la compilation :

```shell
dune clean
```

Les scripts `.sh` compilent et lancent les tests de chaque module séparément :

```bash
bash test_laby.sh
```

`clear.sh` supprime les fichiers issus de la compilation.

## Contenu du dépôt

- `Doc/` — le rapport détaillé
- `test/` — fichiers de labyrinthes, valides ou non, utilisés par les tests

## Rapport

<!-- EDIT : remplacer par le nom exact du fichier présent dans Doc/ -->
[**Rapport détaillé du projet**](Doc/rapport.pdf) — conception, algorithmes et
choix d'implémentation.

---

Projet réalisé en binôme avec Rayan Lalaoui, licence double diplôme
mathématiques-informatique, Université Paris-Saclay.

