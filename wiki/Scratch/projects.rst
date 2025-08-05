.. _KidsBlock-Tutorials:

KidsBlock Tutorials
===================
.. _4.-Projects:

Projets
.. _4.1-Project-:-Lighting-System:

4.1 Projet : Système d'éclairage


**Commençons notre premier projet, le système d'éclairage.**

--------------

Allumer une LED est l'une des pratiques Arduino les plus fondamentales.

Cette leçon de démarrage est conçue pour les débutants afin de comprendre la programmation matérielle et logicielle sur la carte de développement ESP32 et de maîtriser les connaissances de base en circuits et en programmation.

.. image:: ./scratch_img/cout1.png
   :alt: img

Par conséquent, notre guide tutoriel est simple. Et ce projet intriguant peut être appliqué dans des scénarios réels à la maison ou au bureau.

Dans ce projet, vous aurez appris les connexions et paramètres de base de la carte de développement ESP32 dans la programmation Arduino. De plus, certaines fonctions vous seront également présentées, comme allumer/éteindre une LED via le niveau de sortie d'une broche numérique ou par un bouton.

En somme, il s'agit d'un tutoriel de niveau débutant pour poser les bases des pratiques Arduino ultérieures.

--------------

.. _4.1.1-Flow-Diagram:

4.1.1 Diagramme de flux
^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230607175228556.png
   :alt: image-20230607175228556

--------------

.. _4.1.2-Light-up-an-LED:

4.1.2 Allumer une LED
^^^^^^^^^^^^^^^^^^^^^

**Description :**

LED, abréviation de Light Emitting Diode (diode électroluminescente), est un semi-conducteur à état solide qui convertit l'énergie électrique en lumière visible, c'est pourquoi on l'appelle aussi éclairage à état solide.

Lorsque le courant traverse une LED, elle s'allume.

**LED diverses :**

.. image:: ./scratch_img/cou1.png
   :alt: img

--------------

Le **module LED** est un dispositif de sortie, dont la luminosité et les clignotements peuvent être contrôlés. Pour l'utilisation, vous devez simplement le brancher directement dans les broches de sortie numérique de la carte de développement.

.. image:: ./scratch_img/cou12.png
   :alt: img

--------------

**Principe de fonctionnement :**

Lorsque S est à un niveau haut, le transistor Q1 est en conduction, et la tension VCC passe à travers la LED pour l'allumer.

.. image:: ./scratch_img/couy1.png
   :alt: img

**Paramètres :**

- Tension : 3~5V
- Courant : ≤1,5mA
- Puissance : 0,07W

--------------

**Schéma de câblage :**

**Connectez le module LED à io27.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj1.png
   :alt: img

--------------

**Code de test :**

- Ouvrez Kidsblock et choisissez le bon appareil et port.

   .. image:: ./scratch_img/st1.png
      :alt: img

- Faites glisser |image19| de |image20| vers la zone d'édition de code. Les blocs de code ne s'exécutent que lorsqu'ils sont dans cette zone.

   .. image:: ./scratch_img/st12.png
      :alt: img

- Avec ce bloc, lors du démarrage de la carte de développement, le code s'exécutera.

   .. image:: ./scratch_img/st11.png
      :alt: img

- Dans |image21|, faites glisser "\ **forever**\ " et collez-le sous le bloc précédent. Le bloc "\ **forever**\ " indique une boucle.

   .. image:: ./scratch_img/st20.png
      :alt: img

- Faites glisser un bloc "**LED pin output**" de |image22| et collez-le dans "\ **forever**\ ". Réglez la broche sur IO27 et le niveau de sortie sur HIGH, de sorte que la broche LED continuera à sortir un niveau haut.

.. image:: ./scratch_img/st21.png
   :alt: img

.. image:: ./scratch_img/st22-1.png
   :alt: img

- Ajoutez un délai de 1s. Dupliquez le bloc "**LED pin output**" mais réglez la sortie sur LOW, et ajoutez également un délai. Alors la LED s'allumera et s'éteindra en circulation.

   .. image:: ./scratch_img/st22.png
      :alt: img

**Résultat du test :**

La LED clignote par seconde, car io27 sur la carte ESP32 sort alternativement un niveau haut et bas chaque seconde. De plus, diverses applications interactives peuvent également être réalisées via une LED, comme une LED respirante, des lumières à écoulement d'eau et un feu de police clignotant.

.. container:: table-wrapper

   ============== ========
   Niveau d'alimentation Résultat
   ============== ========
   HIGH           LED allumée
   LOW            LED éteinte
   ============== ========

--------------

**Extension : LED respirante**

**Description :**

Les interfaces IO du MCU (arduino UNO, ESP32 et Raspberry Pi Pico) ne sortent que des signaux numériques (niveau haut ou bas). Par exemple, dans l'expérience précédente (allumer une LED), les sorties numériques ne sont que HIGH(3,3V) et LOW(0V).

Si le MCU sort un niveau haut de 3,3V ou un niveau bas de 0V, la tension d'entrée devrait être à 0~3,3V. Ainsi, PWM (**Pulse Width Modulation**) est nécessaire pour sortir différentes valeurs de tension, ce qui est appelé "sortie analogique".

.. image:: ./scratch_img/cou1k1.png
   :alt: img

--------------

**Connaissances :**

Qu'est-ce que PWM ?

PWM contient trois éléments : Fréquence(Hz), Période, Cycle de service(%).

- **Fréquence PWM (f) :** le nombre de fois que le signal change de haut à bas et revient à haut en une seconde. Généralement parlant, la fréquence est le nombre de périodes PWM en une seconde.

- **Période PWM (T) :** Période = 1 / Fréquence (T=1/f, et 1 signifie 1 seconde). Par exemple : f = 50Hz, donc T = 20ms, ce qui implique qu'il y a 50 fois de période par seconde.

- **Cycle de service PWM :** le rapport de temps de HIGH à toute la période. Si Période = 10ms et 8ms est le temps de largeur d'impulsion, le niveau bas occupe 2ms, donc le cycle de service = 8/(8+2) = 80%.

.. image:: ./scratch_img/cou1k2.png
   :alt: img

**Conclusion : À une fréquence de signal appropriée, PWM change la tension de sortie effective en changeant le cycle de service en une période.** En termes simples, dans un temps spécifié, plus le port IO sort de niveau haut, plus la valeur PWM est grande, et plus la LED sera lumineuse.

.. image:: ./scratch_img/cou1k3.png
   :alt: img

**Code de test :**

.. image:: ./scratch_img/st23.png
   :alt: img

- Définissez une variable **item** et assignez-lui 0.

   .. image:: ./scratch_img/st25.png
      :alt: img

- Faites glisser un bloc "**forever**" et collez un bloc "**repeat**" dedans. Réglez le nombre de répétitions à 255.

   .. image:: ./scratch_img/st26.png
      :alt: img

- Faites glisser un bloc "**variable mode**" dans "**repeat**" et réglez le mode sur "\ **++**\ ", ce qui signifie que **item** augmentera de 1 après chaque exécution.

   .. image:: ./scratch_img/st27.png
      :alt: img

- Trouvez le bloc pour régler PWM qui est contenu dans |image23| comme montré ci-dessous, vous devez donc seulement régler la broche correspondante et la valeur analogique pour sortir PWM.

   .. image:: ./scratch_img/st28.png
      :alt: img

- Réglez la broche LED :

      .. image:: ./scratch_img/st29.png
         :alt: img

- Réglez le canal : (16 canaux au total : incluant 0~15)

      .. image:: ./scratch_img/st30.png
         :alt: img

- Réglez la valeur de sortie PWM sur **item**, qui ajoutera automatiquement 1 de 0 à 255. **La sortie PWM est 0~255, donc nous réglons le nombre de répétitions à 255.**

      .. image:: ./scratch_img/st31.png
         :alt: img

- Ajoutez un délai à 0,01s, de sorte que la LED s'allumera progressivement plutôt que tout d'un coup.

   .. image:: ./scratch_img/st32.png
      :alt: img

- Dupliquez le bloc "**repeat**" comme suit, mais réglez le mode sur "**－－**", qui diminue la variable **item** à chaque fois. Et la LED s'assombrira progressivement.

   .. image:: ./scratch_img/st33.png
      :alt: img

**Résultat du test**

La LED s'allume et s'assombrit progressivement ; elle respire uniformément.

.. image:: ./scratch_img/st34.gif
   :alt: img

--------------

.. _4.1.4-A-Button:

4.1.4 Un bouton
^^^^^^^^^^^^^^^

**Description**

Le **module bouton** est un dispositif d'entrée. Le MCU lit son niveau d'alimentation pour détecter si le bouton est pressé.

.. image:: ./scratch_img/cou13.png
   :alt: img

--------------

**Schéma électrique :**

.. image:: ./scratch_img/couy12.png
   :alt: img

**Paramètres :**

- Tension : 3~5V
- Courant : ≤1,1mA
- Puissance : ≤5,5mW

--------------

**Le principe du module bouton est un circuit contrôlé par ce bouton.**

- **Lorsque le bouton est pressé**, le circuit est en état fermé de sorte que le courant passe à travers le bouton vers GND, ce qui fait que la broche d'entrée numérique détecte un niveau bas.
- **Lorsque le bouton est relâché**, le circuit est coupé et le niveau de la broche augmente en raison d'une résistance de tirage, ce qui fait que la broche numérique détecte un niveau haut.

--------------

**Schéma de câblage :**

**Connectez le module bouton à io5**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj12.png
   :alt: img

--------------

**Code de test**

- Initialisez d'abord le port série, et réglez le débit en bauds à 115200.

   .. image:: ./scratch_img/st36.png
      :alt: img

- Réglez la broche sur IO5 et le mode sur entrée. Ce qui suit est un bloc "**forever**".

   .. image:: ./scratch_img/st37.png
      :alt: img

