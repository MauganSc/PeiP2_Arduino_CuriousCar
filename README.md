![Polytech](http://www.polytechnice.fr/jahia/jsp/jahia/templates/inc/img/polytech_nice-sophia.png)

Ce projet est réalisé dans le cadre de la formation de prépa intégrée de Polytech'NiceSophia.

# Projet Arduino : Curious Car (en cours de développement)
Curious Car est une voiture radiocommandée qu'on peut aussi contrôler par Wi-Fi depuis un ordinateur ou un smartphone. Une caméra web sans fil accrochée sur la voiture permet de voir où va la voiture. Les capteurs de distance devant et derrière permettent à la voiture d'éviter des obstacles. Un mini haut-parleur sur la voiture permet de transmettre des messages audio prédéfinis. On peut aussi allumer et éteindre les lumières de la voiture. Curious Car fait un bel exemple de robot de téléprésence.

Etape 1 : Acquérir le matériel nécessaire
-
| Elément | Quantité | Image |
|---------|:--------:|-------|
| Voiture radiocommandée | x1 | <img src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Voiture%20radiocommand%C3%A9e.png" alt="Voiture radiocommandée" height="100"> |
| Carte Arduino | x1 | <img alt="ATmega328P-XMINI" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Carte%20Arduino%20ATmega328P-XMINI.png" height="100"> |
| Carte Node Mcu 1.0 | x1 | <img alt="Carte Node Mcu 1.0" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Carte%20Wi-Fi%20Node%20Mcu%201.0.png" height="100"> |
| Cable USB micro | x1 | <img alt="Cable USB micro" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Cable%20USB%20micro.png" height="100"> |
| Caméra IP | x1 | <img alt="Caméra IP" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Cam%C3%A9ra%20IP.png" height="100"> |
| Mini haut-parleur | x1 | <img alt="Mini haut-parleur" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Mini%20haut-parleur.png" height="100"> |
| Module carte SD | x1 | <img alt="Module carte SD" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Module%20carte%20SD.png" height="100"> |
| Carte SD | x1 | <img alt="Carte SD" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Carte%20SD.png" height="100"> |
| Capteurs de distance HC-SR04 | x2 | <img alt="HC-SR04" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Capteurs%20de%20distance%20HC-SR04.png" height="100"> |
| LED RGB | x2 | <img alt="LED RGB" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/LED%20RGB.png" height="100"> |
| LED rouge | x1 | <img alt="LED rouge" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/LED%20rouge.png" height="100"> |
| LED bleue | x1 | <img alt="LED bleue" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/LED%20bleue.png" height="100"> |
| Résistances 220 Ohm | x8 | <img alt="220 Ohm" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/R%C3%A9sistances%20220%20Ohm.png" height="100"> |
| Batterie rechargeable 7.2 V | x1 | <img alt="Batterie rechargeable 7.2 V" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Batterie%20rechargeable%207,2%20Volts.png" height="100"> |
| Carte de test | x1 | <img alt="Carte de test" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Carte%20de%20test.jpg" height="100"> |
| Fils Arduino | | <img alt="Fils Arduino" src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Fils%20Arduino.png" height="100"> |

Et bien sûr on aura besoin d'un ordi pour programmer les cartes Arduino et Node Mcu.

Etape 2 : environnement informatique
-
On installe [Arduino IDE](https://www.arduino.cc/en/main/software) sur l'ordinateur si ce n'est pas encore fait. Cet environnement va nous permettre de programmer les cartes Arduino et Node Mcu 1.0.

Ensuite, il faut installer le driver USB pour pouvoir utiliser votre carte Arduino. Dans ce projet, j'utilise la carte [ATmega328P Xplained MINI](https://www.microchip.com/developmenttools/productdetails.aspx?partno=atmega328p-xmini), donc j'ai installé le driver correspondant qu'on peut trouver sur cette [page](http://users.polytech.unice.fr/~pmasson/Enseignement-arduino.htm).

Pour pouvoir travailler avec [Node Mcu 1.0](http://www.hotmcu.com/nodemcu-lua-wifi-board-based-on-esp8266-cp2102-module-p-265.html), on doit installer le driver [USB to UART](https://www.silabs.com/products/development-tools/software/usb-to-uart-bridge-vcp-drivers).

Etape 3 : connexion entre l'ordinateur et la carte Wi-Fi + ajout des diodes
-
On connecte la carte Node Mcu 1.0 à l'ordinateur. On lance Arduino IDE. On va dans le menu "File > Preferences". Dans "Additional Boards Managers URLs", on ajoute l'url suivante :

<img src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Preferences.png" alt="Preferences" width="600">

Dans le menu "Tools > Board > Boards Manager", on choisit le paquétage "esp8266" et on l'installe.

<img src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Boards%20Manager.png" alt="Boards Manager" width="600">

Après l'installation de ce paquétage, on relance Arduino IDE. Et maintenant dans le menu "Tools > Board" on peut trouver notre carte Node Mcu 1.0 pour travailler avec.

Remarque : dans le menu "Tools > Upload Speed", il faut bien vérifier qu'on a "9600", car c'est la vitesse de téléchargement qui correspond à cette carte, comme c'est marqué sur sa face arrière :

<img src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Node%20Mcu%20face%20arri%C3%A8re.JPG" alt="Node Mcu face arrière">

(à compléter)

Etape 3 : connexion entre la carte Wi-Fi et l'Arduino + ajout des capteurs de distance
-
(à compléter)

Etape 4 : connexion du circuit moteur à l'Arduino + test
-
A l'intérieur de la voiture, on identifie les I/O qui déclenchent les mouvements de la voiture.

Dans mon cas c'est facile car ces I/O sont marqués sur la carte :

<img src="https://github.com/Livelinndy/PeiP2_Arduino_CuriousCar/blob/master/images/Circuit%20moteur.JPG" alt="Circuit moteur">

L - left
R - right
F - forward
B - backward

Dans d'autres cas, il faut chercher le datasheet du module de transmission radio.

(à compléter)

Etape 5 : connexion du haut-parleur et du module carte SD à l'Arduino + test
-
(à compléter)

Etape 6 : optimisation du code
-
(à compléter)

Etape 7 : circuit d'alimentation
-
(à compléter)

Etape 8 : assemblage de la voiture
-
(à compléter)

Etape 9 : caméra
-
(à compléter)

Etape 10 : PROFIT!!!
-
(à compléter)
