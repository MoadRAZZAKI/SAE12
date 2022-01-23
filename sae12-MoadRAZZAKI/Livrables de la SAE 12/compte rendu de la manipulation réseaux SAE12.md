<center> <h1 style="color:#55DCC0";>Compte rendu SAE 13 Partie minpulation :</h1> </center>
<br/>

## <span style="color:#7DF617"> *Sommaire :* </span>
<br/>

[1.   Description de la manipulation](#-description--)

[2.   Schéma du réseau simple qui permet la communication entre les postes](#-shéma-du-réseau-simple-qui-permet-la-communication-entre-deux-postes--)

[3. commandes utilisées pour réaliser cette manipulation](#-commandes-utilisés-pour-réaliser-cette-manipulation--) 

<br/>

-----

<br/>

## <span style="color:#FF4E4E"> *Description :* </span>

<br/>


>Il s'agit d'une maquette que l'on doit réaliser afin de montrer au CTO de notre entreprise qu'on est câpable de faire un schéma réseau pour chaque salle et que l'on peut gérer la communication entre deux postes, cette manipulation va nous permettre aussi d'enrichir nos connaissances en réseaux ainsi que de développer nos compétances en ce domaine et améliorer nos capacités de compréhension en faisant des recherches sur les notions réseaux qu'on comprends pas. 

<br/>

 ##  <span style="color:#FF4E4E"> *Shéma du réseau simple qui permet la communication entre deux postes :* </span>

<br/>

<img src="captures/schéma de la maquette.png" >

<br/>

**Les équipements informatiques utilisés** : 2 ordinateurs, 2 switchs ( un switch qui permet la connexion entre les deux ordinateurs et l'autre celui de la salle qui nous connecte au routeur de l'iut ), 2 routeurs .
 
 <br/>
<br/>

**Les adresses ip utilisés pour les deux pc sont** : 192.168.88.249/24 pour le premier PC et 192.168.88.247/24 pour le deuxième , ensuite pour le routeur j'ai utilisé l'adresse 192.168.88.254/24 dans le premier réseau en vert , et l'adresse 10.205.0.179/16 dans le deuxième réseau en bleu et une passerelle par défaut via le routeur de l'iut. 


 ##  <span style="color:#FF4E4E"> *Commandes utilisés pour réaliser cette manipulation :* </span>
 
 <br/>

  premiérement, il faut brancher le routeur à la goulotte et ensuite le switch au routeur , dans ce  switch on doit brancher les deux PC .
 ### **les paramètres de la carte réseau du deuxième PC deuxième PC :**

  pour afficher les propriétés de ma carte réseau sous windows j'ai utilisé la commande **ipconfig /all** :

  <br/>

   <img src="captures/capture 3.png" >

<br/>

> comme on peut le remarquer ce pc est bien connecté à la passerelle **192.168.88.1/24** ( passerelle par défaut )

<br/> 

  sur le pc numéro 1 on va utilisé la commande **ip a show eno1** sous Linux pour voir les propriétés de sa carte réseau :

  <br/>

  <img src="captures/capture1 (1).png" >

  et pour afficher les deux adresses du routeur, on tape la commande **ip address print** sur le terminal du routeur MicroTik :
  
  <br/>

  <img src="captures/capture6.png" >
  
  <br/>

  on remarque que notre routeur a deux adresses IP, une le permet de jouer le rôle de la passerelle dans le premier réseau, et la deuxième le permet de communiquer avec le deuxième réseaux, il relie alors le réseau vert à internet.

  <br/>


ensuite, pour vérifier la connexion entre les deux PC je vais essayer d'envoyer des requêtes ICMP d'un pc vers l'autre en utilisant la commandes PING sur windows :

<br/>

**du premier PC vers le deuxième :**

<br/>

  <img src="captures/capture4.png" >

  on remarque que tout les paquets envoyés du premier PC ont bien été 
reçu par le deuxième PC.

<br/>

**du deuxième PC vers le premier :**

<br/>

  <img src="captures/capture 1.png" >

<br/>

On va essayer ensuite de déterminer l'itinéraire vers le site www.google.fr en utilisant la commande **tracert** sur windows, cette commande tente d'effectuer le traçage de la route qu'un paquet IP suit pour accéder à un hôte Internet, en lançant des paquets sonde UDP de courte durée de vie , puis en guettant une réponse ICMP TIME_EXCEEDED provenant des passerelles qui se trouvent sur la route. 
Les sondes sont lancées avec une valeur égale à 1 TTL, qui est augmentée d'un TTL à chaque fois jusqu'à ce qu'un message ICMP PORT_UNREACHABLE soit généré. Le message ICMP PORT_UNREACHABLE indique si l'hôte a été localisé ou si la commande a atteint le nombre maximal de bonds autorisés pour la fonction de trace.

<br/>

<img src="captures/capture 2.png" >

<br/>

de même sur Linux on peut tracer la route d'un paquet IP en utilisant la commande **mtr www.google.fr**:

<br/>

<img src="captures/capture3.png" >

et enfin, pour s'assuerer qu'on a internet sur les deux PC on peut utiliser la commande **PING** :

<span style="color:#38D2D0">**sortie de la commande sur le terminal :**</span>

<br/>

<img src="captures/capture2.png">

<br/>

<center><p>2022 &copy; Moad RAZZAKI -<span style="color:#3DFF05"> Tous droits réservés</span></p></center>