- Lisez le niveau d'alimentation de la broche numérique 5. Si c'est 1, imprimez 1. Sinon, imprimez 0.

   .. image:: ./scratch_img/st38.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st35.png
   :alt: img

**Résultat du test**

Ouvrez le moniteur série et réglez le débit en bauds correspondant.

Lorsque le bouton est relâché, la valeur est 1 ; si vous pressez le bouton, elle devient 0.

.. image:: ./scratch_img/st39.png
   :alt: img

Dans KidsBlock, nous pouvons lire l'état de la broche d'entrée numérique en programmant pour détecter si le bouton est pressé. Ainsi, de nombreuses applications interactives peuvent être réalisées via un module bouton, comme l'allumage/extinction de LED et l'ajustement de la luminosité d'affichage.

--------------

**Extension : Bouton à verrouillage automatique**

Un bouton à verrouillage automatique ne ressort pas lorsque vous le pressez sans le maintenir, et il ne ressort jamais à moins que vous le pressiez à nouveau. Il fonctionne comme un interrupteur. Pour les boutons réguliers, une telle fonction peut être réalisée via MCU et logiciel.

**Code de test**

- Définissez deux variables : **item** comme la valeur du bouton lu et **button** comme la valeur décalée par le bouton.

   .. image:: ./scratch_img/st40.png
      :alt: img

- Assignez la valeur du bouton lu à **item**.

   .. image:: ./scratch_img/st41.png
      :alt: img

- Déterminez si le bouton est pressé. Si c'est le cas, décalez la valeur de **button** et imprimez-la.

   .. image:: ./scratch_img/st43.png
      :alt: img

- Délai de 0,01s pour éliminer les vibrations du bouton.

- Si un état fermé est détecté au bouton, un délai sera exécuté pour éliminer les **vibrations du porche avant**. Généralement, le délai est dans les 5ms～10ms (les propriétés mécaniques décident). Après que les vibrations disparaissent, vérifiez à nouveau l'état du bouton. Si le niveau d'état fermé est toujours maintenu, il est confirmé qu'il y a un bouton pressé.
- Lorsqu'un bouton relâché est détecté, un délai de 5ms～10ms devrait également se produire pour supprimer les **vibrations du porche arrière**, de sorte que le programme pour le bouton puisse être exécuté.

- Lorsque le bouton est pressé, **button** égale 1. Pressez-le à nouveau, **button** passe à 0, alternativement.

Code complet :

.. image:: ./scratch_img/st44.png
   :alt: img

**Résultat du test**

Téléchargez le code et ouvrez le moniteur série.

Lorsque vous pressez le bouton une fois, 1 sera affiché. Si vous pressez le bouton pour la deuxième fois, la valeur devient 0. Maintenant, un bouton commun possède la fonction d'un bouton à verrouillage automatique.

.. image:: ./scratch_img/st46.png
   :alt: img

--------------

.. _4.1.3-Lighting-Control:

4.1.3 Contrôle d'éclairage
^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description**

Dans les expériences de base ci-dessus, nous remodelons un bouton à verrouillage automatique pour contrôler la LED. Un bouton à verrouillage automatique convient à toutes les situations où un certain état doit être maintenu, par exemple, lorsque la LED doit s'allumer pendant une longue période, la carte de développement ESP32 est requise pour certaines opérations.

Dans cette expérience, nous adopterons la carte Arduino ESP32 pour vous guider à implémenter un système d'éclairage et simuler des scènes de la vie réelle pour contrôler la lumière via le bouton.

--------------

**Schéma de câblage :**

**Connectez le bouton à io5 et la LED à io27**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj13.png
   :alt: img

--------------

**Code de test :**

Flux de code :

.. image:: ./scratch_img/flo1.png
   :alt: img

Code complet :

Basé sur le code pour le bouton à verrouillage automatique, nous ajoutons des blocs "**LED pin output**".

.. image:: ./scratch_img/st47.png
   :alt: img

**Résultat du test :**

**Lorsque vous pressez le bouton une fois, la LED s'allume ; si vous pressez à nouveau, la LED s'éteint. Cette opération est une boucle, qui est cohérente avec le principe d'éclairage dans la réalité.**

--------------

Dans ce chapitre, nous avons démontré comment programmer et contrôler via KidsBlock, et nous avons appris les bases ainsi que certains concepts logiciels et matériels dans des expériences telles que le bouton à verrouillage automatique et le système de contrôle d'éclairage.

Ceux-ci sont essentiels pour un bon développeur KidsBlock. Ensuite, nous vous guiderons pour continuer à explorer plus d'applications et de compétences, que vous soyez débutant ou vétéran. Nous espérons que vous apprécierez le plaisir et les défis pendant l'apprentissage de KidsBlock. Continuons !

--------------

.. _4.1.5-FAQ:

4.1.5 FAQ
^^^^^^^^^

**Q : La LED ne s'allume pas après avoir téléchargé le code.**

R : Veuillez vérifier si la broche définie dans le code est cohérente avec celle de vos câblages. Si elles sont incompatibles, veuillez l'ajuster en vous référant au code.

--------------

**Q : Le bouton fonctionne parfois mais parfois non.**

R : Veuillez modifier le délai d'élimination des vibrations à une valeur appropriée.

.. code:: c++

    //Éliminer les vibrations du bouton
      delay(10);  //Modifiez la valeur de délai dans cette ligne

--------------

.. _4.2-Project-:-Light-Control-System:

4.2 Projet : Système de contrôle de lumière
Dans ce projet, nous construirons un système de contrôle de lumière par une photorésistance et une LED. C'est un système intelligent pour ajuster la lumière, qui économise l'énergie et améliore l'efficacité également.

.. image:: ./scratch_img/cout2.png
:alt: img

Ce système est compatible avec plusieurs conditions. Grâce à sa photorésistance, il est capable de détecter l'intensité lumineuse le jour ou la nuit, réalisant un système plus intelligent et économe en énergie.

Lorsque la photorésistance détecte que la luminosité ambiante est inférieure à la valeur définie, la LED s'allume. Au contraire, si l'intensité de la lumière ambiante est supérieure à la valeur définie, la photorésistance enverra un signal différent pour éteindre la LED.

.. _4.2.1-Flow-Diagram:

4.2.1 Diagramme de flux
^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230607175802112.png
:alt: image-20230607175802112

.. _4.2.2-Photoresistor:

4.2.2 Photorésistance
^^^^^^^^^^^^^^^^^^^^^^

Description :

Une photorésistance, aussi appelée photocapteur, convertit le signal lumineux en signal électrique (tension, courant et résistance).

Principe de fonctionnement :

Nous plaçons une photorésistance dans un circuit en connexion série et ajoutons une tension appropriée aux deux pôles. Lorsqu'il n'y a pas de lumière, la résistance est infinie et le circuit s'ouvre presque. Cependant, lorsqu'il y a de la lumière, la résistance diminue tandis que le courant augmente, et c'est équivalent à un court-circuit lorsque l'intensité lumineuse est suffisante.

Maintenant nous lirons la valeur de la photorésistance en programmant sur la carte de développement ESP32.

.. image:: ./scratch_img/cou2.png
:alt: img

Schéma électrique :

Lorsque la lumière frappe la photorésistance, plus la lumière est forte, plus la résistance sera petite, donc plus la tension VCC passera à travers la résistance.

.. image:: ./scratch_img/couy21.png
:alt: img

Paramètres :

Tension : 3~5V
Courant : 0,2mA
Puissance : 1mW
Valeur de pic du spectre : 540nm
Résistance lumineuse (10lux) : 5~10KR
Résistance obscure : 0,5MR
Schéma de câblage :

Connectez la photorésistance à io34.

Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !

.. image:: ./scratch_img/couj21.png
:alt: img

Code de test :

Initialisez le port série.

.. image:: ./scratch_img/st48.png
:alt: img

Définissez une variable globale "item" comme la valeur de la photorésistance.

.. image:: ./scratch_img/st49.png
:alt: img

Réglez "item" sur la valeur lue et imprimez-la sur le moniteur série.

.. image:: ./scratch_img/st50.png
:alt: img

Code complet :

.. image:: ./scratch_img/st51.png
:alt: img

Résultat du test :

Ouvrez le moniteur série.

Plus la lumière détectée par la photorésistance est brillante, plus la valeur sera grande.

.. image:: ./scratch_img/st52.png
:alt: img

.. _4.2.3-Light-Control-System:

4.2.3 Système de contrôle de lumière
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Schéma de câblage :

Connectez la photorésistance à io34 et la LED à io27.

Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !

.. image:: ./scratch_img/couj22.png
:alt: img

Code de test :

Flux de code :

.. image:: ./scratch_img/flo2.png
:alt: img

Déterminez :

La valeur de la photorésistance >= 800, la LED s'éteint.

La valeur de la photorésistance =< 800, la LED s'allume.

.. image:: ./scratch_img/st53.png
:alt: img

Code complet :

.. image:: ./scratch_img/st54.png
:alt: img

Résultat du test :

Lorsque la valeur de la photorésistance est supérieure à 800 (en journée), la LED s'éteint. Cependant, si la valeur est inférieure à 800, la LED s'allumera automatiquement.

.. image:: ./scratch_img/st55.png
:alt: img

**Diverses conditions peuvent adopter ce type de système. Grâce à sa photorésistance, il est capable de détecter l'intensité lumineuse le jour ou la nuit, ce qui économise l'énergie et intellectualise tout le système. **

.. _4.2.2-FAQ:

4.2.2 FAQ
^^^^^^^^^

Q : La valeur de la photorésistance ne peut pas être 0.

R : Dans la vie réelle, peu de lumière existe même si vous éteignez toutes les lumières dans votre pièce, donc la valeur de la photorésistance ne fait qu'approcher 0 plutôt que d'égaler 0.

Q : Après avoir téléchargé le code, la LED ne s'allume pas même si la pièce est sombre sans lumières.

