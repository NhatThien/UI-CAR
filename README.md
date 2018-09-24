# Guide des outils de développement

# Pré-requis

## Installer nodejs
Installer nodejs sur Raspberry Pi si cela n'est pas fait.

```
curl -sL https://deb.nodesource.com/setup_8.x | sudo -E bash -
sudo apt-get install -y nodejs
node -v
```

## Initialiser interface de CAN
Initialiser CAN interface en suivant l'instruction suivant:
https://copperhilltech.com/pican2-controller-area-network-can-interface-for-raspberry-pi/
La communication entre serveur nodejs et le CAN est établi sur le **can0**

# Architecture de la plateforme
L'architecture logicielle du système est représentée sur la gure 1. Le server nodejs sont
exécutés sur la Raspberry Pi. L'interface graphique de monitoring est exécutée sur un PC
distant. La communication entre le moniteur et le système de CAN passe par le serveur nodejs
via le WiFi IOT. La communication entre le CAN et app.js est assurée par socketcan extension
de nodejs.

# Mise en place d'un terminal distant sur la Raspberry Pi
Pour se connecter à la Raspberry Pi, vous aurez besoin de créer un accès via ssh. Pour cela,
depuis un PC d'une salle informatique utilisez la commande :

```
ssh pi@10.105.1.x
```

avec x le numéro sur le boitier de la Raspberry Pi.
Le mot de passe est : insa.

# Exécution et installation du serveur nodejs
Normalement, vous n'aurez pas à congurer et à lancer manuellement le serveur nodejs.
Sur chaque Raspberry Pi doit être installé un répertoire UI-CAR contenant l'ensemble de
l'application du serveur. Si besoin, pour lancer nodejs manuellement, il faut commencer par
se connecter à la Raspberry Pi, puis aller dans le répertoire UI-CAR et lancer la commande

```
node app.js
(ou simplement ./app.js).
```

Si le répertoire n'existe pas, il faut récupérer le code sur github en lançant la commande

```
git clone https://github.com/daihitsuji/UI-CAR.git
```

puis installer les dépendances en lançant depuis le répertoire UI-CAR la commande :

```
npm install save
```


