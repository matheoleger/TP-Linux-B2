# :pager: Mettre en place un certificat SSL sur le site web avec let's encrypt

## Qu'est ce qu'un certificat SSL

La définition du certificat SSL se trouve [ici](./definition.md#certificat-ssl).

Un **certificat SSL** utilise un **système de cryptographie**.

Il utilise la cryptographie à clé publique, c'est-à-dire un système ce basant sur 2 clés, une privée et une publique :

- La **clé publique** sert à **chiffrer** les données :
    Le site web ce sert de la clé publique du serveur pour chiffrer les informations afin que personne (mise à part le serveur) ne puissent déchiffrer les données.

- La **clé privée** sert à **déchiffrer** les données :
    Le serveur va quand à lui utiliser la clé privée afin de déchiffrer les données reçus par le/les site(s) web(s).

Ce certificat va nous permettre d'utiliser le protocole **HTTPS** (*"S"* pour *Secure*) au lieu de **HTTP**.

Il y a plusieurs avantages à avoir ce certificat sur nos sites. Les 2 principales sont la **sécurité** et la **confiance**.

## Configuration d'un certificat SSL

Pour commencer, il faut installer l'outils `certbot` de [Let's Encrypt](./definition.md#lets-encrypt).

> :bulb: Un programme de gestion de certificats en Python et sous licence Apache appelé ``certbot​`` s’installe sur le client (le serveur web d’un inscrit). - [Wikipédia](https://fr.wikipedia.org/wiki/Let%27s_Encrypt)

Cette outils va permettre de faire toute la gestion du certificat, il valide le domaine et configure d'autres choses (HTTPS, renouvellement du certificat etc...).

Notre nom de domaine étant privé, on ne pourra pas faire la manipulation jusqu'au bout. En effet, **Let's Encrypt** à besoin d'un nom de domaine valide afin de créer un certificat SSL. (J'expliquerais en temps voulu, ce qu'il aurait fallut faire afin de finir la tâche)

Nous allons don commencer par télécharger le paquet `certbot`.

De nombreux tutoriels sur internet, propose des manières différentes de télécharger `certbot`. Nous allons ici, utiliser la **méthode officielle** du [site de certbot](https://certbot.eff.org/lets-encrypt/debianbuster-apache.html) pour l'installer sur notre machine sous **Debian 11**.


Tout d'abord, nous devons installer le gestionnaire de paquêt [Snap](./definition.md#Snap). Pour ce faire, nous allons installer `snapd` via la commande :

```sh
sudo apt-get install snapd
```

![snapd](./img/ssl/2021-10-03-220453.jpg)

Une fois l'outils installé, il faut installé la dernière version du `core snap` (coeur du logiciel) pour avoir la dernière version de ``snapd`` :

```sh
sudo snap install core
```

Après quelques temps d'attente, on devrait avoir le message :

```sh
core 16-2.45.2 from Canonical✓ installed
```

Si jamais il était déjà installé, on peut faire la commande `sudo snap refresh core` afin d'avoir la dernière version du logiciel.

Avant de continuer, le site de `certbot` recommende de supprimer toutes versions, potentiellement existante, de `certbot` :

```sh
sudo apt-get remove certbot
```

On peut maintenant passer à l'installation de `certbot` :

```sh
sudo snap install --classic certbot
```

Une fois installer, pour que le nom `certbot` soit reconnu comme une commande, il faut taper la ligne suivante dans le terminale :

```sh
sudo ln -s /snap/bin/certbot /usr/bin/certbot
```

Avant de commencer à faire les commandes liés à `certbot`, on doit activer 2 modes sur les services ``apache`` :

- le module **SSL**.
- le module **rewrite**.

Pour vérifier s'ils sont déjà installé :

```sh
sudo apachectl -M
```
Si dans les modules, il y a les 2, alors il n'y a rien à faire de plus. Personnellement, je ne les avais pas :

![modules](./img/ssl/2021-10-03-214950.jpg)

Il faut donc les installer respectivement avec les lignes :

```sh
sudo a2enmod ssl

sudo a2enmod rewrite
```

![sslapache](./img/ssl/2021-10-03-215248.jpg)

![sslapache](./img/ssl/2021-10-03-215319.jpg)

Il faut maintenant relancer les services Apache :

```sh
sudo systemctl reload apache2
```

Afin d'avoir un certificat il faut utiliser le système de **vhost** d'*Apache* : Nous allons donc devoir **reconfigurer** notre site web.

----

### Mise en place d'un Vhost avec Apache

En effet, nous avons vu dans la section *[Installation d'Apache (et PHP)](./site-web.md#installation-dapache-(et-php))* que nous n'avions pas besoin de faire les **configurations d'un hôte virtuel** pour afficher notre site web. Malheureusement, nous en avons besoin pour mettre en place la **certification SSL**.


Donc il faut commencer par créer le fichier `.conf` correspondant à notre site web :

- On va dans le répertoire `/etc/apache2/sites-available/` :
    ```sh
    cd /etc/apache2/sites-available/
    ```

- On créé le fichier ``inform.conf`` :
    ```sh
    sudo nano inform.conf
    ```

- Nous allons y ajouter la configuration du Virtual Host :
    ```html
        <VirtualHost *:80>
                ServerName inform
                ServerAlias inform
                DocumentRoot /var/www/html/inform
                <Directory /var/www/html/inform>
                        Options -Indexes +FollowSymLinks -MultiViews
                        AllowOverride all
                        Order allow,deny
                        allow from all
                </Directory>
                ErrorLog /var/log/apache2/inform.error.log
                CustomLog /var/log/apache2/inform.access.log combined
        </VirtualHost>
    ```

    Explication des éléments composants le ``.conf``
    - `*:80` : indique que le site web peut être utilisé sur le **port 80**.
    - `ServerName` : hôte pour lequel la configuration sera utilisée. Il n'y a qu'un seul **ServerName** possible par ``vhost``.
    - `ServerAlias` : Un ``vhost`` peut en avoir plusieurs.
    - `DocumentRoot` : On y met le chemin d'accès au fichier du site web.
    
    Il y a quelques informations supplémentaires pour un ``virtual host`` plus complet :
    
    - `ErrorLog` : Endroit où il faut enregistrer les logs d'erreurs.

    - `CustomLog` : Autres logs.

- Une fois le fichier complété, on peut maintenant créer un dossier pour notre site :
    ```sh
    sudo mkdir /var/www/html/inform/
    ```
    Puis, dans notre cas, on va faire une copie du fichier index.html (configuré précédemment) :
    ```sh
    sudo cp /var/www/html/index.html /var/www/html/inform/
    ```

- Maintenant, il faut activer la configuration de l'hôte virtuel :
    ```sh
    sudo a2ensite inform
    ```

- Avant de redémarrer, on peut tester notre configuration :
    ```sh
    sudo apache2ctl -t
    ```
 
- Il ne reste plus qu'à redémarrer le service Apache :
    ```sh
    sudo systemctl reload apache2
    ```

Si tout fonctionne, on devrait avoir notre page qui apparait dans le navigateur lorsque l'on écrit le nom de domaine.

----

On peut maintenant utiliser `certbot` :

C'est à ce moment là que l'on ne peut plus avancer si on n'a pas un nom de domaine valide.

En effet, il faut que notre nom de domaine soit bien composé d'un **TLD** (Top level domain) et d'un **SLD** (Secondary Level domain). Et il faut qu'il soit **reconnu comme actif** (il faut l'avoir acheté).

Il y a plusieurs façon d'utiliser ``certbot`` :

- Pour une configuration **automatique** :
    
    ```sh
    sudo certbot --apache
    ```
    Cette commande va vous configurer votre ``virtualHost`` automatiquement :

    ![cerbotauto](./img/ssl/2021-10-04-090845.jpg)

    (Sur l'image ci-dessus, j'avais modifié le nom de domaine par inform.test afin de voir si cela fonctionnait quand on utilisait un nom de domaine composé d'un TLD et d'un SLD)

    Une fois ceci fait, le cerificat devrait être créé et configuré automatiquement.

- Pour une configuration "**semi-automatique**" (on donne directement le nom de domaine) :

    ```sh
    sudo certbot --apache -d inform.test -d www.inform.test
    ```

    (Là encore j'avais changé le nom de domaine) 

- Pour une configuration **manuelle** :
    ```sh
    sudo certbot certonly --webroot --webroot-path /var/www/html/inform/ --domain inform.test --email matheoleger@ynov.com
    ```

    Il y a pas mal de configuration à faire dans le fichier du ``vhost``, on peut suivre ce [lien](https://www.memoinfo.fr/tutoriels-linux/configurer-lets-encrypt-apache/) pour le faire.


On peut maintenant **tester** notre **configuration** et **redémarrer** :

```sh
apache2ctl -t
systemctl reload apache2
```

On peut maintenant **tester** le certificat SSL en essayant d'accéder au site avec le **protocole HTTPS**.

On peut aussi utiliser un site de **test de validité** du certificat.

***À noter :*** Let's Encrypt expire au bout de 90 jours, il faut donc faire la commande :

```sh
certbot renew --dry-run
```

On peut donc faire un système CRON (voir [TP n°1](../TP-1/definition.md#crontab)) qui tous les 90 jours va réinitialiser notre certificat SSL.

--------------------------------------------------------

## :chart_with_upwards_trend: Axes d'améliorations

Dans le cas d'un test professionnel, il faudrait essayer avec un nom de domaine valide (même si ce n'est pas le bon, tester avec un nom de domaine ayant un TLD et un SLD)

----

[<--- Configuration d'un nom de domaine pour le site web](./nom-domaine.md) | Page 4 | [ Configuration d'un service de Haute Disponibilité --->](./haute-dispo.md)



