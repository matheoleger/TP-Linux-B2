![logotp2](./img/logo-tp2.png)
# :building_construction: TP n°2 : Mise en place d'un site web, pour un client
---

## :books: Sommaire :

- [Organisation d'un groupe de réflexion](./organisation.md)
- [Création d'un site Web avec Apache (et PHP)](./site-web.md)
- [Configuration d'un nom de domaine pour le site web](./nom-domaine.md)
- [Mettre en place un certificat SSL sur le site web](./ssl.md)
- [Configuration d'un service de Haute Disponibilité avec Corosync et Pacemaker](./haute-dispo.md)
- [Conclusion](./conclusion.md)

---

## :book: Avant de lire

:bulb: À noter que les définitions de certains termes comme par exemple [Apache2](./definition.md#apache2), sont mises comme tel. Pour y accéder, il suffit de cliquer sur le mot en surbrillance, vous arriverez alors à la définition (et l'explication du fonctionnement) écrite par moi.

Retrouvez les définitions du TP n°2 [ici](./definition.md).

Certaines images sont directement tirées d'internet (comme par exemple les schémas). Il y a donc une indication quand c'est le cas.

---

## :clipboard: Consignes : 

Le sujet répond à un objectif, **accompagner le client dans la mise en place de son site Web**.

Après réalisation du sujet, vous retranscrirez vos propos sous la forme d’une **documentation en bon et due forme** (Page de garde, pagination/sommaire, méthodologie, axes d’amélioration, conclusion et annexes au besoin) reprenant la **méthodologie utilisée pour mettre en place le projet** (Captures d’écran attendues).

Les compétences seront évaluées selon les **critères** suivants : 
- **Comprendre** et **analyser** le **cahier des charges** ;
- Définir les **besoins du serveur** Linux en termes de capacité et d’OS ;
- Mettre en place une **machine virtuelle** ;
- Configurer les **services réseaux** ;
- Configurer les **services Web** ;
- Mise en place d’une **solution de haute-disponibilité**.

Temps dédié à la compréhension du sujet et à sa **réalisation** : *8h*.

---

## :hammer_and_wrench: Outils utilisés :

- Utilisation de **VMWare Workstation Player** pour les machines virtuelles.
- Utilisation de **Apache** pour le serveur.
- Utilisation de **GitHub** pour la documentation.

---

## :link: Sources :

- Pour le serveur Apache : https://openclassrooms.com/fr/courses/1733551-gerez-votre-serveur-linux-et-ses-services/5236051-installez-le-serveur-web-le-plus-utilise-au-monde-apache

- Pour la partie OpenSSL : https://guide.ubuntu-fr.org/server/certificates-and-security.html

- Pour la partie de la Haute disponibilité : https://wiki.bruno-tatu.com/wiki/cluster-corosync-pacemaker

    https://memo-linux.com/creer-un-cluster-ha-avec-corosync-et-pacemaker/
---

Page 0 | [Organisation d'un groupe de réflexion --->](./organisation.md)