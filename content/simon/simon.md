## **Résumé du projet**

Petit projet en Arduino cherchant à reproduire le jeu de société "Simon"

## **Description du projet**

Le Simon est au départ un jeu de société crée par Ralph Bear en 1978. Son principe est que le jeu affiche une couleur (rouge, bleu, jaune ou vert) et produit un son toujours associé à cette couleur. Le joueur doit alors appuyer sur la touche de la couleur qui vient de s'allumer dans un délai assez court.

Mon objectif pour ce premier projet d'électronique (enfin d'Arduino) était simplement reproduire ce jeu, avec des leds, des boutons et un buzzer.

## Description avancée

N'y connaissant pas grand chose en électronique, c'est un ami, qui fait ses études dans ce domaine, qui m'a conseillé de réaliser ce projet comme initiation à l'électronique. J'ai donc commencé par me procurer des composants pour mettre en œuvre mon petit projet. J'ai donc eu besoin d'utiliser :

- Des Leds pour les 4 couleurs du Simon (rouge, bleu, jaune et vert)
- Un Buzzer
- Des résistances
- Des cables
- Et bien sur, d'un microcontrôleur, comme un Arduino par exemple

Une fois les composants mis en place, il m'a fallu développer l'algorithme permettant tout simplement de jouer au jeu !

Le fonctionne de cette manière : Chaque partie est séparé par des niveaux et des sous niveaux.

Un sous niveau est une suite d'affichage de LED (et de sons), dans un ordre défini par une variable aléatoire, que le joueur doit reproduire en appuyant sur les boutons.

Quand un joueur passe au sous niveau suivant, la même suite se répète, mais elle est augmenté de 1.

Si tous les sous niveaux d'un niveau sont complété, on monte en niveau. Cela veut dire que les prochains niveaux joueront une note maximale supplémentaire, mais aussi plus rapidement

Cette logique se répète jusqu'à que le joueur se trompe, réinitialisant le jeu.

_Cliquez sur l'image pour voir la démo :_
[![Image preview youtube](../markdown-img/simon/arduino.jpg)](https://www.youtube.com/watch?v=_EgEeAPs9yA)

## **Difficultés et axes d'amélioration**

Comme tout projet, j'ai eu quelques difficultés. Tout d'abord je n'avais pas vraiment d'expérience en électronique et Arduino, ce qui m'a causé de prendre un peu de temps à tout comprendre. Une autre difficulté et d'avoir réalisé le projet en C, qui est le langage de base utilisé pour les Arduino. N'ayant pas l'habitude de coder en C, j'ai eu un peu de mal à implémenté certaines fonctionnalités, comme par exemple : un tableau dynamique.

Comme axe d'amélioration ce serais d'améliorer la structure du code, pour qu'elle soit plus lisible et plus propre.

## Conclusion

En conclusion ce projet a été pour moi une opportunité de découvrir tout l'univers de l'électronique, et cela m'a beaucoup plu. J'espère prochainement refaire des projets dans ce domaine, mais cette fois-ci plus complexe !
