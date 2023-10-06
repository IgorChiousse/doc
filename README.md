# TOUTES LES COMMANDES ET PROCESS 

## DOCKER

### Création de container avec copie d'image 

En ouvrant dans le terminal powershell C:\ docker container run -it alpine:latest  
Nous nous retrouvont dans le container au niveau de la racine root /#: 


### Pour entrer dans le container une fois sortie

C:/ docker start ID(container) 
C:/ docker exec -it ID bash ou sh


### Process de lancement et installation d application  

C:\ docker container run -it alpine:latest
C:\ docker ps -a (verification de tous les containers et images crées) 
C:\ docker contenaire exec -it ID bash ou sh 
root@:/# apt update -y && apt upgrade -y && apt install vim -y
root@:/# mkdir (création de fichier) home/chemin/de/dossier
root@:/# touch (création de fichier) home/chemin/ou/doit/etre/lefichier
root@:/# vim home/chemin/du/fichier/a/réécrire
dans vim appuis sur I pour incerer du texte 
echap puis :wq pour enregistrer :q pour sortir sans enregistrer


### Création de votre image a partir d'une autre image (ubuntu pour l'exemple)

:docker container run -it ubuntu:latest (le container est créé sans etre renomé avec l'image ubuntu)
root@:/# on met tous les apt up et install puis on sort du container 
:docker container ls -a (pour prendre l ID du container)
:docker commit ID nom de l'image voulu exemple: docker commit 123 doudou
l'image avec toutes les instalations sont dans doudou que nous pouvons utiliser pour les containers voulu


### Création de volume (pour sauvegarder un fichier et mettre en relation avec d'autre container)

:docker volume create name(nom du volume)

_pour safe un fichier du container dans le volume créé_
:docker container run -v nom-du-volume:/home/chemin/du/fichier


### Création d'un network

_La création d'un network pour isoler des containers a l'interieur_
:docker network create name(nom du network)
:docker container run -it --name nom-du-cont image:latest
:docker network connect nom-du-network nom-du-container

_Pour regarder les caracteristiques du network_
:docker network inspect nom-du-network


### Faire un script pour executer automatiquement dans un container

créer un dossier sur l'OS(windows) et ouvrir avec VS Code
créer un fichier en .sh
mettre toutes les commandes a executer ex: apt update -y apt upgrade -y apt install vim -y en passant a la ligne pour chaque commande

_pour executer un script dans un container_
docker cp C:/Users/user/chemin/du-fichier-script ID(container):/home/chemin/donner-au-fichier-script 
:docker start ID(container)
:docker exec -it ID bash /home/chemin/donner-au-fichier-script

