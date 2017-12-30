# PID

## 1. Explications des contrôleurs:
* Document explicatif __(fr)__
    * http://www.helimag.com/articles-review/18611-asservissement-et-gyroscopes.html
* Introduction aux PID __(en)__
    * https://www.youtube.com/watch?v=UR0hOmjaHp0&list=PL0Lo7ui69SfLka2ire6v9Swzuu4IJMwIe


## 2. Exemples:
* Avec le contrôle de la trajectoire d'une voiture __(en)__
    * https://www.youtube.com/watch?v=4Y7zG48uHRo
* Contrôle d'une voiture en fonction des différents algos _(P; PD; PID)_ __(en)__
    * https://www.youtube.com/watch?v=XfAt6hNV8XM&feature=iv&src_vid=UR0hOmjaHp0&annotation_id=annotation_891845
* Exemple d'implémentation sans trop de calculs __(fr)__
    * http://www.ferdinandpiette.com/blog/2011/08/implementer-un-pid-sans-faire-de-calculs/


## 3. Pseudocode _([source](http://www.ferdinandpiette.com/blog/2011/08/implementer-un-pid-sans-faire-de-calculs/))_:
>`Kp`, `Ki` et `Kd` sont des __constantes__ dans le code dont il faut déterminer les valeurs optimales.
>__Une grosse partie du travail consistera à déterminer les bonnes valeurs.__
>Afin de régler de façon optimale les PID, une méthode semble intéressante;
>Il faut trouver le point d'_oscillation parfait_ `Ku` sur chaque axe contrôlé, puis en fonction de sa valeur se référer à un tableau indiquant les PID à utiliser.
>[Cette page](https://en.wikipedia.org/wiki/Ziegler%E2%80%93Nichols_method) wikipédia propose une explication.

```
Tous les x millisecondes, faire :
    (E) erreur = consigne - mesure;
    (I) somme_erreurs += erreur;
    (D) variation_erreur = erreur - erreur_précédente;
    (O) commande = Kp * erreur + Ki * somme_erreurs + Kd * variation_erreur;
    erreur_précédente = erreur
```

* (E) L'`erreur` est la différence entre la consigne et la valeur mesurée
* (I) `somme_erreurs` est la somme des erreurs au cours du temps. Permet de corriger si il y a une erreur continue dans le temps
* (D) `variation_erreur` permet de savoir si l'erreur est en train de réduire ou de croître
* (O) C'est la commande à appliquer au système 

## 4. Explication des PID __(section en cours de rédaction)__

>"Un régulateur PID ou correcteur PID (pour « proportionnel intégral dérivé ») est un organe de contrôle permettant d’effectuer une régulation en boucle fermée d’une grandeur physique d'un système industriel ou « procédé » (voir Automatique). C’est le régulateur le plus utilisé dans l’industrie, et il permet de régler un grand nombre de grandeurs physiques."
>_[**source:** Wikipedia](https://fr.wikipedia.org/wiki/R%C3%A9gulateur_PID)_

Cet algorithme prend en entrée la différence entre la consigne et la mesure, traite ses données et donne une correction en sortie.
Le traitement se déroule en 3 actions:
* _(Proportionnelle)_ On multiplie l'erreur mesurée par un facteur `Kp`
* _(Intégrale)_ On intègre l'erreur puis on la divise par le facteur `Ki`
* _(Dérivée)_ L'erreur est dérivée et multipliée par le facteur `Kd`

## 5. Annexes
* Chaîne youtube de vulgarisation des principes de robotique et physique
    * https://www.youtube.com/user/ControlLectures/playlists
* Papier sur la stabilisation d'une caméra
    * http://www.irisa.fr/lagadic/pdf/2001_cviu_cretual.pdf
* Vidéo de réglage de PID sur un multirotor
    * https://www.youtube.com/watch?t=108&v=OeQI49Ubd1Q