R : Augmentez la valeur déterminée de la photorésistance. Dans notre exemple, nous avons réglé à 800. Vous pouvez donc l'ajuster à 1000 ou une valeur plus grande.

.. image:: ./scratch_img/st53.png
:alt: img

.. _4.3-Project-:-Alarm-System:

4.3 Projet : Système d'alarme


Dans ce projet, nous utilisons un capteur de mouvement PIR et un buzzer pour constituer un système d'alarme, qui peut être contrôlé par la carte de développement ESP32.

Comment ça marche ? Les signaux électriques sont détectés et lus par le capteur de mouvement PIR grâce à la programmation sur Arduino IDE, puis il détermine s'il y a une personne. Si c'est le cas, le buzzer alarme. De cette façon, ce système d'alarme coûte beaucoup moins cher pour les familles et les bureaux.

--------------

.. _4.3.1-Flow-Diagram:

4.3.1 Diagramme de flux
^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230606102303743.png
   :alt: image-20230606102303743

--------------

.. _4.3.2-PIR-Motion-Sensor:

4.3.2 Capteur de mouvement PIR
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

Un capteur de mouvement PIR détecte la présence d'une personne en détectant la chaleur dégagée par le corps humain.

De plus, ce capteur est petit et facile à utiliser.

.. image:: ./scratch_img/cou32.png
   :alt: img

--------------

**Schéma électrique :**

.. image:: ./scratch_img/couy31.png
   :alt: img

**Paramètres :**

- Tension : 3~5V
- Courant : 3,6mA
- Puissance : 18mW
- Angle de vue : Y = 90°, X = 110° (valeur théorique)
- Distance de détection : ≤5m

--------------

**Schéma de câblage :**

**Connectez le capteur de mouvement PIR à io23.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj31.png
   :alt: img

--------------

**Code de test :**

Lisez la valeur à la broche IO23 pour déterminer s'il y a un mouvement humain.

.. image:: ./scratch_img/image-20250423083305405.png
   :alt: image-20250423083305405

**Résultat du test :**

Ouvrez le moniteur série.

Lorsque quelqu'un est dans la zone, **Someone** est affiché sur le moniteur, et la LED rouge sur le capteur s'éteint. Cependant, s'il n'y a personne, **No one** sera imprimé et la LED sera toujours allumée.

**ATTENTION** : Le capteur de mouvement PIR n'est pas capable de pénétrer les objets, donc veuillez ne pas couvrir le capteur lors de la détection de mouvements.

.. image:: ./scratch_img/st57.png
   :alt: img

--------------

.. _4.3.3-Buzzer:

4.3.3 Buzzer
^^^^^^^^^^^^

**Description :**

Un buzzer est un avertisseur sonore électronique, qui émet des sons avec différentes fréquences et durées et est alimenté par une tension DC. Ainsi, il peut être utilisé comme rappel ou alarme dans des appareils électroniques considérables, tels que les ordinateurs, imprimantes, photocopieurs, alarmes, jouets électroniques, électronique automobile, téléphones et minuteries.

.. image:: ./scratch_img/cou34.png
   :alt: img

--------------

Un buzzer consiste en un **dispositif de vibration** et un **dispositif de résonance**. Et il y a deux catégories : Buzzers passifs et buzzers actifs.

- Un **Buzzer passif** ne peut pas ``vibrer`` pour émettre du son lui-même, à moins de mettre un signal d'``onde carrée`` avec une certaine fréquence. De plus, le son émis varie en raison de la différente fréquence de l'onde carrée, donc un buzzer passif peut simuler des mélodies.

- Une onde carrée analogique peut être générée en changeant le niveau d'alimentation aux broches. Par exemple, après que le niveau haut dure 500ms, il passe à un niveau bas pendant 500ms supplémentaires puis à un niveau haut à nouveau...
- \**Nous conduisons le buzzer via une onde carrée dans les 200~5000Hz, et nous pouvons calculer la fréquence(f) : *f=1/T* ; T est la période (le temps total de niveau haut et bas). \*\*

.. image:: ./scratch_img/cou35.png
   :alt: img

- Un **Buzzer actif** est capable d'émettre du son automatiquement sans motivateur externe, car il inclut un circuit de conduite qui n'a besoin que d'``alimentation DC``. Cependant, son son est plat avec une fréquence relativement fixe.

--------------

**Dans cette expérience, un buzzer passif est appliqué pour "jouer de la musique".**

--------------

**Schéma électrique :**

.. image:: ./scratch_img/cou38.png
   :alt: img

**Paramètres :**

- Tension : 3~5V
- Courant : ≤5mA
- Puissance : ≤25mW

--------------

**Schéma de câblage :**

**Connectez le buzzer à io16.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj32.png
   :alt: img

--------------

**Code de test :**

**Méthode 1 : Onde carrée analogique**

Un buzzer passif est conduit par des ondes carrées, donc nous stimulons l'onde.

Une onde carrée analogique peut être générée en changeant le niveau d'alimentation de la broche : niveau haut pendant 500us et niveau bas pendant 500us. Donc, le buzzer émettra du son. Aussi, les durées peuvent ajuster le volume du son.

Veuillez essayer 1000us, 1500us, 3000us…Quelle est la différence ?

.. image:: ./scratch_img/cou36.png
   :alt: img

Code :

.. image:: ./scratch_img/st58.png
   :alt: img

- Dans la fonction de délai, l'unité de temps us micro-secondes. Donc le bloc suivant représente un délai de 500ms.

.. image:: ./scratch_img/st59.png
   :alt: img

Selon la formule :

.. math:: f = 1/T

Ainsi, 500us est la durée, et nous pouvons calculer la fréquence = 2kHz, c'est-à-dire que le niveau haut et bas alternent 2000 fois par seconde.

--------------

**Méthode 2 : Blocs haut-parleur**

Nous adoptons les blocs de code Speaker\ |image24| pour conduire le buzzer à vibrer.

**Les blocs haut-parleur génèrent un signal PWM avec une certaine fréquence pour conduire le buzzer à vibrer,** et la durée et le ton sont contrôlés par des paramètres connexes.

Il y a deux façons de définir la durée. L'une est d'ajuster les paramètres de la fonction tone() pour définir une durée, et l'autre est d'adopter une fonction noTone() pour arrêter directement le son. Si vous ne définissez pas de durée dans tone(), le signal sonore sera toujours généré à moins qu'un noTone() l'arrête.

Pour la carte ESP32, un seul son peut être produit à la fois. Si une broche d'ESP32 génère un signal sonore via tone(), il n'est pas acceptable d'émettre du son par cette fonction sur une autre broche.

**Table des tons**

.. image:: ./scratch_img/cou37.png
   :alt: img

Code :

- Faites glisser un bloc "**Tone**" de |image25| comme montré ci-dessous, et réglez la broche sur IO16.

   .. image:: ./scratch_img/st61.png
      :alt: img

- Vous pouvez sélectionner une fréquence à volonté.

   .. image:: ./scratch_img/st62.png
      :alt: img

- No Tone : Il est utilisé pour éteindre tous les tons.

   .. image:: ./scratch_img/st65.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st63.png
   :alt: img

**Résultat du test :**

Méthode 1 : Le buzzer continue d'émettre du son.

Méthode 2 : Le buzzer alarme via la fonction tone().

--------------

**Extension : Jouer de la musique**

Jouer de la musique grâce à tone().

Code complet :

.. image:: ./scratch_img/st64.png
   :alt: img

--------------

.. _4.3.4-Alarm-System:

4.3.4 Système d'alarme
^^^^^^^^^^^^^^^^^^^^^^^

Dans cette expérience, nous construirons un système d'alarme par un capteur de mouvement PIR, un buzzer et une LED. Lorsque le capteur détecte un mouvement, le buzzer émet du son et la LED clignote pour rappeler une intrusion.

--------------

**Schéma de câblage :**

**Connectez le capteur de mouvement PIR à io23, le buzzer à io16, et la LED à io27.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj33.png
   :alt: img

--------------

**Code de test :**

Flux de code :

.. image:: ./scratch_img/flo3.png
   :alt: img

Code complet :

.. image:: ./scratch_img/image-20250423084431295.png
   :alt: image-20250423084431295

**Résultat du test :**

Téléchargez le code et le système d'alarme commence à fonctionner. Lorsqu'il détecte un mouvement, le buzzer alarme et la LED clignote.

--------------

.. _4.3.5-FAQ:

4.3.5 FAQ
^^^^^^^^^

**Q : Les tons du buzzer ne sont pas précis avec les vrais.**

R : Ce buzzer régulier ne fait que stimuler les tons, donc il n'est pas capable de répondre aux exigences professionnelles. Si vous voulez des tons standard, un haut-parleur plus spécialisé est requis.

--------------

**Q : Le capteur de mouvement PIR donne de fausses informations.**

R : Ce capteur de mouvement PIR n'est pas non plus professionnel.

Veuillez garantir les situations suivantes pour éviter une fausse information :

- Évitez les objets soufflés par le vent pour flotter dans la zone de détection, tels que rideaux, vêtements et fleurs.
- Évitez la lumière forte dans la zone de détection, telle que la lumière du soleil, les phares de voiture, les projecteurs et autres sources lumineuses.
- Et ainsi de suite...

--------------

.. _4.4-Project-:-Rain-Detection-System:

4.4 Projet : Système de détection de pluie
NOTE : Asperger de l'eau sur les capteurs (sauf le capteur de vapeur) peut causer un court-circuit ou que les modules ne fonctionnent plus. Si les batteries sont mouillées, même une explosion peut se produire. Soyez très prudent ! Pour les utilisateurs plus jeunes, veuillez opérer avec vos parents. Pour garantir la sécurité, veuillez obéir aux directives et réglementations de sécurité.

Dans ce projet, nous créerons un système de détection de pluie par un capteur de vapeur. Lorsque la pluie est détectée, ESP32 déclenche diverses actions comme envoyer un message, activer les arroseurs et allumer les lumières. Grâce à ce système, la quantité de pluie peut être surveillée, et les fuites d'eau peuvent également être détectées sur les toits ou dans les bâtiments.

