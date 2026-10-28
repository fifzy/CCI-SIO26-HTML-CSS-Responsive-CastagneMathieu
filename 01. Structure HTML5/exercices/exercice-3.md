# Exercice 3 : Produire un document à partir d'un cahier des charges

1. **Document HTML5 en français et encodage :** j'ai utilisé `<!DOCTYPE html>`, `<html lang="fr">` et `<meta charset="UTF-8">`, car le DOCTYPE fait passer le navigateur en mode standard, `lang="fr"` indique la langue aux lecteurs d'écran et aux moteurs de recherche, et l'encodage UTF-8 permet d'afficher correctement les accents.
2. **Titre d'onglet :** j'ai utilisé la balise `<title>` dans le `<head>`, avec l'entité `&mdash;` pour écrire le tiret long, car le titre identifie la page dans l'onglet, les favoris et les résultats des moteurs de recherche, et l'entité permet d'écrire un caractère absent du clavier.
3. **Titre visible :** j'ai utilisé la balise `<h1>` dans le `<body>`, car contrairement au `<title>` qui s'affiche dans l'onglet, le `<h1>` s'affiche dans la page et constitue le titre principal de son contenu.
4. **Mission du service :** j'ai utilisé une balise `<p>` contenant deux phrases, car un paragraphe regroupe un bloc de texte : ici, la gestion du parc informatique et le dépannage des utilisateurs.
5. **Horaires d'ouverture :** j'ai utilisé un second `<p>`, précédé d'un sous-titre `<h2>` (non demandé), car le `<h2>` signale une nouvelle section sous le titre principal et rend la page plus lisible.
6. **Affichage sur téléphone :** j'ai utilisé `<meta name="viewport" content="width=device-width, initial-scale=1">` dans le `<head>`, car sans elle le navigateur mobile simule un écran d'ordinateur large puis dézoome ; `width=device-width` utilise la largeur réelle de l'écran et `initial-scale=1` fixe le zoom à 100 % au chargement.
7. **Commentaire HTML :** j'ai placé `<!-- Auteur : Mathieu Castagné -->` juste après la balise `<body>`, car un commentaire est ignoré par le navigateur : il n'apparaît pas dans la page mais reste lisible dans le code source.
8. **Indentation :** j'ai décalé chaque élément de 2 espaces par rapport à son parent, car l'indentation rend visible l'imbrication des balises et facilite la relecture du code.

## Vérification dans le navigateur

- **Onglet et accents :** en ouvrant la page dans Firefox, l'onglet doit afficher le titre avec le tiret long, et les accents (é, è, à) doivent s'afficher correctement.
- **Console (F12) :** aucun message d'erreur, et `document.compatMode` doit renvoyer `"CSS1Compat"` (mode standard).
- **Affichage téléphone :** avec `Ctrl+Maj+M` (mode d'affichage adaptatif) et un modèle de téléphone, le texte doit être lisible sans zoomer. En retirant temporairement la balise viewport, le texte devient minuscule, ce qui prouve son utilité.
- **Commentaire :** il ne doit pas apparaître dans la page, mais il doit être visible avec `Ctrl+U` (code source) et dans l'Inspector, à l'intérieur du `<body>`.