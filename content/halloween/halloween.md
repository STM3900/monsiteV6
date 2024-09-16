## Présentation du projet

Ce petit projet portant le nom original d'_Halloween_, est un projet d'électronique se basant sur une carte Arduino, et des trucs en plus. Son principe et de jouer une séquence de lumière et de son qui s'active quand il fait sombre.

Alors comment que ça marche tout ça ? Eh bien nous allons le voir !

## La structure physique du projet (hardware)

Pour que ce projet ai pu prendre forme, bah faut bien brancher des trucs ensemble pour que ça marche !

![photo du circuit du projet, avec en arrière plan la carte Arduino](../markdown-img/halloween/IMG20211026215720.jpg)

^ photo du circuit du projet, avec en arrière plan la carte Arduino

Voici les composants du projet :

- Une carte Arduino
- Un buzzer
- Une photorésistance (permet de mesurer la luminosité)
- 2 Led RGB
- 7 résistances
- Des câbles

Vous ne comprenez pas tous les composants listés ci-dessus ? Ne vous en faites pas je vais tout expliquer !

## Explications des composants

### La carte Arduino

Bon on va commencer par ce qui fait fonctionner tout le projet : La carte Arduino ! C'est littéralement le cerveau de tout cet ensemble, mais comment ça marche et c'est quoi en vrai ?

Une carte Arduino, c'est en fait ce que l'on appelle un _Microcontrôleur_ ! Un microcontrôleur, c'est une carte électronique, qui fait littéralement ce qu'on lui demande : on peut "injecter" du code, et dès qu'elle sera alimenté en électricité, elle l’exécutera, tout simplement.

La puissance de cette carte viens de sa simplicité, et de son système plus ou moins modulaire : en fait vous pouvez voir que sur la carte, il y a des sorte de petits trous qui sont destinés à être utilisé pour y brancher des composants électroniques !

![Photo rapprochée de la carte Arduino : on y aperçoit les pins de branchement](../markdown-img/halloween/IMG20211026215736.jpg)

^ Photo rapprochée de la carte Arduino : on y aperçoit les pins de branchement

Ces petits trous (que l'on appelle "pin" dans le game) son numérotés et peuvent avoir différentes fonctions.

Donc voila, le principe d'un microcontrôleur c'est tout simplement une carte sur laquelle on peut y brancher des composants et qui permet ensuite de les faire interagir à notre guise !

Parlons maintenant rapidement des deux familles de composants existant !

### Les composants d'entrée

Les composants d'entrée, permettent à l'Arduino d'avoir des informations qui lui seront utile plus tard. Le composant envoi sa donnée, vers la carte. Par exemple, pour ce projet j'ai utilisé une photorésistance, qui est un composant d'entrée qui donne à la carte une valeur qui varie en fonction de la luminosité de la pièce !

### Les composants de sortie

Ces composants, sont un peu l'opposé des composants d'entrée : il effectue une action, quand la carte leurs dit quoi faire. C'est donc la carte qui envoi une information au composant, et qui l'excecute. Par exemple, pour ce projet, j'ai utilisé des LEDs, ainsi qu'un buzzer (un composant qui fait du bruit) et je peux les activer depuis ma carte !

maintenant que les différents types de composants ont été présentés, je vais pouvoir expliquer la logique de base du circuit !

## Explication de la logique du projet

En réalité, la logique du projet est toute simple : La photorésistance envoie toute les demie-secondes une valeur indiquant la luminosité présente. Si elle est inférieure à une valeur indiquant que le système est dans un endroit sombre, l'Arduino active une séquence de lumière et de son.

Et voila c'est tout-

Mais comment faire en sorte que cette description devienne réalité et que notre superbe circuit fasse ça ? Et bien c'est simple : on tape sur un clavier jusqu'à que l'Arduino fasse ce qu'on a envie de faire !

Donc comme vous l'avez compris, il va falloir écrire du code pour faire fonctionner ce beau monde !

## Présentation de la structure d'un projet Arduino

Comme cette explication est dédiés aux personnes savant coder ou non, je vais expliquer tout ça simplement, et sans trop de détails pour éviter de perdre trop de gens !

Déjà, le code que l'ont écrit pour cette carte Arduino, est en langage C. C'est un langage qui à le double de mon âge et qui fera très bien le taff.

Voici la structure d'un programme Arduino :

```c
#include <Arduino.h>

void setup() {
  // code d'initialisation, ne s'exécute qu'une fois

}

void loop() {
  // code principal, s'exécute en boucle, indéfiniment

}
```

jusqu'à la, rien de fou, mais c'est la base de tout programme Arduino : on écrit notre code soit dans la fonction `setup()`, soit dans la fonction `loop()`. Dans un projet standard, on met plutôt dans le `setup()`, tout le code qui permet d'initialiser notre projet (donc celui qui permet de dire par exemple qu'il y a une LED branchée sur le pin 11), et dans le `loop()`, notre code principal.

