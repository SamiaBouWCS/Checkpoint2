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

Fichier 1 :
Q.3.11


