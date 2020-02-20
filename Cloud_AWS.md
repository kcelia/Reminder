## Traditionnellement 
Traditionnellement, les adminstrateurs systèmes installaient/manipulaient/configuraient/déployaient manuellement les infrastrutures (BdD, Serveur, Routeur, Réseau) :arrow_right: Erreur de manipulation/configuration et risque de panne ou perte de données.

Grâce au mouvement DevOps, on est passé a des techniques de virtualisation, tels que: *VMware*, OpenStack, Xen ou KVM. 
La virtualisation a permis de passer du lourd au leger/du physique au conceptuel/du concret à l'absrait.

Par la suite, au lieu d'investir dans du matériel, les organisations ont préféré aquérir des outils logiciels, tels que: *Docker*, Kubernets, Ansible, Chef, Puppet, Terraform, ect.

Pour finir, ils ont transferé des datacenters vers le _Cloud_, grâce à des services comme **Amazon Web Services (AWS), Azure, Google Cloud**.



# Amazon 
In 2006, Amazon Web Services, Inc. (AWS) began offering IT infrastructure services to businesses in the form of **web services**, now commonly known as **Cloud Computing**

Amazon du site e-commerce, qui pour ses propres besoins a faire une plateform de cloud en interne As a Service, puis l'ont offert au public "Simple Storage Service - S3"/blob storage / service fiable 


## Cloud Computing

Le National Institute of Standard Technology (NIST) définit le CC comme 
un modèle de traitement permettant l'accès à la
demande  à un ensemble de ressources de calcul partagées (serveur, réseau, volumes de stockage, applications et services, ressources mises à disposition par le réseau) 
provisionnées et libérées avec un effort minime.

## Caractéristique du Cloud

> Designing highly available, cost-efficient, fault-tolerant, scalable systems

Termes | Définition
---|------------
on-demand delivery / Service à la demande | Un client peut faire une demande pour n'importe quel type de ressourceet a n'importe quel instant, la réponse du cloud doit être immédiate. Contrairement aux datacenters classiques, ou solliciter une ressorce pouvait prendre des semaines. Les autorisations d'accès se font sans l'intervention humaine.
rapid access to flexible and low-cost / Accès rapide au au réseau | Réseau à prendre au sens large, smartphones, laptops, stations de travail, etc.
pay-as-you-go pricing/billing / Service mesurable | Mesurer l'usage qui fait des ressources, un client paye ce qu'il utilise à la seconde. 
Mutualisation des ressources |  Un herbergeur cloud possède d'énorme ressource IT, partagé entre l'ensemble de ses clients en fonction de la demande. Elle permet l'élasticité dans les ressources du Cloud, en adaptant  les ressources au varition de la demande 
Elasticity & scalability / Provisionnement rapide | La capacité du cloud d'allouer dynamiquement des ressource de manière automatique et rapide en fonction des besoins à la hausse ou à la baisse, le scaling horizontal (scale out) ou vertical (scale up), de façon durable ou temporaire rapidement. e.g., Auto Scaling, Amazon Simple Queue Service (Amazon SQS), Elastic Load Balancing, Amazon CloudFront)

### Avantage

![upside](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Upside.png)

