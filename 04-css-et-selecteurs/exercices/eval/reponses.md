# Évaluation : Écrire des sélecteurs

## Q1. Le titre d'identifiant « logo » en blanc

```css
#logo {
    color: white;
}
```

Le sélecteur d'identifiant cible le seul élément qui porte `id="logo"`, le `h1`.

## Q2. Tous les titres h2 en bleu

```css
h2 {
    color: blue;
}
```

Le sélecteur de balise cible tous les `h2` du document, quel que soit l'article.

## Q3. Tous les éléments de classe « prix » en gras

```css
.prix {
    font-weight: bold;
}
```

Le sélecteur de classe cible tous les éléments qui ont la classe `prix`, livres et DVD compris.

## Q4. Uniquement les prix des livres en vert

```css
.livre .prix {
    color: green;
}
```

Le sélecteur descendant ne cible que les `.prix` situés dans un élément de classe `livre` ; le DVD a la classe `dvd`, son prix n'est donc pas concerné.

## Q5. Uniquement les articles « nouveaute » avec un fond jaune clair

```css
article.nouveaute {
    background-color: lightyellow;
}
```

Balise et classe collées : seuls les `article` qui ont la classe `nouveaute` sont ciblés, ici « Linux en pratique ».

## Q6. « resume » et « slogan » en italique, en une seule règle

```css
.resume, .slogan {
    font-style: italic;
}
```

La virgule regroupe deux sélecteurs : la même règle s'applique aux éléments de classe `resume` et à ceux de classe `slogan`.

## Q7. Uniquement le texte du pied de page en gris

```css
footer p {
    color: gray;
}
```

Le sélecteur descendant ne cible que les paragraphes situés dans le `footer`.

## Q8. Relier la feuille css/eval.css

```html
<link rel="stylesheet" href="css/eval.css">
```

Cette ligne se place dans le `<head>` du document, par exemple après le `<title>`.

## Q9. Couleur des prix

```css
.prix { color: black; }          /* (0, 1, 0) */
article .prix { color: green; }  /* (0, 1, 1) */
.livre .prix { color: red; }     /* (0, 2, 0) */
```

- **Prix du premier livre : rouge.** Les trois règles le ciblent ; `.livre .prix` (0, 2, 0) a deux classes et bat `article .prix` (0, 1, 1) et `.prix` (0, 1, 0).
- **Prix du DVD : vert.** `.livre .prix` ne le cible pas (l'article a la classe `dvd`) ; entre les deux règles restantes, `article .prix` (0, 1, 1) bat `.prix` (0, 1, 0) grâce à la balise en plus.
