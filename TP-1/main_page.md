# :floppy_disk: TP n°1 :

## Sommaire du TP n°1 :

- [Mise en place d'une machine virtuelle](./main_page.md#mise-en-place-d-une-machine-virtuelle)
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