De plus, il est facile de connecter le capteur de vapeur à la carte ESP32, qui forme un système de détection de pluie simple mais efficace.

.. image:: ./scratch_img/cout4.png
:alt: img

.. _4.4.1-Flow-Diagram:

4.4.1 Diagramme de flux
^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230607180917475.png
:alt: image-20230607180917475

.. _4.4.2-Steam-Sensor:

4.4.2 Capteur de vapeur
^^^^^^^^^^^^^^^^^^^^^^^

Description :

Le capteur de vapeur détecte la présence d'eau, donc il est généralement utilisé dans la détection de pluie. Si la pluie frappe le pad conducteur sur le capteur, il enverra un signal à la carte Arduino.

.. image:: ./scratch_img/cou41.png
:alt: img

Schéma électrique :

.. image:: ./scratch_img/couy41.png
:alt: img

Paramètres :

Tension : 3~5V
Courant : 1,5mA
Puissance : 7,5mW
Schéma de câblage :

Connectez le capteur de vapeur à io35.

Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !

.. image:: ./scratch_img/couj41.png
:alt: img

Code de test :

Initialisez le port série.

.. image:: ./scratch_img/st67.png
:alt: img

Lisez la valeur du capteur à la broche io35 et imprimez-la par seconde.

.. image:: ./scratch_img/st68.png
:alt: img

Code complet :

.. image:: ./scratch_img/st69.png
:alt: img

Résultat du test :

Touchez la zone de détection avec un doigt mouillé. Plus la zone que vous touchez est grande, plus la valeur sera grande.

Vous pouvez ouvrir le moniteur série pour observer la valeur actuellement détectée (plage : 0~4095).

.. image:: ./scratch_img/st70.png
:alt: img

.. _4.4.3-Rain-Detection-System:

4.4.3 Système de détection de pluie
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Description :

Lorsque le capteur de vapeur détecte la pluie, il envoie un signal à la carte pour déclencher diverses actions, par exemple, le buzzer alarme pour rappeler qu'il pleut. Ceci est particulièrement utile pour le jardinage et l'agriculture en extérieur, permettant aux utilisateurs de prendre les précautions nécessaires pour éviter l'arrosage excessif.

De plus, ce système peut être utilisé pour détecter les fuites d'eau pour prévenir les dommages dus à l'intrusion d'eau. Dans l'ensemble, le capteur de vapeur est polyvalent et efficace dans diverses applications.

Schéma de câblage :

Connectez le capteur de vapeur à io35 et le buzzer à io16.

Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !

.. image:: ./scratch_img/couj42.png
:alt: img

Code de test :

Flux de code :

.. image:: ./scratch_img/flo4.png
:alt: img

Code :

Initialisez le port série, et définissez une variable item comme la valeur du capteur reçue.

.. image:: ./scratch_img/st71.png
:alt: img

Recevez la valeur du capteur et imprimez-la sur le moniteur série.

.. image:: ./scratch_img/st72.png
:alt: img

La valeur reçue détectée par le capteur est dans les 800 ~ 1999 :

.. image:: ./scratch_img/st73.png
:alt: img

La valeur reçue détectée par le capteur est dans les 2000 ~ 2999 :

.. image:: ./scratch_img/st74.png
:alt: img

La valeur reçue détectée par le capteur est supérieure à 3000 :

.. image:: ./scratch_img/st75.png
:alt: img

À la fin des blocs de code, ajoutez un "No Tone" pour éteindre le buzzer.

.. image:: ./scratch_img/st76.png
:alt: img

Code complet :

.. image:: ./scratch_img/st77.png
:alt: img

Résultat du test :

Plus la valeur détectée est grande, plus le son émis par le buzzer sera fort.

.. _4.4.4-FAQ:

4.4.4 FAQ
^^^^^^^^^

Q : Le capteur de vapeur est-il étanche ?

R : La zone de détection peut être exposée à l'eau, mais les jonctions de fil ne sont pas étanches. Pendant l'expérience, veuillez faire attention à la quantité d'eau pour qu'elle ne soit pas trop importante pour prévenir un court-circuit.

Q : Bien qu'un long temps se soit écoulé depuis que le capteur a détecté l'eau, le buzzer continue de bourdonner.

R : Il continue de bourdonner car il y a encore des gouttes d'eau dans la zone de détection. Veuillez simplement les nettoyer.

.. _4.5-Project:-Solar-Power-System:

4.5 Projet : Système d'énergie solaire


.. image:: ./scratch_img/cou51.png
   :alt: img

.. _4.5.1-Description:

4.5.1 Description
^^^^^^^^^^^^^^^^^

Le panneau solaire convertit l'énergie solaire en électricité pour la LED. Il convient à de multiples applications, telles que l'éclairage extérieur, la charge d'appareils mobiles et l'alimentation de secours. Par conséquent, vous pouvez établir un système d'énergie solaire sophistiqué et efficace selon vos propres besoins.

--------------

.. _4.5.2-Working-Principle:

4.5.2 Principe de fonctionnement
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Comment le panneau solaire convertit-il l'énergie solaire en électricité ?**

.. image:: ./scratch_img/cou52.png
   :alt: img

Le panneau solaire absorbe la lumière et convertit directement ou indirectement le rayonnement solaire en électricité. Comparé à la génération d'électricité au charbon ordinaire, l'énergie solaire, éolienne et hydraulique sont plus économes en énergie et respectueuses de l'environnement.

--------------

**Comment la lumière se convertit-elle en électricité ?**

Ensuite, parlons du processus de conversion de l'intérieur vers l'extérieur dans un panneau solaire.

**Le Soleil émet de l'énergie en ondes avec une large gamme de longueurs d'onde, de l'ultraviolet au visible à la lumière infrarouge.**

- Longueur d'onde de l'ultraviolet : 150~400nm ;
- Longueur d'onde de la lumière visible : 400~760nm ;
- Longueur d'onde de la lumière infrarouge : 760~4000nm ;

**Le panneau absorbe une de ces gammes de longueur d'onde et les convertit en électricité. Mais comment ? Continuons.**

--------------

**La partie active de la plupart des cellules de panneau solaire est faite d'un semi-conducteur --- silicium(Si).**

.. image:: ./scratch_img/cou53.png
   :alt: img

La conductivité d'un semi-conducteur est entre un conducteur et un isolant à température atmosphérique. Généralement, il ne peut pas bien conduire, mais sa conductivité s'améliore dans certaines conditions.

--------------

.. image:: ./scratch_img/cou54.png
   :alt: img

**Le diagramme ci-dessus montre la structure interne du semi-conducteur dans la cellule solaire, qui est divisée en trois couches :**

1. **La couche supérieure (partie rouge)** consiste en Silicium(Si) et un peu de Phosphore(P). Ce dernier porte plus d'électrons que le premier, fournissant suffisamment d'électrons pour la couche supérieure. En raison de ces électrons se déplaçant librement, cette couche est conductrice, donc elle est appelée **Négative ou type N.**
2. **La couche du milieu (partie grise)** contient trop peu d'électrons pour conduire.
3. **La couche inférieure (partie verte)** inclut principalement Silicium(Si) et Bore(B). Ce dernier porte moins d'électrons que le premier, de sorte que très peu d'électrons se déplacent librement, causant le manque d'électrons qui sont décrits comme charge positive effective. Par conséquent, cette couche est nommée **Positive ou type P.**

.. image:: ./scratch_img/cou55.png
   :alt: img

**Habituellement, seule la couche du milieu du panneau solaire absorbe les ondes lumineuses avec une longueur d'onde de 350~1140nm.** Selon la distribution spectrale dans les paragraphes précédents, les absorptions sont l'ultraviolet à onde longue, l'infrarouge à onde courte et la lumière visible.

**La longueur d'onde de l'ultraviolet est si courte qu'elle s'arrête à la surface.**

.. image:: ./scratch_img/cou56.png
   :alt: img

**La longueur d'onde de la lumière infrarouge est trop longue pour être absorbée par le panneau, donc elle passe généralement à travers ou est réfléchie.**

.. image:: ./scratch_img/cou57.png
   :alt: img

La couche du milieu absorbe la lumière et frappe les électrons du silicium dans la couche supérieure, les laissant dans un état libre, et des trous d'électrons vides sont générés à l'endroit où ils étaient avant.

.. image:: ./scratch_img/cou58.gif
   :alt: img

Les trous portent une charge positive. Pendant ce temps, les électrons libres se déplacent vers le haut pour atteindre la couche de type N, tandis que les trous se déplacent vers le bas pour atteindre la couche de type P.

**En conclusion, les électrons dans les couches supérieure et inférieure sont frappés après que la couche du milieu absorbe l'énergie solaire. Par conséquent, la couche de type N porte une charge négative comme pôle négatif, tandis que la couche de type P est chargée positivement comme pôle positif. Dans ce cas, tant que les deux couches sont connectées, cela conduit.**

--------------

Si la lumière du soleil brille sur le panneau solaire, la situation ci-dessus durera, et un grand nombre d'électrons libres et de trous seront produits. Comme notre conclusion va, les électrons se déplacent vers le haut tandis que les trous se déplacent vers le bas, ce qui forme les deux pôles et génère du courant.

.. image:: ./scratch_img/cou59.gif
   :alt: img

--------------

.. image:: ./scratch_img/cou510.png
   :alt: img

L'énergie solaire est une source d'énergie alternative, qui présente la durabilité et la rentabilité.

Cependant, l'électricité générée par un panneau solaire peut être convertie en plusieurs watts de puissance, ce qui est suffisant pour une calculatrice ou un chargeur de téléphone portable, mais pas assez pour faire fonctionner un grille-pain d'un kilowatt.

