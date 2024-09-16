## **Résumé du projet**

Écrire des notes, gérez vos todos, et bien plus, tout ça dans une interface conviviale et personnalisable ! Qubi est un site mettant à disposition un tableau de bord personnalisable sur lequel il est possible de disposer différents widgets, ayant tous une fonction à eux !

## **Description du projet**

Qubi est un site (et aussi un projet personnel) qui a pour but initial de me mettre au défi et de me sortir de ma zone de confort. Et nous allons voir que je suis bien, bien sorti de celle-ci...

Le principe de base de Qubi repose sur ses widgets : C'est un site modulaire ou chaque widget contient toute une fonctionnalité en lui, plus ou moins complexe. Cette structure de projet a été très pratique pour apprendre, car chaque widget était un peu un projet dans un projet !

![Untitled](../markdown-img/qubi/qubigif.gif)

## Description avancée

Qubi est de loin le projet le plus complexe que j'ai réalisé en Vue/Nuxt.js en 2021. Je vais essayer d'essayer rapidement son fonctionnement.

Tout le site gravite autour du système de grille, qui permet de placer les widget, de les déplacer et de modifier leur taille. À côté de ce système, réside un objet qui est en gros le pilote du site : il contient toutes les informations des widgets affichés, comme le type, la taille, la position, etc.

Pour savoir quel widget afficher quand l'utilisateur souhaite en ajouter, un composant entre en jeu et permet de déterminer quel widget affiché, et de charger sa configuration.

Chaque widget est un composant, donc cela veut dire qu'il a son propre petit écosystème, dans lequel est conçu son fonctionnement. Cela est très pratique, car ça permet de s'abstraire du reste du code du projet et de se focaliser uniquement sur les fonctionnalités de notre widget.

Et enfin, toutes les données liées aux widgets, et au pilote du projet son stockées dans un endroit appelé le store : c'est une zone du projet qui permet de déclarer des variables, et des méthodes (et plus) de manière globale, et centralisée. Par exemple un composant A peut afficher une donnée du store, et si le composant B vient à changer cette donnée, elle sera automatiquement mise à jour dans le composant A.

## **Difficultés et axes d'amélioration**

Comme dit plus haut, Qubi est le projet qui m'a le plus donné de fil à retordre (et fait perdre des nuits de sommeil). Le fait d'utiliser le système du Store pour la première fois m'a entraîné à faire des choix trop précipité dans mon projet que j'ai par la suite regretté. J'ai eu des difficultés plus ou moins pendant tout le développement, car je faisais des trucs que je n'avais pas du tout l'habitude de faire, et je sais que j'ai résolu certains problèmes d'une manière pas optimale. La conséquence de ça est que l'architecture du projet est assez bancale, et un peu complexe à comprendre, et je suis certain qu'il est possible de la simplifier et de l'optimiser. Mais ce sera pour un autre projet !

Mais ces difficultés m'ont permis de faire un grand pas en avant sur mon apprentissage de Nuxt.js et j'en suis reconnaissant.

## Conclusion

Malgré les nombreuses difficultés de ce projet, entrainant une grosse pause du développement pendant le mois de septembre, j'ai beaucoup apprécié ce projet. J'ai vraiment eu la sensation d'apprendre des éléments qui me seront utiles dans mes prochains projets et j'ai hâte de les mettre en place !
