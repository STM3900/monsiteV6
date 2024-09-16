## Présentation du projet

Me revoici avec un nouveau projet d’IoT ! Celui-ci est parti d’une idée très simple :

Je voulais créer un petit prototype permettant de contrôler une ampoule connectée à distance, en appuyant sur des boutons par exemple. Au final, ce projet est devenu un peu plus massif, car j’ai conçu (enfin plus utilisé) tout un écosystème me permettant de contrôler l’ampoule, mais aussi d’autres appareils.

## Structure physique du projet

La structure de cette télécommande n’a rien de bien compliqué, même si de nouveaux éléments entrent en jeu depuis le dernier projet :

### Alimentation

Lors du dernier projet, j’avais utilisé une carte Arduino. Cette carte fonctionne sous 5V et avait un abaisseur de tension intégré, ce qui lui permettait de recevoir une pile de 9V sans soucis.

Pour ce projet, j’utilise un microcontrôleur s’appelant l’**ESP8266**. Il est beaucoup moins cher qu’une carte Arduino, et possède une antenne wifi intégré, lui permettant de communiquer avec le web et d’autres appareils.

L’ESP8266 fonctionne sous une tension de 3.3V et ne possède pas d’abaisseur de tension. Il a fallu donc que je me renseigne pour en acheter un pour faire la conversion entre une pile de 9V et la carte.

### Soudure

Ayant un peu plus de temps, j’ai décidé que pour ce projet, j’allais souder les différents boutons et composants sur une plaque PCB afin d’avoir un rendu un peu plus présentable. Mais cela ne sera pas sans difficultés.

---

Mais plus concrètement de quoi est composé le projet ?

- Un microcontrôleur ESP8266
- 6 boutons
- Un abaisseur de tension réglable en 3.3V
- Une pile 9V
- Une plaque PCB
- Des résistances
- Des câbles

Et voilà, encore une fois, rien de très complexe sur les branchements

## Branchement du circuit

Après avoir conçu un prototype sur Breadboard fonctionnel, le schéma de branchement ressemble à ça :

![Untitled](../markdown-img/remotelight/schema.jpeg)

Rien de bien dur. Voici à quoi ressemble la télécommande une fois assemblée :

![Untitled](../markdown-img/remotelight/telefront.png)

La télécommande tient d’elle-même en position verticale, et elle à un petit interrupteur à côté de l’ESP pour l’allumer. Voyons maintenant à quoi ressemble l’arrière de la télécommande…

![Untitled](../markdown-img/remotelight/teleback.png)

Beaucoup de câbles ! Il va sans dire que bien que cette installation donne un style un peu “cyberpunk” à la télécommande, cela la rend aussi très vulnérable lors de la manipulation. En effet, il serait très facile de débrancher des câbles accidentellement en manipulant la télécommande (ce qui est arrivé durant des tests oups)

Plus d’informations dans “Axes d’améliorations”…

Maintenant que notre télécommande est prête, comment la faire communiquer avec la lampe ? Et bien, ce n’est pas si simple que ça !

## Comment faire communiquer notre télécommande à l’ampoule ?

Voici la partie qui m’a le plus retourné les méninges ! N’ayant absolument aucune idée de comment faire ça, j’ai fait ce que chaque développeur fait quand il ne sait pas quelque chose : chercher sur le net

Mon idée de base était que mon ampoule pouvait communiquer en Wifi, et que l’ESP8266, pouvait lui aussi communiquer en Wifi. Donc par une magie noire, je pouvais faire parler les deux, peux être en répliquant ce que fait l’application de l’ampoule ou je-ne-sais-quoi…

Me rendant compte que j’avais mal jugé la complexité de mon projet et que j’étais un peu perdu, j’ai demandé quelques conseils sur un réseau social très pratique pour poser des questions sur des sujets précis : **Reddit**

Un utilisateur me recommanda d’utiliser un logiciel open-source très puissant s’appelant “**Home Assistant**”. Celui-ci serait capable de faire la liaison entre mon ESP8266, mais aussi la lampe grâce à son système d’intégration d’app.

Ce logiciel, peut s’installer sur une machine virtuelle, ou directement sur un raspberry. N’étant qu’à l’étape de prototypage, j’ai décidé de le faire sur une machine virtuelle. (et je n’avais pas l’argent d’acheter un raspberry 999999999€ à cause de la crise)

## HomeAssistant

