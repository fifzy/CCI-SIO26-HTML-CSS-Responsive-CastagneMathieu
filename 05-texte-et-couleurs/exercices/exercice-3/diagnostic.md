# Exercice 3 : diagnostic de la présentation illisible

## Méthode

- Le HTML n'est pas modifié : seuls le `<head>` et la balise `<link>` sont ajoutés.
- `style-avant.css` : la feuille fournie, recopiée telle quelle.
- `style-apres.css` : la feuille corrigée.
- Comparaison en basculant le `href` de la balise `<link>` entre les deux fichiers, avec un rechargement **Ctrl + Maj + R**.
- Contrastes mesurés dans l'inspecteur de Firefox (clic sur la pastille de couleur à côté de `color`) et vérifiés avec un outil en ligne (WebAIM Contrast Checker).
- Objectif : au moins **4,5:1** pour le texte courant (niveau AA des WCAG).

## Défauts et corrections

### `body`

| Déclaration avant | Défaut | Correction |
|---|---|---|
| `background-color: #333333;` et `color: #444444;` | Texte gris foncé sur fond gris foncé : couleurs presque identiques, contraste de 1,3:1. Le texte se fond dans le fond. | `background-color: #f5f5f5;` et `color: #222222;` : texte foncé sur fond très clair. |
| `font-family: "Papyrus";` | Police fantaisie, décorative, difficile à lire sur un texte long et inadaptée à une procédure technique. Pas de famille générique de repli : si Papyrus n'est pas installée (cas de Fedora), le navigateur choisit une police au hasard. Les guillemets ne sont pas un défaut (facultatifs sans espace dans le nom). | `font-family: 'Segoe UI', sans-serif;` : police lisible avec repli générique. Les guillemets sont obligatoires ici à cause de l'espace. |
| `font-size: 10px;` | Trop petit : le texte courant doit faire au moins 16 px. | `font-size: 1rem;` : 16 px par défaut, et la taille suit le réglage du navigateur de l'utilisateur. |
| `line-height: 1;` | Interligne trop serré : les lettres qui descendent (p, g, j) frôlent celles de la ligne suivante, l'œil a du mal à changer de ligne. | `line-height: 1.5;` : valeur sans unité, proportionnelle à la taille du texte. |

### `h1`

| Déclaration avant | Défaut | Correction |
|---|---|---|
| `color: #ffff00;` et `background-color: #ffffff;` | Jaune pur sur blanc : contraste de 1,07:1, le titre est pratiquement invisible. | `color: #0b3d91;` (bleu foncé) ; `background-color` **supprimé** : le titre laisse voir le fond de la page. |
| `font-size: 12px;` | Le titre principal est **plus petit** que le texte courant : hiérarchie visuelle inversée. | `font-size: 1.5rem;` (24 px). |
| `text-align: right;` | En français, on lit de gauche à droite : un titre aligné à droite paraît « perdu » au bout de la ligne. | `text-align: center;` |

### `h2`

| Déclaration avant | Défaut | Correction |
|---|---|---|
| `color: #555555;` | Gris moyen sur le fond `#333333` : contraste de 1,69:1. | `color: #0b3d91;` : même bleu que le `h1`, titres cohérents entre eux. |
| `font-size: 11px;` | Plus petit que le texte courant : la hiérarchie n'est pas respectée. | `font-size: 1.25rem;` (20 px) : entre le texte (16 px) et le `h1` (24 px). |

### `p`

| Déclaration avant | Défaut | Correction |
|---|---|---|
| `color: #999999;` | Gris clair sur blanc : contraste de 2,85:1, sous le minimum. | `color: #222222;` |
| `background-color: #ffffff;` | Rectangles blancs sur la page sombre : effet « patchwork ». | Supprimé : les paragraphes laissent voir le fond de la page. |
| `font-size: 9px;` | Illisible. | `font-size: 1rem;` |
| `font-weight: 100;` | Graisse beaucoup trop fine pour du texte courant. | `font-weight: 400;` (= `normal`). |
| `text-align: justify;` | Le texte justifié crée des espaces irréguliers entre les mots (« rivières » blanches). | `text-align: left;` |

