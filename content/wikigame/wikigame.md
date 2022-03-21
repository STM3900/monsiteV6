## Description du projet

Wikigame est un petit jeu en python se basant sur le jeu de wikipédia ! L'objectif du jeu est d'aller d'une page A à une page B (donnés aléatoirement) en moins de coups possibles, et en ne passant que par des liens wikipédia.

## Description technique

Le site fonctionne suivant cet ordre :

- Tout d'abord le site choisit deux bornes : une de début et une de fin, (par exemple Gnocchi en début et Grenoble en fin) en se basant sur une page sélectionnée aléatoirement
- Le site génère ensuite la variable du compteur, et "scanne" la page wikipédia de l'article et extrait tous ses liens valides (pas de doublons, pas d'hyperliens, que ceux dans une certaine zone)
- Avec les liens extrait, le site génère sa page, en affichant le nom de l'article, le nombre de coups, une courte description, puis enfin, tous les liens
- Quand l'utilisateur clique sur un lien, le site compare si sa destination correspond à la borne de fin, si c'est le cas, la partie est gagné et un message de victoire apparaît, ainsi que le nombre de cours que l'utilisateur a fait
- Mais si la destination ne correspond pas, le site ajoute 1 au compteur et l'amène sur la page, en procédant de la méthode que celle de l'étape 2 et 3
- L'utilisateur peut aussi revenir en arrière d'une, ou plusieurs pages, mais celui-lui coûtera 2 coups.

## Difficultés et axes d'amélioration

La principale difficulté de ce projet était le système d'extraction de liens sur une page wikipédia, qui m'a posé pas mal de difficultés.

Le temps aussi a joué contre moi, je n'ai pas pu implémenter toutes les idées que j'avais en tête comme par exemple un meilleur historique de page et une navigation plus fluide entre les pages.

## Conclusion

En conclusion ce projet était très agréable à faire, et m'a permis d'apprendre beaucoup d'éléments en python !
