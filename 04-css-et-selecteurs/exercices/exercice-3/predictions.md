# Exercice 3, partie B : Prédire la présentation

## Spécificité des règles

| N° | Règle | Spécificité |
|---|---|---|
| 1 | `p { color: black; font-size: 16px; }` | (0, 0, 1) |
| 2 | `.texte { color: blue; }` | (0, 1, 0) |
| 3 | `div p { color: green; }` | (0, 0, 2) |
| 4 | `.intro { color: orange; font-size: 20px; }` | (0, 1, 0) |
| 5 | `p.texte { font-weight: bold; }` | (0, 1, 1) |
| 6 | `.texte { font-weight: normal; }` | (0, 1, 0) |
| 7 | `p#special { color: purple; }` | (1, 0, 1) |
| 8 | `p { color: gray; }` | (0, 0, 1) |
| 9 | `h1 { color: red; }` | (0, 0, 1) |
| 10 | `.titre { color: navy; }` | (0, 1, 0) |
| 11 | `.conteneur { color: brown; }` | (0, 1, 0), sur le `div` |

## Résultat

| Élément | Couleur | Taille | Graisse | Règle gagnante pour la couleur et raison |
|---|---|---|---|---|
| `h1` | navy | 32 px | gras | `.titre` (0, 1, 0) bat `h1` (0, 0, 1) : **spécificité**. Le brun du `div` n'est qu'hérité, il perd face à toute règle qui cible directement le `h1`. Taille et graisse : valeurs par défaut du navigateur pour un `h1` (2em, soit 32 px, et gras). |
| premier paragraphe | orange | 20 px | gras | `.intro` et `.texte` valent (0, 1, 0) et battent `p` et `div p` ; `.intro` est écrite après `.texte` : **ordre**. Taille : `.intro` (0, 1, 0) bat `p` (0, 0, 1). Graisse : `p.texte` (0, 1, 1) bat `.texte` (0, 1, 0) même si elle est écrite avant : **spécificité**. |
| `em` (dans le 1er p) | orange | 20 px | gras | Aucune règle ne cible `em` : il reçoit la couleur, la taille et la graisse du paragraphe par **héritage**. Il est en italique (style par défaut de `em`). |
| second paragraphe | purple | 16 px | gras | `p#special` (1, 0, 1) contient un identifiant, elle bat toutes les autres : **spécificité**. Taille : seule `p` la définit (16 px). Graisse : `p.texte` (0, 1, 1) bat `.texte` (0, 1, 0). |
| troisième paragraphe | green | 16 px | normal | `div p` (0, 0, 2) bat les deux règles `p` (0, 0, 1) : **spécificité** (deux balises contre une). Le gris de la dernière règle `p` perd, même s'il est écrit en dernier. Graisse : aucune règle, valeur normale. |

## À retenir

- La spécificité passe avant l'ordre : l'ordre ne départage que deux règles de même spécificité (premier paragraphe, couleur).
- Une valeur héritée (le brun du `div`) perd toujours face à une règle qui cible l'élément lui-même, même très peu spécifique.
- Les pièges du support : la dernière règle `p { color: gray; }` ne s'applique à aucun paragraphe, et `.texte { font-weight: normal; }` est écrite après `p.texte` mais perd quand même.
