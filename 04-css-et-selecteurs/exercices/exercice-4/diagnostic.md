# Exercice 4 : Diagnostiquer une règle inefficace

Les causes ont été corrigées une par une, en rechargeant la page après chaque correction.

| N° | Symptôme | Cause | Correction | Vérification dans l'inspecteur |
|---|---|---|---|---|
| 1 | Aucun style ne s'applique, la page reste avec les styles par défaut. | Le `<link>` pointe vers `styles.css` (avec un « s », à la racine) alors que la feuille est `css/style.css`. | `href="css/style.css"` | Onglet Réseau : erreur 404 sur `styles.css` avant la correction ; ensuite `style.css` est chargé (200) et ses règles apparaissent dans l'onglet Règles. |
| 2 | Le titre ne s'agrandit pas. | Le sélecteur `.titre-page` cible une classe, mais le `h1` porte `id="titre-page"`. | `#titre-page` | En sélectionnant le `h1`, la règle n'apparaissait pas dans l'onglet Règles ; après correction, `font-size: 2.5rem` est affiché et appliqué. |
| 3 | L'alerte n'est ni rouge ni en gras. | Point-virgule manquant après `red` : le navigateur lit `color: red font-weight: bold`, valeur invalide, et ignore les deux déclarations. | `color: red;` | Déclaration barrée avec un triangle d'avertissement (valeur invalide) ; après correction, les deux déclarations sont actives. |
| 4 | L'information n'est pas verte. | `colour` (orthographe anglaise) n'est pas une propriété CSS, elle est ignorée. | `color: green;` | Déclaration barrée avec l'indication « propriété inconnue » ; après correction, elle est active. |
| 5 | DHCP (service actif) reste gris. | Conflit de spécificité : `.liste-services li` (0, 1, 1) bat `.actif` (0, 1, 0), même si `.actif` est écrite avant. | `.liste-services .actif` (0, 2, 0) | Sur le `li` DHCP, `color: green` de `.actif` était barrée (écrasée par la règle grise) ; après correction, c'est le gris qui est barré. |
| 6 | Le lien Aide ne s'agrandit pas. | `1.2 rem` : l'espace entre le nombre et l'unité rend la valeur invalide. | `font-size: 1.2rem;` | Déclaration barrée avec un triangle d'avertissement ; après correction, onglet Calculé : 19.2 px (1,2 × 16 px). |

## À retenir

- Une seule erreur de syntaxe (point-virgule, unité, nom de propriété) suffit à faire ignorer une déclaration, sans message dans la page : il faut regarder l'inspecteur.
- Si aucune règle ne s'applique, vérifier d'abord le chemin du `<link>` dans l'onglet Réseau.
- `.` cible une classe et `#` un identifiant : le sélecteur doit correspondre à l'attribut utilisé dans le HTML.
- Une règle correcte peut aussi perdre face à une règle plus spécifique.
