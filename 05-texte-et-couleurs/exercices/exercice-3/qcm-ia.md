# Exercice 4 : vérifier la compréhension

Quiz mené avec l'IA dans le rôle du tuteur : une question à la fois, réponse de mémoire (sans ouvrir les feuilles CSS ni les notes), puis correction.

## Prompt utilisé

```text
Tu es mon tuteur CSS. Pose-moi une question à la fois sur : color, background-color,
font-family, font-size, font-weight, font-style, text-align, px/em/rem, contraste.
Attends ma réponse avant de corriger. Ne me donne pas la réponse avant que j'aie essayé.
Après 10 questions, fais un bilan de mes points faibles.
```

## Questions

### Question 1
**Question n° 1 :** Quelle est la différence entre `color` et `background-color` ? Donne un exemple d'utilisation pour chacune.

**Réponse (avant correction) :** Color défini la couleur le contenu d'un texte comme p ou body alors que Background color defini le fond de la page.

**Correction de l'IA :** `color` définit bien la couleur du texte, et il s'applique à n'importe quel élément contenant du texte (`h1`, `a`, `.alerte`…). `background-color` ne colore pas forcément la page : il colore le fond **de l'élément ciblé** (toute la page sur `body`, seulement le bloc sur `.note`). Il manquait des exemples de code, par exemple `body { color: #222222; }` et `.note { background-color: hsl(57, 71%, 90%); }`.

**Réponse initiale :** partiellement juste

**À retenir :** `background-color` colore le fond de l'élément ciblé, pas uniquement celui de la page.

### Question 2
**Question n° 2 :** Pourquoi faut-il toujours terminer une déclaration `font-family` par une famille générique comme `sans-serif` ? Que se passe-t-il si on l'oublie ?

**Réponse (avant correction) :** Si aucune famille n'est renseigne le navigateur utilisera la générique.

**Correction de l'IA :** Le raisonnement est inversé. La famille générique est une solution de secours garantie que l'on écrit soi-même en dernier. Si on l'oublie et que la police demandée n'est pas installée, le navigateur utilise **sa police par défaut** (souvent avec empattement, type Times), et le style voulu est perdu.

**Réponse initiale :** partiellement juste

**À retenir :** la générique, c'est moi qui l'écris, en dernier, pour garder le bon type de police. Sans elle, le navigateur choisit à ma place.

### Question 3
**Question n° 3 :** Le bleu `#0b3d91` s'écrit `rgb(11, 61, 145)`. Explique comment on obtient le 61 à partir de l'hexadécimal.

**Réponse (avant correction) :** 48 + 13 = 61

**Correction de l'IA :** Résultat juste, mais il faut expliquer d'où viennent les nombres : la paire du vert est `3d`, 3 × 16 = 48, `d` vaut 13, donc 48 + 13 = 61.

**Réponse initiale :** juste

**À retenir :** (premier chiffre × 16) + second chiffre, avec a = 10, b = 11, c = 12, d = 13, e = 14, f = 15.

### Question 4
**Question n° 4 :** Quelle est la différence entre `font-weight` et `font-style` ? Donne une valeur courante pour chacune.

**Réponse (avant correction) :** font-weight joue sur l'épaisseur comme `bold` et font-style joue sur l'inclinaison `italic`.

**Correction de l'IA :** Juste. `font-weight` accepte aussi des nombres de 100 à 900 (`400` = `normal`, `700` = `bold`). Les deux propriétés sont indépendantes : un texte peut être gras et italique.

**Réponse initiale :** juste

**À retenir :** `font-weight` règle l'épaisseur, `font-style` l'inclinaison, et on peut les cumuler.

### Question 5
**Question n° 5 :** Avec `html { font-size: 16px; }`, trois `div` imbriquées ont chacune `font-size: 2em;`. Quelle est la taille en px de la troisième `div` ?

**Réponse (avant correction) :** 72 (erreur de saisie signalée après coup, réponse visée : 128)

**Correction de l'IA :** Avec `em`, on multiplie la taille du parent à chaque niveau : 2 × 16 = 32, 2 × 32 = 64, 2 × 64 = **128 px**.

**Réponse initiale :** fausse

**À retenir :** en `em` imbriqué, on multiplie à chaque niveau. Avec 2em, la taille double : 32, 64, 128. Relire sa réponse avant de la valider.

### Question 6
**Question n° 6 :** Même situation, mais avec `font-size: 2rem;` sur les trois `div`. Quelle est la taille de la troisième ?

**Réponse (avant correction) :** 32

