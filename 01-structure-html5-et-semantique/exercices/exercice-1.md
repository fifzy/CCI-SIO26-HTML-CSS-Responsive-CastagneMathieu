	## Document A

### Erreur 1 : `lang="fr"` est manquant

A la ligne 1 l'attribut `lang="fr"`est manquant ce qui pose un problème au niveau de l'accessibilité, un lecteur d'écran peut prononcer le texte avec le mauvais accent; les outils de traductions et les moteurs de recherche ne connaissent donc pas la langue de la page

### Erreur 2 : `<head>` placé à l’intérieur de `<body>` au lieu d’être avant lui

A la ligne 3 à 6 le navigateur crée un `<head>` vide; il ignore donc la `<head>` mal placée et range `meta` et `title` dans le `body`

### Erreur 3 : `<p>` écrit à la place  de `</p>` 

A la ligne 8 le navigateur ferme le paragraphe tout seul et crée un second  `<p>` vide

### Erreur 4 : `<!DOCTYPE html>` placé en fin de fichier au lieu de la ligne 1

A la ligne 10, le `<!DOCTYPE html>` est mal placé il doit être placé en tout début de la page en ligne 1
Dans le navigateur il imite le comportement des vieux navigateurs, donc la mise en forme CSS de la page peut s’afficher différemment de ce qu’on attend en passant en mode quirks (BackCompat)



# Document B



### Erreur 1 :  Balise `<title>` absente du `<head>`

A la ligne 3 et 5 il manque la balise `<title>` qui n'affiche pas de titre dans l'onglet du navigateur, il affiche à la place le chemin du fichier donc la page est mal identifiée

### Erreur 2 : Faute de frappe : `UFT-8` au lieu de `UTF-8`

Ligne 4 : La déclaration est ignorée (message d'erreur dans la console du navigateur), le navigateur doit donc deviner l'encodage

### Erreur 3 : Fermetures inversées : `</html>` avant `</body>`

Ligne 9 et 10 : Aucun effet visible, le navigateur corrige l’ordre tout seul, mais le document est invalide et repose sur la tolérance du navigateur