Les systèmes d'énergie solaire satisfont les besoins de différents utilisateurs et bénéficient également à l'environnement. Combiné avec la programmation Arduino, ce type de système construit une variété d'applications solaires utiles et efficaces, comme l'éclairage automatique, les chargeurs et les maisons intelligentes.

Généralement parlant, l'énergie solaire promet bien pour un avenir merveilleux et durable.

--------------

.. _4.5.3-Parameters:

4.5.3 Paramètres
^^^^^^^^^^^^^^^^

- Tension : 5V
- Courant : 80mA
- Puissance : 400mW
- Dimensions : 60*60mm

--------------

.. _4.5.4-Test-Result:

4.5.4 Résultat du test
^^^^^^^^^^^^^^^^^^^^^^

Les codes ne sont pas requis dans ce projet. Importamment, nous apprenons sur la nouvelle énergie environnementale --- l'énergie solaire.

Lorsqu'un bon éclairage est fourni, la LED s'allumera en jaune. Plus la lumière est brillante, plus la LED sera brillante.

--------------

.. _4.5.5-FAQ:

4.5.5 FAQ
^^^^^^^^^

Q : Pourquoi le panneau solaire fonctionne-t-il encore sans lumière du soleil ?

R : Il fonctionne non seulement avec la lumière du soleil mais aussi avec la lumière ambiante. Plus la lumière est brillante, plus la tension sera grande, et plus la LED sera lumineuse.

--------------

.. _4.6-Project:-Smart-Feeding-System:

4.6 Projet : Système d'alimentation intelligent
Dans ce projet, le module ultrasonique détecte si les animaux sont dans la zone d'alimentation, et le Servo ouvre automatiquement la boîte d'alimentation pour les volailles. De plus, l'incorporation de l'IOT permet la surveillance à distance de tels systèmes d'alimentation qui fournit beaucoup de commodité.

Dans l'ensemble, l'automatisation et l'opération à distance optimisent le processus d'alimentation pour ce système.

.. image:: ./scratch_img/cout6.png
:alt: img

.. _4.6.1-Flow-Diagram:

4.6.1 Diagramme de flux
^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230607085516167.png
:alt: image-20230607085516167

.. _4.6.2-Servo:

4.6.2 Servo
^^^^^^^^^^^

Description :

Servo, aussi appelé Dispositif Servo RC, est un moteur avec un retour. Communément, le Servo effectue un contrôle de position précis et sort un couple élevé, qui apparaît le plus souvent dans les projets de robotique, les voitures RC, les avions et les aéronefs.

.. image:: ./scratch_img/cou64.png
:alt: img

Structure interne :

.. image:: ./scratch_img/cou61.png
:alt: img

① Signal(S) : Il reçoit le signal de contrôle du microcontrôleur.
② Potentiomètre : la partie de retour du Servo. Il mesure la position de l'arbre de sortie.
③ Carte intégrée (Contrôleur interne) : le cœur du Servo. Il traite le signal de contrôle externe et le signal de retour de position et conduit le Servo.
④ Moteur DC : la partie d'exécution. Il sort la vitesse, le couple et la position.
⑤ Système d'engrenages : Il met à l'échelle les sorties du moteur à l'angle de sortie final selon un certain rapport de transmission.
Conduire le Servo :

Signal(S) reçoit PWM pour contrôler la sortie du Servo, et la position de l'arbre de sortie dépend directement du cycle de service de PWM.

Par exemple :

Si nous envoyons un signal avec une largeur d'impulsion de 1,5ms au Servo, son arbre(corne) tournera à la position du milieu(90°) ;
Si largeur d'impulsion = 0,5ms, l'arbre tourne à son minimum(0°) ;
Si largeur d'impulsion = 2,5ms, l'arbre tourne à son maximum(180°).
NOTE : L'angle maximum varie selon les types de Servos. Certains sont 170° tandis que certains ne sont que 90°. Malgré cela, les Servos bougent généralement de moitié (du maximum) s'ils reçoivent un signal avec une largeur d'impulsion de 1,5ms.

.. image:: ./scratch_img/cou62.png
:alt: img

La période d'un Servo dure généralement 20ms et il produit des impulsions à une fréquence de 50Hz. La plupart des servos fonctionnent normalement à 40~200Hz.

Schéma de câblage :

Connectez le Servo à io26.

Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à GND. Ne les inversez pas !

.. image:: ./scratch_img/couj61.png
:alt: img

Code de test :

Initialisez le port série et définissez une variable item avec une assignation de 80.

.. image:: ./scratch_img/st78.png
:alt: img

Réglez item à l'angle du Servo de 80° à 180°, tournant 1° toutes les 15ms.

.. image:: ./scratch_img/st79.png
:alt: img

Le Servo tourne 1° toutes les 15ms, de 180° à 80°.

.. image:: ./scratch_img/st80.png
:alt: img

Code complet :

.. image:: ./scratch_img/st81.png
:alt: img

Résultat du test :

La boîte d'alimentation s'ouvre lentement puis se ferme, ce qui est contrôlable.

NOTE : Le servo SG90 peut tourner 180°. Comme la boîte d'alimentation est petite, 100° de rotation suffisent pour fermer complètement la boîte.

80° : complètement ouvert
120° : à moitié ouvert
180° : fermé
.. image:: ./scratch_img/cou63.gif
:alt: img

ATTENTION

**Ne mettez pas vos doigts dans la boîte pour éviter de les pincer ! **

Ne bloquez pas la porte avec quelque chose pour éviter d'endommager le servo !

.. _4.6.3-Ultrasonic-Sensor:

4.6.3 Capteur Ultrasonique
^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

.. image:: ./scratch_img/cou65.png
   :alt: img

**Schéma Électrique :**

.. image:: ./scratch_img/couy61.png
   :alt: img

--------------

La fréquence des ondes sonores que l'humain peut entendre est de 20Hz ~ 20KHz,
tandis que les ondes ultrasoniques sont au-delà de cette plage.

**Ultrasonique :**

.. image:: ./scratch_img/cou66.png
   :alt: img

Le module ultrasonique convertit l'électricité et les ondes ultrasoniques l'une
en l'autre par effet piézoélectrique, et il transmet et reçoit également
les ondes ultrasoniques.

Ce type d'onde présente une directivité, une forte pénétration et une
concentration facile de l'énergie sonore.

.. image:: ./scratch_img/cou67.png
   :alt: img

Dans ce système de télémétrie ultrasonique, nous programmons d'abord sur MCU (carte de développement ESP32) pour générer une onde carrée originale à 40KHz et
piloter le module ultrasonique pour l'émettre. Immédiatement, le module
calcule la distance à l'objet après avoir reçu l'onde réfléchie (Echo) amplifiée et mise en forme par le circuit. Ici, il enregistre la
durée d'émission et de réflexion et calcule la distance
selon la différence de temps.

Simplement, le MCU contrôle le module pour émettre une onde ultrasonique qui rebondit
après avoir rencontré des obstacles et est reçue par le module. La
différence de temps entre eux est un facteur important dans le calcul de la
distance (la vitesse de propagation du son dans l'air est de 340m/s).

--------------

**Schéma de Câblage :**

**Connectez l'Echo du module Ultrasonique à io13 et Trig à io12.**

**Attention : Connectez le jaune à S(Signal) et le rouge à V(Alimentation). Ne
les inversez pas !**

.. image:: ./scratch_img/couj62.png
   :alt: img

--------------

**Code de Test :**

Définissez la broche correcte : Trig à la broche io12 ; Echo à la broche io13.

.. image:: ./scratch_img/st83.png
   :alt: img

**Résultat du Test :**

Dans ce kit, la plage de détection est comprise entre 3~8cm.

Ouvrez le moniteur série, et observez.

.. image:: ./scratch_img/st82.png
   :alt: img

--------------

.. _4.6.4-Smart-Feeding-System:

4.6.4 Système d'Alimentation Intelligent
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

Le système d'alimentation intelligent nourrit intelligemment les volailles domestiques via un
module ultrasonique et un servo. Le premier détecte la distance aux
animaux tandis que le second contrôle l'ouverture ou la fermeture de la boîte d'alimentation. Quand
un animal de compagnie est détecté près de la boîte, le servo l'ouvre pour nourrir.

--------------

**Schéma de Câblage :**

**Connectez l'Echo du module Ultrasonique à io13 et Trig à io12 ;
connectez le servo à io26.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation) et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj63.png
   :alt: img

--------------

**Code de Test :**

Flux de Code :

.. image:: ./scratch_img/flo6.png
   :alt: img

Code :

-  Initialisez le port série. Définissez une variable et assignez-lui 180.

   .. image:: ./scratch_img/st84.png
      :alt: img

-  Définissez la broche correctement, et imprimez la valeur reçue.

   .. image:: ./scratch_img/st85.png
      :alt: img

-  Déterminez la valeur de distance détectée. Si elle est comprise entre 2cm ~ 7cm, la
   boîte d'alimentation s'ouvrira.

   .. image:: ./scratch_img/st86.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st87.png
   :alt: img

**Résultat du Test :**

Quand un animal est détecté, ouvrez la boîte d'alimentation.

--------------

**ATTENTION**

\**Ne mettez pas vos doigts dans la boîte pour éviter de vous pincer ! \*\*

**Ne bloquez pas la porte avec quelque chose pour éviter d'endommager le servo !**

--------------

.. _4.6.5-FAQ:

4.6.5 FAQ
^^^^^^^^^

Q : Le servo ne fonctionne pas.

R : Il peut être bloqué par lui-même ou par des fils lors du montage de la plaque inférieure.
avant l'installation, veuillez d'abord ajuster le servo à 180°. Pour comment,
veuillez vous référer au guide d'installation.

--------------

Q : La distance détectée est inexacte.

R : Lors de la détection, veuillez mesurer depuis la tête d'émission. Ici,
ce module n'est pas un détecteur de haute précision, donc des erreurs peuvent exister.

