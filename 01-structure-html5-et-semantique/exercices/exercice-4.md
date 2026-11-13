# Exercice 4 : Documenter une commande

## 1. Hiérarchie des titres et choix des listes

- **`h1` « La commande ping »** : un seul titre principal, car c'est le sujet de toute la page.
- **`h2` « Syntaxe », « Options courantes », « Utilisation pas à pas »** : ce sont trois parties de même niveau, directement sous le titre principal.
- **`h3` « Tester le réseau local » et « Tester Internet »** : ce sont deux sous-parties de « Utilisation pas à pas », donc un niveau en dessous. La hiérarchie ne saute aucun niveau (`h1` puis `h2` puis `h3`).
- **`ul` pour les options** : les options sont présentées sans ordre particulier, l'ordre de la liste n'a pas de sens.
- **`ol` pour la procédure** : les quatre étapes doivent être suivies dans l'ordre, la numérotation a un sens.
- **`p` + `strong` pour l'avertissement** : c'est une phrase importante du texte, pas le titre d'une partie ; `strong` exprime son importance sans détourner une balise de titre pour son apparence.

## 2. Titre de l'onglet et titre de la page

Le `<title>`, placé dans le `<head>`, n'apparaît pas dans la page : il s'affiche dans l'onglet, les favoris, l'historique et les résultats des moteurs de recherche. Le `<h1>`, placé dans le `<body>`, est le titre visible du contenu de la page. Ici, le cahier des charges impose le même texte pour les deux (« La commande ping »), mais ils ont des rôles différents.

## 3. Rôles de HTML, CSS et JavaScript

- **HTML** structure le contenu de la page et donne du sens à chaque élément (titre, paragraphe, liste…).
- **CSS** définit la présentation de ce contenu (couleurs, polices, tailles, disposition).
- **JavaScript** rend la page dynamique : il réagit aux actions de l'utilisateur et peut modifier le contenu sans recharger la page.

## 4. Du fichier reçu à l'affichage

1. Le navigateur reçoit le fichier HTML envoyé par le serveur web (ici Apache, via HTTP).
2. Il lit le DOCTYPE (mode standard) et l'encodage (`meta charset`) pour interpréter correctement les caractères.
3. Il analyse le code et construit l'arbre du document (le DOM), visible dans l'inspecteur.
4. Il charge les ressources liées (feuilles CSS, images, scripts) et applique les styles, ceux par défaut s'il n'y a pas de CSS.
5. Il calcule la mise en page en fonction de la largeur de l'écran (balise viewport), puis dessine la page à l'écran.

## 5. Recherches et vérifications

- **Balise `meta viewport`** (MDN) : `<meta name="viewport" content="width=device-width, initial-scale=1.0">` indique au navigateur mobile d'utiliser la largeur réelle de l'écran et un zoom de 100 %. Sans elle, le téléphone simule un écran d'ordinateur et réduit la page. Vérifié dans Firefox avec la vue téléphone (Ctrl + Maj + M).
- **Entités HTML** (MDN) : les caractères `<` et `>` s'écrivent `&lt;` et `&gt;`, sinon le navigateur les prend pour le début d'une balise. Utilisé pour afficher `<destination>` dans la syntaxe.
- **Balise `code`** (MDN) : élément sémantique qui indique un fragment de code informatique. Utilisé pour toutes les commandes et options.
- **Balise `strong`** (MDN) : indique un contenu d'importance forte. Utilisée pour l'avertissement, à la place d'un titre choisi pour son apparence.
- **Options de ping** (`man ping`, Linux) : la ligne SYNOPSIS donne la forme générale `ping [options] <destination>`, où les crochets signalent ce qui est facultatif. Les options `-c`, `-i`, `-s` et `-p` ont été choisies dans cette page.
- **Fonctionnement de ping** : la commande utilise le protocole ICMP (requête et réponse d'écho). Un ping vers une adresse IP qui répond, alors qu'un ping vers un nom de domaine échoue, indique une panne DNS. Un ping sans réponse ne prouve pas que l'appareil est éteint, car un pare-feu peut bloquer ICMP.