- Cloud services become an operational expense (pay only when you consume computing resources and pay only for how
much you consume) instead of a capital expense (invest heavily in data centers and servers before knowing how you’re going to
use them)
- Libre Service 
- Time to market (mise à disposition rapide)
- Scaling à la demande et Economies of Scale (complexification de l'infrastructure) 
- Reconfigure the computing environment quickly to adapt to changing business requirements


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
Between the cloud and existing on-premises infrastructure to extend and grow an organization’s infrastructure.

Architecture: AWS Direct Connect, AWS Storage Gateway, Amazon Virtual Private Cloud (Amazon VPC), AWS Directory Service

![Cloud_Hybride](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Stockage-Cloud-Hybride.png)


### Bakcups, Multi-AZ, 

There 2 different types of _Backups_ for AWS:

1. Automated Backups:
- Allows you to recover your database to any point in time within a **retention period** (conservation)

The _retention period_: can be between 1 and 35 days

- Takes a full daily snapshot and will also store transaction logs throughout the day.

How we do a restore with automated backups ? When you recover, AWS will first choose the most recent daily backup so choose the snapshot that's most recent and then apply those transaction logs that are relevant to that day.

- Allows you to do a point in time recovery down to a second within the retention period

- Is enabled by default, the backup data is stored on S3 and you're going to get free storage space equal to the size of your database.

- BackUps are taken within a defined window. During the backup window, storage I/O may be suspended while your data is being backed up and you may experience some elevated latency

```
Service > Database > RDS > Create DB Instance or Select An existing Instances

// 1 - Take snapshot
Instances > Instance Actions > Take Snapshop: name_manual_snapshot 

// 2 - Copy & encryption
// Then, you can select the copy_manual_snapshot and copy it in a region (deploy new instance) by:
> Instance Action > Copy Snapshot
// Then, scroll down 
> Enable encryption or Disable encryption 

// 3 - Restore the instance to a point in time
// Apply with transactions, logs to that snapshot and then bring it back to a point in time

Instance Action > Restore
```

1. Database Snapshots:
- When we do a database snapshot it's going to take a snapshot of the database.
- It's done manually (use initiated). They are stored (_standalone file_) even after you delete the origianl RDS Instance, unlike Automated BackUps (AB will also be deleted with it as well)

> Whenever you restore either an automatic backup or a manual snapshot, the restored version of the database will be a new RDS Instance with a new DNS EndPoint

2. Encryption
At rest, is supported for MySQL, Oracle, SQL Server, PostgreSQL, Maria DB and Aurora
It is done using the AWS Key Management Service (KMS) service.
Once your RDS Instance is encrypted, the data stored at rest in the underlying storage is encrypted, as are its automated backups, read replicas and snapshots.

1. Multi-AZ
- Allows you to have an exact copy of your production database in another Availability Zone.
AWS handdles the replication for you, so when your production database is written to, this write will automatically be synchronized to the standby database. 

In the event of database maintenance or DB Instance failure or an availability zone failure, AWS will automatically follow it to the standby so that the database operations can resume quickly without administrative intervention
- Is Synchronous

Services > Database > RDS > Instances > Instances Actions > Modify > Multi-AZ-Deployment: Yes
1. Read Replicas
- Scaling out your database so that you take the load off the primary database and you spread that load across one or more read replicas.

-  You can also have Read Replicas of Read Replicas in different AZ or R (but watch out for latency) 
- Allows you to have a read only copy of your production database, This is achieved using asynchronous replication
- you use read replicas primarily for very real heavy database workloads so use Read replicas to scale out.
- Is Asynchronous 
- Is available for Aurora, MariaDB, MySQL, PostgreSQL, MySQL Server
- Used for scaling, not for DR
- you must have automatic backups tuned on in order to deploy a read replica
- you can have up to 5 read replica copies of any database 
- Each read replica will have its own DNS end point 
- You can have RR that have Multi-AZ

Services > Database > RDS > Instances > Instances Actions > Create read Replicas
# Services
![Service](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS_130_Services.png)

## Amazon Elastic Compute Cloud (Amazon EC2):
> Break EC2 down: 
>> C2: In cloud
>> Elastic: The computing service can expand and retract as needed

  + An instance is basically a compute/a virtual server wich is operating system agnostic, you can use it to run a local/web application on a scalable and affordable Virutal Machine in the cloud
  + Permet aux clients d'obtenir/configurer/exploiter les ressources
  + Permet aux clients de gérer les autorisations d'accès au réseau 
  
### 1. Creating an instance with EC2:
![]()
1. **Select or install an _Image_ **

Amazon Machine Image (AMI): Combination of an operationg system, and then some applications preinstalled) 

1. **Select an _Instance Type_**
Selecting : Number of CPUs, amount of RAM and Network perfomance, AWS will **create instance type and families**
  > Families provide a profile: General Purpose, Memory Optimized, Compute Optimized, ...
  
1. **Configure Instance Details**
Assign a certain number of instance to be replicated ==> Create **Auto Scaling Group** according to rules set  

1. **Add Storage - Elastic Block Storage (EBS)**

1. **Add Tags**

1. **Configure Security Group** 
  - Control who can SSH into EC2 instance
  - Allow acces between EC2 instances, allow acces to databases 
  - Accept HTTP requests
  
1. **Review Instance Launch**
Create an instance with an existing key pair, which will allow you to SSH in to the instance