.. image:: ./scratch_img/cou69.png
   :alt: img

--------------

.. _4.7-Project:-Temperature-Control-System:

4.7 Projet : Système de Contrôle de Température
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Dans ce projet, nous démontrerons comment utiliser un capteur de température et d'humidité, un ventilateur et un affichage LCD1602 pour constituer un système intelligent de contrôle de température
et d'humidité.

Le système mesure la température et l'humidité ambiantes et contrôle le ventilateur pour
refroidir selon les besoins. Quand la température dépasse le seuil défini, le
ventilateur se met automatiquement en marche pour réduire la température ambiante en dessous de la
valeur définie. Pendant ce temps, les valeurs actuelles de température et d'humidité seront
affichées sur LCD1602.

Par conséquent, il réalise un ajustement automatique de la température et de l'humidité ambiantes, ce qui est parfait pour les projets qui nécessitent ces fonctions.

.. image:: ./scratch_img/cout7.png
   :alt: img

--------------

.. _4.7.1-Flow-Diagram:

4.7.1 Diagramme de Flux
^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230607121651834.png
   :alt: image-20230607121651834

--------------

.. _4.7.2-Temperature-and-Humidity-Sensor:

4.7.2 Capteur de Température et d'Humidité
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

Le capteur de température et d'humidité DHT11 produit des signaux numériques. Il
applique les principes d'acquisition et de conversion de signaux analogiques ainsi
que la technologie de détection de température et d'humidité, de sorte qu'il présente
une stabilité à long terme et une haute fiabilité. De plus, le capteur intègre
un capteur d'humidité résistif de haute précision et un capteur de
température thermosensible résistif, et est connecté avec un MCU 8 bits
haute performance.

.. image:: ./scratch_img/cou71.png
   :alt: img

--------------

**Moyens de Communication DHT11 :**

DHT11 communique via monobus (un seul bus) qui échange et
contrôle les données.

-  Monobus transmet **Bit de Données** :

   -  Format de données du monobus : transmet 40bit de données à chaque fois, et
      bit de poids fort en premier.
   -  valeur entière d'humidité 8bit + valeur décimale d'humidité 8bit + valeur entière de
      température 8bit + valeur décimale de température 8bit + parité 8bit.
   -  **NOTE : La valeur décimale d'humidité égale 0.**

-  **Bit de Parité** :

   -  valeur entière d'humidité 8bit + valeur décimale d'humidité 8bit + valeur entière de
      température 8bit + valeur décimale de température 8bit.
   -  La parité 8bit égale les 8 derniers bits du résultat.

**Diagramme de Temporisation :**

.. image:: ./scratch_img/cou73.png
   :alt: img

\**NOTE : \*\*

**L'hôte lit toujours les valeurs de température et d'humidité de la dernière
mesure depuis DHT11. Par conséquent, si l'intervalle entre deux
mesures est long, veuillez détecter consécutivement deux fois et adopter le
second résultat.**

Pour plus de détails, veuillez visiter le site officiel d'ASAIR :
http://www.aosong.com/products-21.html

--------------

**Schéma de Câblage :**

**Connectez le capteur de température et d'humidité à io17.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj71.png
   :alt: img

--------------

**Code de Test :**

-  Initialisez le port série et le capteur.

   .. image:: ./scratch_img/st89.png
      :alt: img

-  Le moniteur série imprime et actualise les valeurs d'humidité et de température
   par seconde.

   .. image:: ./scratch_img/st90.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st91.png
   :alt: img

**Résultat du Test :**

.. image:: ./scratch_img/cou71-1.png
   :alt: img

Ouvrez le moniteur série, et vous verrez la valeur actuelle de température et
d'humidité.

.. image:: ./scratch_img/st88.png
   :alt: img

--------------

.. _4.7.3-LCD-1602-Module:

4.7.3 Module LCD 1602
^^^^^^^^^^^^^^^^^^^^^^

**Description :**

LCD 1602 possède une interface standard à 14 broches (sans rétroéclairage) ou 16 broches
(avec rétroéclairage), économisant les broches du MCU. Son affichage pilote
IC pour réaliser le contrôle I2C.

.. image:: ./scratch_img/cou72.png
   :alt: img

--------------

**Communication Série I2C :**

La communication I2C, connue entièrement sous le nom de Circuit Inter-Intégré (IIC) ou
Interface à Deux Fils (TWI), est un protocole de communication à double bus (un maître et un
esclave) couramment utilisé, qui est développé par Phillips
Semiconductor (acheté par US NXP Semiconductors).

Le plus grand avantage est que seulement deux fils complètent la transmission
de données, ce qui simplifie largement les circuits. Au total, le bus I2C peut
connecter 127 nœuds en parallèle, donc il supporte plusieurs maîtres et esclaves.

Généralement, l'alimentation externe n'est pas nécessaire pour les esclaves, car le bus I2C va
transmettre l'alimentation vers eux :

.. image:: ./scratch_img/cou75.png
   :alt: img

Le bus I2C transmet les données via une transmission de données 8 bits. Habituellement,
les données d'un octet sont composées de neuf signaux d'horloge, huit d'entre eux transmettent
les données et le dernier marque la fin de transmission.

De plus, le bus I2C supporte la transmission de données multi-octets en répétant le
processus ci-dessus continuellement.

Le protocole I2C consiste essentiellement en :

-  **Signal de démarrage** : Avant la transmission, l'expéditeur transmet un signal de démarrage
   pour informer le récepteur du point de départ.
-  **Adresse** : Elle notifie au récepteur à qui les données sont envoyées.
-  **Données** : Elles sont transmises un octet à la fois et bit par bit.
-  **Signal de fin** : Quand la transmission se termine, l'expéditeur termine les données avec
   un signal de fin pour informer le récepteur que le processus est terminé.

**Diagramme de Temporisation du Protocole Série :**

Pour plus de détails, veuillez visiter le site officiel :
https://www.nxp.com/

.. image:: ./scratch_img/cou76.png
   :alt: img

.. image:: ./scratch_img/cou77.png
   :alt: img

Nous vous fournissons un fichier de bibliothèque **Wire.h** sur Arduino pour le
protocole I2C, dans lequel les fonctions peuvent être directement appelées pour communiquer avec
les dispositifs I2C/TWI.

Pour les détails de la bibliothèque, veuillez vous référer à :

https://www.arduino.cc/reference/en/language/functions/communication/wire/

--------------

**Schéma de Câblage :**

**Connectez le LCD au BUS I2C comme montré ci-dessous.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj72.png
   :alt: img

--------------

**Code de Test :**

-  Initialisez l'adresse I2C du LCD et allumez son rétroéclairage.

   .. image:: ./scratch_img/st92.png
      :alt: img

-  Définissez la position du curseur LCD dans les axes X et Y (l'axe X affiche un
   maximum de 16 caractères, et l'axe Y affiche un maximum de 2
   colonnes).

   .. image:: ./scratch_img/st93.png
      :alt: img

-  Saisissez le contenu d'impression (Pas plus de 16 caractères, sinon il
   ne sera pas complet).

   .. image:: ./scratch_img/st94.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st95.png
   :alt: img

**Résultat du Test :**

LCD1602 allume son rétroéclairage et affiche "\ **HELLO WORLD 0**\ " et
"\ **HELLO WORLD 1**\ ".

.. image:: ./scratch_img/cou78.png
   :alt: img

--------------

.. _4.7.4-Fan-Module:

4.7.4 Module Ventilateur
^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

Le Moteur 130 est capable d'ajuster la vitesse via PWM. Dans le processus, deux broches sont
nécessaires pour être connectées pour le contrôle.

Le module convient à de multiples applications, telles que la dissipation thermique d'ordinateur
et la production industrielle. De plus, il est compact et
facile à installer, ce qui est très pratique.

.. image:: ./scratch_img/cou710.png
   :alt: img

--------------

**Schéma Électrique :**

.. image:: ./scratch_img/cou712.png
   :alt: img

--------------

**Schéma de Câblage :**

**Connectez le moteur à io18 et io19.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj73.png
   :alt: img

--------------

**Code de Test :**

-  Définissez la broche du ventilateur **INA**

   .. image:: ./scratch_img/st96.png
      :alt: img

-  Définissez l'état du niveau de puissance d'**INA**, qui détermine la direction de rotation
   du ventilateur.

   .. image:: ./scratch_img/st97.png
      :alt: img

-  Définissez la broche du ventilateur **INB**.

   .. image:: ./scratch_img/st98.png
      :alt: img

-  Définissez la sortie analogique à **INB**, qui décide de la vitesse de rotation.

   -  Quand INA est à l'état haut, plus la sortie analogique à INB est faible, plus
      le ventilateur tournera rapidement.

   -  Quand INA est à l'état bas, plus la sortie analogique à INB est grande, plus
      le ventilateur tournera rapidement.

      .. image:: ./scratch_img/st99.png
         :alt: img

**Résultat du Test :**

Le moteur 130 tourne alternativement à gauche et à droite toutes les 2 secondes.

.. image:: ./scratch_img/cou79.png
   :alt: img

\**NOTE : \*\*

**Des arrêts intermittents existent lors du changement de direction de rotation. Ils
empêchent un courant excessif au moment de l'inversion. Sinon, une
réinitialisation forcée peut se produire en raison d'une alimentation insuffisante sur la
carte de développement.**

--------------

.. _4.7.5-Temperature-Control-System:

4.7.5 Système de Contrôle de Température
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

Ici, nous lisons la valeur du capteur de température et d'humidité DHT11
via la communication monobus, et les valeurs seront affichées sur le
LCD. Si les valeurs dépassent le seuil défini, le ventilateur se mettra en marche pour
la déshumidification et le refroidissement pour protéger les animaux et les plantes dans la
ferme. Remarquablement, ce système est facile à installer avec de multiples
fonctions, telles que le contrôle de vitesse via PWM et la transmission de données par
monobus.

