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

## Caractéristique du Cloud

> Designing highly available, cost-efficient, fault-tolerant, scalable systems

An | Fr | Définition
----|------------|------------
on-demand delivery | Service à la demande | Un client peut faire une demande pour n'importe quel type de ressourceet a n'importe quel instant, la réponse du cloud doit être immédiate. Contrairement aux datacenters classiques, ou solliciter une ressorce pouvait prendre des semaines. Les autorisations d'accès se font sans l'intervention humaine.
rapid access to flexible and low-cost | Accès rapide au au réseau | Réseau à prendre au sens large, smartphones, laptops, stations de travail, etc.
pay-as-you-go pricing/billing | Service mesurable | Mesurer l'usage qui fait des ressources, un client paye ce qu'il utilise à la seconde. 
Mutualisation des ressources: Un herbergeur cloud possède d'énorme ressource IT, partagé entre l'ensemble de ses clients en fonction de la demande. Elle permet l'élasticité dans les ressources du Cloud, en adaptant  les ressources au varition de la demande 
Elasticity & scalability| Provisionnement rapide | La capacité du cloud d'allouer dynamiquement des ressource de manière automatique et rapide en fonction des besoins à la hausse ou à la baisse, le scaling horizontal (scale out) ou vertical (scale up), de façon durable ou temporaire rapidement. e.g., Auto Scaling, Amazon Simple Queue Service (Amazon SQS), Elastic Load Balancing, Amazon CloudFront)

### Avantage

![upside](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Upside.png)
- Cloud services become an operational expense (pay only when you consume computing resources and pay only for how
much you consume) instead of a capital expense (invest heavily in data centers and servers before knowing how you’re going to
use them)
- Libre Service 
- Time to market (mise à disposition rapide)
- Scaling à la demande et Economies of Scale (complexification de l'infrastructure) 
- Reconfigure the computing environment quickly to adapt to changing business requirements

## Region and Availability Zones 

- Achieve the greatest possible fault tolerance and stability. 
- Reduce single points of failure further
- The AZ are connected through low-latency links. 
![R_&_AZ](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-R-vs-AZ%20-%20Copy.png)
![region](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AW-R%20-%20Copy.png)

## Accessing the Platform
![acces_platefom](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Accessing-aws-cloud.png)

## Type de Cloud Computing 

### Infrastructure As A Service - IAAS
![IAAS](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS_IAAS.png)

### Platform As A Service - PAAS
![PAAS](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-PAAS.png)

### Software As A Service - SAAS 
![SAAS](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-SAAS.png)

## Cloud Computing Deployment Models (Mode d'hébergement)
It is important to understand how each strategy applies to architectural options and decisions.

### Cloud Public / An all-in cloud-based application
An environment that exclusively runs in the cloud.
![Cloud_Public](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Stockage-Cloud-Public.png)

### Cloud Privé
On-premises deployment
![Cloud_Prive](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Stockage-Cloud-prive.png)

### Cloud Hybride / A hybrid deployment
![Cloud_Hybride](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Stockage-Cloud-Hybride.png)

Between the cloud and existing on-premises infrastructure to extend and grow an organization’s infrastructure while connecting cloud resources to internal system.
Architecture: AWS Direct Connect, AWS Storage Gateway, Amazon Virtual Private Cloud (Amazon VPC), AWS Directory Service

# Amazon 
In 2006, Amazon Web Services, Inc. (AWS) began offering IT infrastructure services to businesses in the form of **web services**, now commonly known as **Cloud Computing**

Amazon du site e-commerce, qui pour ses propres besoins a faire une plateform de cloud en interne As a Service, puis l'ont offert au public "Simple Storage Service - S3"/blob storage / service fiable 

### Disponibilté vs Durabilité
- Durabilité - 11.9: Signifie que les objects postés sur S3 sont disponible à 99.999999999, peu de chance que les données disparaissent (replication a travers le monde)
- Disponibilte: 99.90% assez faible pour de l'hebergement, on est généralement sur du 99.95% ou 99.99 dans le cloud et service d'hergement

# Services


![Service](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS_130_Services.png)

- Amazon Elastic Compute Cloud (Amazon EC2):
  + Un service Web qui fournit une capacité de calcul redimensionnable dans le cloud. 
  + Permet aux clients d'obtenir/configurer/exploiter les ressources.
  + Permet aux clients de lancer des ressources de calcul avec une variété de systèmes d'exploitation, à les charger avec des applications personnalisées et à gérer les autorisations d'accès au réseau 
- Amazon Simple Storage Service (Amazon S3),
- AWS Elastic Beanstalk
- AWS CloudFormation
- AWS OpsWorks
- Amazon VPC
- AWS Identity and Access Management (IAM) 

### Sans AWS
![service_exemple](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS_Service_example.png)

#### Avec AWS
![service_exemple_avec_aws](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS_Service_example_aws.png)