Logiciel Open-Source, facile d’utilisation, possédant une interface moderne, et surtout, extrêmement personnalisable et configurable, HomeAssistant est une pépite dont je ne connaissais pas le nom avant. Ce logiciel est au cœur de ce projet car il servira à faire le lien entre l’ESP, ainsi que l’ampoule connectée.

Pour arriver à établir la connexion entre les différents appareils, il faut configurer plusieurs trucs sur HomeAssistant, les voici :

_pour la suite de l’article, HomeAssitant sera abrégé sous le terme “HA”_

### Intégration de l’ampoule sur _HA_

Pour faire la communication entre l’ampoule et _HA_, j’ai fait la découverte d’une app, ou plutôt d’un service s’appelant “**Tuya**”, celui-ci permet déjà de connecter son téléphone à l’ampoule, afin de l’utiliser normalement. Mais en plus de cela, Tuya propose une plateforme web qui permet d’associer son application, à une API, permettant donc, de piloter l’ampoule en utilisant l’API, au lieu de l’app.

Encore mieux, _HA_ possède une intégration permettant d’ajouter facilement un compte Tuya à son écosystème ! Il suffit juste d’y renseigner les informations de son compte Tuya, ainsi que de son projet IoT, et l’intégration s’occupe d’ajouter les appareils présents sur le compte Tuya directement dans _HA_ !

![Untitled](../markdown-img/remotelight/hatuya.png)

### Installer un broker MQTT sur _HA_

Déjà, la première question que l’on peut se poser c’est : Qu’est-ce que le **MQTT** et qu’est ce qu’un **broker** ?

MQTT est un acronyme signifiant “**Message Queuing Telemetry Transport”**, c’est un protocole de communication open source fonctionnant sur un modèle dit “d’abonnement” et “d’abonnés”

Un Broker est simplement un système qui gère les flux MQTT, un peu comme un serveur.

#### Comment fonctionne le protocole MQTT ?

Comme dit précédemment, le MQTT fonctionne sur base d’abonnement et d’abonnés. Cela signifie qu’il est possible de créer différents “**topics**” (imaginez qu’un topic est une newsletter) et que des appareils peuvent **publier** des informations dessus, et que d’autres peuvent s’abonner ! Les appareils abonnés seront notifiés dès qu’une information sera publiée sur le topic.

