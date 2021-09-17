# :book: Définition pour le TP n°1

## Apache2

Lien de la documentation source: https://doc.ubuntu-fr.org/apache2

>  Un **serveur HTTP** permet à un site web de communiquer avec un navigateur en utilisant le protocole HTTP(S) et ses extensions (WebDAV, etc.). **Apache** est probablement le **serveur HTTP** le plus populaire. C'est donc lui qui met à disposition la plupart des sites Web du WWW.
> Il est produit par la Apache Software Foundation. C'est un logiciel libre fourni sous la licence spécifique Apache. *- Documentation Ubuntu*

> On utilise généralement Apache en conjonction avec d'autres logiciels, permettant d'interpréter du code et d'accéder à des bases de données. Le cas le plus courant est celui d'un **serveur LAMP** (Linux Apache MySQL PHP). *- Documentation Ubuntu*

**Pour résumer :** *Apache est un serveur HTTP, très utilisé pour la création de service web*.

## PHP

Lien de la documentation source: https://fr.wikipedia.org/wiki/PHP

> PHP: **Hypertext Preprocessor**, plus connu sous son sigle **PHP** (sigle auto-référentiel), est un langage de programmation libre, **principalement utilisé** pour produire des **pages Web dynamiques via un serveur HTTP**, mais pouvant également fonctionner comme n'importe quel langage interprété de façon locale. PHP est un langage impératif **orienté objet**. *- Wikipedia*

**Pour résumer :** *PHP est un langage de programmation qui est souvent utilisé pour créer des pages Web*.

## MariaDB

Lien de la documentation source: https://fr.wikipedia.org/wiki/MariaDB

> MariaDB est un **système de gestion de base de données** édité sous licence GPL. Il s'agit d'un **fork communautaire de MySQL** : la gouvernance du projet est assurée par la fondation **MariaDB**, et sa maintenance par la société **Monty Program AB**, créateur du projet. Cette gouvernance confère au logiciel l’assurance de rester libre. *- Wikipedia*

**Pour résumer :** *MariaDB est un fork communautaire de MySQL, c'est un système de gestion de bases de données.*

## GLPI

Lien de la documentation source: https://fr.wikipedia.org/wiki/Gestionnaire_Libre_de_Parc_Informatique

> GLPI (Gestionnaire Libre de Parc Informatique) est un logiciel libre de gestion des services informatiques (ITSM) et de gestion des services d'assistance (issue tracking system et ServiceDesk). Cette solution libre est éditée en PHP et distribuée sous licence GPL. *- Wikipedia*

> GLPI est une application web qui aide les entreprises à gérer leur système d’information. Parmi ses caractéristiques, cette solution est capable de construire un inventaire de toutes les ressources de la société et de réaliser la gestion des tâches administratives et financières. *- Wikipedia*

**Pour résumer :** *GLPI est un logiciel de gestion des services informatiques et de gestion des services d'assistance.*

## FusionInventory

Lien de la documentation source: https://fr.wikipedia.org/wiki/FusionInventory

> FusionInventory est un logiciel servant à l'inventaire et la maintenance d'un parc informatique à l'aide d'autres logiciels de ce type tels que GLPI ou OCS Inventory. *- Wikipedia*

## Crontab

Lien de la documentation source: https://www.linuxtricks.fr/wiki/cron-et-crontab-le-planificateur-de-taches

> Crontab est un outil qui permet de lancer des applications de façon régulière, pratique pour un serveur pour y lancer des scripts de sauvegardes, etc. *- Linuxtricks*

Pour résumer : *Crontab est un outil qui va permettre d'exécuter des commandes/des scripts de manière récurrente.*

Afin d'éditer un fichier ``crontab``, on fait la commande :

```sh
crontab -e
```

Ceci ouvrira un fichier dans lequel on peut écrire. Il faudra ici écrire l'action à faire, et l'heure/la date d'exécution.

Le ``crontab`` est dépendant à chaque utilisateur. Si l'on veut ouvrir un *cron* en tant qu'administrateur, on fait :

```sh
sudo crontab -e
```

Il existe plusieurs options à la commande :

- Pour **supprimer** un *crontab*

    ```sh
    crontab -r
    ```
