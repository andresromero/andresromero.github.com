---
layout: masonry
title: Instructions TP Traitement d'Images 1
---

# Introduction
Le but de ce TP est de d’implanter en C différentes opérateurs de TI et de les tester sur des images réelles
et de synthèse.

Les codes C fournis sont séparés en modules :

* *nrutil* : extension de la bibliothèque d’allocation mémoire de NRC. Permet en particulier le chargement
et l’écriture d’image au format PGM
* *mutil* : misc util : routines diverses
* *gauss* : formule de Gauss en 1D et 2D
* *filterNRC* : operateurs de filtrage : filtrage gaussien, filtrage moyen, filtrage médian
* *histogramNR* : manipulation d’histogramme, principalement seuillage optimal d’Otsu
* *lutNR* : fonctions de seuillage à base de LooK Up Table
* *contourNR* : opérateurs de détection de contours
* *morphoNR* : opérateurs de morphologie mathématique
* *noise* et *random* : générateurs aléatoires
* *test* : fonction principale de test
* *my_path* : header définissant les chemins d’accès aux différents répertoires
* *test_filterNR* : fonctions de test des opérateurs de filtrage
* *test_contourNR* : fonctions de test des opérateurs de détection de contours
* *test_morphoNR* : fonctions de test des opérateurs morphologiques

Ce sont dans les fichiers filterNRC, lutNRC et morphoNR que vous devez remplir les fonctions vides.
C’est dans le fichier my_path que vous devez spécifier les chemins effectifs sur votre machine. Enfin ce sont
dans les fichiers test_filterNR, test_contourNR et test_morphoNR que vous devez ajouter de nouveaux
tests. Pour cela, copiez le bloc de code et modifier le paramètre (en première ligne de chaque bloc) afin
de réaliser un traitement supplémentaire. Le découpage est le suivant : toute fonction préfixée par test_
contient l’appel à une routine de traitement et lui passe en argument les paths nécessaires ainsi que le
nom de l’image utilisée (sans bruit) et avec bruit. Toute fonction C préfixée par routine_ contient un
traitement avec un jeu de paramètre donné (1 valeur de sigma pour le filtrage guassien, 1 taille de noyau
pour le lissage moyen ou pour le lissage médian, ...).

De même, il y a un certains nombre de répertoires prédéfinis :

* *src* : répertoire contenant les images sources
* *noise* : répertoire contenant les images bruitées
* *denoise* : répertoire contenant les images débruitées
* *contour* : répertoire contenant les images de contours, en niveau de gris (après l’opérateur de détection
de contours), et en binaire (après seuillage)
* *mrohpo* : répertoire contenant les images après traitement morphologique
Dans un premier temps, le but est de coder un certains nombre d’opérateurs et de les appliquer sur
des images sans bruit ou faiblement bruitées. Dans un second temps, le but est de combiner des pré-
traitements et des post-traitements afin d’améliorer les images de contours.

Le compte rendu, doit contenir des explications sur la démarche suivie ansi que votre analyse sur la
façon dont vous avez géré le bruit. Vos explications seront illustrés par des exemples de résultats avec à
partir d’image faiblement bruitées et d’autres fortement bruitées. La prise d’initiative dans la combinaison
d’opérateur sera évaluée.

Votre compte-rendu sera une archive zip (exclusivement) à votre nom. Cette archive devra contenir un répertoire à votre nom, contenant les différences codes C ainsi que le comptre rendu au format pdf. L’archive sera à envoyer par mail à l’adresse *andres.romero@lri.fr*. Le sujet de ce mail sera APP5_TI. Le respect de ces consignes ainsi que la qualité des commentaires (dans le compte-rendu) et dans les codes sources sera prise en compte dans l’évaluation.
Pour visualiser les images au format PGM (binaire) : différents viewers sont disponibles comme Irfanview
ou XnView.

# Remplir fonctions vides dans les fichiers:

* filterNRC
* lutNRC 
* morphoNR

# Travail à faire

Le travail à faire reprend les différentes étapes de la figure 1.

1. ajouter les codes d’opérateurs manquant dans les fichiers *filterNRC*, *lutNRC* et *morphoNR*.
2. ajouter des noms d’images à traiter ou à retraiter (image avec bruit gaussien ou avec bruit impul-
sionnel) dans les fonctions *test_*.
3. ajouter des nouveaux appels à des fonctions de traitement (nouvelle valeur de paramètre) dans les
fonctions *routine_*.

# Bruitage

Les fonctions de bruitage (bruit gaussien, bruit impulsionnel) sont fournies, tout comme la fonction pour
générer des images contenant un carré dont le niveau de gris est séparé de celui du fond d’un certain
écart.

1. Bruiter les images de synthèse avec du bruit gaussien et du bruit impulsionnel. Un exemple est
fourni, en faire d’autres.
2. qu’observe-t-on ?

# Débruitage

1. Coder la fonction effectuant un opérateur de lissage de type moyenneur (average en anglais) en
s’inspirant du lissage gaussien fourni.
2. Coder la fonction effectuant un opérateur de lissage de type médian (basé sur un tri classique).
3. tester les filtres de débruitage sur du bruit additionnel ou du bruit impulsionnel

# Détection de contours
1. Coder la fonction effectuant le calcul de la norme L1 du gradient de Sobel.
2. Coder la fonction effectuant le calcul de la norme L1 du gradient de FGL.
3. Tester les deux opérateurs sur des images sans bruit, puis avec bruit.
4. Seuiller les images (soit avec un seuil manuel, soit avec l’opérateur d’Otsu).

# Morphologie Mathématique
1. Implanter les opérateurs suivants :
	* érosion et dilatation, pour des images binaires et en niveaux de gris,
	* ouverture et fermeture (qui réaliseront des appels aux fonctions précédentes),
	* filtres alternés séquentiels, basés sur un ensembles d’ouverture et sur un ensemble de fermetures

2. tester les différents opérateurs sur des images avec ou sans bruit impulsionnel.

# Compiler le code

{% highlight bash %}
$ unzip tp1_filtrage_APP5.zip
$ cd tp1_filtrage_APP5
$ make
$ ./tp
{% endhighlight %}