Mais bon des exemples valent mieux que des mots alors voyons voir comment j'initialise mon projet

## Initialisation du projet

```c
#include <Arduino.h>

**/* Déclaration des pins */
const byte redPinLeft = 9;
const byte greenPinLeft = 10;
const byte bluePinLeft = 11;

const byte redPinRight = 3;
const byte greenPinRight = 5;
const byte bluePinRight = 6;

// sert à stocker la valeur de la couleur des LEDS
byte oldRedPinRight;
byte oldGreenPinRight;
byte oldBluePinRight;

const int buzPin = 2;     // Buzzer
const int sensorPin = A0; // Capteur de luminosité

// Variable
int sensorVal; // C'est ici que sera stocké la valeur de la luminosité**

void setup()
{
  **pinMode(redPinLeft, OUTPUT);
  pinMode(greenPinLeft, OUTPUT);
  pinMode(bluePinLeft, OUTPUT);

  pinMode(redPinRight, OUTPUT);
  pinMode(greenPinRight, OUTPUT);
  pinMode(bluePinRight, OUTPUT);

  displayColor(0, 0, 0);**
}

void loop() {
  // code principal, s'exécute en boucle, indéfiniment

}
```

Wow wow wow ! ça en fait du code d'un coup ! Pas de panique. Rien de difficile. Je vous avez parlé du fait que l'ont pouvait écrire notre code dans la fonction setup, mais aussi dans la fonction loop, et bien il est aussi possible d'en écrire en dehors de ces deux fonctions ! Ce code écrit en dehors, est un code global, qui sera accessible aussi bien dans setup, que dans loop !

Mais pas besoin de retenir tout ça, le plus important, c'est ce qu'on y fait dans cet espace. Donc le code situé avant la fonction setup, est la pour déclarer des variables globales, si nous seront très utiles par la suite !

<aside>
💡 Une variable, est tout simplement quelque chose qui porte un nom, qui stocke un truc (une valeur). Par exemple, je peux avoir une variable qui s'appelle `nom`, et dont la valeur est "Théo" . Ainsi, si je veux dire "Bonjour Théo", je peux écrire "Bonjour" + nom , car la valeur de notre variable et bel est bien "Théo"

</aside>

L'intérêt des variables que l'ont initialise au début de notre code, est de le rendre plus lisible. Par exemple, je déclare une variable qui s'appelle **`redPinLeft`** et qui a comme valeur **`9`.** 9 correspond au pin qui est utilisé par cette LED (on a deux LED RGB, mais une LED RGB est composé de 3 LEDS de différentes couleurs, c'est pour ça qu'on déclare 6 variables de LED)

On peut voir que dans notre Setup, nous initialisons nos LED, en les associant à un port, et en disant que c'est un composant de sortie (au lieux de devoir marquer `pinMode(9, OUTPUT)`, on peut marquer `pinMode(redPinLeft, OUTPUT)`, qui est bien plus parlant !

Et voila, juste comme ça nous avons initialisé nos variables et maintenant il ne reste plus qu'à passer aux choses sérieuses !

## La fonction loop()

```c
void loop()
{
  analogRead(sensorPin) < 125
      ? ledAnimation()
      : displayColor(0, 0, 0);

  delay(500);
}
```

Bah c'est tout ? Eh oui, voici le code qu'il y a dans la fonction `loop()`, donc qui est exécuté en boucle. Alors qu'est ce qu'il se passe ? C'est tout simple : Si le capteur de luminosité (`sensorPin()` indique une valeur en dessous de 125 (donc un endroit très sombre) il va exécuter la fonction `ledAnimation()`. Sinon, il éteints les LEDS.

Ensuite le programme attend une demie seconde (la fonction `delay()` met en pause le programme pendant 500 millisecondes), et on répète !

Mais du coup, que fait cette fameuse fonction `ledAnimation()` ? Et bien, c'est en réalisé la dedans que toute la magie se passe, donc allons voir comment ça marche !

## La fonction ledAnimation()

```c
void ledAnimation()
{
  delay(10000);
  transitionRedLight(100, 4000);
  delay(5000);
  blinkRedLight(200, 50);
  transitionRedLight(100, 1000);
  delay(4500);
  blinkRedLight(200, 40);
  blinkRedLight(200, 100);
  delay(3000);
  blinkRedLight(200, 30);
  blinkRedLight(200, 100);
  blinkRedLight(200, 50);
  blinkRedLight(200, 20);
  transitionRedLight(100, 1000);
  delay(4000);
  blackout(2000);
  delay(5000);
  blinkRedLight(200, 30);
  blinkRedLight(200, 100);
  blinkRedLight(200, 50);
  blinkRedLight(200, 40);
  blinkRedLight(200, 20);
  blinkRedLight(200, 10);
  blackout(300);
  delay(50);
  blackout(100);
  delay(100);
  blackout(200);
  whiteWoke(1000);
  delay(1000);
  transitionRedLight(100, 4000);
}
```

