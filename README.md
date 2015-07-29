# PID

## 1. Explications des contrôleurs:
* Document explicatif __(fr)__
    * http://www.helimag.com/articles-review/18611-asservissement-et-gyroscopes.html
    * Introduction aux PID __(en)__
        * https://www.youtube.com/watch?v=UR0hOmjaHp0&list=PL0Lo7ui69SfLka2ire6v9Swzuu4IJMwIe


## 2. Exemples:
* Avec le contrôle de la trajectoire d'une voiture __(en)__
    * https://www.youtube.com/watch?v=4Y7zG48uHRo
    * Contrôle d'une voiture en fonction des différents algos _(P; PD; PID)_
        * https://www.youtube.com/watch?v=XfAt6hNV8XM&feature=iv&src_vid=UR0hOmjaHp0&annotation_id=annotation_891845
	* Exemple d'implémentation sans trop de calculs __(fr)__
	    * http://www.ferdinandpiette.com/blog/2011/08/implementer-un-pid-sans-faire-de-calculs/

## 3. Pseudocode _(récupéré de [ce site](http://www.ferdinandpiette.com/blog/2011/08/implementer-un-pid-sans-faire-de-calculs/))_:
>`Kp`, `Ki` et `Kd` sont des __constantes__ dans le code dont il faut déterminer les valeurs optimales.
>__Une grosse partie du travail consistera à déterminer les bonnes valeurs.__
>Afin de régler de façon optimale les PID, une méthode semble intéressante;
>Il faut trouver le point d'_oscillation parfait_ `Ku` sur chaque axe contrôlé, puis en fonction de sa valeur se référer à un tableau indiquant les PID à utiliser.
>[Cette page](https://en.wikipedia.org/wiki/Ziegler%E2%80%93Nichols_method) wikipédia propose une explication.

```
Tous les x millisecondes, faire :
    erreur = consigne - mesure;
    somme_erreurs += erreur;
    variation_erreur = erreur - erreur_précédente;
    commande = Kp * erreur + Ki * somme_erreurs + Kd * variation_erreur;
    erreur_précédente = erreur
```