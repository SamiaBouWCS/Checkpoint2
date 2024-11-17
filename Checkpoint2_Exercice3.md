## Exercice 3 : Vérification d'une infrastructure réseau 

### b- Découverte du réseau
**Q.3.1 Quel est le matériel réseau A ?** Le matériel réseau A est un switch.
**Quel est son rôle sur ce schéma vis-à-vis des ordinateurs ?**
Le rôle du switch est de recevoir du routeur du réseau B des données sous forme de paquets et de 
déterminer où ces paquets doivent être envoyés en fonction des adresses MAC des ordinateurs de manière intelligente et efficace tout en réduisant les collisions.

**Q.3.2 Quel est le matériel réseau B ?** Le matériel du réseau B est un routeur.
Quel est son rôle pour le réseau 10.10.0.0/16 ?

**Q.3.3 Que signifie f0/0 et g1/0 sur l’élément B ?**
- f0/0 signifie que c'est l'interface physique FastEthernet qui fonctionne à une vitesse de 100 Mbps (avec le 0 en numéro de slot et le second 0 en numéro de l'interface.) 
- g1/0 signifie que c'est l'interface physique GigaEthernet de type Gigabit Ethernet qui fonctionne à une vitesse de 1Gbps (avec le 1 en numéro de slot et le second 0 en numéro de l'interface.)  

**Q.3.4 Pour l'ordinateur PC2, que représente /16 dans son adresse IP ?** (@IP : 10.11.80.2/16)
Le /16 représente le masque de sous-réseau de 255.255.0.0. 
Ce qui signifie que la partie réseau de l'adresse IP 10.11.80.2 va couvrir les deux premiers octets (10.11), et les deux derniers octets (80.2) seront utilisés pour adresser des hôtes dans ce réseau.
Le réseau 10.11.0.0/16 pourrait donc contenir des adresses IP allant de 10.11.0.1 à 10.11.255.254 (ce qui donne 65 536 adresses possibles pour les hôtes).

**Q.3.5 Pour ce même ordinateur, que représente l'adresse 10.10.255.254 ?**
L'adresse 10.10.255.254 appartient au réseau 10.10.0.0/16 donc pas le même réseau que le PC2.

### c- Etude théorique

**Q.3.6 Pour les ordinateurs PC1, PC2, et PC5 donne :**
L'adresse de réseau, la première adresse disponible, la dernière adresse disponible, l'adresse de diffusion

Adressage | PC1 10.10.4.1/16 | PC2 10.11.80.2/16 | PC5 10.10.4.7/15
 :--- | :---: | :---: | :---: 
adresse de réseau | 10.10.0.0 | 10.11.0.0 | 10.10.0.0
première adresse disponible | 10.10.0.1 | 10.11.0.1 | 10.10.0.1
dernière adresse disponible | 10.10.255.254 | 10.11.255.254 | 10.11.255.254
adresse de diffusion | 10.10.255.255 | 10.11.255.255 | 10.11.255.255

**Q.3.7 En t'aidant des informations que tu as fourni à la question 3.6, et à l'aide de tes connaissances, indique parmi tous les ordinateurs du schéma, lesquels vont pouvoir communiquer entre-eux.**
Les ordinateurs qui vont pouvoir communiquer entre eux sont le PC1, le PC3, le PC4 et le PC5. 

**Q.3.8 De même, indique ceux qui vont pouvoir atteindre le réseau 172.16.5.0/24.**
Les cinq ordinateurs vont pouvoir atteindre le réseau 172.16.5.0/24. 

**Q.3.9 Quel incidence y-a-t'il pour les ordinateurs PC2 et PC3 si on interverti leur ports de connexion sur le matériel A ?**
Il y aura un changement d'adresse mac mais pas des adresses ip, ils ne pourront pas communiquer et créer un impact de sécurités et donc affecter la communication entre les ordinateurs. 

**Q.3.10 On souhaite mettre la configuration IP des ordinateurs en dynamique. Quelles sont les modifications possible ?**
Les modifications possibles sont d'ajouter et paramétrer un serveur DHCP sur le réseau ainsi que  d'activer les adresses ip des ordinateurs en DHCP.

### d. Analyse de trames
**Fichier 1 :**
**Q.3.11 Sur le paquet N°5, quelle est l'adresse mac du matériel qui initialise la communication ? Déduis-en le nom du matériel.**
L'adresse mac du matériel qui initialise la communication est : 00:50:79:66:68:00 correspondant au nom du matériel : PC1.  

**Q.3.12 Est-ce que la communication enregistrée dans cette capture a réussi ? Si oui, indique entre quels matériels, si non indique pourquoi cela n'a pas fonctionné.**
La communication enregistrée dans cette capture a bien réussi et il s'agit d'un ping entre le PC1 et le PC2. 

**Q.3.13 Dans cette capture, à quel matériel correspond le request et le reply ? Donne le nom, l'adresse IP, et l'adresse mac de chaque materiel.**

Le request et le reply correspondent aux informations dans le tableau ci-dessous : 

| PC | PC1 | PC2 |
| :--- | :----: | :----: |
| MAC |  00:50:79:66:68:00  | 00:50:79:66:68:03  |
| IP | 10.10.4.1  | 10.10.4.2  |

**Q.3.14 Dans le paquet N°2, quel est le protocole encapsulé ? Quel est son rôle ?**
Dans le paquet n°2 le protocole encapsulé est le protocole ARP. Son rôle est de résoudre des IP à des adresses MACS 

**Q.3.15 Quels ont été les rôles des matériels A et B dans cette communication ?**

Le matériel B n'a pas de rôle.
Le matériel A diffuse la requête ARP sur tous le réseau, puis redirige la réponse de PC4 vers PC1

**Fichier 2 :**

**Q.3.16 Dans cette trame, qui initialise la communication ? Donne l'adresse IP ainsi que le nom du matériel.**
Celui qui initialise la communication est le PC3 ayant pour adresse ip 10.10.80.3.

**Q.3.17 Quel est le protocole encapsulé ? Quel est son rôle ?**
Le protocole encapsulé est une requête ping. Son rôle est d'attendre une réponse afin de vérifier si l'hôte interrogé est joignable.

**Q.3.18 Est-ce que cette communication a réussi ? Si oui, indique entre quels matériel, si non indique pourquoi cela n'a pas fonctionné.**
La communication n'a pas réussie. La cible est dans un autre réseau logique même si physiquement c'est le même réseau.

**Q.3.19 Explique la ligne du paquet N° 2**
C'est une réponse de la passerelle du routeur dans le réseau local. La ping a tenté par défaut de sortir par cette passerelle 
pour chercher un potentiel 10.11.80.2 mais le routeur ne connaissant pas la route vers cette adresse IP lui a répondu que la destination n'était pas atteignable.

**Q.3.20 Quels ont été les rôles des matériels A et B ?**
Le rôle du switch  est de transmettre les paquets dans un même réseau ce qui n'est pas le cas. Donc il n'a eu aucun rôle.
Le rôle du routeur est de transmettre les paquets entre différents réseau. Il a donc tenté sans même connaitre le chemin vers le réseau 10.11.0.0.16.

**Fichier 3 :**

**Q.3.21 Dans cette trame, donne les noms et les adresses IP des matériels sources et destination.**
Le PC4 : 10.10.4.2 
172.16.5.253 : Interface du deuxième routeur R2 

**Q.3.22 Quelles sont les adresses mac source et destination ? Qu'en déduis-tu ?**

CA:01:DA:D2:00:1C  : MAC de l'interface du router r1 dans le réseau 10.12.2.0/24  
CA:03:9E:EF:00:38  : MAC de l'interface du router r2 dans le réseau 10.12.2.0/24  

**Q.3.23 A quel emplacement du réseau a été enregistré cette communication ?**
Cette communication a été enregistrée sur le routeur R1.


