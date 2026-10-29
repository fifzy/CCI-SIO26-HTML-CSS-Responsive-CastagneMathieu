# Notes exercice 1

- Tests : page ouverte dans le navigateur et clic sur chaque lien ; liens externes (MDN en nouvel onglet, W3C dans le même onglet), ancres du sommaire, retour en haut et lien mail fonctionnent.
- Plaquette : erreur 404, car le test a été fait sur une copie de la page sur Fedora, sans le dossier `docs/`. Test à refaire depuis la VM (Apache).
- Problèmes rencontrés : création des dossiers (`mkdir -p`), Git n'affiche pas les dossiers vides, chemin relatif mal écrit (nom de dossier en double), guillemet fermant oublié dans un `href`.
- Retenu : un lien vers une ancre a besoin d'un `href="#nom"` et d'un `id="nom"` identiques sur l'élément d'arrivée.