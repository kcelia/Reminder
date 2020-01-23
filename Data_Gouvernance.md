> Goal 
>> Etre un _Data Driven_ (axé sur les données) et faire de _l'analytics to action_ (connecter l'analyse à l'action)
>> Make a Data Driven argument (décisions commerciales/... axées sur la donnée)

### Pour être Data driver, l'organisation a besoin de trois choses: 
- savoir d'où viennent les données;
- savoir ce que signifient les données;
- savoir si les données sont exactes.

## La donnée
- Stratégique active car elle ajoute une valeur commerciale à l'entreprise 
- Se doit d'être _fiable_, sinon ==> décision biaisée qui peut mener un **Data Browl** (barrage).
- Questions are raised:  
  * D'où vient-il? 
  * Qu'est-ce que ça veut dire? 
  * Quelles mesures lui ont été appliquées? 
  * Qui peut y accéder? 
  * Est-ce correct? 
  * Comment puis-je le réparer? 

### Comment surmonter cela? --> Configurer une organisation avec des processus.

# Data gouvernance

Un système décisionnel partagé pour reconnaître la valeur des données (la démocratisation des données).
La DG est un processus défini et spécifique qu'une organisation suit pour évaluer, gérer, utiliser, améliorer, surveiller, maintenir et protéger les données organisationnelles afin de générer des résultats commerciaux. La DG consiste à décider de la signification des données, de leur utilisation, de leur exactitude et des règles à suivre. 

Le modèle est :
- Spécifique à l'organisation
- Fexible et conçus pour les business users et data stewards (gestionnaires de données)
* Plays a big role in this new data driven mindset goal
* DG is a decision making, monitoring and enforcement body that has authority over Data management
* DG is deciding what to do about data and following up to make sure it's done.

La gouvernance:
- Nécessaire à cause des 3Vs, des risques des prises de décisions sur les données, les besoins en confirmité... 
- Garantir la sécurité et la fiabilité des données dans un environnement _hybride_ complexe (_Cloud_)
- Trouver un compromis entre les besoins impératifs (innovation et agilité) et les contraintes/régulation
* Plusieurs metiers: Data Steward, Data Custodian, Data Owner, Data Producer...

Néanmoins, la gourvernance :
  - Peut limiter des accès à des users
  - Toute la donnée n'a pas besoin d'être gouvernée de la même façon
  - Les services informatiques seront toujours impliqués dans la DG, mais les user métier sont des partenaires égaux dans le système et peuvent mener des analyses et des BI en libre-service. 
  - Il existe un certain risque autour de l'implémentations de la DG
  
> DG is made up of "Policy + Process + Rules"

## Dimension de la GD  
 - La QD 
 - La précision
 - L'exhaustivité 
 
# 4 elements d'une bonne gouvernance 

## Comprendre
-  Le fait d'être guidé par les données influence la culture, les processus décisionnels
- Connaissance métier
- Savoir comment les intègrer 
- Elaborer une stratégie de gestion des métdonnées pour comprendre le format des données
## Mise à jour 
- Donner un accès a bas coût et avec des capacités de calcul infinies (Cloud) 
## Proteger 
## Intégration 
- Tranformer la donnée en y mettant de la gouvernance et la présenter de la meilleure manière qui soit

# Relation with the Data Mangement 
DM is the control of data architecture, quality, policy, security, practices and procedures. 
It allows us to ensure that shared information is accurate (correct), consistent and secure.
DM takes the decisions of DG and implements the architectures, process, tools and policies

## Data Gouvernance Center (DGC)
Un système d'enregistrement qui permet de se logger dessus et d'avoir un enregistrement clair pour tout élément de données donné. Ainsi, on sait d'où provient le rapport et qui est le propriétaire des informations. 

## Collibra Data Governance Center : Plateforme de gouvernance de données
-  Le Chemin Prescriptif: vous aidera à mettre en œuvre, à développer votre maturité !

CDGC comprend sept applications classées par fonction.
- Le catalogue et le dictionnaire de données: Aident à trouver d'où proviennent les données.
  - Le catalogue:       
      - Inventaire des données (emplacement centralisé), y compris les attributs qui indiquent les définitions de qualité et la ligné.
      - S'intègre à Tableau.
      - Dans crowdsourcing: Les utilisateurs sont en mesure de fournir un examen des notes, d'étiqueter et d'annoter différents ensembles de données. Comment vos collègues utilisent les mêmes ensembles de données et comment ils recommandent leur utilisation. 
      - Identifier les ensembles de données adaptés à leurs besoins.
  - Dictionnaire
      - Documente les métadonnées techniques, la façon dont elles sont utilisées. 
      - Contenient les définitions des données, des colonnes et des noms de table. 
      - Intérogeable (montrera combien de systèmes le changement aura un impact)
      - Généralement, un dico existe déjà dans une base de données et il suffit de l'importer dans la DGC.
- Le glossaire métier et les données de référence:  Aident à comprendre la signification des données. 
  - Glossary:
      - Glossaire métier élaborer lors du démarrage du programme de GD et évolutif.
      - Définir des termes commerciaux supplémentaires, descriptions/contexte significatifs, la politique de l'entreprise.
      - Garantit que chacun utilise le bon terme et la bonne définition dans le bon contexte pour ses besoins.
  - Données de référence
      - Opérationnalisent vos données. 
      - Garantit des normes cohérentes pour vos données de référence. 
      - Montre comment les données sont organisées, classées et connectées, ce qui donne à l'utilisateur en libre-service une plus grande précision pour les rapports et l'analyse.  
- Policy Manager, Data Helpdesk et Stewardship: Permettent de savoir que les données sont correctes et fiables. 
  - Policy Manager: 
      - Fournit un moyen de définir facilement les stratégies, leur signification et le domaine qu'elles affectent. 
      - Aide à créer/réviser/mettre à jour vos politiques de données au fur et à mesure de leur adoption et de leur mise en œuvre dans toute l'organisation. Par exemple, tout le monde peut voir l'impact de la confidentialité et de la sécurité des données en ce qui concerne les différents actifs de données. 
      - Il offre transparence et confiance en comprenant que les bonnes politiques et règles métier ont été appliquées, et se traduira par le respect des règles organisationnelles ou des rapports réglementaires.
  - Data Helpdesk: 
      - Permet à tout utilisateur de se connecter rapidement et de suivre les problèmes/escalades de données (des workflows existent)
      - Garantit que la résolution des problèmes est une priorité et prise en charge en temps opportun.
  - Stewardship  
    - Synchronise vos données citoyens. 
    - Il aide les administrateurs de données à gérer vos tâches quotidiennes et à collaborer avec les parties prenantes de l'organisation. 
    - Il offre une propriété et des responsabilités transparentes pour le partage des données dans l'entreprise. 
    - Il permet d'établir une structure organisationnelle comprenant des escalades, des hiérarchies, des contacts de propriété et des responsabilités. 
