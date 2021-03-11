# TD 1

## Nombre d'apparition d'un motif

### Motif hardcoded

```
fonction principale
problème: calculer le nombre d'apparition d'un motif dans une séquence de lettres
terminée par un point
types
    chaine: chaine de caractères // vecteur de caractères
constantes
    chaine motif // motif de taille *longueur*

algorithme
variables
    caractère lettre // la lettre courante
    entier avancée // avancée dans le motif
    entier nbApparition // nombre d'apparition du motif dans la séquence
début
    avancée <- 0 
    lettre <- lire()
    nbApparition <- 0

    tant que (lettre != '.') faire
        si (lettre = motif[avancée])
            si (avancée = longueur - 1)
                nbApparition +<- 1
                si lettre = motif[0]
                    avancée <- 1
                sinon 
                    avancée <- 0   
                fin si
            sinon 
                avancée +<- 1
            fin si
        sinon
            si (lettre = motif[0]) alors
                avancée <- 1
            sinon 
                avancée <- 0   
        fin si
    fin tant que

    afficher nbApparition
fin
```

### Motif quelconque

```
fonction principale
problème: calculer le nombre d'apparition d'un motif dans une séquence de lettres
terminée par un point
types
    chaine: chaine de caractères // vecteur de caractères

algorithme
variables
    caractère lettre // la lettre courante
    entier avancée // avancée dans le motif
    entier nbApparition // nombre d'apparition du motif dans la séquence
    entier longueur
    chaine motif // motif de taille *longueur*
début
    longueur <- lire()
    motif <- lire()
    avancée <- 0 
    lettre <- lire()
    nbApparition <- 0

    tant que (lettre != '.') faire
        si (lettre = motif[avancée])
            si (avancée = longueur - 1)
                nbApparition +<- 1
                si lettre = motif[0] alors
                    avancée <- 1
                sinon 
                    avancée <- 0   
                fin si
            sinon 
                avancée +<- 1
            fin si
        sinon
            si (lettre = motif[0]) alors
                avancée <- 1
            sinon 
                avancée <- 0   
        fin si
    fin tant que

    afficher nbApparition
fin
```

## Jeu des allumettes

```
fonction principale 
constantes
    entier nbAllumettes_init // le nombre d'alumettes au début de la partie

algorithme
variables
    entier choix // le nombre d'allumettes retirées
    entier nbAllumettes // le nombre d'allumettes restant
    bool joueur // au tour du joueur
    entier reste // le nombre d'alumettes restantes modulo 4
    bool correct // indique si l'entrée est autorisée
début
    correct <- faux
    nbAlumettes <- nbAlumettes_init
    joeur <- vrai // le joueur commence
    afficher(nbAllumettes)
    tant que (nbAllumettes > 0) faire
        si (joueur) 
            tant que (!correct) faire
                afficher("Combien d'allumettes voulez vous retirer?")
                choix <- lire()
                si (estEntier(choix) et choix >= 1 et choix <= 3)
                    correct <- vrai
                    nbAllumettes -<- choix
                fin si
            fin tant que
        sinon // tour de l'ordinateur
            reste <- nbAllumettes mod 4
            si (reste = 0) faire // il n y pas de bon choix dans ce cas
                choix = 1 
            sinon 
                choix <- reste - 1
        fin si
        afficher(nbAllumettes)
        joueur <- !joueur
        correct <- faux
    fin tant que
    si (joueur) alors
        afficher("L'ordinateur a gagné")
    sinon
        afficher("Le joueur a gagné)
    fin si
fin
```
