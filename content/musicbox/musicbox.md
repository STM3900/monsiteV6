## Présentation du projet

Ce petit projet et une première tentative de réaliser un bidule électronique qui ne soit plus à l’état de prototype ! Il se base encore sur une carte Arduino, mais possède également une carte pour lire une carte microSD contenant des fichiers mp3, ainsi qu’un haut-parleur et des boutons

Comme son nom l’indique, cette petite boite a pour simple but de jouer de la musique (plus précisément la bande originale du jeu Inscryption) que l’on peut mettre sur pause, et en ayant la possibilité de faire défiler les différentes musiques tout en ayant un contrôle sur le son.

## La structure physique du projet (hardware)

Le projet est composé de quelques composants :

- Une carte Arduino
- Un DFPlayer Mini, permettant d’insérer une carte microSD et d’y lire des fichiers mp3
- Trois boutons
- Un potentiomètre pour régler le volume
- Un haut-parleur

## Branchement du circuit

Pour ce premier essai de circuit que je n’allais pas démonter par le futur, j’ai fait le choix de relier le circuit sur des “breadboards” de prototypage et de les mettre dans une boite en carton.

![Photo du circuit de la boite à musique. On y voit l’Arduino connecté au lecteur de carte SD, lui-même connecté ](../markdown-img/musicbox/boiteopen.png)

^ Photo du circuit de la boite à musique. On y voit l’Arduino connecté au lecteur de carte SD, lui-même connecté

Bien que ce ne soit pas vraiment très professionnel comme rendu, et ne sachant pas comment faire de la soudure, je me suis contenté de ce rendu. Cela constitue une petite base qui sera améliorée pour les prochains projets de ce genre !

## Fonctionnement du projet

Bon, rien de bien dur que ce soit sur le code, ou le fonctionnement ! Au lancement de la carte, le lecteur audio joue la première musique chargée dans la carte microSD. Il est ensuite possible avec les boutons de mettre en pause, ou de passer à la musique précédente ou suivante. Enfin, le potentiomètre permet de régler le volume de celles-ci

## Demo

_Cliquez sur l'image pour voir la démo :_

[![Image preview youtube](../markdown-img/musicbox/boitepres.png)](https://www.youtube.com/watch?v=2fT92TD4VNI)

## Difficultés et axes d’amélioration

Pour ce projet, j’ai eu un bon petit paquet de difficultés. En voici quelques-unes :

### Contrainte de temps

La plus grosse difficulté de ce projet était que j’étais soumis à une deadline d’une semaine. En effet, ce projet accompagne un cadeau que j’ai fait à une amie et j’ai eu l’idée de celui-ci, pile avant la date de rendu. La conception, l’achat, et la réalisation de ce projet à du se faire en une seule petite semaine, ce qui me poussa à faire des concessions (abandonner le fait de souder).

### Faible niveau en électronique

Mon niveau en électronique n’étant que celui d’un débutant, je n’avais aucune idée de comment réaliser un circuit qui pouvait jouer de la musique… Heureusement, beaucoup d’informations et de très bons tutos sont disponible sur le net et cela m’as grandement aidé à réaliser ce projet !

### Faible niveau en conception de boitier

Comme vous pouvez le voir sur les différentes images, je n’ai pas d’expérience pour réaliser de jolis boîtiers en électronique, donc j’en ai conçu un en découpant une boite en carton avec un cutter et en collant les breadboard et autres composant avec du scotch double face

![Untitled](../markdown-img/musicbox/boitecontrol.png)

Comme le montre cette image, il y a des câbles exposés qui risquent d’être débranchés accidentellement lors de l’utilisation de la boite.

Si la conception de petits projets en électronique de ce genre continue de me plaire autant, je m’achèterais sûrement une imprimante 3D afin de rendre mes projets plus beaux et plus résistants !

## Conclusion

Malgré les difficultés, j’ai adoré réaliser ce projet, et c’est très satisfaisant de pouvoir créer quelque chose que l’on peut tenir dans ses mains (à l’instar d’un site web), et qui en plus, diffuse de la musique d’un jeu que l’on aime beaucoup !

Je pense faire d’autres projets dans ce genre, mais cette fois-ci en prenant un peu plus de temps.
