# 📐 2023-USMB-MMAA-CMI-COMPUTER-VISION-DROITE_HOUGH

🎓 Projet en **Vision par Ordinateur**, réalisé dans le cadre du Master MMAA et du CMI en Mathématiques Appliquées – Université Savoie Mont Blanc.

Objectif : **implémenter la détection de droites** dans une image via deux représentations de la **Transformée de Hough** : l’espace cartésien (m, p) et l’espace polaire (r, θ).

---

## 🎯 Objectifs pédagogiques et techniques

- Approfondir la compréhension des bases de la vision par ordinateur.
- Implémenter manuellement des algorithmes de détection de formes.
- Travailler sur la discrétisation de l’espace des paramètres, les matrices d’accumulation et l’analyse de scores.
- Appliquer des méthodes de conversion entre différents espaces de représentation.

---

## 🧪 Partie 1 : Transformée de Hough en espace paramétrique (mp)

### 🔧 Méthodes principales

#### `tracerMP(m, p, hauteur, largeur, maxColor, FILENAME)`
Trace une droite `y = mx + p` dans une image générée au format PPM.  
Les pixels proches de la droite sont coloriés en rouge, les autres restent blancs.  
Inclut un **effet d’anti-aliasing** pour un rendu plus réaliste.

##### Paramètres 
- `m` et `p` : des constantes décrivant l'équation d'une droite `y = mx + p`.
- `hauteur` et `largeur` : des entiers définissant les dimensions de l'image à générer.
- `maxColor` : un entier définissant la valeur maximale de chaque canal de couleur RGB pour les pixels de l'image (ex. 255 pour une image en couleurs 24 bits).
- `FILENAME` : une chaîne de caractères contenant le nom du fichier de sortie.

#### `transformeeHoughMP(image)`
Lit une image PPM et **détecte les pixels appartenant à une droite** `y = mx + p` en incrémentant un **buffer d’accumulation** selon les valeurs discrétisées de `(m, p)`.

##### Détails du code 
- Lit l'image depuis un fichier.
- Crée des vecteurs `disc_M` et `disc_P` pour discrétiser l'espace Hough.
- Incrémente les cellules du buffer pour les pixels correspondant à la droite.
- Retourne le vecteur des valeurs `(mp)` correspondantes.

### ⚙️ Méthode spécifique

#### `incrementeMP(buffer, x, y)`
Pour chaque pixel, discrétise les droites `y = mx + p` pouvant le contenir, et **incrémente le buffer** en fonction de la distance du pixel à la droite.

##### Détail du code :
Elle parcourt chaque élément du buffer et incrémente les cellules proches de la droite en fonction de leur distance au pixel.

---

## 🌀 Partie 2 : Transformée de Hough en espace paramétrique (r, θ)

### 🔧 Méthodes principales

#### `tracerRTheta(r, theta)`
Génère une image représentant une droite définie par ses coordonnées polaires `(r, θ)`.  
Les pixels proches de la droite sont marqués en rouge dans une image PPM.

##### Détails 
Le parcours des pixels est effectué pour calculer la distance du pixel à la droite, et les pixels proches sont colorés en rouge.

#### `transformeeHoughRTheta(image)`
Détecte les droites dans une image PPM à l’aide de la transformée de Hough polaire.  
Crée et remplit un **buffeur `(r, θ)`**, en fonction des pixels blancs de l’image.

##### Détails du code 
Elle lit une image PPM, discrétise les espaces `r` et `thêta`, et incrémente un buffer d'accumulation pour les pixels correspondants à une droite.

### ⚙️ Méthodes spécifiques

#### `incrementeRTheta(buffer, x, y)`
Pour chaque pixel blanc de l’image, calcule toutes les droites possibles passant par ce point en coordonnées `(r, θ)` et incrémente le buffer.

#### `vers_MP(r, θ)`  
Convertit les coordonnées polaires `(r, thêta)` en coordonnées cartésiennes `(m, p)`.

#### `vers_polaire(m, p)`  
Convertit les coordonnées cartésiennes `(m, p)` en coordonnées polaires `(r, thêta)`.

---

## 🎯 Partie 3 : Meilleure approximation en cas de scores multiples

### `trouve_barycentre(tableau_2D)`
En cas d’ambiguïté (plusieurs cellules avec un score maximal dans le buffer), cette méthode **calcule le barycentre des coordonnées** concernées pour proposer la meilleure estimation de droite.

---

## 💡 Compétences démontrées

- Traitement d’image bas-niveau (format PPM, manipulations pixel par pixel)
- Implémentation complète d’un algorithme de détection basé sur la transformée de Hough
- Gestion de buffers d’accumulation et discrétisation d’espaces paramétriques
- Conversion entre différents systèmes de coordonnées
- Utilisation de techniques de prétraitement (anti-aliasing)

---

## 📁 Technologies & Outils

- Langage : **C**
- Format d’image : **PPM**
- Représentation mathématique : droite en (m, p) et (r, θ)

---

## 🎓 Contexte académique

Projet universitaire réalisé dans le cadre du **Master Modélisation Mathématique et Analyse Appliquée** (MMAA) et du **CMI en Mathématiques Appliquées** – Université Savoie Mont Blanc.

---

## 🤝 Intéressé par la vision par ordinateur ou les modèles mathématiques en IA ?
N’hésitez pas à me contacter ou à ouvrir une *issue* !
