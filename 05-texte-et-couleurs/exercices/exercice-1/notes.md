# Exercice 1 : mise en forme typographique

## Propriétés utilisées

- `font-size` : définit la taille du texte. La taille de base (18 px) est fixée **une seule fois**, sur `html` (consigne 9). Les autres tailles sont en `rem` : `h2` à `1.5rem`, `.chapo` à `1.1rem` et `footer` à `0.85rem`.
- `font-family` : choisit la police. Je l'ai définie sur `body` (`Arial, sans-serif`) pour qu'elle s'applique à toute la page grâce à l'**héritage**. La famille générique `sans-serif` se met toujours en dernier, sans guillemets : c'est la police de repli si Arial n'est pas installée. Sur Fedora, Arial n'est pas présente par défaut et elle est remplacée par une police compatible (Liberation Sans).
- `color` : couleur du texte. Utilisée sur `body` (#222222), `h1`, `h2`, `footer` (le même bleu dans trois formats), `.sous-titre` (#555555) et `.note` (brun foncé).
- `background-color` : couleur de fond. Utilisée sur `body` (#f5f5f5) pour toute la page, et sur `.note` (jaune pâle). Si on la met sur `p` au lieu de `body`, seuls les paragraphes ont le fond gris et le reste de la page reste blanc.
- `text-align` : alignement horizontal du texte dans son bloc. `center` sur `h1`, `.sous-titre` et `footer`.
- `font-weight` : graisse (épaisseur) du texte. `bold` sur `h2` et `.chapo`. Les `h2` sont déjà en gras par défaut dans les navigateurs, mais je l'ai écrit pour rendre la consigne 4 explicite.
- `font-style` : inclinaison du texte. `italic` sur `.sous-titre`. À ne pas confondre avec `font-weight`, qui gère l'épaisseur.

## Sélecteurs

- Un sélecteur de **balise** s'écrit avec le nom de la balise, sans chevrons : `html`, `body`, `h1`, `footer`.
- Un sélecteur de **classe** s'écrit avec un point suivi de la **valeur** de l'attribut `class` : `<p class="sous-titre">` donne `.sous-titre`. Ni `p` ni `class` n'apparaissent dans le sélecteur.
- Un sélecteur invalide (par exemple `1` au lieu de `h1`) fait ignorer **toute la règle**, sans message d'erreur.

## Choix de l'unité : `rem`

- `rem` se rapporte **toujours** à la taille de l'élément racine `html`, quelle que soit la profondeur de l'élément. `1.5rem` vaut donc toujours 1,5 × 18 = 27 px.
- `em` se rapporte à la taille du **parent** : si un ancêtre change de taille (par exemple `article { font-size: 0.9em; }`), le résultat change et l'effet se cumule. Ici, `em` aurait donné le bon résultat par chance, pas par construction.
- `px` est figé : 27 px écrit en dur ne suivrait plus la taille de base, alors que la consigne 9 demande que tout s'y rapporte.
- La racine se définit en `px` (c'est la référence), tout le reste en `rem`. Écrire `rem` sur `html` n'aurait pas de sens : il se rapporterait à lui-même.
- Une valeur ne porte qu'**une seule** unité : `16pxrem` est invalide et la déclaration est ignorée.

## Formats de couleur

Le même bleu est écrit dans trois formats (consigne 10) :

| Élément | Format | Valeur |
|---|---|---|
| `h1` | hexadécimal | `#0b3d91` |
| `h2` | `rgb()` | `rgb(11, 61, 145)` |
| `footer` | `hsl()` | `hsl(217.6, 85.9%, 30.6%)` |

- **Conversion hexadécimal vers `rgb()`** : chaque paire est un nombre en base 16, converti avec (premier chiffre × 16) + second chiffre (a = 10, b = 11… f = 15).
  - `0b` = 0 × 16 + 11 = 11
  - `3d` = 3 × 16 + 13 = 61
  - `91` = 9 × 16 + 1 = 145 (piège : en hexadécimal, `91` ne vaut pas 91)
- **Conversion vers `hsl()`** : obtenue avec Firefox (inspecteur, Maj + clic sur la pastille de couleur pour changer de format). Je garde les décimales : arrondie à `hsl(218, 86%, 31%)`, la couleur serait légèrement différente, alors que la consigne demande **le même** bleu.
- **Pourquoi le pied de page en bleu** : la consigne 8 ne fixe pas sa couleur, donc je ne contredis aucune consigne. Il reprend la couleur des titres, ce qui unifie la page.
- **Fond des notes en `hsl()`** : je suis parti d'un jaune `#e5de64`, soit environ `hsl(57, 71%, 65%)`, trop soutenu pour un jaune « pâle ». Avec `hsl()`, j'ai gardé la teinte et la saturation et j'ai seulement monté la luminosité à 90 % : `hsl(57, 71%, 90%)`. C'est l'intérêt de ce format pour éclaircir ou assombrir une couleur.
- Les noms de fonctions se collent à leur parenthèse : `rgb (11, 61, 145)`, avec un espace, est invalide.

## Contrastes (minimum AA : 4,5:1 pour le texte courant)

| Texte | Fond | Contraste | AA |
|---|---|---|---|
| #222222 (texte courant) | #f5f5f5 | 14,6:1 | ✅ |
| #555555 (sous-titre) | #f5f5f5 | 6,8:1 | ✅ |
| #0b3d91 (titres, pied de page) | #f5f5f5 | 9,2:1 | ✅ |
| #5b3c11 (notes) | hsl(57, 71%, 90%) | 9,1:1 | ✅ |

Mesure dans Firefox : inspecteur, clic sur la pastille de couleur à côté de `color`, le sélecteur affiche le contraste avec le fond.

## Vérifications dans le navigateur

Tailles mesurées dans l'onglet **Calculé** (Computed) de l'inspecteur, identiques aux prédictions :

| Élément | Calcul | Prédiction | Mesure |
|---|---|---|---|
| `h2` | 1,5 × 18 | 27 px | 27 px |
| `.chapo` | 1,1 × 18 | 19,8 px | 19,8 px |
| `footer p` | 0,85 × 18 | 15,3 px | 15,3 px |

Le `<p>` du pied de page n'a pas de règle propre : il **hérite** la taille de son parent `footer`.

## Pièges rencontrés

- Recopier les backticks `` ` `` des exemples dans le fichier CSS : la déclaration devient invalide.
- Oublier le point-virgule ou l'accolade fermante : la règle suivante peut être « avalée ».
- Mauvais chemin dans `href` (`css/style.css` au lieu de `style.css`) : la page s'affiche sans style, l'erreur 404 n'apparaît que dans l'onglet Réseau.
- Recharger avec **Ctrl + Maj + R** pour éviter l'ancienne version de la feuille en cache.