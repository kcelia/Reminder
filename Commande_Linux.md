## Agir en tant que Root

1. Pour se connecter en tant qu'utilisateur root et faire les opérations qui lui sont réservées: `$ su root`
  - Le mdp de utilisateur root est demandé
  - Sous Ubuntu l'utilisateur root n'est pas actif (pas de mdp), pour l'activer `Sudo password root`.
    + Se connecter quand même: `$ sudo su - `
    + Donner un mdp au compte root: `$ sudo passwd`. Ensuite, la commande  `$ su -` devrait fonctionner directementt. 
      * "su" keeps your regular user environment
      * "su -" gives you root's environment 

1. Etant un Sudoers, pour exécuter une commande en tant que root sans changer d'user : `sudo commande`.
  - Le mdp de utilisateur lançant sudo est demandé 
  - Sous Debian la commande `sudo` n'est pas installée par défaut.