- Pour **supprimer** un *crontab* mais avec une demande de confirmation

    ```sh
    crontab -i
    ```
- Pour **afficher** le contenu d'un *crontab* (elle permet aussi de voir s'il existe un crontab pour un utilisateur)

    ```sh
    crontab -l
    ```

Dans le fichier ``crontab``, on doit y écrire la ligne qui fera exécuter une commande (ou un script) à un moment donné.

La ligne se présente comme ceci : 

```sh
# min hour dom month dow command
* * * * * the_command
```

Plus précisément : 

```sh
# .---------------- minute (0 - 59)
# |  .------------- heure (0 - 23)
# |  |  .---------- jour du mois (1 - 31)
# |  |  |  .------- mois (1 - 12) OR jan,feb,mar,apr ...
# |  |  |  |  .---- jour de la semaine (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# |  |  |  |  |
# *  *  *  *  *  la commande à exécuter
```

## FQDN

Lien de la documentation source: https://www.ionos.fr/digitalguide/domaines/gestion-de-domaine/fqdn/

![fqdn_schema](https://www.ionos.fr/digitalguide/fileadmin/DigitalGuide/Screenshots_2019/fqdn-EN-1.png)
(Image provenant du même site que la source)

> FQDN signifie *Fully Qualified Domain Name*, en français « nom de domaine complètement qualifié » (ou : « nom de domaine complet »). Le FQDN est l’adresse absolue d’un site Internet. « Entièrement qualifié » fait référence à une identification unique garantie par le fait que tous les niveaux de domaine sont indiqués. Le FQDN contient le nom d’hôte et le domaine, y compris le domaine de premier niveau, et peut être attribué de façon univoque à une adresse IP. *- IONOS*

**Pour résumer :** *Le FQDN c'est le nom de domaine complet, ce qui nous permet de comprendre son utilisation. (web, mail etc...)*

Comme on peut le voir dans le schéma ci-dessus, on a le **TLD** (*top-level domain* ou *domaine de premier niveau*), qui sera, par exemple, "fr", "com", "org" etc...

On a ensuite le **domaine** (pour avoir un nom de domaine, il faut le racheter à des entreprises comme OVH).

Et ensuite le **nom d'hôte**, qui permet de savoir à quel type de domaine il est question : web (www), mail etc...


## MTA

Lien de la documentation source : https://fr.wikipedia.org/wiki/Mail_Transfer_Agent

> Un *Mail Transfer Agent* est un logiciel pour serveur de transmission de courriers électroniques.

> Un MTA reçoit, habituellement par le protocole SMTP, les emails envoyés soit par des clients de messagerie électronique (MUA), soit par d'autres MTA. Son rôle est de redistribuer ces courriers à des Mail Delivery Agent et/ou d'autres MTA. 

**Pour résumer :** *Un MTA est un logiciel permettant la transition d'e-mail.*

## MDA

Lien de la documentation source : https://fr.wikipedia.org/wiki/Mail_Delivery_Agent

> Un agent de distribution du courriel, en anglais Mail Delivery Agent souvent abrégé par son sigle MDA, est le logiciel qui intervient dans la dernière étape du processus de distribution d'un courrier électronique. C'est le composant chargé de déposer le message dans la boîte aux lettres de l'utilisateur. 

Pour résumé : Un MDA c'est un logiciel déposant le message dans la boîte mail de l'utilisateur.

Afin de faire ce qu'il doit faire, le MDA a besoin d'un protocole spécialisé : *LMTP*.

Il y a aussi des protocoles associés aux mails comme le protocole **POP** et **IMAP** :
- le protocole **POP** (Post Office Protocol) est un protocole qui permet de récupérer les mails situés sur un serveur de messagerie.
- le protocole **IMAP** (Internet Message Access Protocol) est un protocole qui permet d'accéder à ses courriers électroniques directement sur les serveurs de messagerie

La grande différence entre les 2 protocoles, c'est la synchronisation. En effet, le protocole **IMAP** est **synchronisé** en temps réel, par conséquent, on peut retrouver nos mails, même si on change d'équipement. Contrairement au protocole **POP**.