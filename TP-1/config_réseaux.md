# :desktop_computer: Mise en place d'une machine virtuelle et configuration des services réseaux

## Avant de commencer.

Tout d'abord, il faut installer une **VM serveur** (Debian 11) et une **VM cliente** (Windows 10).

Pour ce faire, on utilise (dans notre cas) l'outil **VMWare Workstation Player**

![vmware](./img/configuration_VM/vmware.jpg)

Comme on peut le voir, il y a bien 2 VMs d'installées.

## :electric_plug: Configuration réseau

Afin que les 2 machines virtuelles puissent communiquer entre elles, il va falloir configurer la partie réseau comme ceci :

Tout d'abord, il faut se rendre dans ***Manage > Virtual Machine Settings***

![param](./img/configuration_VM/réseaux/2021-09-13-163937.jpg)

Puis, il faut aller dans la partie ***Network Adaptateur*** et choisir ***Bridged***

![bridge](./img/configuration_VM/réseaux/2021-09-13-164233.jpg)

Si jamais, il y a un problème lors du lancement de la Machine Virtuelle (plus de connexion avec le réseau). Il se peut que la configuration en pont n'utilise pas le bon adaptateur par défaut.

Par conséquent, il faut aller sur ***Configure Adapters*** et choisir le bon adaptateur :

![adaptaters](./img/configuration_VM/réseaux/2021-09-13-224818.jpg)

Il faut faire la même configuration des "adaptateurs réseaux", pour les 2 VMs.

Ensuite, il ne **reste plus qu'à vérifier** :

Pour comprendre, voici les adresses IPv4 :
- IPv4 de la machine virtuelle sous Debian 11 (serveur) : `192.168.1.63`
- IPv4 de la machine virtuelle sous Windows 10 (client) :
`192.168.1.64`
- IPv4 de la machine hôte sous Windows 10 : `192.168.1.56`

Toutes les machines sont bien dans le même réseau. Elles ont d'ailleurs toutes une adresse de **passerelle/route** qui est `192.168.1.1`

Afin de vérifier si tout fonctionne, on va utiliser la commande `ping` (valable sur Linux et Windows)

:warning: Il peut y avoir un problème avec la VM Windows à cause du pare-feu. Si jamais le `ping` de la VM Debian vers la VM Windows ne marche pas, il faut donc soit désactiver le pare-feu soit le paramétrer.

Et voici donc les `ping` réalisés :


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

### :electric_plug: Accès à Internet

Dans notre cas, on n'a pas eu besoin de configurer quelque chose pour que cela fonctionne. En effet, le DNS a été configuré automatiquement pour les 2 VMs :

![reseaux](./img/configuration_VM/réseaux/2021-09-15-153302.jpg)

![reseaux2](./img/configuration_VM/réseaux/2021-09-15-153557.jpg)

Il récupère automatiquement l'adresse de passerelle.

Mais dans le cas où Internet ne marcherait pas, alors il faut configurer le DNS.

Pour la VM Windows, il faut aller dans `Centre Réseaux et Partages > (le nom du réseau) > Propriétés` puis il faut cliquer sur ``TCP/IPv4`` et sur `Propriétés`

## :electric_plug: Le SSH

Afin de rendre la configuration des outils (FusionInventory et GLPI) plus simple, on a installé ``openSSH`` afin de pouvoir accéder au serveur via notre machine hôte (machine sur laquelle on faisait les recherches pour configurer le serveur). 

Pour ce faire, il faut simplement installer le package openssh-server sur notre machine serveur :
```bash
matheoleger@debianmatheo:~$ sudo apt install openssh-server 
```
Une fois ceci fait, on peut directement accéder au shell via une autre machine.

> :bulb: Sur Windows 10, "OpenSSH client" est installé par défaut. Par conséquent, aucune installation n'est nécessaire.

![shellviawin](./img/configuration_VM/ssh/connection-ssh.jpg)

Comme on peut le voir ci-dessus, on utilise la commande `ssh username@ipadress` (le `username` correspond au nom de l'utilisateur du serveur auquel on veut accéder et `ipadress` c'est l'adresse de la machine serveur)

## :chart_with_upwards_trend: Axes d'améliorations

Même si dans notre cas cela n'est pas important, on pourrait configurer le Pare-feux de la machine cliente, afin qu'elle accepte les pings des machines se trouvant dans le même sous-réseaux.

---

[<--- Page de garde](./main_page.md) | page 1 | [Configuration d'un outil de gestion de ticket --->](./config_glpi.md)