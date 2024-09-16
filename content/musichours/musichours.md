## Description du projet

MusicHours est un site vous permettant, à partir d'une ville de votre choix, d'avoir une musique et un thème s'adaptant à l'heure et à la météo de celle-ci !

Ce projet est né fin 2019, pendant les vacances de la toussaint, suite à une idée que j'avais, mais que je ne pouvais pas réaliser avant d'avoir appris le langage JavaScript.

Cette idée, venait tout droit des jeux vidéo de la série d'Animal Crossing, ou la musique diffusée en jeu, change toutes les heures, s'adaptant aux différentes ambiances qu'il peut y avoir dans une journée. Etant fan de cet attribut, assez unique en son genre, j'ai eu l'idée de faire un site qui pourrait jouer une musique, en fonction de l'heure à laquelle nous sommes, et lui donner une allure assez agréable à regarder pour pouvoir le faire tourner en fond.

C'est donc dans cette idée que je me suis lancé sur le développement du site, en me mettant en tête que ce ne serait qu'un petit projet qui ne prendrait pas beaucoup de temps.

Au final, MusicHours fut le plus gros projet que j'ai pu faire en informatique, avec plus de 70 heures de dev, et surtout qui m'a permis d'apprendre énormément d'éléments en js.

## Description technique

Au départ le site ne devait jouer de la musique qu'en fonction de l'heure. Je suis donc parti sur un système très simple qui consistait juste à mettre 24 musiques mp3 dans un dossier, ou elles étaient nommées d'un nombre entre 0 et 23, et d'en fonction de l'heure de notre pc, chargé celle qui correspondait.

Et voilà, j'avais donc fini mon site en quelques heures ! Mais bon je ne voulais pas vraiment en rester là. J'ai donc voulu ajouter des fonctionnalités.

J'ai donc ajouté un cycle d'aurore / jour / crépuscule / nuit au site, puis ensuite un soleil et une lune qui bougeait en fonction de l'heure.

Étant assez satisfait du site, je me suis dit que je pouvais en rester la, mais j'ai eu une idée qui a allongé le temps de développement de 60 heures : celle de faire en sorte que le site réagisse en fonction de la météo d'une ville rentrée.

Ayant une expérience d'environ 2 semaines en javascript, je n'avais absolument aucune idée de comment réaliser cette action, et en demandant à des amis et en suivant des tutos, j'ai donc compris que je devrais utiliser une api, qui me permettrait de récupérer les données météorologiques d'une ville donnée. Et cette api vient directement du site [https://openweathermap.org/](https://openweathermap.org/), qui propose une api gratuite, et avec le recul, pas très dure à utiliser.

Avec donc cette api, et des heures de galères, j'avais réussi à faire en sorte que le site réagisse quand il pleuvait dans une ville fixe.

Mais je me suis dit qu'il était dommage d'arrêter là, et j'ai donc fait en sorte que l'utilisateur puisse choisir sa ville, puis ensuite que le site réagisse à plus de météos différentes (orage, brouillard, neige), ainsi que des variantes de musiques en fonction de la météo (la bande son du jeu Animal Crossing : New Leaf possède des musiques prévues quand il pleut, ou neige).

Mais voulant toujours ajouter des fonctionnalités au site, j'ai vu qu'il était possible de récupérer le fuseau horaire de la ville, en plus de sa météo. J'ai donc fait en sorte que l'heure affichée sur le site s'adapte automatiquement à celle de la ville, en plus d'avoir rajouté des variantes de style par rapport aux saisons.

Et c'est comme ça que ce site qui n'était qu'au départ, un petit projet à vu le jour !

![Untitled](../markdown-img/musichours/comparatif.png)

## Difficultés et axes d'amélioration

Ce projet a été l'un des plus durs que j'ai pu faire dans ma vie d'étudiant en seconde année, car il me confrontait en permanence sur des problèmes sur lesquels je n'avais strictement aucune idée de comment faire pour les résoudre.

Mais les plus grosses difficultés de ce projet était la connexion à l'api, la récupération et le traitement des données reçues.

Bien que je sois assez satisfait du site, il y a une multitude d'éléments qui peuvent être améliorés, comme par exemple :

- Utiliser un meilleur système pour traiter les musiques, autre que de toutes les stocker dans un dossier et les sélectionner dynamiquement
- Écrire le code d'une manière plus propre, dans différents dossiers et avec plus de fonctions
- Améliorer le site de façon générale

En fait, j'aimerais beaucoup faire une nouvelle version de ce site, à partir de zéro, qui serait plus belle, plus détaillée, avec plus de fonctionnalités (comme par exemple de prendre en compte le vent des villes pour faire bouger les arbres, etc.), mais je n'en ai pas encore les compétences !

## Conclusion

En conclusion MusicHours à été sans doute le projet le plus agréable et formateur de cette seconde année d'école. Il 'm'a permis d'apprendre vraiment beaucoup de fonctionnalités en js et il était vraiment satisfaisant d'arriver à faire des choses que l'ont pensait impossible 10 heures plus tôt, en prenant juste le temps de chercher et de ne pas hésiter à demander de l'aide à des personnes plus fortes que soit pour avoir des avis et des indices de comment faire !
