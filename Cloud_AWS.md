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

### Cloud Privé / On-premises deployment
![Cloud_Prive](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Stockage-Cloud-prive.png)

### Cloud Hybride / A hybrid deployment
![Cloud_Hybride](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Stockage-Cloud-Hybride.png)

Between the cloud and existing on-premises infrastructure to extend and grow an organization’s infrastructure while connecting cloud resources to internal system.
Architecture: AWS Direct Connect, AWS Storage Gateway, Amazon Virtual Private Cloud (Amazon VPC), AWS Directory Service

# Amazon 
In 2006, Amazon Web Services, Inc. (AWS) began offering IT infrastructure services to businesses in the form of **web services**, now commonly known as **Cloud Computing**

Amazon du site e-commerce, qui pour ses propres besoins a faire une plateform de cloud en interne As a Service, puis l'ont offert au public "Simple Storage Service - S3"/blob storage / service fiable 


# Services
![Service](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS_130_Services.png)

## Amazon Elastic Compute Cloud (Amazon EC2):
  + Break EC2 down: 
    - C2: In cloud
    - Elastic: The computing service can expand and retract as needed
  + An instance is basically a compute, you can use it to run a local/web application on a scalable and affordable Virutal Machine in the cloud
  + An instance is a virtual server wich is operating system agnostic 
  + Un service Web qui fournit une capacité de calcul redimensionnable dans le cloud. 
  + Permet aux clients d'obtenir/configurer/exploiter les ressources.
  + Permet aux clients de lancer des ressources de calcul avec une variété de systèmes d'exploitation, à les charger avec des applications personnalisées et à gérer les autorisations d'accès au réseau 
  
### Creating an instance with EC2:
  1. Select or install an _Image_ 
Amazon Machine Image (AMI): Combination of an operationg system, and then some applications preinstalled) 
  1. Select an _Instance Type_
  Selecting : Number of CPUs, amount of RAM and Network perfomance, AWS will **create instance type and families**
  
  Families provide a profile: General Purpose, Memory Optimized, Compute Optimized, ...
  1. Configure Instance Details
  Assign a certain number of instance to be replicated ==> Create **Auto Scaling Group** acording to rules set  
  1. Add Storage - Elastic Block Storage (EBS)
  1. Configure Security Group 
  - Control who can SSH into EC2 instance
  - Allow acces between EC2 instances
  - Allow acces to databases 
  - Accept HTTP requests
  1. Review Instance Launch
  Create an instance with an existing key pair, which will allow you to SSH in to the instance
  
 ### Pricing
 <!> Stop/Launch the instance when you need it 
- Amazon charges EC2 instances by the hour.
- Prices change bases on: 
  - Instance Type 
  - AMI Type
  
  
## Elastic Block Storage (EBS):
It's specifically for using with EC2, it's not the same as Amazon S3
  
## Amazon Simple Storage Service (Amazon S3)
- Store any type of file, the maximum object size is 5TB (upload in a single _PUT_ operation in 5GB, beyond there are other methods to upload a larger object in separate operations)


### Bucket
![AWS-Traditional-IT-Storage-vs-AWS]()

## Access

## How AWS is organized geographically speaking ? 
> Region & Available Zone

![AWS-Regions-vs-Availability-Zones]()

![AWS-Connectivity-between-AZ-in-Regions]()

![AWS-Console-Regions]()

- **Regions** are physical locations where certain services are hosted, there are many regions throughout the world
- **Availability Zone**: Isolated regions, collection of datacenters that have separate power, networking and connectivity. But connect with hyper-fast fiber optics.
- AZ are fault tolerant 

> By scaling your application in several AZ, you can achieve nearly unlimited uptime for your application (reduce latency) and satisfy compliance requirements on distance. But, it does not protect against accidental deletion.

- Root resource to which you can:
  + Operation Add, delete, modify objects
  + Configuration options that you can set on buckets like:
    ### Permission
    ### Hosting options
    ### Logging
    ### Encryption 
    ### Lifecycle
    ![AWS-Data-Lifecycle]()
    ### Trigger events when objects are added/modified/deleted
    ### Preserve older versions of objects
    ### Replicate objects across regions 
    Reduce latency (or use another CloudFront Service)
    * Reduce latency (or use another CloudFront Service) and satisfy compliance
    * Crossregion replication does not protect against accidental deletion.
    ### Host Static
    To alow anonymous/authenticated users acces, use a host static files for websites
    ### URL
    Once created, buckets (objects contained within) are accessed via URL

### Pricing
The pricing is based on 3 first aspects:
- Amount of data stored
- Number of requests
- Amount of dara transferred
- Different per region 

### Relational Database Service (RDS)

A collection de service for managed relational databases and infrastructure 
> Managed: AWS takes care of all the backups, software updates. 
> Unmanaged: like installing a database on an EC2 instance, you would then be responsible for figuring out backups, redundancy, updating the software with security 
You can: 
- Take DB Snapshopts 
- Increasing the size 

### RDS Database
![RDS-Database]()
Each carries a different price, configuration and connection options

### Pricing
Prices depends on:
- Type of database
- Region
- EC2 Instance Type 

### Access via security groups 

## Route53
- Amazon service for DNS management, both inside and outside AWS
- To configure domain names to resolve to internal AWS services  
> Domain Name system: translates human-readable URLs to IP addresses
- Route53 or LoadBalancers don't have visible IP addresses 
```Bash
1. First 
DNS Management > Setting up a Hosted Zone
// Hosted Zone: Root Domain Name, like google.com 
```
### Pricing
Prices depend on the number of created Hosted Zone and the amount of requests 
### Health checks 

## Lambda
Write (in different languages) simple function and return the result
It can be envoked from many sources

## Identity Access Management
![AWS-IAM-Logo]()
- Allows you to manage uses and also manage that level of access to the AWOS console
- It gives you centralized control over your AWOS account
- It also gives you shared access to AWOS account 
- It gives you granular permissions :
  + enable different levels of access to different users within your organization
  + Granular enough to limit a single user to the ability to perform a single action on a specific resource from a specific IP address during a specific time window
- It allows you to set up your own password rotation policy it integrates 
- It enables access to store or retrieve data located in an bucket or within a dynamo DB database.


### Access to 
IAM is controlled like most other AWS Cloud services:


AWS Management Console | CLI | SDK
-----------------------|------|----------
An easy way to start learning | Start scripting repeated tasks using the CLI | Start writing your own tools and complex processes by manipulating IAM directly through the REST API via one of several SDKs.

### Users, Groups, Roles and Policies
![User-Groups-Roles-Policies]()
## AWS Elastic Beanstal
## AWS CloudFormation
## AWS OpsWorks
## CloudFront 
To edge files to users to Reduce Latency 
## Amazon VPC
To controll access and secure you instances 
- AWS Identity and Access Management (IAM) 

### Sans AWS
![service_exemple](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS_Service_example.png)

#### Avec AWS
![service_exemple_avec_aws](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS_Service_example_aws.png)




