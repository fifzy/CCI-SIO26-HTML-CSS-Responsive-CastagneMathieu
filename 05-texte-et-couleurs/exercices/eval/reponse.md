## Question 10

`.prix` est en `2em`, donc sa taille dépend de celle de son parent. Ici le parent est `<main>`, qui hérite de la taille du `body` (1.125rem, soit 18 px avec le réglage par défaut de 16 px). Le prix fait donc 2 × 18 = 36 px.

Le texte du pied de page est en `0.8rem`, qui se calcule à partir de la taille de l'élément racine `<html>`, c'est-à-dire la taille par défaut du navigateur, sans tenir compte du `body` ni des autres parents : 0.8 × 16 = 12,8 px.

Si l'utilisateur passe sa taille par défaut à 20 px, toutes ces valeurs augmentent dans la même proportion (le body passe à 22,5 px, le prix à 45 px et le pied de page à 16 px). La page reste lisible et respecte ce réglage d'accessibilité, ce qui ne serait pas le cas avec des tailles en `px` fixes.
