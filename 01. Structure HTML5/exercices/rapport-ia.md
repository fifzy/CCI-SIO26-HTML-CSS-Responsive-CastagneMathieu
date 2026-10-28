# Rapport d'utilisation de l'IA - Séance 1 : Structure HTML5, Markdown et Git

Étudiant : Mathieu Castagné - Date : 14/10/2026

Outil et modèle utilisés : Claude (Anthropic), modèle Claude Opus 5.5

*Note : la séance compte environ 99 messages (dont des envois de code et de captures d'écran). Seuls les échanges principaux sont détaillés ci-dessous, dans l'ordre chronologique. Les parties factuelles de ce rapport ont été pré-remplies par l'IA à partir de l'historique de la conversation.*

## Prompt 1

- Heure : 09:42
- Phase : exercice n° 1 (repérage des erreurs)
- Prompt envoyé (verbatim) :

> Selon moi il n'y a pas d'erreur dans le documents a part peut être le texte de l'onglet Dans le document B j'ai reperér `<meta charset="UFT-8">` qui a une faute d'orthographe

- Résumé de la réponse : l'IA valide l'erreur `UFT-8` mais conteste l'absence d'erreurs dans le document A. Elle donne un indice sur la structure d'un document HTML5 (première ligne, ordre de `<html>`, `<head>` et `<body>`) sans donner la solution.
- Vérification effectuée : ouverture du document B dans Firefox, le mot « Élève » s'affiche correctement. Dans la console : message indiquant que l'encodage déclaré n'est pas supporté et que la déclaration est ignorée ; `document.characterSet` renvoie `"UTF-8"`.
- Utilisation : erreur `UFT-8` retenue, conséquence comprise grâce à la console (déclaration ignorée, encodage deviné par le navigateur). L'idée de départ « pas d'erreur dans le document A » a été abandonnée : le document en contenait quatre.

## Prompt 2

- Heure : 09:53
- Phase : exercice n° 1 (recherche)
- Prompt envoyé (verbatim) :

> je peut avoir un exemple de doucment HTML5

- Résumé de la réponse : l'IA fournit un squelette HTML5 à trous (première ligne, `<head>` et `<body>` à compléter) avec des questions pour guider, et un lien vers la page MDN sur la structure HTML.
- Vérification effectuée : comparaison du squelette avec le document A. Repérage du `<p>` à la place de `</p>` (ligne 8) et du DOCTYPE (d'abord considéré comme absent, puis identifié comme mal placé en fin de fichier).
- Utilisation : squelette utilisé comme grille de comparaison ligne par ligne, et non recopié. Première réponse sur la ligne 1 erronée (`<html lang="fr">` au lieu du DOCTYPE), corrigée après un indice de l'IA.

## Prompt 3

- Heure : 10:04
- Phase : exercice n° 1 (repérage des erreurs)
- Prompt envoyé (verbatim) :

> Head est en bas de body

- Résumé de la réponse : l'IA précise que `<head>` n'est pas en dessous mais à l'intérieur de `<body>`, et demande d'observer dans l'Inspector comment Firefox a interprété le code.
- Vérification effectuée : dans l'Inspector, `<head>` est vide et `<meta>` et `<title>` sont rangés dans `<body>`. L'Inspector montre aussi deux paragraphes, dont un vide, à cause du `<p>` non fermé.
- Utilisation : correction retenue (`<head>` est à l'intérieur de `<body>`, pas en dessous). La conséquence a été constatée dans l'Inspector avant d'être formulée dans le tableau des erreurs.

## Prompt 4

- Heure : 10:15
- Phase : exercice n° 1 (formalisation)
- Prompt envoyé (verbatim) :

> Le mode quirk permet d'activer le mode standard total si il est placé au début

- Résumé de la réponse : l'IA signale une confusion entre le DOCTYPE et le mode quirks, puis propose une phrase à trous pour expliquer le mode quirks (imitation des anciens navigateurs, effet possible sur le CSS).
- Vérification effectuée : `document.compatMode` testé dans la console : `"CSS1Compat"` avec le DOCTYPE en première ligne, `"BackCompat"` pour le document A.
- Utilisation : phrase à trous complétée par l'étudiant (« nouveaux navigateurs » corrigé en « vieux navigateurs » après une question de l'IA), puis reprise comme conséquence de l'erreur 4 du document A.

## Prompt 5

- Heure : 10:27
- Phase : exercice n° 1 (formalisation)
- Prompt envoyé (verbatim) :

> redonne moi le tableau des erreurs pour que je puisse corriger

- Résumé de la réponse : l'IA fournit un tableau récapitulatif des 7 erreurs trouvées dans les deux documents (ligne, nature, conséquence).
- Vérification effectuée : pas de vérification supplémentaire : le tableau reprend les constats déjà faits dans la console et l'Inspector.
- Utilisation : tableau mis en forme par l'IA à partir des erreurs repérées au fil des échanges ; une partie des formulations des conséquences vient de l'IA. Il a servi de base aux corrections, puis à la rédaction de exercice-1.md.

## Prompt 6

- Heure : 11:04
- Phase : exercice n° 1 (version corrigée)
- Prompt envoyé (verbatim) :

> montre comment ca devrais se presenter

- Résumé de la réponse : après plusieurs essais d'indentation, l'IA montre un exemple de document indenté (avec un contenu différent) et explique la règle : chaque niveau d'imbrication ajoute le même nombre d'espaces.
- Vérification effectuée : comparaison de chaque nouvelle version avec l'exemple, et relecture par l'IA de quatre versions successives.
- Utilisation : règle d'indentation retenue et appliquée progressivement au document A. La version envoyée sur GitHub ce jour-là était cependant une version antérieure, sans les guillemets ni l'indentation corrigée.

## Prompt 7

- Heure : 13:06
- Phase : exercice n° 1 (rédaction du Markdown)
- Prompt envoyé (verbatim) :

> [envoi du brouillon complet de exercice-1.md, non reproduit ici]

- Résumé de la réponse : l'IA relève l'absence de titres Markdown et de lignes vides, l'absence des versions corrigées, une ligne concernée manquante (erreur 3 du document B), le terme « balise » inexact pour le DOCTYPE, et plusieurs fautes d'orthographe.
- Utilisation : une partie des corrections appliquée avant le commit (titres `###`, lignes vides, « problème », « traductions », « deviner », ligne ajoutée pour l'erreur 3 du document B). D'autres n'ont pas été appliquées ce jour-là (« À la », chevrons autour de `<meta>`, `<title>` et `<body>`).

## Prompt 8

- Heure : 13:14
- Phase : transfert des fichiers vers la VM (scp)
- Prompt envoyé (verbatim) :

> comment je peut commit mon travail, le clone HTML CSS est sur ma Ubuntu

- Résumé de la réponse : l'IA demande d'abord où se trouvent les fichiers (Fedora ou VM), propose deux options (copie avec `scp` ou clone du dépôt sur Fedora), puis guide pas à pas la construction de la commande `scp` (option `-r`, guillemets, chemin absolu, alias SSH `dev`).
- Vérification effectuée : commande finale écrite par l'étudiant après 5 essais corrigés : `scp -r "/home/fifzy/Bureau/Cours/Schossig/HTML - CSS/01. - Structure HTML5/Exercice" dev:/var/www/html/cours_html/`. Copie confirmée par `git status` sur la VM (dossier `Exercice/` détecté comme non suivi).
- Utilisation : commande construite par l'étudiant à partir des indications, sans copier de commande toute faite. Retenu : `scp` se lance depuis la machine qui possède la source, et le préfixe `machine:` désigne le chemin distant.

## Prompt 9

- Heure : 14:04
- Phase : exercice n° 2 (page HTML)
- Prompt envoyé (verbatim) :

> [envoi du fichier ma-page.html, première version]

- Résumé de la réponse : l'IA relève les guillemets manquants sur `charset`, le tiret du titre différent de la consigne, deux phrases sans point, un `<br>` inutile, le `&` à remplacer par une entité HTML, des fautes d'orthographe et une indentation incohérente.
- Utilisation : corrections appliquées (guillemets, points, orthographe, `<br>` retiré, `&` remplacé par `&` après une recherche sur les entités HTML, indentation retravaillée), sauf le tiret du titre, que l'étudiant a choisi de ne pas modifier ce jour-là.

## Prompt 10

- Heure : 16:04
- Phase : exercice n° 3 (vérification)
- Prompt envoyé (verbatim) :

> [envoi du fichier service-info.html]

- Résumé de la réponse : l'IA valide l'indentation et le viewport, puis signale le commentaire manquant (point 7), le titre d'onglet différent de la consigne (majuscule et tiret) et un pluriel. Après ajout du commentaire, elle conseille de le placer sur sa propre ligne.
- Utilisation : commentaire ajouté avec la syntaxe `<!-- -->` trouvée par l'étudiant. La version envoyée sur GitHub ce jour-là le plaçait toutefois avant `<body>` au lieu de l'intérieur, et le titre d'onglet et le pluriel n'étaient pas encore corrigés.

## Bilan de la séance

- Nombre de prompts : 10 prompts détaillés dans ce rapport, sur environ 99 messages envoyés pendant la séance (dont envois de code et captures d'écran)
- Ce que l'IA a bien fait / mal fait :
    - Bien fait : la plupart du temps, l'IA a guidé par des questions et des indices au lieu de donner les réponses, et a proposé des moyens de vérifier ses explications dans le navigateur (console, Inspector, `document.compatMode`). Les corrections étaient expliquées, avec la conséquence de chaque erreur.
    - Mal fait : elle a proposé un modèle hors sujet pour l'exercice 3 avant d'avoir lu l'énoncé, et une de ses réponses s'est coupée en pleine question. Quand l'étudiant l'a demandé, elle a aussi donné directement certaines réponses (balise viewport, idées clés de l'exercice 2, commandes de vérification), ce qui a réduit la part de recherche personnelle sur ces points.
- Erreurs ou approximations détectées :
    - Exercice 3 : interprétation erronée de « service informatique » (service réseau au lieu de l'équipe informatique d'un lycée) et modèle DHCP hors sujet, donné avant la lecture de l'énoncé.
    - Exercice 1 : une réponse de l'IA s'est arrêtée au milieu d'une question, qu'il a fallu reposer.
- Ce que j'ai compris sans l'IA (ou à partir d'un simple indice) :
    - repérage de la faute `UFT-8` dans le document B, avant toute aide ;
    - repérage du `<p>` à la place de `</p>`, de l'attribut `lang="fr"` manquant, de la balise `<title>` absente et de l'ordre de fermeture inversé de `</html>` et `</body>` ;
    - le lien entre l'attribut `lang` et l'accessibilité ;
    - la nécessité de guillemets autour d'un chemin contenant des espaces, et l'option `-r` pour copier un dossier ;
    - la syntaxe d'un commentaire HTML et la valeur `width=device-width`, trouvées en cherchant sur le web ;
    - la correction de `git add` seul en `git add Exercice/`, à partir du message d'erreur de Git.
