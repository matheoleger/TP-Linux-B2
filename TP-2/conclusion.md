# :heavy_check_mark: Conclusion

## Elements réussis

Globalement, j'ai réussi ce qui était demandé :

- Mise en place d'un site web :
    Cette partie a été entièrement réussi. J'ai préféré utiliser le HTML au lieu du PHP.
- Mise en place d'un nom de domaine :
    Cette partie a aussi été réussi. J'ai fait plein de recherche sur les noms de domaines et sur le DNS.
- Mise en place d'un certificat SSL :
    Cette partie a été réussi, mais après plusieurs essais. En effet, mes erreurs m'ont permit de comprendre qu'il existait plusieurs manière d'avoir un Certificat SSL. Dans notre cas, il fallait avoir un certificat auto-signé.
- Mise en place d'une HA :
    Cette partie a peut-être été réussi. En effet, j'ai un doute sur la fiabilité de ma méthode pour le fonctionnement avec Apache. En revanche, je sais que mon adresse de ``failover`` fonctionne comme demandé.


## Elements améliorables

On a pu voir à la fin de chaque partie (ou presque), des axes d'amélioration.

Les éléments qui seraient à améliorer dans le cadre professionnel :

- **la sécurité** : 
    - Au niveau du SSL, nous avons utilisé une clé privée, sans *phrase de passe*, ce qui est très peu recommandé.
    - En globalité, la sécurité via l'ouverture de certains port. On a ouvert des ports mais il faut configuré niveau sécurité plus en profondeur.

- **La méthode utilisé** :
    - Dans le cas du SSL, on pourrait utiliser une **CA** (personnel ou non) afin de signer nos certificats, et éviter des messages de préventions sur la fiabilité de notre site web.
    - Dans le cas de la **HA**, on pourrait trouvé le moyen de configuré Apache d'une manière plus pérennisable ?
    - Dans le cas du nom de domaine, l'utilisation d'un DNS comme **Bind9** serait plus judicieux pour une solution pérennisable.


## Les difficultés rencontrés

Lors de ce TP, j'ai rencontré **quelques difficultés** :

- **SSL** : J'ai relativement eu du mal sur cette partie. En effet, la configuration demandé, via Let's Encrypt, n'était pas possible pour notre solution, car il fallait avoir un nom de domaine vérifiable. Il a donc fallut que je reprenne depuis le début, et cela n'a pas été facile.
- **HA** : Les tutoriels trouvés était globalement fait pour fonctionner sous **CentOS**. Les rares tutoriels sur Debian/Ubuntu, ne fonctionnait pas complétement. Au final j'ai dû passé beaucoup de temps à mélanger les solutions afin d'avoir quelque chose de convenable. 

---

[<--- Configuration d'un service de Haute Disponibilité](./haute-dispo.md) | Page 6 | [Définition --->](./definition.md)

