# Exercice 2 : Structurer un texte brut

## Éléments du squelette

- `<!DOCTYPE html>` : indique au navigateur que le document est en HTML5.
- `<html lang="fr">` : élément racine qui contient toute la page ; `lang="fr"` déclare la langue (utile aux lecteurs d'écran et aux moteurs de recherche).
- `<head>` : contient les informations sur la page, qui ne s'affichent pas dans son contenu.
- `<meta charset="UTF-8">` : définit l'encodage, ce qui permet d'afficher correctement les accents.
- `<title>` : texte affiché dans l'onglet du navigateur.
- `<body>` : contient tout le contenu visible de la page.

## Justification des choix

- **Titres** : un seul `h1` pour le sujet de la page (« Installer un serveur web Apache sur Debian »), puis des `h2` pour les quatre parties de même niveau (Prérequis, Installation, Caractéristiques principales, Pour aller plus loin).
- **`ol` pour l'installation** : les étapes doivent être réalisées dans un ordre précis, la numérotation a un sens.
- **`ul` pour les caractéristiques** : ce sont des éléments sans ordre particulier.
- **`strong` pour l'avertissement** : la phrase signale un risque de sécurité, elle a une importance forte ; `strong` exprime ce sens, alors que `b` ne ferait que changer l'apparence.
- **Titre d'onglet différent du `h1`** : l'onglet doit rester court et identifiable, le `h1` décrit précisément le contenu.