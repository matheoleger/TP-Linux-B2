# :artificial_satellite: Configuration d'un service de Haute Disponibilité avec Corosync et Pacemaker

## Qu'est ce que la *Haute disponibilité*

La définition de la Haute disponibilité se trouve [ici](./definition.md#HA).

Dans notre cas, la **haute disponibilité** fonctionne avec 2 machines serveurs. Le serveur dit *master*, sera le serveur principale. Il fera tourner notre serveur web quand il n'y a pas de problème. Mais dans le cas où la machine *master* ne marche plus, alors c'est la machine *slave* qui prend le relais. En effet, cette machine à la même configuration (au niveau software) que la *master* (donc dans notre cas, installation d'Apache.)

La machine *slave* n'a pas besoin d'être aussi performante que notre serveur principale. En effet, ce n'est qu'un serveur de "back-up", donc cette machine n'est là que dans le cas où il y a un problème avec la machine principale.

Mais alors, comment mettre en place un **site web** avec une seule adresse IPv4 ?

Et bien, c'est avec des outils comme [Corosync](./definition.md#corosync) et [Pacemaker](./definition.md#pacemaker) que nous mettons en place ce genre de chose. En effet, nous allons mettre en place une adresse IP virtuelle, ce qui permet de passer d'une machine à une autre, sans ce soucier des changements d'adresse IP.


## Configuration d'un service de *Haute Disponibilité*

