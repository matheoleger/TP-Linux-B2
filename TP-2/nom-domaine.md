# :ticket: Configuration d'un nom de domaine pour le site web

## Qu'est ce qu'un nom de domaine

La définition du nom de domaine se trouve [ici](./definition.md#nom-de-domaine).

Pour faire simple, on utilise des noms de domaine pour naviguer sur internet (ou encore envoyer des mails).

En effet, il serait possible de naviguer sur internet via des adresses IP. Mais malheureusement, il serait difficile de les retenir, par conséquent il existe les noms de domaines qui permettent d'avoir un identifiant plus simple pour accéder à des sites web.

### :floppy_disk: Exemples :

Si on `ping` le nom de domaine `www.google.fr`, on obtient :

![google](./img/dns/ping-google.jpg)

À noter que, si l'on fait la commande `ping -4 <adresse>` on obtiendra l'adresse IPv4 du site que l'on essaye de `ping`. (voir ci-dessous)

![google](./img/dns/ping-google-4.jpg)

Dans mon cas, l'adresse utilisé pour accéder au service de **Google**, c'est `142.250.201.163`.

On peut d'ailleur taper cette adresse IPv4 dans notre navigateur :

![google](./img/dns/google-ip.jpg)

Ce qui nous dirige vers **Google** :

![google](./img/dns/google-page.jpg)

D'après [afnic.fr](https://www.afnic.fr/noms-de-domaine/tout-savoir/) : 
> Le nom de domaine est composé d’une chaîne de caractères (nom propre, marque ou association de mots clés) et d’une extension qui indique l’espace de nommage. Il existe plusieurs types d’extensions : 
> - Des extensions nationales (ccTLD, “Country Code Top Level Domain”), comme le .fr, le .re ou les autres noms de domaine ultramarins gérés par l’Afnic ;
> - Des extensions génériques (gTLD, “Generic Top Level Domain”) dont les plus connues sont le .com, .net, .info, .biz. Depuis quelques années, de nombreuses nouvelles extensions génériques ont fait leur apparition, comme .paris, .bzh, .alsace, .corsica.

Le nom de domaine est unique, mais attention, dans un espace de nommage, c'est-à-dire qu'on peut avoir un site **inform.net** qui sera totalement différent d'un site **inform.com**.

Il faut faire la demande de ce nom de domaine pour l'utiliser publiquement. 

Pour en revenir sur l'étape de redirection de l'adresse IPv4 vers le nom de domaine :

Afin de traduire le nom de domaine en adresse IPv4 (qui nous permet d'accéder au site correspondant) on se sert d'un [DNS](./definition.md#DNS).

> :bulb: Chaque domaine doit être défini, au minimum, dans **deux serveurs DNS**. Ces serveurs peuvent être **interrogés** pour connaître l'**adresse IP associée** à un **nom d'hôte** ou le **nom d'hôte** associé à **une adresse IP**. - [Wikipédia](https://fr.wikipedia.org/wiki/Nom_de_domaine)




