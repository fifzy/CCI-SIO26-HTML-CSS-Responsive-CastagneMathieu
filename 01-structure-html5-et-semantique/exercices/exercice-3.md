## Extrait A

- **Ce qui ne va pas** : la hiérarchie saute un niveau. On passe directement du `h1` au `h3`, sans `h2`.
- **Pourquoi c'est un problème** : les titres structurent le document comme un sommaire. Un lecteur d'écran annonce « titre de niveau 1 » puis « titre de niveau 3 » : l'utilisateur croit qu'une partie manque. Les moteurs de recherche interprètent aussi mal la structure.
- **Correction justifiée** : j'ai remplacé les deux `h3` par des `h2`. Le modèle OSI et le modèle TCP/IP sont deux modèles distincts et de même importance, donc deux parties de même niveau directement sous le titre principal.

## Extrait B

- **Ce qui ne va pas** : la page contient trois `h1`. Tous les titres sont au même niveau, alors que « Installation » et « Configuration » sont des parties du guide.
- **Pourquoi c'est un problème** : le `h1` représente le sujet principal de la page, il ne doit y en avoir qu'un. Avec trois `h1`, les lecteurs d'écran et les moteurs de recherche ne savent plus quel est le vrai sujet, et la structure ne reflète pas le contenu.
- **Correction justifiée** : « Guide du technicien » reste le seul `h1`, car c'est le titre général. « Installation » et « Configuration » passent en `h2`, car ce sont deux parties de même niveau du guide.

## Extrait C

- **Ce qui ne va pas** : deux erreurs. La hiérarchie saute un niveau entre le `h2` « Sauvegardes » et les `h4`. Et « Conclusion » est en `h1`, placé à la fin, alors que ce n'est pas le sujet principal.
- **Pourquoi c'est un problème** : la structure ne correspond plus au contenu. Un lecteur d'écran annonce un niveau manquant, puis présente la conclusion comme le titre principal de la page, ce qui rend la navigation incompréhensible.
- **Correction justifiée** : « Sauvegardes » devient le seul `h1`, car c'est le sujet de la page. Les deux types de sauvegarde passent en `h2`, car ce sont deux parties de même niveau. « Conclusion » passe en `h2`, car elle conclut tout le document et se place au même niveau que les autres parties.

## Extrait D

- **Ce qui ne va pas** : le titre `h2` est placé à l'intérieur d'un paragraphe `p`.
- **Pourquoi c'est un problème** : un paragraphe ne peut contenir que du texte et des éléments en ligne, pas un titre. Le navigateur corrige lui-même l'erreur en fermant le paragraphe avant le titre, ce qui crée deux paragraphes vides dans le document (visibles dans l'inspecteur). Le code n'est pas valide et la structure réelle ne correspond pas à ce qui est écrit.
- **Correction justifiée** : j'ai retiré les balises `p` autour du `h2`. Un titre est un élément de structure à part entière, il n'a pas besoin d'être dans un paragraphe.

## Extrait E

- **Ce qui ne va pas** : l'avertissement est balisé comme un titre `h2`, alors que ce n'est pas le titre d'une partie du document.
- **Pourquoi c'est un problème** : la balise a été choisie pour son apparence (gros et en gras), pas pour son sens. Le lecteur d'écran l'annonce comme une partie, et elle apparaît dans le sommaire de la page comme un chapitre, ce qui fausse la structure.
- **Correction justifiée** : j'ai remplacé le `h2` par un paragraphe `p` contenant un `strong`. Le `p` indique que c'est une phrase du texte, et le `strong` signale qu'elle est importante, ce qui est le vrai sens d'un avertissement.

## Situations

| Situation | Balise(s) | Justification |
|---|---|---|
| S1. Étapes pour configurer une IP statique | `ol` + `li` | Les étapes doivent être réalisées dans un ordre précis, la numérotation a un sens. |
| S2. Ports courants d'un serveur web | `ul` + `li` | Les ports sont énumérés sans ordre particulier. (Remarque : seuls 80/HTTP et 443/HTTPS sont des ports web ; 22 sert à SSH et 25 à SMTP.) |
| S3. Avertissement « Ne jamais exécuter cette commande en production » | `p` + `strong` | C'est un avertissement : son contenu a une importance forte, ce qu'exprime `strong`. |
| S4. Insister sur « avant » dans « Sauvegardez avant de modifier » | `em` (autour du seul mot « avant ») | On met l'accent sur un mot pour en changer l'intonation, ce qui est le rôle de `em`. |