Voici un diagramme trouvé sur [ce site](https://arduino.blaisepascal.fr/mqtt-avec-arduino/) expliquant de manière plus visuelle le protocole MQTT

![Untitled](../markdown-img/remotelight/schemamqtt.png)

On y voit à gauche un capteur de température qui publie sur le topic portant le nom `température` une valeur correspondant à `28°C`.

A droite, il y a deux appareils, un ordinateur et un téléphone. Ils sont tous les deux abonnés au même topic que le capteur de température, ce qui signifie qu’ils reçoivent le message du capteur !

Ce protocole est donc très pratique pour faire communiquer des capteurs, avec un, ou plusieurs appareils, tout en gardant une structure claire, car il est possible de créer plusieurs topics afin de mieux organiser notre flux de données.

### Installer NodeRed sur _HA_

**NodeRed** est un outil de développement, basé sur les flux pour la programmation visuelle qui permet de faire communiquer différents appareils et surtout effectuer diverses actions à partir d’information.

NodeRed à la particularité de fonctionner via une interface web, ou il est possible d’y connecter des “Node” (c’est pour ça que ça s’appelle NodeRed) entre elle pour faire diverses actions. Ainsi, il est très facile de réaliser des actions non évidentes simplement, comme par exemple allumer la lumière quand on reçoit un certain message sur un topic MQTT…

Voici une capture d’écran d’une interface NodeRed toute simple, faisant une seule action

![Untitled](../markdown-img/remotelight/noderedexemple.png)

On peut y voir qu’une node d’_input_ est reliée à une node de _debug_, qui affiche simplement le message envoyé dans la console à droite de l’écran.

Il existe tout un attirail de nodes différentes, dont deux qui nous intéresse grandement : La node de type MQTT, et celle d’HomeAssistant. En effet, NodeRed pouvant s’installer directement dans HomeAssistant, le logiciel ajoute automatiquement des nodes permettant de gérer les appareils connectés dessus, ce qui nous simplifie le travail !

Maintenant que tout est installé il est temps d’assembler les différentes parties de notre projet et de les faire fonctionner ensemble !

## Structure de l’écosystème

Voici un diagramme illustrant comment communique et fonctionne les différents appareils de l’écosystème de mon projet :

![GnoccHome.png](../markdown-img/remotelight/GnoccHome.png)

Notre télécommande, va envoyer des informations dans divers topics, qui seront traités par NodeRed pour être converti en information à envoyer à l’ampoule via l’API de Tuya.

On peut remarquer qu’une entité dont je n’ai pas encore parlé, figure sur le diagramme. Une certaine “**ARRBox**”. Cette entité est en fait un petit projet que j’avais réalisé entre temps pour un ami, et qui grossièrement est une boite musicale. Pour tester un peu l’étendue du MQTT, je me suis amusé à la reprogrammer pour activer des sons depuis la télécommande, ou l’interface d’_HA_ en utilisant différents topics MQTT !

## Structure du projet dans NodeRed

Voici à quoi ressemble le NodeRed du projet :

![Untitled](../markdown-img/remotelight/nodered.png)

On peut voir que le “**flow**” est composé de petits groupes de nodes toutes simple. En effet, les nodes de couleurs rosâtres correspondes à des topics MQTT, qui s’occupe de transmettre l’information reçue aux nodes vertes (pour un affichage console) et aux nodes bleues, qui correspondent à l’ampoule connectée !

Maintenant que tout est mis en place, notre projet fonctionne !

## Démonstration

_Cliquez sur l'image pour voir la démo :_

[![Image preview youtube](../markdown-img/remotelight/remotedemo.png)](https://www.youtube.com/watch?v=QTSX4rNyHMg)

## Difficultés

Ce projet, qui a pris une sacré ampleur, n’as pas été sans difficultés. En voici les plus notables :

### Manque de connaissance en IoT

La difficulté la plus évidente était le fait que je n’avais pas vraiment de grandes connaissances en IoT, et tout ce qui est dans la communication d’objets connectés. J’ai donc pas mal pataugé avant de trouver une solution viable.

### Difficultés pendant la soudure

La plus grosse difficulté de ce projet est arrivée lors de l’assemblage des composants sur la carte PCB. En effet, étant encore novice en soudure, j’ai fait pas mal d’erreurs lors de celle-ci, et je sais que je n’ai pas soudé de manière optimale. De plus, j’ai du totalement recommencer l’assemblage de la télécommande, car ma première version était trop mal soudé et ne faisait que court circuiter :(

Cette seconde version de la télécommandé est, certes fonctionnelle, mais a été faite un peu trop rapidement et manque d’éléments importants en soudure (comme de la gaine thermorétractable).

Elle est aussi assez fragile, et si elle est manipulée sans trop de précautions, des câbles peuvent s’emmêler, ou même se rompre.

Et surtout, elle manque un élément qui a été retiré lors de sa seconde création : une LED RGB permettant de savoir le statut de la télécommande (allumée / en cours de connexion au wifi / connexion au MQTT / hors ligne). En effet lors du premier prototype, j’ai tout simplement mal branché la LED et je l’ai fait griller 😐 Et donc je n’en avais plus de rechange pour la seconde version de la télécommande, comme quoi, il est important de bien faire attention aux endroits où l’on soude !

![Untitled](../markdown-img/remotelight/remotedead.png)

## Axes d’amélioration

Ce projet, bien que très formateur sur des technologies que je ne connaissais peu ou pas du tout, est loin d’être parfait et beaucoup de points d’amélioration peuvent être établis, en voici :

### Meilleure réalisation de la télécommande

Si je devais refaire la télécommande, je pense que je prendrais le temps d’étudier la meilleure façon de bien connecter les câbles afin de rendre le circuit plus propre, mais aussi plus sûr en l’isolant des courts-circuits (en y mettant de la gaine thermorétractable), et en le rendant plus robuste en faisant en sorte que les connections ne soient pas fragiles.

Je pense peut-être commencer à me pencher sur l’impression 3D, comment concevoir des boîtiers et autre, car je pense que cela me permettrait d’avoir un rendu beaucoup plus propre !

### Achat de meilleur matériel

L’ampoule connectée que j’avais prise était une ampoule premier prix, trouvé un peu au pif dans un magasin. Celle-ci fonctionne bien, mais elle est un peu capricieuse sur certains points.

### Mise en place d’HomeAssistant sur un Raspberry

Actuellement, _HA_ est installé sur une machine virtuelle de mon ordinateur. Bien que cela soit très pratique pour des tests, l’installer sur une machine à part serait un grand plus, surtout que le système fonctionnerait en permanence !

## Conclusion

Ce projet a été l’un des plus intéressants à faire depuis un petit bout de temps, et il m’a permis de découvrir tout un univers de domotique et m’as donné pleins d’idées pour de futurs projets !
