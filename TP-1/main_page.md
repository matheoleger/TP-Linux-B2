![logotp1](./img/logo-tp1.png)
# :building_construction: TP n°1 : configuration de l'infrastructure pour un client.
---

## :books: Sommaire :

- [Mise en place d'une machine virtuelle et configuration des services réseaux](./config_réseaux.md)
- [Configuration d'un outil de gestion de ticket](./config_glpi.md)
- [Ajout au serveur, d'un plugin de remontée de poste client pour pouvoir réaliser l’inventaire du parc](./config_fusioninventory.md)
- [Mise en place d'un poste client Windows 10 et remonter le poste client dans l’inventaire GLPI](./config_fusioninv_agent.md)
- [Mise en place d'une sauvegarde de GLPI](./sauvegarde_glpi.md)

---

## :book: Avant de lire

:bulb: À noter que les définitions de certains termes comme par exemple [Apache2](./definition.md#apache2), sont mises comme tel. Pour y accéder, il suffit de cliquer sur le mot en surbrillance, vous arriverez alors à la définition (et l'explication du fonctionnement) écrite par moi.

Retrouvez les définitions [ici](./definition.md).

Certaines images sont directement tirés d'internet (comme par exemple les schémas). Il y a donc une indication quand c'est le cas.

---

## :clipboard: Consignes : 

Le sujet répond à un objectif, **accompagner le client dans la configuration de son infrastructure**.

Après réalisation du sujet, vous retranscrirez vos propos sous la forme d’une **documentation en bon et due forme** (Page de garde, pagination/sommaire, méthodologie, axes d’amélioration, conclusion et annexes au besoin) reprenant la **méthodologie utilisée pour mettre en place le projet** (Captures d’écran attendues).

Les compétences seront évaluées selon les **critères** suivants : 
- **Comprendre** et **analyser** le **cahier des charges** ;
- Définir les **besoins du serveur** Linux en termes de capacité et d’OS ;
- Mettre en place une **machine virtuelle** ;
- Configurer les **services réseaux** ;
- Configurer un **outil de gestion de ticket** ;
- Configurer une **sauvegarde** ;
- Mettre en place un **serveur de messagerie**.

Temps dédié à la compréhension du sujet et à sa **réalisation** : *18h*.

---

## :hammer_and_wrench: Outils utilisés :

- Utilisation de **VMWare Workstation Player** pour les machines virtuelles.
- Utilisation de **GLPI**.
- Utilisation de **FusionInventory**.
- Utilisation de **OpenSSH** pour rendre la configuration plus simple et rapide à faire.
- Utilisation de **GitHub** pour la documentation.

---

## :link: Sources :

- Pour le GLPI : https://openclassrooms.com/fr/courses/1730516-gerez-votre-parc-informatique-avec-glpi/5993816-installez-votre-serveur-glpi

- Pour le plugin FusionInventory : https://openclassrooms.com/fr/courses/1730516-gerez-votre-parc-informatique-avec-glpi/5994176-installez-le-plugin-et-l-agent-fusioninventory

- Pour la sauvegarde automatique : https://christiansueur.com/sauvegarde-automatique-de-votre-serveur-glpi/

---

| page 0 | [Mise en place d'une machine virtuelle et... --->](./config_réseaux.md)