## Traditionnellement 
Traditionnellement, les adminstrateurs systèmes installaient/manipulaient/configuraient/déployaient manuellement les infrastrutures (BdD, Serveur, Routeur, Réseau) :arrow_right: Erreur de manipulation/configuration et risque de panne ou perte de données.

Grâce au mouvement DevOps, on est passé a des techniques de virtualisation, tels que: *VMware*, OpenStack, Xen ou KVM. 
La virtualisation a permis de passer du lourd au leger/du physique au conceptuel/du concret à l'absrait.

Par la suite, au lieu d'investir dans du matériel, les organisations ont préféré aquérir des outils logiciels, tels que: *Docker*, Kubernets, Ansible, Chef, Puppet, Terraform, ect.

Pour finir, ils ont transferé des datacenters vers le _Cloud_, grâce à des services comme **Amazon Web Services (AWS), Azure, Google Cloud**.

## Cloud Computing

Le National Institute of Standard Technology (NIST) définit le CC comme 
un modèle de traitement permettant l'accès à la
demande  à un ensemble de ressources de calcul partagées (serveur, réseau, volumes de stockage, applications et services, ressources mises à disposition par le réseau) 
provisionnées et libérées avec un effort minime.

- A la demande signifie : sans intervention humaine, avec les datacenters classique solliciter une ressorce pouvait prendre des semaines.
- Accès au réseau: au sens large, smartphones, laptops, stations de travail, etc
- Provisionnement rapide: Elasticité, fait réference à la capacité du cloud d'effectuer, de manière autimatique, le scaling horizontal (scale out) ou vertical (scale up).

Avantage | Inconvenient
---------|---------
Cout Réduit (mis à disposition par le fournisseur Cloud) | Not yet
Libre Service | Not yet
Time to market (mise à disposition rapide) | 
Scaling à la demande (complexification de l'infrastructure) | Not yet 

Amazon S3:
Amazon du site e-commerce, qui pour ses propres besoins a faire une plateform de cloud en interne As a Service, puis l'ont offert au public "Simple Storage Service - S3"/blob storage / service fiable 

### Disponibilté vs Durabilité
- Durabilité - 11.9: Signifie que les objects postés sur S3 sont disponible à 99.999999999, peu de chance que les données disparaissent (replication a travers le monde)
- Disponibilte: 99.90% assez faible pour de l'hebergement, on est généralement sur du 99.95% ou 99.99 dans le cloud et service d'hergement


### Machine Virtuelle
Tarification: payer à la seconde