**Correction de l'IA :** Juste. `2rem` = 2 × 16 = 32 px pour les trois `div`, car `rem` se rapporte toujours à la racine : aucun effet cumulatif.

**Réponse initiale :** juste

**À retenir :** en `rem`, la profondeur ne compte pas.

### Question 7
**Question n° 7 :** Quel rapport de contraste minimum faut-il atteindre pour du texte courant au niveau AA des WCAG ? Et pourquoi le contraste est-il important pour l'accessibilité ?

**Réponse (avant correction) :** Pour du texte courant, le niveau AA des WCAG (critère 1.4.3, Contraste minimum) exige un rapport d'au moins 4,5:1 entre la couleur du texte et celle de son arrière-plan.

**Correction de l'IA :** Le chiffre est juste (4,5:1), mais la deuxième partie manque : un contraste suffisant permet de lire aux personnes malvoyantes, daltoniennes ou âgées, et à tout le monde dans de mauvaises conditions (soleil sur l'écran, écran de mauvaise qualité). Pour les grands textes, le minimum est de 3:1.

**Réponse initiale :** partiellement juste

**À retenir :** 4,5:1 minimum pour le texte courant (3:1 pour les grands textes), pour que tous les utilisateurs puissent lire.

### Question 8
**Question n° 8 :** Dans l'exercice 3, pourquoi `text-align: justify` était-il considéré comme un défaut ?

**Réponse (avant correction) :** Car tout est au meme niveau.

**Correction de l'IA :** Pour aligner le texte sur les deux bords, le navigateur étire les espaces entre les mots. Les espaces deviennent irréguliers et forment des « rivières » blanches qui gênent la lecture, surtout pour les personnes dyslexiques.

**Réponse initiale :** fausse

**À retenir :** `justify` crée des espaces irréguliers entre les mots. Pour le texte courant à l'écran, on préfère `text-align: left`.

### Question 9
**Question n° 9 :** Pour obtenir une version plus claire d'une couleur, quel format de couleur est le plus pratique, et sur quelle valeur faut-il agir ?

**Réponse (avant correction) :** Le format le plus pratique est HSL (Hue, Saturation, Lightness), et il suffit d'augmenter la valeur L (luminosité).

**Correction de l'IA :** Juste. On garde la teinte et la saturation et on augmente seulement la luminosité (comme le jaune pâle de l'exercice 1, de 65 % à 90 %). Pour foncer, on baisse L. Le canal alpha, lui, ne fonce pas : il rend la couleur transparente.

**Réponse initiale :** juste

**À retenir :** en `hsl()`, on augmente L pour éclaircir et on la baisse pour foncer.

### Question 10
**Question n° 10 :** Dans l'exercice 3, tu as ajouté `font-weight: bold` à l'alerte en plus de la couleur rouge. Pourquoi la couleur seule ne suffisait-elle pas ?

**Réponse (avant correction) :** Car cela aurait mélanger l'alerte dans le reste du texte.

**Correction de l'IA :** Le gras fait bien ressortir l'alerte, mais la raison principale est l'accessibilité : une personne daltonienne qui ne perçoit pas le rouge verrait l'alerte comme un texte ordinaire. Une information ne doit jamais passer uniquement par la couleur.

**Réponse initiale :** partiellement juste

**À retenir :** jamais d'information transmise uniquement par la couleur ; toujours un second indice (gras, mot « Attention », icône).

## Résultat

| Juste | Partiellement juste | Fausse |
|---|---|---|
| 4 (Q3, Q4, Q6, Q9) | 4 (Q1, Q2, Q7, Q10) | 2 (Q5, Q8) |

## Bilan : trois points faibles et comment les travailler

1. **Les calculs `em` imbriqués et la conversion hexadécimale** (Q5, et la confusion entre la taille de référence et le résultat pendant l'exercice 2) : refaire des tableaux de prédiction avec d'autres coefficients (2em, 0.8em) et d'autres racines, en posant chaque multiplication, puis vérifier dans l'onglet Calculé.
2. **Justifier une réponse, pas seulement la donner** (Q1, Q3, Q7) : pour chaque propriété, s'entraîner à dire « à quoi elle sert, sur quel élément, avec un exemple de code », et toujours expliquer d'où vient un nombre.
3. **Les règles de lisibilité et d'accessibilité** (Q8, Q10, Q2) : relire la partie 4 de la synthèse et, pour chaque règle, retenir le **public concerné** (malvoyants, daltoniens, dyslexiques) ; s'auto-interroger sur le « pourquoi » de chaque correction de l'exercice 3.