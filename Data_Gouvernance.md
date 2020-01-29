> Goal 
>> Etre un _Data Driven_ (axé sur les données) et faire de _l'analytics to action_ (connecter l'analyse à l'action)
>> Make a Data Driven argument (décisions commerciales/... axées sur la donnée)
>> Consider la donnée comme un atout dans une organisation est un défi

### Pour être Data driver, l'organisation a besoin de trois choses: 
- savoir d'où viennent les données;
- savoir ce que signifient les données;
- savoir si les données sont exactes.

## La donnée
- Stratégique active car elle ajoute une valeur commerciale à l'entreprise.
- Se doit d'être _fiable_, sinon ==> décision biaisée qui peut mener un **Data Browl** (barrage).
- The estimated cost of bad data for US businesses is $700 billion a year.
- Questions that are raised:  
  * D'où vient-il? 
  * Qu'est-ce que ça veut dire? 
  * Quelles mesures lui ont été appliquées? 
  * Qui peut y accéder? 
  * Est-ce correct? 
  * Comment puis-je le réparer? 

### Comment surmonter cela?  --> Configurer une organisation avec des processus.

# Data gouvernance

![Data_Gouverance_Vs_Data_Transaction](https://github.com/kcelia/Reminder/blob/master/Master_Data_VS_Transaction_Data.png)

Un système décisionnel partagé pour reconnaître la valeur des données (la démocratisation des données).
La DG est un processus défini et spécifique qu'une organisation suit pour évaluer, gérer, utiliser, améliorer, surveiller, maintenir et protéger les données organisationnelles afin de générer des résultats commerciaux. La DG consiste à décider de la signification des données, de leur utilisation, de leur exactitude et des règles à suivre. 

Le modèle est :
- Spécifique à l'organisation
- Fexible et conçus pour les business users et data stewards (gestionnaires de données)
* Plays a big role in this new data driven mindset goal
* DG is a decision making, monitoring and enforcement body that has authority over Data management
* DG is deciding what to do about data and following up to make sure it's done.

La gouvernance:
+ Nécessaire à cause des 3Vs, des risques des prises de décisions sur les données, les besoins en confirmité... 
+ Garantir la sécurité et la fiabilité des données dans un environnement _hybride_ complexe (_Cloud_)
+ Trouver un compromis entre les besoins impératifs (innovation et agilité) et les contraintes/régulation
+ Plusieurs metiers qu'on peut cartographier la structure organisationnelle au sein de l'organisation dans une matrice RACI : la transparence dans la propriété et la responsabilité (Data Steward, Data Custodian, Data Owner, Data Producer...
) de qui serait responsable. 
 * Data Owner:
 - S’implique dans l’*acquisition et l’appropriation d’un ensemble de données*, il ne s’occupe pas de la conservation des données et de leur recensement 
 * Data Steward/Gardien de l’organisation des données/Gestionnaire de données:
  D'un point de vu consommation:
  - A une visibilité globale sur un projet d’acquisition
  - Contrôle la cartographie des données et de leur gestion (collecter/sécurisé/mesurer la qualité de la donnée). 
  - Responsable référent dans un projet de gouvernance des données
  - Travaille avec les équipes business pour définir les objectifs du projet de gouvernance des données.
  - Capablede reporter les problèmes/escalade
  Dans point de vu technique/Data technical Steward:
  - Il peut etre un data architect, ingineer, quelqu'un qui travaille un peu plus granulairement sur les aspects techniques du cadre de gouvernance du point de vue de l'architecture
  - Oriente les Data Scientist et BI a trouver les bonnes données
  - Tenu responsable de la mise à jour des changements au fil du temp
 * Data Consumers:
 - Est une unité commerciale
 - Gère les activités commerciales (À un moment donné, nous sommes des consommateurs de données)
 * Data financial Analyst/Analyste Financier: Parle des opérations et de marketing.

Néanmoins, la gourvernance :
  - Peut limiter des accès à des users
  - Toute la donnée n'a pas besoin d'être gouvernée de la même façon
  - Les services informatiques seront toujours impliqués dans la DG, mais les user métier sont des partenaires égaux dans le système et peuvent mener des analyses et des BI en libre-service. 
  - Il existe un certain risque autour de l'implémentations de la DG
  
> DG is made up of "Policy + Process + Rules"

### Dimension de la GD  
 - La QD 
 - La précision
 - L'exhaustivité 
 
### Process: 
Quelle valeur la gouvernance des données apportera-t-elle à votre organisation? (qui, quoi, quand, où, pourquoi et comment)

# Relation with the Data Mangement 
DM is the control of data architecture, quality, policy, security, practices and procedures. 
It allows us to ensure that shared information is accurate (correct), consistent and secure.
DM takes the decisions of DG and implements the architectures, process, tools and policies

# Data Gouvernance Center (DGC)
Un système d'enregistrement qui permet de se logger dessus et d'avoir un enregistrement clair pour tout élément de données donné. Ainsi, on sait d'où provient le rapport et qui est le propriétaire des informations. 

## Collibra Data Governance Center : Plateforme de gouvernance de données (Collibra implementation Method - CIM)
-  Le Chemin Prescriptif: vous aidera à mettre en œuvre, à développer votre maturité!
CDGC comprend sept applications classées par fonction.

## 1. Le catalogue et le dictionnaire de données: Aident à trouver d'où proviennent les données.
### 1.1 Le catalogue: 
- Chercher des données
- Inventaire des données (emplacement centralisé), y compris les attributs qui indiquent les définitions de qualité et la ligné.
- S'intègre à Tableau.
- Dans crowdsourcing: Les utilisateurs sont en mesure de fournir un examen des notes, d'étiqueter et d'annoter différents ensembles de données. Comment vos collègues utilisent les mêmes ensembles de données et comment ils recommandent leur utilisation. 
- Identifier les ensembles de données adaptés à leurs besoins.
### 1.2 Dictionnaire
 - Documente les métadonnées techniques, la façon dont elles sont utilisées. 
 - Contenient les définitions des données, des colonnes et des noms de table. 
 - Intérogeable (montrera combien de systèmes le changement aura un impact)
 - Généralement, un dico existe déjà dans une base de données et il suffit de l'importer dans la DGC.
## 2. Le glossaire métier et les données de référence:  Aident à comprendre la signification des données. 
### 2.1 Glossary:
- Ens de terminologies commerciales, de taxonomies et d'autres hiérarchies, et comment elles diffèrent selon les différents domaines d'une organisation.
- Liste de tous: les actifs approuvés, KPI, BR, acronymes mis à la disposition de la communauté des utilisateurs, regarder des domaines comme le catalogue de rapports clients.
- Glossaire métier élaborer lors du démarrage du programme de GD et évolutif.
- Définir des termes commerciaux, descriptions/contexte significatifs, la politique de l'entreprise.
- Un Glossaire métier permet de garantit que chacun utilise le bon terme et la bonne définition dans le bon contexte pour ses besoins (clarté et similitude au sein d'une entreprise).
- `> traçabilité`: Plus de détails, donne:
   + Une visualisation qui aide à comprendre la valeur à vie et comment elle est définie dans différents contextes.
   + Comment un terme commercial est défini dans différents contextes (c.-à-d. Finance et marketing)
   + Définitions, exemples descriptifs et synonymes s'ils sont attribués
   + Statut de l'actif
- `> Quality`: Voir le score de qualité des données pour ce terme commercial
   + Le nombre de règles a échoué/adoptées et score de qualité et le résultat
### 2.2 Données de référence
 - Opérationnalisent vos données. 
 - Garantit des normes cohérentes pour vos données de référence. 
 - Montre comment les données sont organisées, classées et connectées, ce qui donne à l'utilisateur en libre-service une plus grande précision pour les rapports et l'analyse.  
## 3. Policy Manager, Data Helpdesk et Stewardship: Permettent de savoir que les données sont correctes et fiables. 
### 3.1 Policy Manager: 
- Fournit un moyen de définir facilement les stratégies, leur signification et le domaine qu'elles affectent. 
- Aide à créer/réviser/mettre à jour vos politiques de données au fur et à mesure de leur adoption et de leur mise en œuvre dans toute l'organisation. Par exemple, tout le monde peut voir l'impact de la confidentialité et de la sécurité des données en ce qui concerne les différents actifs de données. 
- Il offre transparence et confiance en comprenant que les bonnes politiques et règles métier ont été appliquées, et se traduira par le respect des règles organisationnelles ou des rapports réglementaires.
### 3.2 Data Helpdesk: 
- Permet à tout utilisateur de se connecter rapidement et de suivre les problèmes/escalades de données (des workflows existent)
- Garantit que la résolution des problèmes est une priorité et prise en charge en temps opportun.
### 3.3 Stewardship  
- Synchronise vos données citoyens. 
- Il aide les administrateurs de données à gérer vos tâches quotidiennes et à collaborer avec les parties prenantes de l'organisation. 
- Il offre une propriété et des responsabilités transparentes pour le partage des données dans l'entreprise. 
- Il permet d'établir une structure organisationnelle comprenant des escalades, des hiérarchies, des contacts de propriété et des responsabilités. 


## CIM se compose de cinq phases différentes:
1. Phase de préparation/Prep-Project Startup:
  - Define project goals/Plan
1. Phase de conception/Blueprint/Design:
 - Workshop
1. Phase de configuration et de construction/Configuration & Build:
1. Phase de préparation finale/Final Preparation:
1. Phase de transition/Transition/Post Go-Live Support:

# Steps:

## 1. Créer une communauté:
- La composante organisationnelle racine est la communauté. 
- Communities represent different groups of people who own certain domains.
 ```bash
  Dashborad > Create > Organization > Community > 'NameCommunity' > Create
  // Nom unique et sensible à la casse, apparaitera dans le Browser
  // On peut créer simultanément plusieurs communautés
  // Une communauté est souvent organisée de la même manière qu'une entreprise
  ```
 ### 1.1 Créer une sub-communauté:
- To reflect a business or division of a company.
- To define ownership over a collection of assets for a group of PMEs.
- To focus and partition data governance efforts for a group of people.
-  Il existe 2 façons de créer une communauté:
    a. `Dashborad > Organization > 'MainCommunity > 'NameSubCommunity' > Create`
    b. Depuis la page parent: `'ParentPage > Create > Organization > 'NameSubCommunity'`

Une fois la communauté crée, il faut ajouter des actifs/assets, qui sont regroupés dan sune structure logique "Domaine".

## 2. Create a Domaine to add business terms
Une communauté peut avoir plusieurs domaines.

   2.1. Create Glossary Domain: 
     ```bash
     'NameCommunity' > Create > Organization > Glossary > 'Fill out: Glossary's name/...'
     // Remarque: Si le domaine est créer depuis le Dashborad, il faut préciser la Communauté 
     ```       
    2.2. Create Policy Domain: Gouvenance/Série de politiques de règles
    2.3. Organisation (sub-community)
    2.5. Catalogue de rapport: (collection de rapports/définitions avec la liste des attributs)

## 3.Assets/Actifs (Business Rules + Acronym).
- Ces actifs vont être organisés à l'intérieur de ces communautés et domaines.
- Représentent les *composants structurels* du modèle d'exploitation. 
- Les actifs sont souvent regroupés selon leur *fonction, leur projet ou leur domaine de connaissances*.
- Il existe 5 types d'actifs: 
 + actifs commerciaux
 + actifs technologiques
 + actifs de données
 + actifs de gouvernance
 + actifs des problèmes
- Les actifs sont: des termes commerciaux, des acronymes, des politiques, des colonnes, des tableaux, des schémas, vraiment tout ce que vous voulez définir, gouverner et boucler, et valoriser en tant que actif, est un atout au sein de Collibra.

### Caractéristiques (Attribut + Relation)
### 3.1 Attribut(description textuelle)
![Exemple_Attribut](https://github.com/kcelia/Reminder/blob/master/Attribut_type.png)

Les actifs ont des caractéristiques différentes appelées attributs, et ces attributs peuvent avoir des relations différentes.
#### 3.1.1. Les types d'attribut (décrit l'actif):
- Un attribut est une valeur littérale qui capture des informations sur un actif et un attribut est une instance d'exactement un type d'attribut. 
- Un type d'attribut définit formellement la classe d'informations contenue dans un attribut. 
- Create: 
   ```bash
    Acronym/Asset> Add Characteristic> Attibuts > 'Type Attribut'
    // Tags: Trouver d'autres articles similaires
    ```
  Exemple 1: Un terme commercial de type d'actif portant le nom client a une description de type d'attribut avec la valeur de la personne qui a passé au moins une commande pour au moins un produit. 
  Exemple 2: Un actif peut être appelé cheveux, mais les attributs peuvent être de couleur, de longueur, de texture, etc.
#### 3.1.2. Import/Export Attribut
   Import: `NameGlossary > Export > Add the Characteritics Needed For reimport > Export`
   
   Export: `Import_Icon > Assets > 'Select File' > Next > Update the Name`
   
### 3.1.3. Load Attributs that did not exist in Collibra
1.  La première étape consiste à créer un point d'atterrissage à Collibra pour ce glossaire: 
    ```bash 
    // 1. Community
    Dashbord > Create > Organization > Cummunity > 'Fileout'
    // 2. Glossary Domain
    NameCummunity > Create > Organization > Glossary > 'NameGlossary' 
    // Vérifier lors du chargement du domaine comme un glossaire quels types d'actifs
    // Add a column "Type: Business Term/..."
    // 3. Import
    'NameGlossary' > Import_Icon > Assets  > Select File > Next > ... > Import
    // Option de mappage 
    // Keep the: Test import 
    ```
1. Create column/Attribut's file qui ne sont pas présents dans collibra: 
   ```bash
   'NameCommunity' > CreateDomainGlossary > Modify_View > Select_columns 
   'Name Community' > Settings > Charistics > Attributs > Add > 'Name/Description/Kind:Number... '
   // Si les attributs souhaités ne sont pas dans Select_Columns 
   ```
1. Assignement 
Avant de pouvoir utiliser les attributs nouvellement crées, il doivent être _Attribué/assigné en tant que caractéristique valide au (x) type (s) d'actifs souhaité (s)_
 ```bash
Settings > Asset Typpe > Business Term > Global Assignement > Edit > Add cheristics > 'attribut' 
// Dans global Assignement:  Liste principale de tous les attributs
// Changer l'ordre d'affichage
 ```
 1. Complete the view and Save it 
 1. Import file 
 
### 3.2 Relation. 
- Définit association entre deux actifs, comment ils sont liés l'un à l'autre. 
- Instance d'un type de relation. Un type de relation est bidirectionnel. La source et la cible d'une relation sont deux types d'actifs.
- Create: 
   ```bash
    Acronym/Asset> Add Characteristic> Relation > 'Type Relation' > 'Edit' 
    // Tags: Trouver d'autres articles similaires
    ```
Exemple: 
- les relations entre les actifs sont tout ce qu'un terme commercial est synonyme d'un autre terme commercial
- une colonne fait partie d'un tableau
- une politique est appliquée par une norme

#### 3.2.1 Load Relations 

1.  Landing Zone: 
    ```bash 
    // 1. Community
    Dashbord > Create > Organization > Cummunity > 'Fileout'
    // 2. Glossary Domain1 
    NameCummunity > Create > Organization > Glossary > 'NameGlossary' 
    // Si la relation n'existe pas dans Collibra, crée un Domain
    // 3. CodeList Domain2 for the relation
    'NameGlossary' > Create > Organization  > CodeList > 'NameCodeList'
    ```
 
 Lors du chargement d'une relation, vous devez d'abord décider de quel côté vous chargez (Sens de la relation).
 
    
 1. Editans save View 
    A. Racine (domaine 1):
    ```bash
    > ParentPage > 'NameGlossary1' > Columns_and_Rows_Icon > Columns > Relation > Eg:Has code Value
    Public > Make this default vieux > Pin
    ```
    B. La queue (domaine 2)
    ```bash
    ParentPage > NameCodeList > Columns and Rows_Icon > Columns > Edit > Relation > Code_Value_is_code_for a     Business Term
    ```
 1. Edit file: 
 - Establish Source/Nil
 - Domain and Type for each Assets
 
 1. Import File
 `> Import > Assets > Select_File > Mappage > Next > Test_Report`
 
### 3.1 Create Business Terms 
Business Terms are case sensitive and can be characterized with acronyms.
 a. `ParentPage > Create > Assets > Business Terms` or `DashBorad > Create > Suggested > Business Term > 'Fill out: Term1, Term2, ... In Domain: NameGlossary`
 Remarque: Si les termes commérciaux existent déja dans un fichier Excel, l'importer `> Import my assets > Find file` 
   `'NameGlossary' > Overview > Characteristic > ... // Add synonym or ...`
 b. Approval for each created BR
 `Traceability > Diagram // To see the relations`
  `> Workflows > Approval // Depends on the assigned responsability `
### 3.2 Create Acronym
 Create: `ParentPage > Create > Assets > Acronym > 'Fill out: NameGlossary/NameAcronym'`

### 3.3 View pour plus de détails
Cim propose une view par défaut mais on peut en créer à droite : 
```bash
NameGlossary > Save as > 'Fill out: NameView/ViewSharingOptions'
// Promote View: Make this default view or/and Pin this view
```

- Les vues sont indépendantes ce qui permet de voir les choses de différentes manières.   
- Permettent de filtrer les colonnes ou lignes inutiles pour visualiser uniquement ce dont vous avez besoin.
- Conserve la vue d'origine pour revenir si nécessaire.

### 3.3.1 Exporter une vue
 Exporter: 
 ```bash
 ParentPage > Export_Icon > Assets > 'Fill out'
 // Select View
 // Add the characteristics needed for re-impor: Alignement correcte
 // Name the file 
 // Select type file
 ```
Remarque: A l'ouverture du fichier importer, une nouvelle colonne est ajoutée UUID, sous chacun des domaines et communautés. 
### 3.3.2 Importer
```bash
ParentPage > Import_Icon > Assets > 'Select_file' > Import
// Si erreur de UUID, clique Next
```
1. Définir des responsabilités et la gestion de l'ensemble de la matrice RACI 
  Stewardshi's application/ Module d'Intendance establishes the responsabilities
  `> Stewardship > 'Name Community' > Responsabilities > Role...`
   
1. Add technical metadata to the catalog (the structure of a schema)
  ```bash
  > Catalog > Data Dictionary > Create > 'Create Catalog Data set' or 'Ingest From Data source'
  // Create Catalog Data set: Logical Dataset
  // Ingest From Data source: Il existe plusieurs gamme de systèmes (Excel, Cloudera, ...), le schema est le même que celui du serveur
  ```
  a. Select a set of columns to create a new dataset
  Create a logical Dataset on top on of the phycical metada: `Select columns > Add To Data Set > New Data Set > 'Fill out' > Create & Add Data`
  b. Ask for approval:  `Overview > Characteristic > Related To > 'Fill ou/Tags...`
  c. Présentation: *Asset Model* (top attributs customized)
1. Create a domain for Policy Manager
a. Créer le domain
 ```bash
 Browser > 'Name Community' > Create > Organization > Placy Domain > 'Fill out' > Create 
 // On peut avoir différentes politiques dispersées dans les différents secteurs d'activité 
 ```
 b. Ajouter un index dans toute l'oganisation dans *Policy Manager*
 > Policy Manager > Create > Policy > 'Fill out/in the 'Name Domain'/add responsabilities...'

  In order to link a data set to a particular policy, the following steps are required:

  1. Within the relevant community>Create Organization>Policy Domain
  1. In Policy Manager>Create Policy
  1. Set Responsibilities

On peut dire que la politique est applicable à un ensemble de données,
 
1. Crete a Policy Manager 

1. Shop 
`Search > Add To Data Basket` then `Request Data Sets Access`
Lorsque nous extrayons ces données, nous allons à nouveau parcourir un workflow: Demander à différentes personnes de vérifier les choses (la licence/politique/...) liées liées à cet ens dd **Policy Manager" 

1. Log an issue in Data Helpdesk

En tant que user: `Acceuil > Quick Actions > Log Data Issue > 'Fill out'`

En tant que Data Steward: 
```Bash
> Data Helpdesk > 'Issue's List' 
// le DS peut faire une hiérarchisation
// Ajouter plus de colonnes pour plus d'information
```

1. Customized dans Settings

Eg. Ajouter l'attribut cost:
```bash 
> Settings > Attributes > Add > 'Fill out' > Save 
// On peut ajouter l'attribut Cost aux asset types
> Assignment > Data Set > Data Set Attributes > Edit > 'Fill out' > Save
```

 https://university.collibra.com/lessons/introduction-to-working-with-assets/
