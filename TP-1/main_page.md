# :floppy_disk: TP n°1 :

## Sommaire du TP n°1 :

- [Mise en place d'une machine virtuelle](./main_page.md#desktop_computer-mise-en-place-dune-machine-virtuelle)
- Configuration des services réseaux 
- Configuration d'un outil de gestion de ticket 
- Ajout au serveur, d'un plugin de remontée de poste client pour pouvoir réaliser l’inventaire du parc 
- Mise en place d'un poste client Windows 10 et remonter le poste client dans l’inventaire GLPI
- Mise en place d'une sauvegarde de GLPI

## :desktop_computer: Mise en place d'une machine virtuelle

### :electric_plug: Configuration réseau

Tout d'abord, il faut installer une **VM serveur** (debian 11) et une **VM client** (windows 10).

Pour ce faire, on utilise (dans notre cas) l'outils **VMWare Workstation Player**

![vmware](./img/configuration_VM/vmware.jpg)

Comme on peut le voir, il y a bien 2 VM d'installer.

Afin que les 2 machine virtuelles puissent communiquer entre elle, il va falloir configurer la partie réseau comme ceci :

Tout d'abord, il faut se rendre dans ***Manage > Virtual Machine Settings***

![param](./img/configuration_VM/réseaux/2021-09-13-163937.jpg)

Puis, il faut aller dans la partie ***Network Adaptateur*** et choisir ***Bridged***

![bridge](./img/configuration_VM/réseaux/2021-09-13-164233.jpg)

Si jamais, il y a un problème lors du lancement de la Machine Virtuelle (plus de connection avec le réseau). Il se peut que la configuration en pont n'utilise pas le bon adaptateur par défaut.

Par conséquent, il faut aller sur ***Configure Adapters*** et choisir le bon adaptateur :

![adaptaters](./img/configuration_VM/réseaux/2021-09-13-224818.jpg)

Il faut faire la même configuration des "adaptateurs réseaux", pour les 2 VMs.

Ensuite, il ne **reste plus qu'a vérifier** :

Pour comprendre, voici les adresses IPv4 :
- IPv4 de la machine virtuelle sous Debian 11 (serveur) : `192.168.1.63`
- IPv4 de la machine virtuelle sous Windows 10 (client) :
`192.168.1.64`
- IPv4 de la machine hôte sous Windows 10 : `192.168.1.56`

Toutes les machines sont bien dans le même réseau. Elles ont dailleurs toutes une adresse de **passerelle/route** qui est `192.168.1.1`

Afin de vérifier si tout fonctionne, on va utiliser la commande `ping` (valable sur Linux et Windows)

:warning: Il peut y avoir un problème avec la VM Windows à cause du pare-feu. Si jamais le `ping` de la VM Debian vers la VM Windows ne marche pas, il faut donc soit désactiver le pare-feu soit le paramètrer.

Et voici donc les `ping` réaliser :


De la machine hôte (sous Windows) vers la machine virtuelle (sous Debian) :
![ping](./img/configuration_VM/réseaux/2021-09-13-225341.jpg)


De la machine virtuelle (sous Debian) vers la machine hôte (sous Windows) :
![ping](./img/configuration_VM/réseaux/2021-09-13-225726.jpg)

De la machine hôte (sous Windows) vers la machine virtuelle (sous Windows) : (il a fallut désactiver le pare-feu de la VM Windows)
![ping](./img/configuration_VM/réseaux/2021-09-14-113053.jpg)

De la machine virtuelle (sous Windows) vers la machine hôte (sous Windows) :
![ping](./img/configuration_VM/réseaux/2021-09-14-113333.jpg)

De la machine virtuelle (sous Debian) vers la machine virtuelle (sous Windows) : (il a fallut désactiver le pare-feu de la VM Windows)
![ping](./img/configuration_VM/réseaux/2021-09-13-231301.jpg)

De la machine virtuelle (sous Windows) vers la machine virtuelle (sous Debian) : 
![ping](./img/configuration_VM/réseaux/2021-09-13-230604.jpg)

Tout fonctionne.