### 2. Launch an instance in Windows 
2.1. Install Putty
```Bash
> Google > 'Putty'  > Putty download Page > For Windows on Intel x86 > putty.exe + puttygen.exe 
```
2.2. Launch EC2 Instance 
```Bash
> Step 7 - Review Instance Launch > Launch > Create New Key Pair > Key Pai Name: 'MyPuttyKey' 
> Download Key Pair // MyPuttyKey.pem 
                   // To be able to use it with Putty, convert it to PPK file
> Launch Instances 
// In the browser, you can see 
// Your instances are now launching and have been initiated I-2343FDFD433 (i)
```
2.3. Convert File
```Bash
> puttygen.exe > Run Anyway > Load (load the key file) > Save Private Key > Yes > Save it as MyPuttyKey.ppk
```
2.4. Launch the instance in Cloud
```Bash
> Hit (i) > Save IP Address 
> putty.exe 
> Host Name (or IP Address): ec2-user@IP-Address 
> Save Session: ec2-user@IP-Address
> SSH > Auth > Brower > Open: MyPuttyKey.kkp
> Session > Save 
> Select & Load & Open: ec2-user@IP-Address  > Terminal > Yes
// If the terminal is not easy to handle, 
> putty.exe > Select & Load: ec2-user@IP-Address > Windows > Appearance / ... > Save > Open 

// Finaly, we have Linux on the Cloud
```
2.5. Hands on Amazon Linux AMI
```bash

$ sudo su 
// YUM - Yellowdog Updater Modified
// -y for -YES 
# yum update -y 

// Pour des applications Web
# yum install httpd -y

// Once, Httpd installed, start the service 
# service httpd start 

// If the instance reboot we want Apache to come back on automatically
# chkconfig httpd on 

// Show the status of the service
# service httpd status 

// Create the application within the html service
# cd /var/www/html 
// Add <html><body><h1>Hello Cloud Gurus</h1></body></html> to index.html
# nano index.html 
// See the message, through the browser > IP Address

```

### Encryption of an existing EC2 instance
You work for a web analytics firm who have recently migrated their application to AWS. The application sits behind an Elastic Load Balancer and it monitors user traffic to their website. You have noticed that in the application logs you are no longer seeing your users public IP addresses, instead you are seeing the private IP address of the elastic load balancer. This data is critical for your business and you need to rectify the issue immediately. What should you do?
Creat a snapshot of the EC2 volume. then Create a copye of that volume, checking the box to enable encryption, create an AMI pf the copied snapshot and then redeploy the EC2 instance using the encrypted AMI
Delete the old EC2 Instance

You create the role and attach it to the existing EC2 instance. How fast will the changes take to propagate? Immediatly 

### Pricing  
<!> Stop/Launch the instance when you need it 
- Amazon charges EC2 instances by the hour.
- Prices change bases on: 
- Instance Type 
- AMI Type

------------------  
## Elastic Block Storage (EBS):
- It's specifically for using with EC2, it's not the same as Amazon S3
- Configure _encryption_ when creating the EBS volume

## Amazon Simple Storage Service (Amazon S3)

- It's object-based storage (Not a block storage), like: files, images, pages. It's not for operating systems and not for databases
- Store any type of file, the maximum object size is 5TB (upload in a single _PUT_ operation in 5GB, beyond there are other methods to upload a larger object in separate operations)
- There is unlimited storage (no allocation space) and AWS take care of the capacity management/capacity on your behalf 
- It allows you to store and retrieve any amount of data from anywhere on the web.
- High availability and disaster recovery (if AWS lose one of their devices/facilities, or there is a faulty device or a faulty datacenter or a faulty availability, the S3 service will still be available)
- S3 is a simple key value store 
- S3 is not an OS

### Amazon Simple Storage Service (Amazon S3) Basics 

### 1. Bucket ~ folder 

![AWS-Traditional-IT-Storage-vs-AWS](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Traditional-IT-Storage-vs-AWS.png)

- S3 is a universal namespace, the bucket names must be unique globally and it's similar to a DNS or an Internet Address
![Bucket-name]()
- Subresources - Bucket specific configuration
- Bucket policies, Access control Lists: Ways to control access to the contents of your pocket.
Cross Origin Ressource sharing (CORS): Setting up the capability for files that were located in one bucket to access the files within another bucket 

#### 1.1 Create Bucket 
![Upload-Bucket]()

#### 1.2 Add Folder Whithin Bucket
``` Select buckt > Create Folder > Fill out ``` 

#### 2. How AWS is organized geographically speaking ? 
> Region & Available Zone

![AWS-Regions-vs-Availability-Zones](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Regions-vs-Availability-Zones.png) 
![AWS-Connectivity-between-AZ-in-Regions](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Connectivity-between-AZ-in-Regions.png)

![AWS-Console-Regions](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-console-regions.png)

2.1. **Regions**:
Regions are physical locations where certain services are hosted, there are many regions throughout the world

2.2. **Availability Zone**: 
- Isolated regions
- Collection of datacenters that have separate power, networking and connectivity. But connect with hyper-fast fiber optics.
- AZ are fault tolerant 
- Individual instances are provisioned in AZ

