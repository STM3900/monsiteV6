## Description du projet

Pour ce projet d'école, le sujet était tout simplement, en utilisant Phaser.io un framework JavaScript, de faire un jeu. Nous avons carte blanche sur le type de jeu et ce que l'on allait créer

N'ayant pas trop d'idées au départ, je me suis souvenu des jeux d'arcades auquel j'aimais bien jouer quand j'étais plus jeune, et je me suis souvenu d'Asteroids, un jeu où l'on contrôle un petit vaisseau de pixel et ou l'objectif et d'exploser le plus d'astéroïdes possibles tout en faisant attention à ne pas se les prendre.

J'ai décidé de partir sur cette idée et de refaire le jeu depuis zéro en y ajoutant plus de fonctionnalités !

## Description technique

Le jeu propose plusieurs fonctionnalités :

- Tout d'abord, quand le joueur lance la partie, il possède 3 vies, si il les perd, la partie est terminée
- Le joueur peut se déplacer uniquement en avant, mais peut orienter la direction de son vaisseau. Les astéroïdes se déplacent uniquement en ligne droite, avec un angle défini aléatoirement qui reste fixe
- Le joueur peut tirer son vaisseau et ainsi détruire des astéroïdes. Lui permettant de gagner des points, mais divisant aussi les astéroïdes en petits morceaux
- Une fois par vie, le joueur peut utiliser son SuperTir, qui détruit tout ennemi en ligne droite pendant un court instant
- Pour gagner plus de points, le joueur peut augmenter son combo s'il ne rate pas sa cible à plusieurs reprises. Au bout de 10 astéroïdes touchés d'affilé, le joueur obtient le SuperCombo, qui augmente considérablement sa cadence de tir

![Asteroids](../markdown-img/asteroids/asteroids.gif)

Le jeu possède aussi un système de classement, qui n'est pas accessible dans la version publique. Celui-ci enregistre les 5 meilleurs scores.

## Difficultés et axes d'amélioration

Comme difficultés pour ce projet, il y avait tout d'abord le fait de devoir apprendre depuis zéro un nouveau framework, pas si bien documenté que ça. Et ensuite faire l'api du système de classement.

Comme axe d'amélioration, j'aurais aimé ajouter encore plus de fonctionnalité, comme par exemple un système ou le jeu s'adapterait en fonction d'une musique.

## Conclusion

Asteroids a été le plus gros projet que j'ai fait en cette année 2021, et sûrement l'un de ceux où j'ai pris le plus de plaisir à le faire !
