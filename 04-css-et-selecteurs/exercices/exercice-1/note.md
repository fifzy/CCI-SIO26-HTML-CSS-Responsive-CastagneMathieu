# Exercice 1 : Associer HTML et CSS

**Anatomie d'une règle** : dans `h1 { color: #1f3a5f; }`, `h1` est le **sélecteur**, `color` est la **propriété**, `#1f3a5f` est la **valeur** ; `color: #1f3a5f;` est une **déclaration**.

- **Externe** (`<link>` dans le `<head>`) : un seul fichier modifie toutes les pages du site.
- **Interne** (`<style>` dans le `<head>`) : pratique pour une seule page, mais à modifier dans chaque page.
- **En ligne** (attribut `style`) : prioritaire sur tout le reste, mais à réécrire sur chaque élément (20 titres = 20 fois).
- **Constat** : en ligne (rouge) > interne placé après le `<link>` (vert) > externe (bleu foncé) ; j'utiliserai la feuille externe pour mon portfolio.