# Exercice 3, partie A : Calculer des spécificités

Rappel : la spécificité s'écrit (a, b, c), avec a = identifiants, b = classes, attributs et pseudo-classes, c = balises. On compare colonne par colonne, de gauche à droite, sans additionner.

## 1. Spécificité de chaque sélecteur

| Sélecteur | (a, b, c) | Détail |
|---|---|---|
| `p` | (0, 0, 1) | 1 balise |
| `.carte` | (0, 1, 0) | 1 classe |
| `#entete` | (1, 0, 0) | 1 identifiant |
| `header nav a` | (0, 0, 3) | 3 balises |
| `ul.menu li` | (0, 1, 2) | 1 classe, 2 balises |
| `#menu a.actif` | (1, 1, 1) | 1 identifiant, 1 classe, 1 balise |
| `a:hover` | (0, 1, 1) | 1 pseudo-classe, 1 balise |
| `input[type="text"]` | (0, 1, 1) | 1 attribut, 1 balise |
| `.carte .titre` | (0, 2, 0) | 2 classes |
| `body #page .contenu p` | (1, 1, 2) | 1 identifiant, 1 classe, 2 balises |

## 2. Comparaison de paires

| Paire | Spécificités | Gagnant | Raison |
|---|---|---|---|
| `.titre` / `h1.titre` | (0, 1, 0) / (0, 1, 1) | `h1.titre` | Égalité sur a et b, `h1.titre` l'emporte sur c. |
| `#menu a` / `.menu .lien.actif` | (1, 0, 1) / (0, 3, 0) | `#menu a` | La colonne a est comparée en premier : un identifiant bat n'importe quel nombre de classes. |
| `p` / `*` | (0, 0, 1) / (0, 0, 0) | `p` | Le sélecteur universel `*` ne compte pour rien. |

## 3. Même spécificité

Quand deux règles ont la même spécificité, c'est **la dernière déclarée** dans la feuille de style qui gagne.

Avec `.carte { color: blue; }` puis `.titre { color: red; }`, `<p class="titre carte">` est **rouge** : les deux sélecteurs valent (0, 1, 0) et `.titre` est écrite en dernier. L'ordre des classes dans l'attribut `class` ne compte pas.

## 4. Ordre de priorité

Du plus fort au plus faible : `!important` > style en ligne > `#id` > classe > balise.

`<p id="menu">` avec `#menu { color: green; }` et `p { color: blue !important; }` est **bleu** : `!important` passe avant la spécificité, même face à un identifiant.