Oula, c'est quoi ce truc ? Et bien en fait, cette bouillie de code, est la fonction qui va s'occuper d'animer nos LEDS et d'emmètre du son. Bien que là, elle semble grosse et compliqué à lire, on peut voir qu'en réalité, elle n'exécute qu'une série de fonctions, avec du délais entre temps.

_Encore des fonctions dans des fonctions ? Je comprends rien, c'est du code ou des poupées russes ?_

En fait, la logique de ce programme, fonctionne par pleins de petites fonctions simples, qui permettent, ensemble, de faire quelque chose de complexe ! Laissez moi vous expliquer :

## Explication de la logique du code

Laissons le code de côté quelques instants. Comme expliqué plus haut, le principe du projet est de faire en sorte de jouer une séquence de lumière et de son. Une séquence, c'est juste des LEDS qui s'allument, et s'éteignent selon un principe simple. Et très souvent, dans une longue séquence, il y a des morceaux de notre animation de LED qui se répètes.

Pour éviter de se compliquer la tache à écrire toute la séquence d'un coup, en répétant plusieurs fois les mêmes animations, on peut juste faire en sorte de créer les "briques" de notre séquence, en la décomposant.

Par exemple, j'aimerais que ma séquence :

- Allume les LEDS en rouge pendant 4 secondes
- Les fasse clignoter
- Attendre
- Mette la couleur des LEDS sur blanc
- Attendre
- Les fasse clignoter encore
- etc

On peut donc, avant d'écrire notre séquence compliquée, déterminer ce que concrètement nos LEDS vont faire, et les séparer en fonctions, qui seront très facilement réutilisables !

Pour notre projet, nous avons besoin que nos LEDS puissent :

- S'allumer en rouge, de manière progressive
- Clignoter tout en jouant un son
- S'éteindre pendant une durée choisie
- S'allumer en blanc, en émettant une successions de sons

Et voila, il suffit ensuite de créer une fonction par fonctionnalité, et il sera ensuite simple de faire notre séquence !

Revenons donc sur notre séquence, et analysons la avec notre œil nouveau :

```c
void ledAnimation()
{
  delay(10000);

	// Notre séquence se divise en plusieurs petites animations

  transitionRedLight(100, 4000); // Allume les LEDS, sur un rouge léger, en 4 secondes
  delay(5000);

  blinkRedLight(200, 50); // Fait clignoter les LEDS sur un rouge moyen, rapidement,
													// tout en jouant un son
  transitionRedLight(100, 1000);
  delay(4500);

  blinkRedLight(200, 40);
  blinkRedLight(200, 100);
  delay(3000);

  blinkRedLight(200, 30);
  blinkRedLight(200, 100);
  blinkRedLight(200, 50);
  blinkRedLight(200, 20);
  transitionRedLight(100, 1000);
  delay(4000);

  blackout(2000); // Éteint les LEDS pendant 2 secondes, tout en jouant un son
  delay(5000);

  blinkRedLight(200, 30);
  blinkRedLight(200, 100);
  blinkRedLight(200, 50);
  blinkRedLight(200, 40);
  blinkRedLight(200, 20);
  blinkRedLight(200, 10);
  blackout(300);
  delay(50);

  blackout(100);
  delay(100);

  blackout(200);
  whiteWoke(1000); // Allume les LEDS en blanc, et joue une séquence de sons
									 // pendant 1 seconde
  delay(1000);

  transitionRedLight(100, 4000);
}
```

Et voila ! Ce gros pâté de code n'étais qu'en fait la séquence de son et lumière qui se joue quand il fait sombre. Grace à ce système de fonctions faisant juste une animation, il est très facile de modifier la séquence et de faire un peu ce que je veux avec !

## Conclusion

Et voila qui conclu cette explication de ce petit projet ! Bon j'ai peut être _un peu_ trop expliqué, mais pas grave. Mais en résumé ce projet m'a permis d'avancer un peu dans mon apprentissage d'électronique, ce qui me permettra de faire des projets plus ambicieux l'année prochaine !

## Liens

GitHub du projet :

[GitHub - STM3900/Halloween](https://github.com/STM3900/Halloween)

Vidéo de présentation :

[https://www.youtube.com/watch?v=vOoJI8yQE7I](https://www.youtube.com/watch?v=vOoJI8yQE7I)