Remarque : `color` et `font-size` sont déjà définis sur `body` et les paragraphes en **héritent**. Les répéter dans `p` n'est pas une erreur, mais on pourrait les supprimer pour avoir une feuille plus courte et plus facile à maintenir.

### `a`

| Déclaration avant | Défaut | Correction |
|---|---|---|
| `color: #555555;` | Le contraste passe (7,46:1 sur le blanc des paragraphes), mais un gris proche du texte ne permet pas de **repérer** le lien. | `color: #0f53c9;` : un bleu, couleur que les utilisateurs associent aux liens. |

Le **soulignement** par défaut des liens est conservé : le lien reste repérable même pour une personne qui distingue mal les couleurs.

### `.alerte`

| Déclaration avant | Défaut | Correction |
|---|---|---|
| `color: #ff7f00;` et `background-color: #ff0000;` | Orange sur rouge : contraste de 1,58:1. C'est pourtant le message le plus important de la page. | `color: #bd0a0a;` (rouge foncé) ; fond rouge **supprimé**. |
| (aucune) | L'alerte ne repose que sur la couleur : invisible pour une personne qui ne perçoit pas le rouge. | Ajout de `font-weight: bold;` : l'alerte se distingue aussi par la graisse. |

Piège évité : ajouter un canal alpha (`#ff0000bd`) ne fonce pas la couleur. Au contraire, la transparence laisse passer le fond clair et réduit le contraste. Pour foncer une couleur, on baisse sa luminosité.

### `footer p`

| Déclaration avant | Défaut | Correction |
|---|---|---|
| `color: #3a3a3a;` | Aucun : gris très foncé, contraste de 11,37:1 sur le blanc d'origine. | **Conservée.** |

Le pied de page était illisible à cause de la règle `p` (9 px, graisse 100), qui s'applique aussi au `<p>` du footer. En corrigeant `p`, le pied de page est corrigé en même temps.

## Rapports de contraste avant / après

| Élément | Avant (texte / fond) | Contraste avant | Après (texte / fond) | Contraste après | AA |
|---|---|---|---|---|---|
| Texte de `body` | #444444 / #333333 | 1,3:1 | #222222 / #f5f5f5 | 14,6:1 | ✅ |
| `h1` | #ffff00 / #ffffff | 1,07:1 | #0b3d91 / #f5f5f5 | 9,2:1 | ✅ |
| `h2` | #555555 / #333333 | 1,69:1 | #0b3d91 / #f5f5f5 | 9,2:1 | ✅ |
| Paragraphes | #999999 / #ffffff | 2,85:1 | #222222 / #f5f5f5 | 14,6:1 | ✅ |
| Lien | #555555 / #ffffff | 7,46:1 | #0f53c9 / #f5f5f5 | 6,2:1 | ✅ |
| Alerte | #ff7f00 / #ff0000 | 1,58:1 | #bd0a0a / #f5f5f5 | 6,0:1 | ✅ |
| Pied de page | #3a3a3a / #ffffff | 11,37:1 | #3a3a3a / #f5f5f5 | 10,4:1 | ✅ |

Avant correction, **5 éléments sur 7** étaient sous les 4,5:1. Après correction, tous les textes dépassent le niveau AA, et la plupart atteignent le niveau AAA (7:1).

## Hiérarchie des tailles après correction

| Élément | Valeur | Taille calculée |
|---|---|---|
| `h1` | `1.5rem` | 24 px |
| `h2` | `1.25rem` | 20 px |
| Texte courant | `1rem` | 16 px |

h1 > h2 > texte : la hiérarchie visuelle est rétablie.