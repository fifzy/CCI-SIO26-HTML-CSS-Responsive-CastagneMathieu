# Exercice 2 : Cibler des éléments

| N° | Sélecteur | Pourquoi il convient |
|---|---|---|
| 1 | `p` | Sélecteur de balise : il cible tous les paragraphes du document, où qu'ils soient. |
| 2 | `.important` | Sélecteur de classe : il cible tous les éléments qui ont la classe `important`, quel que soit leur type (`<p>` ou `<li>`). |
| 3 | `#entete` | Sélecteur d'identifiant : il cible le seul élément qui porte `id="entete"`, le `<header>`. |
| 4 | `h1, h2` | Sélecteur de groupe : la virgule applique la même règle aux `<h1>` et aux `<h2>`. |
| 5 | `p.important` | Balise et classe collées : seulement les `<p>` qui ont la classe `important`, donc pas le `<li>` « Install party ». |
| 6 | `a.actif` | Balise et classe collées : seulement le lien `<a>` qui a la classe `actif`, c'est-à-dire « Actualités ». |
| 7 | `footer p` | Sélecteur descendant : l'espace veut dire « dans », donc seulement les `<p>` situés dans le `<footer>`. |
| 8 | `#agenda li` | Sélecteur descendant : seulement les `<li>` situés dans l'élément d'identifiant `agenda`, pas ceux du menu, qui sont dans `#entete`. |
| 9 | `.important.rappel` | Deux classes collées sans espace : seulement l'élément qui a les deux classes à la fois, « N'oubliez pas votre carte ». |

## Vérification

Chaque règle a été testée dans le navigateur, puis dans l'inspecteur (clic droit, Inspecter), en vérifiant aussi les éléments qui ne devaient **pas** changer : le `<li>` « Install party » ne passe pas en rouge (règle 5), les liens du menu ne passent pas en vert (règle 8), le paragraphe « Inscriptions ouvertes… » ne passe pas en italique (règle 9).

« Install party » reçoit deux règles en même temps, le gras de `.important` (règle 2) et le vert de `#agenda li` (règle 8) : elles ne touchent pas la même propriété, donc elles s'appliquent toutes les deux.