## 5. Recherches et vérifications

- **Balise `meta viewport`** (MDN) : `<meta name="viewport" content="width=device-width, initial-scale=1.0">` indique au navigateur mobile d'utiliser la largeur réelle de l'écran et un zoom de 100 %. Sans elle, le téléphone simule un écran d'ordinateur et réduit la page. Vérifié dans Firefox avec la vue téléphone (Ctrl + Maj + M).
- **Entités HTML** (MDN) : les caractères `<` et `>` s'écrivent `&lt;` et `&gt;`, sinon le navigateur les prend pour le début d'une balise. Utilisé pour afficher `<destination>` dans la syntaxe.
- **Balise `code`** (MDN) : élément sémantique qui indique un fragment de code informatique. Utilisé pour toutes les commandes et options.
- **Balise `strong`** (MDN) : indique un contenu d'importance forte. Utilisée pour l'avertissement, à la place d'un titre choisi pour son apparence.
- **Options de ping** (`man ping`, Linux) : la ligne SYNOPSIS donne la forme générale `ping [options] <destination>`, où les crochets signalent ce qui est facultatif. Les options `-c`, `-i`, `-s` et `-p` ont été choisies dans cette page.
- **Fonctionnement de ping** : la commande utilise le protocole ICMP (requête et réponse d'écho). Un ping vers une adresse IP qui répond, alors qu'un ping vers un nom de domaine échoue, indique une panne DNS. Un ping sans réponse ne prouve pas que l'appareil est éteint, car un pare-feu peut bloquer ICMP.