Dans l'ensemble, c'est un système pratique qui aide les agriculteurs à surveiller et contrôler
le statut en temps réel pour améliorer l'efficacité de production.

--------------

**Schéma de Câblage :**

-  **Connectez le capteur de température et d'humidité à io17.**
-  **Connectez le module moteur (ventilateur) à io18 et io19**
-  **Connectez LCD1602 au BUS I2C.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj74.png
   :alt: img

--------------

**Code de Test :**

Flux de Code :

.. image:: ./scratch_img/flo7.png
   :alt: img

Code :

-  Initialisez LCD pour définir une adresse, et effacez l'affichage. Allumez son
   rétroéclairage et définissez la position du curseur :

   .. image:: ./scratch_img/st100.png
      :alt: img

-  Initialisez le capteur DHT11 et choisissez une broche correspondante. Définissez
   deux variables comme valeurs de température et d'humidité.

   .. image:: ./scratch_img/st101.png
      :alt: img

-  Dans la boucle, assignez respectivement les valeurs détectées aux deux
   variables.

   .. image:: ./scratch_img/st102.png
      :alt: img

-  Affichez les valeurs sur LCD.

   .. image:: ./scratch_img/st103.png
      :alt: img

-  Déterminez la valeur de température et d'humidité. si la température est
   supérieure à 29° ou l'humidité dépasse 80, le ventilateur tournera.

   .. image:: ./scratch_img/st104.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st105.png
   :alt: img

**Résultat du Test :**

Quand la température atteint 29°C, le ventilateur se mettra en marche pour dissiper
la chaleur. Quand elle est inférieure à 29°C, le ventilateur s'éteindra (le ventilateur ne fait que
simuler la dissipation thermique, donc l'effet n'est pas bon), ce qui économise
l'énergie pour la ferme.

--------------

.. _4.7.6-FAQ:

4.7.6 FAQ
^^^^^^^^^

#Q : Le capteur de température et d'humidité est-il étanche ?

R : Non. Il détecte la température et l'humidité ambiantes (dans l'air), donc
veuillez ne pas le mettre dans l'eau.

--------------

#Q : La carte ESP32 se réinitialise quand le ventilateur tourne.

R : Quand le ventilateur tourne, plus de courant est requis que pour les autres capteurs, donc
la tension et le courant peuvent fluctuer dans le circuit. Surtout au
moment de l'inversion du ventilateur, les fluctuations peuvent être trop importantes, résultant en une
réinitialisation due à une tension et un courant extrêmement bas dans la carte de développement
ESP32.

--------------

.. _4.8-Project:-Soil-Humidity-Monitoring-System:

4.8 Projet : Système de Surveillance de l'Humidité du Sol
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

--------------

**Faites attention ! Ne laissez pas déborder l'eau des bassins en plastique dans
les expériences. Renverser de l'eau sur d'autres capteurs peut causer non seulement un court-circuit ou des modules hors service mais aussi une génération de chaleur et même une explosion. Soyez très prudent ! Surtout pour les utilisateurs plus jeunes, veuillez opérer avec vos parents. Pour garantir la sécurité, veuillez obéir aux directives et réglementations de sécurité.**

--------------

.. image:: ./scratch_img/cout8.png
   :alt: img

--------------

.. _4.8.1-Flow-Diagram:

4.8.1 Diagramme de Flux
^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230607161101154.png
   :alt: image-20230607161101154

--------------

.. _4.8.2-Soil-Humidity-Sensor:

4.8.2 Capteur d'Humidité du Sol
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

Les capteurs d'humidité du sol sont principalement utilisés pour mesurer la teneur en eau dans
le sol volumétrique, surveiller l'humidité du sol, irriguer les cultures et protéger
les forêts. Ce type de capteur est intégré dans le système d'irrigation agricole
pour fournir de l'eau régulièrement et efficacement, ce qui optimise
l'irrigation pour une meilleure croissance des plantes.

.. image:: ./scratch_img/cou81.png
   :alt: img

--------------

**Schéma Électrique :**

.. image:: ./scratch_img/couy81.png
   :alt: img

--------------

**Schéma de Câblage :**

**Connectez le capteur d'humidité du sol à io32.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj81.png
   :alt: img

--------------

**Code de Test :**

-  Initialisez le port série.

   .. image:: ./scratch_img/st106.png
      :alt: img

-  Imprimez la valeur du capteur lue.

   .. image:: ./scratch_img/st107.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st108.png
   :alt: img

**Résultat du Test :**

Ouvrez le moniteur série.

Touchez la zone de détection du capteur avec un doigt humide et la
valeur d'humidité actuellement détectée sera imprimée sur le moniteur (plage :
0~4095).

.. image:: ./scratch_img/st109.png
   :alt: img

--------------

.. _4.8.3-Soil-Humidity-Monitoring-System:

4.8.3 Système de Surveillance de l'Humidité du Sol
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Nous adoptons LCD1602 pour révéler la valeur en temps réel de la valeur d'humidité du sol.
Quand la valeur est inférieure à l'humidité minimale définie, le buzzer émettra
un son pour inciter les agriculteurs à l'irrigation.

**Schéma de Câblage :**

-  **Connectez le capteur d'humidité du sol à io32.**
-  **Connectez le buzzer à io16.**
-  **Connectez le LCD1602 au BUS I2C.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj82.png
   :alt: img

--------------

**Code de Test :**

Flux de Code :

.. image:: ./scratch_img/flo8.png
   :alt: img

Code :

-  Initialisez LCD et effacez son affichage. Allumez le rétroéclairage pour
   observer la valeur affichée.

   .. image:: ./scratch_img/st110.png
      :alt: img

-  Initialisez le port série et définissez une variable.

   .. image:: ./scratch_img/st111.png
      :alt: img

-  Lisez la valeur de la valeur d'humidité du sol et assignez-la à la
   variable. LCD montre la valeur.

   .. image:: ./scratch_img/st112.png
      :alt: img

-  Déterminez la valeur lue. Si elle est inférieure à 200, le buzzer
   alarmera.

   .. image:: ./scratch_img/st113.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st114.png
   :alt: img

**Résultat du Test :**

Quand la valeur détectée par le capteur d'humidité du sol est inférieure au
seuil défini, le buzzer émet un son pour alarmer.

--------------

.. _4.8.4-FAQ:

4.8.4 FAQ
^^^^^^^^^

Q : Le capteur d'humidité du sol est-il étanche ?

R : À l'exception de la zone de détection, le capteur n'est pas
étanche. Renverser de l'eau sur une autre zone peut résulter en un court-circuit.

--------------

.. _4.9-Project:-Water-Level-Monitoring-System:

4.9 Projet : Système de Surveillance du Niveau d'Eau
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

--------------

**Faites attention ! Ne laissez pas déborder l'eau des bassins en plastique dans
les expériences. Renverser de l'eau sur d'autres capteurs peut causer non seulement un court-circuit pour perturber les opérations normales mais aussi une génération de chaleur et même une explosion. Soyez très prudent ! Surtout pour les utilisateurs plus jeunes, veuillez
opérer avec vos parents. Pour garantir la sécurité, veuillez obéir aux directives et réglementations de sécurité.**

--------------

.. _4.9.1-Flow-Diagram:

4.9.1 Diagramme de Flux
^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230607165214387.png
   :alt: image-20230607165214387

--------------

.. _4.9.2-Water-Level-Sensor:

4.9.2 Capteur de Niveau d'Eau
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

Le capteur de niveau d'eau est facile à utiliser, portable et rentable. Il
intègre une série de lignes parallèles exposées pour mesurer le volume d'eau et de gouttelettes. Non seulement le capteur est plus petit et plus intelligent que
d'autres détecteurs d'eau, mais il présente également :

-  Transition fluide entre le volume d'eau et le volume analogique ;
-  Grande flexibilité. Le capteur produit des valeurs analogiques de base ;
-  Faible consommation d'énergie et haute sensibilité ;
-  Se connecte directement aux microprocesseurs ou circuits, et convient à
   diverses cartes de développement et contrôleurs, tels que les contrôleurs Arduino, STC et les microcontrôleurs AVR à puce unique.

.. image:: ./scratch_img/cou91.png
   :alt: img

--------------

**Schéma de Câblage :**

**Connectez le capteur de niveau d'eau à io33.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj91.png
   :alt: img

--------------

**Code de Test :**

.. image:: ./scratch_img/st115.png
   :alt: img

**Résultat du Test :**

Ouvrez le moniteur série.

Touchez la zone de détection du capteur avec un doigt humide et la
valeur actuellement détectée sera imprimée sur le moniteur (plage : 0~4095).

.. image:: ./scratch_img/st116.png
   :alt: img

--------------

.. _4.9.3-Water-Level-Monitoring-System:

4.9.3 Système de Surveillance du Niveau d'Eau
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Le système de surveillance du niveau d'eau supervise le changement du niveau d'eau
pour clarifier les problèmes à temps et prendre des mesures pour éviter les catastrophes. Il est
largement utilisé dans les projets de conservation de l'eau, le drainage urbain et
la surveillance environnementale.

**Schéma de Câblage :**

-  **Connectez le capteur de niveau d'eau à io33.**
-  **Connectez le buzzer à io16.**
-  **Connectez le LCD1602 au BUS I2C.**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj92.png
   :alt: img

--------------

**Code de Test :**

Flux de Code :

.. image:: ./scratch_img/flo9.png
   :alt: img

Code :

-  Initialisez le LCD et allumez son rétroéclairage ; effacez tout affichage et
   puis imprimez le niveau d'eau.

   .. image:: ./scratch_img/st117.png
      :alt: img

-  Définissez une variable comme le niveau d'eau détecté.

   .. image:: ./scratch_img/st118.png
      :alt: img

-  Lisez la valeur du capteur et affichez-la sur LCD.

   .. image:: ./scratch_img/st119.png
      :alt: img

