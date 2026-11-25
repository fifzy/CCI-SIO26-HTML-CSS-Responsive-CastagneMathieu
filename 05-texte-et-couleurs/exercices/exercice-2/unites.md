# Exercice 2 : comparer les unités `em` et `rem`

## Feuilles de style testées

`version-em.css` :

```css
html { font-size: 16px; }
.niveau1, .niveau2, .niveau3 { font-size: 1.5em; }
```

`version-rem.css` :

```css
html { font-size: 16px; }
.niveau1, .niveau2, .niveau3 { font-size: 1.5rem; }
```

Les virgules dans le sélecteur appliquent la même règle aux trois classes, sans la recopier.

Pour les tests à 20 px, seule la valeur de `html` change (`font-size: 20px;`).

## Méthode de test

- Un seul `index.html` : on change le `href` de la balise `<link>` pour passer de `version-em.css` à `version-rem.css`.
- Rechargement avec **Ctrl + Maj + R** après chaque modification (pour éviter le cache).
- Mesure dans l'inspecteur de Firefox, onglet **Calculé** (Computed), propriété `font-size`.

## Prédictions et mesures (en px)

| Unité | Racine | Niveau 1 | Niveau 2 | Niveau 3 |
|---|---|---|---|---|
| `em` | 16 px | 24 / 24 | 36 / 36 | 54 / 54 |
| `rem` | 16 px | 24 / 24 | 24 / 24 | 24 / 24 |
| `em` | 20 px | 30 / 30 | 45 / 45 | 67,5 / 67,5 |
| `rem` | 20 px | 30 / 30 | 30 / 30 | 30 / 30 |

*Format des cellules : prédiction / mesure.*

### Calculs

- **`em`, racine 16 px** : 1,5 × 16 = 24, puis 1,5 × 24 = 36, puis 1,5 × 36 = 54.
- **`rem`, racine 16 px** : 1,5 × 16 = 24 pour les trois niveaux.
- **`em`, racine 20 px** : 1,5 × 20 = 30, puis 1,5 × 30 = 45, puis 1,5 × 45 = 67,5.
- **`rem`, racine 20 px** : 1,5 × 20 = 30 pour les trois niveaux.

Astuce de calcul : 1,5 fois un nombre, c'est le nombre plus sa moitié.

## Explication des écarts

Aucun écart entre les prédictions et les mesures. Les différences observées viennent du fonctionnement des deux unités :

- **`em` se rapporte au parent.** Le niveau 1 se calcule à partir de `body` (qui hérite de la racine), le niveau 2 à partir du niveau 1, le niveau 3 à partir du niveau 2. La taille est donc **multipliée** par 1,5 à chaque imbrication : c'est l'**effet cumulatif**.
- **`rem` se rapporte toujours à la racine `html`.** La profondeur de l'élément ne change rien : les trois niveaux ont la même taille. Il n'y a **pas d'effet cumulatif**.
- **Quand la racine passe de 16 à 20 px**, les deux versions grandissent, puisque `em` et `rem` remontent tous les deux jusqu'à la racine. Mais avec `em`, l'écart entre les niveaux grandit aussi à cause de la multiplication en chaîne.

Erreur à éviter : la taille de la racine (16 px) est la **référence** du calcul, pas le résultat.

## Règle de choix

- **`px`** : pour une valeur fixe qui ne doit jamais varier (bordures, détails fins) ; elle ne suit ni la taille de base ni le réglage du navigateur.
- **`em`** : pour une taille qui doit suivre celle de son parent (proportions à l'intérieur d'un composant) ; attention à l'effet cumulatif quand on imbrique.
- **`rem`** : pour les tailles de texte du site ; tout se rapporte à la racine, donc changer une seule valeur sur `html` met toute la page à l'échelle de façon cohérente.