> By scaling your application in several AZ, you can achieve nearly unlimited uptime for your application (reduce latency and single points of failure), satisfy compliance requirements on distance. But, it does not protect against accidental deletion and dchieve the greatest possible fault tolerance and stability. 

### 3. Objects 
S3 is a simple Key-Value store ==> Object-Based 

#### 3.1. Create an object
![Create-Bucket]()

#### 3.2. Open an object
![Open-Object]()

Term      | Definition 
----------|----------
The key   | Name of the object or the file name 
The value | Data which is made up of a sequence of bytes.
Metadata  | Data about data you are storing (the owner of the data, the project that the file is related to)
Version ID| For _Versioning_ and S3 does support version control, you can you can keep multiple versions of the same file 


Object URL  ?????????????
 
### 4. CRUD Operation (Add, delete, modify and update objects)

- When you upload/add a file into S3, you're going to receive an HTTP 200 code when you use CLI or IPA not the Browser
- Transfer acceleration is really just a service which allows you to accelerate file transfer speeds when you're uploading lots of files into S3

### Data Consistency Model
  * Read after Write consistency for PUTS (upload object) of new objects: Access the file as soon as you upload the file 
  * Eventual Consistency for overwrite PUTS and DELETES (can take some time to propagate)

### 5. Durability and Availability  

***Durability***: S3 garantees 99.99% of availablity/accessiblity. It refers to the uptime, the amount of time the service is available. Wich is low for such a service 

***Durability***: S3 guarantees 99.99999999999 durablity. It corresponds to the amount of data that you can expect to lose over a given year. This is way S3 is a safe place

