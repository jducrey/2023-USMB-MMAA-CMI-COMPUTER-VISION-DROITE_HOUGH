# PROJET_802
Projet de vision par ordinateur (reconnaissance d'une droite, à l'aide de la transformée de Hough)

🎓 Projet réalisé dans le cadre du Master MMAA et du CMI en Mathématiques Appliquées – Université Savoie Mont Blanc

# Partie 1 : Pour la transformée de Hough en espace paramétrique (mp)

## 2 Méthodes membres :

### Tracer MP :
La méthode `tracerMP` trace une droite `y = mx + p` dans une image et enregistre cette image dans un fichier.

#### Paramètres :
- `m` et `p` : des constantes décrivant l'équation d'une droite `y = mx + p`.
- `hauteur` et `largeur` : des entiers définissant les dimensions de l'image à générer.
- `maxColor` : un entier définissant la valeur maximale de chaque canal de couleur RGB pour les pixels de l'image (ex. 255 pour une image en couleurs 24 bits).
- `FILENAME` : une chaîne de caractères contenant le nom du fichier de sortie.

#### Détails :
La méthode crée un fichier PPM avec l'image générée. Elle parcourt chaque pixel de l'image pour calculer la distance du pixel à la droite, et en fonction de cette distance, le pixel est colorié en rouge (proche de la droite), ou en blanc (loin de la droite). Un effet d'anti-aliasing est également appliqué.

### Transformée Hough MP :
Cette méthode lit une image au format PPM et détecte les pixels appartenant à une droite `y = mx + p`. Un buffer d'accumulation est utilisé pour enregistrer le score d'occurrence de chaque droite dans l'espace `(mp)`.

#### Détails du code :
- Lit l'image depuis un fichier.
- Crée des vecteurs `disc_M` et `disc_P` pour discrétiser l'espace Hough.
- Incrémente les cellules du buffer pour les pixels correspondant à la droite.
- Retourne le vecteur des valeurs `(mp)` correspondantes.

## 1 Méthode spécifique :

### IncrementeMP :
La méthode `incrementeMP` prend en entrée un buffer, les coordonnées d'un pixel `(xy)` et discrétise la droite pour incrémenter le buffer en fonction de la distance du pixel à la droite.

#### Détail du code :
Elle parcourt chaque élément du buffer et incrémente les cellules proches de la droite en fonction de leur distance au pixel.

---

# Partie 2 : Pour la transformée de Hough en espace paramétrique (r-thêta)

## 2 Méthodes membres :

### Tracer RTheta :
La méthode crée une image représentant une droite en coordonnées polaires `(r, thêta)`.

#### Détails :
Le parcours des pixels est effectué pour calculer la distance du pixel à la droite, et les pixels proches sont colorés en rouge.

### Transformée Hough RTheta :
Cette méthode implémente la transformation de Hough dans l'espace `(r-thêta)` pour détecter les droites dans une image.

#### Détails du code :
Elle lit une image PPM, discrétise les espaces `r` et `thêta`, et incrémente un buffer d'accumulation pour les pixels correspondants à une droite.

## 3 Méthodes spécifiques :

### IncrementeRTheta :
Incrémente le buffer pour chaque pixel blanc en utilisant les valeurs `r` et `thêta`.

### Vers_MP :
Convertit les coordonnées polaires `(r, thêta)` en coordonnées cartésiennes `(m, p)`.

### Vers_polaire :
Convertit les coordonnées cartésiennes `(m, p)` en coordonnées polaires `(r, thêta)`.

---

# Partie 3 : Trouver la meilleure approximation s'il y a plusieurs cases avec un score maximal

### Trouve_barycentre :
Calcule le barycentre des coordonnées des points ayant un score maximal dans un tableau 2D.
