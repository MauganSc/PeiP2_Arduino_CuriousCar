![Polytech](http://www.polytechnice.fr/jahia/jsp/jahia/templates/inc/img/polytech_nice-sophia.png)

Ce projet est réalisé dans le cadre de la formation de prépa intégrée de Polytech'NiceSophia.

# Projet Arduino : Curious Car (en cours de développement)
Curious Car est une petite voiture controllable par Wi-Fi via un ordinateur ou un smartphone avec caméra embarquée. Cette caméra nous permet de voir où va la voiture et d'observer ce qui se passe autour. Les capteurs de distance devant et derrière la voiture permettent d'éviter des obstacles en arrêtant la voiture quand l'obstacle est trop près. Un mini haut-parleur sur la voiture permet de jouer des messages audio prédéfinis. On peut aussi allumer et éteindre les lumières et le clignottant de la voiture. Curious Car fait un bel exemple de robot de téléprésence.

On va voir en détail toutes les étapes de conception de Curious Car.

Etape 1 : Acquérir le matériel nécessaire
-
Après avoir défini les objectifs du projet et toutes les fonctionnalités voulues, j'ai commencé par acquérir le matériel nécessaire pour réaliser le projet. Bien sûr, je n'avais pas tout le matériel au début et j'avançais les parties du projet avec le matériel que j'avais déjà en attendant que le reste arrive.

Voici la liste complète du matériel utilisé :

<table style="text-align: center;">
  <tr>
    <td>
      <img src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Voiture%20radiocommand%C3%A9e.png" alt="Voiture radiocommandée" height="100">
      <br>Voiture radiocommandée (x1)<br>Le support
    </td>
    <td>
      <img alt="ATmega328P-XMINI" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Carte%20Arduino%20ATmega328P-XMINI.png" height="100">
      <br>Carte Arduino (x1)<br>Gère le fonctionnement du système
    </td>
    <td>
      <img alt="Carte Node Mcu 1.0" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Carte%20Wi-Fi%20Node%20Mcu%201.0.png" height="100">
      <br>Carte Node Mcu 1.0 (x1)<br>Assure la connexion Wi-Fi
    </td>
  </tr>
  <tr>
    <td>
      <img alt="Caméra IP" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Cam%C3%A9ra%20IP.png" height="100">
      <br>Caméra IP (x1)<br>Transmet la vidéo via Wi-Fi
    </td>
    <td>
      <img alt="Mini haut-parleur" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Mini%20haut-parleur.png" height="100">
      <br>Mini haut-parleur (x1)<br>Joue les messages audio
    </td>
    <td>
      <img alt="Module carte micro SD" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Module%20carte%20SD.png" height="100">
      <br>Module carte micro SD (x1)<br>Ressort les messages audio du mémoire
    </td>
  </tr>
  <tr>
    <td>
      <img alt="HC-SR04" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Capteurs%20de%20distance%20HC-SR04.png" height="100">
      <br>Capteurs de distance HC-SR04 (x2)<br>Assurent l'évasion des obstacles
    </td>
    <td>
      <br>Pilote moteur L293D (x1)<br>Assure le mouvement de la voiture
    </td>
    <td>
      <img alt="Carte SD" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Carte%20SD.png" height="100">
      <br>Carte micro SD (x2)<br>Stocke les messages audio et les vidéos
    </td>
  </tr>
  <tr>
    <td>
      <img alt="LED rouge" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/LED%20rouge.png" height="100">
      <br>LED rouge (x1)<br>Pour le clignottant
    </td>
    <td>
      <img alt="LED bleue" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/LED%20bleue.png" height="100">
      <br>LED bleue (x1)<br>Pour le clignottant
    </td>
    <td>
      <img alt="LED RGB" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/LED%20RGB.png" height="100">
      <br>LED RGB (x2)<br>Pour les lumières de devant
    </td>
  </tr>
  <tr>
    <td>
      <img alt="220 Ohm" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/R%C3%A9sistances%20220%20Ohm.png" height="100">
      <br>Résistances 220 Ohm (x8)<br>Pour les diodes
    </td>
    <td>
      <img alt="Carte de test" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Carte%20de%20test.jpg" height="100">
      <br>Carte de test 400 pts (x1)<br>Pour ne pas souder la carte Wi-Fi
    </td>
    <td>
      <br>Batterie rechargeable 9 V (x1)<br>Pour alimenter le système
    </td>
  </tr>
  <tr>
    <td>
      <img alt="Cable USB micro" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Cable%20USB%20micro.png" height="100">
      <br>Cable USB micro (x1)<br>Pour télécharger les programmes sur l'Arduino et la carte Wi-Fi
    </td>
    <td>
      <img alt="Fils Arduino" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Fils%20Arduino.png" height="100">
      <br>Fils<br>Pour réaliser le câblage
    </td>
    <td>
        <br>Adaptateur pour la batterie 9 V
    </td>
  </tr>
</table>

Et bien sûr on aura besoin d'un ordi pour programmer les cartes Arduino et Node Mcu.

Etape 2 : Préparer l'environnement informatique
-
On installe [Arduino IDE](https://www.arduino.cc/en/main/software) sur l'ordinateur si ce n'est pas encore fait. Cet environnement va nous permettre de programmer les cartes Arduino et Node Mcu 1.0.

Ensuite, il faut installer le driver USB pour pouvoir utiliser votre carte Arduino. Dans ce projet, j'utilise la carte [ATmega328P Xplained MINI](https://www.microchip.com/developmenttools/productdetails.aspx?partno=atmega328p-xmini), donc j'ai installé le driver correspondant qu'on peut trouver sur cette [page](http://users.polytech.unice.fr/~pmasson/Enseignement-arduino.htm).

Pour pouvoir travailler avec [Node Mcu 1.0](http://www.hotmcu.com/nodemcu-lua-wifi-board-based-on-esp8266-cp2102-module-p-265.html), on doit installer le driver [USB to UART](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers).

Maintenant, il va falloir installer le paquétage nous permettant de programmer la carte Wi-Fi.

On connecte la carte Node Mcu 1.0 à l'ordinateur. On lance Arduino IDE. On va dans le menu "File > Preferences". Dans "Additional Boards Managers URLs", on ajoute l'url suivante :

<img src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Preferences.png" alt="Preferences" width="600">

Dans le menu "Tools > Board > Boards Manager", on choisit le paquétage "esp8266" et on l'installe.

<img src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Boards%20Manager.png" alt="Boards Manager" width="600">

Après l'installation de ce paquétage, on relance Arduino IDE. Et finalement dans le menu "Tools > Board" on peut trouver notre carte Node Mcu 1.0 pour travailler avec.

Remarque : avant de télécharger un programme sur Node Mcu 1.0, il faut bien vérifier que dans le menu "Tools > Upload Speed" on a "9600", car c'est la vitesse de téléchargement qui correspond à cette carte, comme c'est marqué sur sa face arrière :

<img src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Node%20Mcu%20face%20arri%C3%A8re.JPG" alt="Node Mcu face arrière">

Une fois l'environnement informatique est préparé, on peut passer aux étapes suivantes où on va réaliser le montage et la programmation du système.

Par la suite, on va réaliser séparement chaqune des fonctionnalités prévues, et à la fin on va les mettre ensemble.

Etape 3 : Lumières
-
On commence par le plus facile : les lumières. Cette étape va aussi nous permettre de tester le fonctionnement de la carte Node Mcu 1.0.

(à compléter)

Etape 4 : Mouvement
-
J'ai décidé d'enlever la carte qui était à l'intérieur de la voiture car elle prenait trop de place et je n'allais pas me servir de la connexion radio 27 MHz qu'elle permettait. J'ai décidé de commander les moteurs directement par l'Arduino à l'aide d'un pilote moteur L293D.

(à compléter)

Etape 5 : Evasion d'obstacles
-
L'évasion d'obstacles s'éffectue par deux capteurs de distance HC-SR04, devant et derrière. Ils sont branchés sur l'Arduino, et comme les moteurs sont aussi branchés sur l'Arduino il n'est pas difficile de programmer l'arrêt de la voiture quand elle est trop proche d'un obstacle.

(à compléter)

Etape 6 : Caméra
-
(à compléter)

Etape 7 : Haut-parleur (optionnel, s'il y a de la place)
-
(à compléter)

Etape 8 : Alimentation
-
(à compléter)

Etape 9 : Optimisation
-
(à compléter)

Etape 10 : PROFIT!!!
-
Résultat final. Des essais.

(à compléter)