In S3 we can :
- enable version control (keep multiple historical versions of the same file and roll back if you lost your file)
- put in safeguards to prevent accidental deletions
- replicate your data (don't just keep it in one place)
- have a backup of your data, 

### Amazon S3 Advanced Features
Beyond the basics, there are some advanced features, that you can set on buckets like:

### Storage tiers/Classes 

### Lifecycle - To set rules around moving your data between different storage stages.

![AWS-Data-Lifecycle](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Data-Lifecycle.png)

### Encryption 

There are 2 different types of encryption:
1. Encryption in Transit:
- Encrypting the data that you are sending to (upload) and from (download) your packets over the network 
- It is done, using SSL or Transport Layer Security (better then SSL)
- It uses HTTPS Protocol to upload and download the file
2. Encryption at rest:
  2.1 Server Side Encryption: There are 3 different types of encryption for Server Side Encryption
  + S3 Managed Keys - SSE-S3 
    * Object is encrypted with its own unique K using strong multi-factor encryption.
    * An additional step, AWS also encrypts the key itself with the masticate which then they then regularly rotate for you.
    * AWS manages the keys for you
    * It's all a 256 bit
  + Key Management Service, Managed Keys, SSE-KMS
    * AWS managed the key for you
    * It gives an added level of protection against unauthorized access (add an additional key "Envelope key" which encrypts you  data's encryption key)
    * Gives an audit trail, which records the use of your encryption keys 
    * You can use your own key or the default key  
  + Server side Encryption with Customer Provided Keys - SSE-C  
    * AWS manages the encryption and decryption activities
    * You're in charge of administering those keys or rotating them  and lifecyrcle of those keys (you manage your own keys)
  2.2 Client Side Encryption:
    - The client encrypts his files locally by his own before uploading into S3
    - The client choses his own encryption methodology 

If you want to enforce the use of encryption for your files in S3, use a **Bucket Policy** to deny all PUT requests that don't include the **w-amz-server-side-encryption** parameter in the request header 

![Force-Encryption]()

Create a new S3 Bucket, then add a _policy_ to **enforce** the use of _Server Side Encryption_

There are 2 ways to enable encryption:
1. Enable encryption via the _console_ 

`Services > S3 > Create Bucket: Enable Ecryption > ... `
![Create-Bucket-Enable-Encryption]()

2. Enforce encryption on your S3 packet by using an _S3 Bucket Policy_
```
Services > S3 > Create Bucket: Do not Enable Ecryption > ... 

... > Select_Bucket > Permission > Buket Policy > Generate Policy 

// Type of Policy: S3 Bucket Plicy 
// Effect: Deny
// Principal: *
// AWS Services: Amazon S3 
// Actions: PUTobject
// Amazon Ressource Name: ARN (Bucket Name)

> Add Condition
Condition: Select: StringNotEquals
Key: Select: S3-amz-server-side-encryption
Value: Choose between ESA256 or ams:kms

> add condition > add statement > generate policy > Copy code - Paste

// Remarque: You may have an error when you use the policy editor
// Look at the resource section, which is the Amazon resource name 
// Some services do not let you specify specific actions for individual resources. 
// So, add "/*" at the end of the ARN (means that the action will apply to all resources within that service, not just that bucket)

// Create an object and select the RIGHT ecryption method. 
// Otherwise, it will raise an error, S3 forbids any attempts to upload a file without using the specified method of encryption.
```

### S3 Security 
By default, all newly created buckets are _Private_ (only the owner of the bucket gets access to the packet and its contents)
Enable access to your bucket by ==> Bucket Policies or Access control Lists.

The bucket Policiers: 
- Set of permissions that are granted by a policy and are applies at a bucket level, which means to _all of the objects within the bucket_ (can't attach a bucket policy to an individual object)
- Bucket Policies are written in JSon

Access control Lits - Object level: 
- Apply different permissions for different objects within a bucket (define which accounts/groups are granted access and also the type of access)
- Fine grained access control

Track the different access requests that are being made to your S3 objects ==> configure access log, all the activities are logged in a file. These logs can be written to another bucket 




### Cross Origin Resource Sharing (CROS): 

Allowing one resource to access another resource. Exemple, allowing code that is in one S3 pocket to access or reference code that is in another S3 bucket.
- Good way to organize your Web site 

> Static Website Hosting 

### Access to files which are located in one signle bucket via Static Website Hosting

### Step 1: Create a Public Pucket & Static WebSite Hosting

```HTML
Service > S3 > Create a PUBLIC Bucket
// Step Set Permission: Uncheck all of the public access protection 
Select Bucket > Properties > Static Website Hosting 
```
### Step 2: Upload file to this bucket

Upload files to the bucket and Grand Pulic read access to this bucket 

![files]()

### Step 3: Access the page via EndPoint URL 

If all our files have loaded successfully we should be able to access them as though they were a Web site.


### Access to files which are located in different buckets via Static Website Hosting

### Step 1: Create 2 public Buckets
### Step 2: Upload files in the 2 backets 

- Update the path of the file
 - Grant public read access to all files 
 
 <!> An error message can appear: Failed to load ressources (even if the bucket is public) 

![]()

### Delimiter 

![URL](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Object-adressed-by-URL.png)
### Permission
### Hosting options
### Logging


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


### Connection EC2 with CLI

Install the CLI on your PC

1.1 Via Access Key
```Bash
Console > Services > EC2 > Running Instance: Take the Ipv4 Public IP

// Open Terminal 
$ ssh ec2-user@35.135.184.58 -i MyNewKey.pem
$ sudo su 
$ aws s3 ls
  Unable to locate credentials 
  $ aws configure
  // Entry your Access key & Secret Access key that you have already downloaded once the creation of the user
    AWS access Key ID: Access_Key
    AWS Secret Access key: Secret_Access_Key
    // If you leave it blank (you don't specify the region), the S3 Bucket will be in EU West  
    Default Region Name: 
    Default format:
    
// No error message
$ aws s3 ls 

// mb: Make Bucket - Create a S3 bucket
$ aws s3 mb s3://mybucket1-ck
  make_bucket: mybucket1-ck 
  
$ aws s3 ls
  2020-02-17 11:37:00 make_bucket: mybucket1-ck 

// Create hello.txt and copy it into mybucket-ck
$ aws s3 cp hello.txt s3://mybucket1-ck

// List eveything inside the bucket 
$ aws s3 ls s3://mybucket1-ck
  hello.txt
```

1.2 See your bucket 

`Services > EC2`

![]()

If you want to **get away** from AccessKey and SecretAccessKeys ==> ROLE 

1.3 Via Role

`Service > IAM`




### Pricing is based on:
- Amount of data stored per GB
- Number of requests (Get, Put, Copy,...)
- Storage Management Pricing (Inventory, Analytics, Objects Tags)
- Transfer Acceleration (CloudFront to optimize transfers) 
- Per region 
- Data Management Pricing (Data Transferred OUt of S3)

![]()

Use Case: Y
A firm is moving its infrastructure to AWS. 
Their environment consists of a three-tier web application: a web tier, an application tier and a relational database tier. 
They have a separate fleet of virtual machines that are used to access large HPC clusters on the fly. 
Their lab researches run multiple projects simultaneously and they will need to launch and decommission 1,000's of nodes on-demand while reducing the time required to complete genomic sequencing from weeks to days. 
In order to stay competitive they need to do this at as low cost as possible, with no long-term contracts. These HPC clusters can run any time day or night and their workloads store information in S3, so the instances can be terminated at any time without any effect on the data. What is the most COST EFFECTIVE EC2 pricing model for their requirements? SPOT INSTANCES

You run the internal intranet for a corporate bank. The intranet consists of a number of webservers and single relational database running Microsoft SQL Server. Your peak demand occurs at 9am every week morning when users are first logging in to the intranet. They can only log in using the company's internal network and it is not possible to access the intranet from any location other than within the office building for security purposes. Management is considering a change and to move this environment to AWS where users will be able to access the intranet via a software VPN. You have been asked to evaluate a migration to AWS and to identify the best EC2 billing model for your company's intranet. You must keep costs low and to be able to scale at particular times of day. You must maintain availability of the intranet throughout office hours. Management do not want to be locked into any contracts in case for some reason they want to go back to hosting internally. What EC2 billing model should you recommend? ON DEMAND 

You are the IT manager at a furniture retailer and they are considering moving their web application to AWS. They currently colocate their servers in a colocation facility and the contract for this facility is now coming to an end. Management are comfortable signing a 3 year contract and want to get the cheapest web servers as possible while still maintaining availability. Their traffic is very steady and predictable. What EC2 pricing model would you recommend to maintain availability and to get the lowest cost price available? ON RESERVED

You work for a government contractor who supply services that are critical to national security. Because of this your corporate IT policy states that no multi-tenant virtualization is authorized within the company. Despite this, they are interested in moving to AWS, but they cannot violate corporate IT policy. Which EC2 billing model would you recommend that they use to achieve this? DEDICATED 

--------------
### Relational Database Service (RDS)

A collection de service for managed relational databases and infrastructure 
> Managed: AWS takes care of all the backups, software updates. 
> Unmanaged: like installing a database on an EC2 instance, you would then be responsible for figuring out backups, redundancy, updating the software with security 
You can: 
- Take DB Snapshopts 
- Increasing the size 

### RDS Database
Each carries a different price, configuration and connection options

![RDS-Database](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-RDS-Database.png)

### Pricing depends on:
- Type of database
- Region
- EC2 Instance Type 

### Create a DB

```
// Step1: Launch Instance
> EC2 > Launch New Instance > Choose_OS > ...

// Step2: Create Database 
```
![Create-DB]()

```
// Step3: Access EC2 via terminal
Change the hostname in connect.php bye the endpoint 
$hostnam = "DNS Address" 

// Step4: Allow instances to talk to each other

// RDS > Instance > Security Group: select_security_group > Inbound > 
```
![]()

### Access via security groups 



--------
## Lambda
Write (in different languages) simple function and return the result
It can be envoked from many sources

----------
## Identity Access Management
![AWS-IAM-Logo](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-IAM-launch.png)

![AWS-First-steps](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-IAM-first-steps.png)

- Allows you to manage uses users, groups, and roles and their corresponding level of access to the AWS platform 
- It gives you centralized control over your AWOS account
- It also gives you shared access to AWOS account 
- IAM is universal ; it can be viewed and utilized by any region
- It gives you granular permissions :
  + enable different levels of access to different users within your organization
  + Granular enough to limit a single user to the ability to perform a single action on a specific resource from a specific IP address during a specific time window
- It allows you to set up your own password rotation policy it integrates 
- It enables access to store or retrieve data located in an bucket or within a dynamo DB database.
- Integrates with existing your Active Directory account allowing single sign-on
- IAM controls access to AWS ***resources only***, like: Launching an Amazon Linux EC2 instance, (Not Installing ASP.NET that will require Windows operating system authorization),Adding a message to an Amazon SQS queue), (not querying an Oracle database that will require Oracle authorization)

IAM Policy: A JSON document which defines one or more permissions
Active Directory: fournir des services centralisés d'identification et d'authentification à un réseau d'ordinateurs 

Features of IAM that will help you secure your infrastructure, including MFA, rotating keys, federation, resolving multiple permissions, and using IAM roles.
- IAM is not an identity store/authorization system for your applications. 
- For using Active Directory in the cloud is AWS Directory Service, which is an Active Directory-compatible directory service that can work on its own or integrate with your on-premises Active Directory. 
- If you are working with a mobile app, consider Amazon Cognito for identity management for mobile applications.

### Access to IAM 
IAM is controlled like most other AWS Cloud services:

AWS Management Console | CLI | SDK
-----------------------|------|----------
An easy way to start learning | Start scripting repeated tasks using the CLI | Start writing your own tools and complex processes by manipulating IAM directly through the REST API via one of several SDKs.

### Users, Groups, Roles and Policies
![User-Groups-Roles-Policies](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-IAM-Rules-Groups-Policy.png)

## Principals 
A principal is an IAM entity that is allowed to interact with AWS resources. A principal can be permanent or temporary, and it can represent a human or an application. There are three types of principals: root users, IAM users, and roles/temporary security tokens.

### 1. Root USER
- The root user is similar to the UNIX root or Windows Administrator account
- He has complete access to all AWS Cloud services and resources in the account
- The root user can be used for both console and programmatic access to AWS resources
- It's strongly recommended that you don't use the root user for your everyday tasks, and use the root user only to create your first IAM user
 
### 2. IAM USER 
- Set up through the IAM service to represent individual people or applications. 
- You might also create dev, test, and production users for applications that need to access AWS Cloud services (best practice ==> ROLE)
- Users are persistent (no expiration period). But can be removed by IAM administrator
- Users can be associated with very granular policies that define these permissions

### 3. POLE/Temporary Security Tokens 
- Roles are used to grant specific privileges to specific actors for a specific duration of time (15 mn to 36h) (AWS provides them a temporary security token from the AWS Security Token Service - STS)
- Actors can be authenticated by AWS or some trusted external system
- You can write your own policies or use one of the managed policies provided by AWS.

### 3.1 Use Cases

![AWS-Use-Cases](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Authentificaation%20Technologies.png)

#### 3.1.1. Amazon EC2 Roles - Granting permissions to applications running on an Amazon EC2 instance.

**Context**: An application running on an Amazon EC2 instance needs to access an Amazon S3 _bucket_.

**Solution1**: A policy granting permission to read and write that bucket can be created and assigned to an **IAM user**, and the application can use the **access key** for that IAM user to access the Amazon S3 bucket.

  **Problem**: 
  - The access key for the user must be accessible to the application. Probably by storing it encrypted in a configuration file. Obtaining the access key is risky, when being passed around or when the time comes to rotate the access key.

**Solution 2**: 
To create an IAM role that grants the required access to the Amazon S3 bucket. 
When the Amazon EC2 instance is launched, the role is assigned to the instance.
When the application running on the instance uses API to access the Amazon S3 bucket, it assumes the role assigned to the instance and obtains a temporary token that it sends to the API (without worrying about authentication).
There is no fixed access key that must be rotated, because the API access uses a temporary token.

> Using IAM roles for Amazon EC2 removes the need to store AWS credentials in a configuration file.
> The benefits of adding a role: Credentials do not need to be stored on the Amazon EC2 instance and Key rotation is not necessary
> A role must still be assigned a policy

#### 3.1.2 Cross-Account Access - Granting permissions to users from other AWS accounts, whether you control those accounts or not
-  This is highly recommended as a best practice, as opposed to distributing access keys outside your organization.

### 3.3.2 Federation—Granting permissions to users authenticated by a trusted external system.
- IAM Identity Providers provide the ability to federate these outside identities with IAM and assign privileges to those users authenticated outside of IAM.
- IAM can integrate with two different types of outside Identity Providers (IdP).
- Access controlled by policy Temporary Expire after specific time interval

OpenID Connect (OIDC) | Security Assertion Markup Language 2.0 (SAML)
----------------------|----------------------------------------------
For federating web identities such as Facebook, Google, or Login with Amazon | For federating internal identities, such as Active Directory or LDAP, IAM supports integration via

In each case, federation works by returning a temporary token associated with a role to the IdP for the authenticated identity to use for calls to the AWS API.

### Authentification & Authorization
![AWS-Autentification-Authorization](https://github.com/kcelia/Reminder/blob/master/Image_AWS/AWS-Authentification-Authorization.png) 

> IAM user accounts can be further secured by rotating keys, implementing MFA, and adding conditions to policies

### Multi-Factor Authentication (MFA)
- Add an extra layer of security to your infrastructure by adding a second method of authentication beyond just a password or access key.
- It requires entering a One-Time Password (OTP) on a small device (hardware or a virtual device via an app on your smart phone, for example, the AWS Virtual MFA app)
- MFA can be assigned to any IAM user account, whether the account represents a person or application.
 
 
---------
## AWS Elastic LoadBalancers
- Create a Domain Name 
- Balance or load across multiple services to not overwhelmed a server or crash you application
- Use Cases: 
  + You got several web servers and you want to equally balance the load between them
  
![AWS-Types-of-load-balancers]()

### Error ELB

ERROR | 504 
------|-----
The *Classique LB* reponds with Error X when | Gateway timeout error - Application stops reponding, maybe because of, application or Web server Layer or Database Layer issues | 
Solution | Identify where the application is failing, and scale it up or out where possible 

### X-Forwarded_For
If you need the IP4 Address of your end user, look for the X-Forwarded-For Header. 

![DNS-Request]()

Use Case: You work for a web analytics firm who have recently migrated their application to AWS. The application sits behind an Elastic Load Balancer and it monitors user traffic to their website. You have noticed that in the application logs you are no longer seeing your users public IP addresses, instead you are seeing the private IP address of the elastic load balancer. This data is critical for your business and you need to rectify the issue immediately. What should you do?
---------
## Route53 

> Domain Name system: translates human-readable URLs to IP addresses

- Is Amazon's DNS Service Network, both inside and outside AWS
- Route53 or LoadBalancers don't have visible IP addresses (a verifier)
- Allows you to map your _domain names_ to **EC2 Instances, Load Balancers and S3 Buckets**. Which means, that R53 essentially allows you to buy a domain name (XXX.com) and then we'd be able to connect that domain name to 3 different services  EC2, LB or S3.

1- Enregister un Domain
2- Enregister a Hosted Zone 

### 1. Create a Domain Name

Create a working Web site, behind an application Load Balancer which is spread across
multiple availability zones. Then when we go to resolve the name XXX.com, that's basically sending traffic to our application. Load Balancer which is sending traffic to our EC2 instance.

```bash
Console > Services > Network: Route53 > DNS Management: Get started Now > 

// If there is no Hosted Zone, register a DOMAIN 
// Hosted Zone: Root Domain Name, like google.com 

// 1.Enregister un Domaine 
> Registered Domains > Register Domain > Choose a domain name: XXX.Select-Domain 
> Check > Add to card > Continue > Contact Details For Your 1 Domain: Fill out 
> Agree & Complete Purchase > Go to Domain

// It might take up 3 days to co mplete

// 2.Hosted Zone
Dashboard > DNS Management > Hosted Zone > Select_your_Domain > Go To Record Sets 
// The records sets: Where we create our DNS records 
// If you use a naked Domain Name, Select an ALIAS 
// Select your record, according on whether EC2, ELB, or S3 is selected 
// Here, we select ELB 
```
![Record-set](https://github.com/kcelia/Reminder/blob/master/Image_AWS/R53-Create-Record-Set.png)
```Bash
// Check the region if you do not see your instance running 
> EC2 > LOAD BALANCING > Load Balancers > Create Load Balancer: Choose a LB
```
![ELB-Create-LB](https://github.com/kcelia/Reminder/blob/master/Image_AWS/ELB-Create-LB.png) 

```Bash
// Dashboard > DN Management > Hosted Zone > Select_Hosted_Zone > Go To Record Sets
> Create Record Set > Select_Alias_ELB

// Finaly, we have created a working Web site it's behind an application LB which is spread across multiple availability zones And then when we go to resolve the XXX.DN that's basically sending traffic to our application LB which is sending traffic to our EC2 Instance

> Brower > XXX.DN > Result
// Alors, que précedement on entrait l'adresse IP 
```


### Pricing
Prices depend on the number of created Hosted Zone and the amount of requests 
### Health checks 

## Elasticache 

> Purpuse:
>> Cache your most frequently used queries from your database.  
Your DB is under a lot of stress/load, read heavy, not prone to frequent changing
>>> Instead of putting data in your database, we put it in _Elastic cache_ and that takes a bit and it takes a lot of load off your production DB.

- Elasticache is a web service that makes it easy to deploy, operate and scale and in-memory cache in the cloud.
- The service improves the performance of web applications by allowing you to retrieve information from fast managed in-memory caches instead of relying entirely on slower disk-based databases.
- Improve latency for many read heavy application workloads (intensive database queries, computationally intensive calculations)
- ElasticCache supports master/slave replication and Multi-AZ which can be used to achieve cross AZ redundancy, with Redis

### Types of Elasticache

Type of ElastiCache | Memcached | Redis 
--------------------|-----------|------
Definition | Widely adopted memory object caching system.ElastiCache is a protocol compliant with Memcached | A popular open-source in-memory key-value store that supports data structures sorted sets and lists
Difference |  | Multi-AZ
Simple, Pure caching solutionto offload the DB, no persistence, not concerned about redundancy, scale cache horizontally (provides additional capabilities like automatic node replacement and auto discovery) | Relation DB, persistant, stateful entity, include failover (like AWS RDS does), store advanced data types (lists, hashes, sets), does sorting and ranking datasets in memory (like leaderboards), multi-AZ, Pub/Sub capabilities 

Similar on the surface : Both are Cache In-memory key Stores 

### ElastiCache Vs Redshift 
ElastiCache | Redshift 
------------|-----------
If your database is feeling stressed, because management running online analytics processing transactions on it ==> Data Warehousing question | OLAP - Take stress off your database, because it's very heavy 

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