-  Déterminez la valeur du niveau d'eau. Si elle est supérieure à 2000, le
   buzzer alarmera.

   .. image:: ./scratch_img/st120.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st121.png
   :alt: img

**Résultat du Test :**

LCD affiche la valeur en temps réel du niveau d'eau. Dans l'expérience, nous
couvrons la zone de détection avec de l'eau pour stimuler le niveau d'eau. Quand
la valeur détectée dépasse le seuil, le buzzer commence à alarmer.

--------------

.. _4.9.4-FAQ:

4.9.4 FAQ
^^^^^^^^^

Q : Le capteur de niveau d'eau est-il étanche ?

R : À l'exception de la zone de détection, le capteur n'est pas
étanche. Renverser de l'eau sur une autre zone peut résulter en un court-circuit.

--------------

.. _4.10-Project:-Auto-Irrigation-System:

4.10 Projet : Système d'Irrigation Automatique
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

--------------

**Faites attention ! Ne laissez pas déborder l'eau des bassins en plastique dans
les expériences. Renverser de l'eau sur d'autres capteurs peut causer non seulement un court-circuit pour perturber les opérations normales mais aussi une génération de chaleur et même une explosion. Soyez très prudent ! Surtout pour les utilisateurs plus jeunes, veuillez
opérer avec vos parents. Pour garantir la sécurité, veuillez obéir aux directives et réglementations de sécurité.**

--------------

Dans ce projet, nous stimulons l'irrigation via une pompe à eau contrôlée par
un module relais. De plus, nous déterminons également s'il y a de l'eau dans le
bassin grâce au capteur de niveau d'eau, et détectons l'humidité du sol par le capteur d'humidité du sol. De cette façon, le système sera plus intelligent dans
le contrôle de la pompe à eau.

.. image:: ./scratch_img/cout10.png
   :alt: img

--------------

.. _4.10.1-Flow-Diagram:

4.10.1 Diagramme de Flux
^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230607183214310.png
   :alt: image-20230607183214310

--------------

.. _4.10.2-Water-Pumping-System:

4.10.2 Système de Pompage d'Eau
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

Dans cette expérience, nous utilisons la carte de développement ESP32 pour allumer/éteindre la
pompe à eau par un module relais. Une pompe élève l'eau et transporte les liquides,
et est habituellement combinée avec un module relais en usage.

Ici, nous connectons le module relais et la pompe à la carte ESP32, et
programmons pour allumer ou éteindre à distance la pompe en commutant l'état
du relais. Pour comment, nous déterminons l'état du relais selon la
valeur de sortie du module ou un temps prédéfini.

--------------

**Module Relais :**

En usage, il est souvent utilisé dans la gestion de haute tension et courant de charge,
disons, moteurs, capteurs haute intensité et lumières haute puissance.

.. image:: ./scratch_img/cou101.png
   :alt: img

-  **Normalement Ouvert (NO) :** Cette broche est normalement ouverte, à moins qu'un signal soit
   reçu par la broche de signal du relais. Par conséquent, les broches communes sont
   déconnectées via la broche NC et connectées via la broche NO.

-  **Contact Commun (COM) :** Cette broche se connecte à d'autres modules, par
   exemple, pompe à eau.

   -  Pompe à Eau :

.. image:: ./scratch_img/cou1011.png
   :alt: img

-  **Normalement Fermé (NC) :** La broche NC est liée avec la broche COM pour former un
   circuit fermé. Elle utilise la carte ESP32 pour contrôler la fermeture et la
   déconnexion du module relais.

--------------

**Paramètres :**

-  Tension d'alimentation : 5V
-  Courant statique : 2mA
-  Tension de contact maximale : 250VAC/30VDC
-  Courant maximal : 10A

**Schéma Électrique :**

.. image:: ./scratch_img/couy101.png
   :alt: img

--------------

**Schéma de Câblage :**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj101.png
   :alt: img

--------------

**Code de Test :**

.. image:: ./scratch_img/st122.png
   :alt: img

**Résultat du Test :**

Après avoir téléchargé le code, l'appareil pompera l'eau une fois.

Dans cette expérience, la pompe à eau est automatisée, réduisant le temps et
les efforts d'opération manuelle et améliorant l'efficacité. Par conséquent, ce
système de pompage d'eau est largement utilisé dans la production agricole et le
traitement de l'eau.

--------------

.. _4.10.3-Auto-Irrigation-System:

4.10.3 Système d'Irrigation Automatique
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

**Description :**

Dans cette expérience, nous implémentons un système d'irrigation intelligent par un capteur d'humidité du sol, un capteur de niveau d'eau, un module relais et une pompe à eau.
Nous connectons les deux capteurs sur la carte de développement ESP32 et programmons pour
lire leurs valeurs de sortie pour contrôler le relais et la pompe à eau.

Si le sol est très sec, le relais se mettra en marche pour contrôler la pompe à eau
pour irriguer les plantes ; Et si le niveau d'eau est trop bas, la pompe à eau
ne pourra pas fonctionner, et le buzzer alarmera. De cette façon,
l'arrosage des plantes et le contrôle du niveau d'eau sont automatisés, ce qui augmente
l'efficacité de production et réduit le temps et les efforts des opérations
manuelles.

--------------

**Schéma de Câblage :**

-  **Connectez le module relais à io25 ; connectez sa broche NC au
   GND(noir) à io2.**
-  **Pompe à eau :**

   -  **Connectez le fil rouge au POWER 3V3 de la carte**
   -  **Connectez le fil noir(GND) à la broche COM du relais**

-  **Connectez le capteur d'humidité du sol à io32**
-  **Connectez le capteur de niveau d'eau à io33**

**Attention : Connectez le jaune à S(Signal), le rouge à V(Alimentation), et le noir à
GND. Ne les inversez pas !**

.. image:: ./scratch_img/couj102.png
   :alt: img

--------------

**Code de Test :**

Flux de Code :

.. image:: ./scratch_img/flo10.png
   :alt: img

Code :

-  Initialisez et effacez le LCD, allumez le rétroéclairage LCD. Définissez deux
   variables comme les valeurs de capteur détectées.

   .. image:: ./scratch_img/st123.png
      :alt: img

-  Assignez les deux valeurs de capteur lues à ces variables.

   .. image:: ./scratch_img/st124.png
      :alt: img

-  Affichez ces valeurs sur LCD.

   .. image:: ./scratch_img/st125.png
      :alt: img

-  Si la valeur du niveau d'eau est inférieure à 700 ou la valeur d'humidité du sol
   est inférieure à 1200, le buzzer alarmera.

   .. image:: ./scratch_img/st126.png
      :alt: img

-  Quand la valeur d'humidité du sol est inférieure à 1200 mais la valeur du niveau d'eau
   est supérieure à 700, la pompe à eau irriguera automatiquement
   la ferme.

   .. image:: ./scratch_img/st127.png
      :alt: img

Code complet :

.. image:: ./scratch_img/st128.png
   :alt: img

**Résultat du Test :**

.. image:: ./scratch_img/cou102.png
   :alt: img

-  LCD 1602 affichera les valeurs actuelles d'humidité du sol et de niveau d'eau. Quand l'humidité détectée est inférieure au seuil défini, cela
   implique que le sol devient aride, et l'irrigation commence
   automatiquement.
-  Quand le niveau d'eau détecté est inférieur au seuil défini, le
   système de pompage d'eau ne fonctionne pas, et le buzzer alarme pour notifier
   que l'eau est insuffisante.
-  Appuyez sur le bouton pour arrêter l'alarme.

--------------

**En résumé, nous avons réalisé un système d'irrigation automatique analogique dans ce
projet, qui contrôle intelligemment l'allumage et l'extinction de la pompe à eau
selon le niveau d'eau. En application, ce système va habituellement pour
la production domestique et agricole.**

--------------

.. _4.10.4-FAQ:

4.10.4 FAQ
^^^^^^^^^^

Q : Les modules sont-ils étanches ?

R : Le module relais ne l'est pas, mais la pompe à eau l'est. Le grade d'étanchéité
de la pompe à eau est IP68.

--------------

Q : La carte ESP32 se réinitialise quand la pompe à eau fonctionne.

R : Quand la pompe à eau fonctionne, plus de courant est requis que pour les autres modules,
donc la tension et le courant peuvent fluctuer dans le circuit. Parfois
les fluctuations peuvent être trop importantes, résultant en une réinitialisation due à une tension et un courant extrêmement bas dans la carte de développement
ESP32.

Quand vous opérez la pompe à eau, veuillez suivre l'exemple de code :

.. image:: ./scratch_img/st127.png
   :alt: img

--------------

Q : Échec de pomper l'eau ?

R : Plusieurs opérations de pompage sont requises pour remplir la pompe à eau avant
de l'utiliser. Ces pompages initiaux ne tirent pas réellement l'eau, mais pour
introduire suffisamment d'eau dans la pompe. Seulement après que la pompe soit pleine
l'eau peut être évacuée. Donc nous sommes d'abord pour remplir, pas pomper.

--------------

.. _4.11-Project:-WIFI-Control-Smart-Farm:

4.11 Projet : Ferme Intelligente Contrôlée par WIFI
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

--------------

**Faites attention ! Ne laissez pas déborder l'eau des bassins en plastique dans
les expériences. Renverser de l'eau sur d'autres capteurs peut causer un court-circuit
ou des modules hors service. Si les batteries sont mouillées, même une explosion peut
se produire. Soyez très prudent ! Pour les utilisateurs plus jeunes, veuillez opérer avec vos parents. Pour garantir la sécurité, veuillez obéir aux directives et réglementations de sécurité.**

--------------

.. image:: ./scratch_img/cout11.png
   :alt: img

--------------

.. _4.11.1-Flow-Diagram:

4.11.1 Diagramme de Flux
^^^^^^^^^^^^^^^^^^^^^^^^^

.. image:: ./scratch_img/image-20230608105334194.png
   :alt: image-20230608105334194

--------------

