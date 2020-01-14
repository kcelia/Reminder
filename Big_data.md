1. 
      | Structurée | Semi-structurée | Non structurée 
------|-----|-----|----
Exemple | Basé sur les tables de BDR (SQL) | Basée sur XML/RDF| Basé sur des caractères et des données binaire (Word PDF, Texte, Logs)
Flexibilité     | Moins flexible      | Plus que les DS et moins que les DNS | Trés flexible
Mise à l'echelle| Difficile           | Plus simple que les DS               | Très facile
Schéma          | Oui                 | Oui                                  | Non


File Systèm:

- Hierarchichical file system (HFS) : Local file system 
- New Technology File System (NTFS) : : Local file system 
- Compact Disc File System (CDFS)

Each file in the LFS is includes by an inode, blocks of data. 

# Base de données **Relationnelle** 

- Les BDRs étaient une **référence** jusqu'au année 70 ;

- Le stockage des données est représentée en ligne (l'ensemble des attributs) ;

- Les données sont de nature structurée et simple ;

- Faire des jointures entre les tables de la BDs ;

- Faire des requêtes complexes avec un langage de haut niveau sans se préoccuper des couches basses ;

- Structured Query Language (SQL) : utilisé par les SGBDRs, tel que :MySQL (open-source database), SQl -SERVER , ORACL ...

- Gérer l'intégrité des données de manière **infaillible** (garantir le contenu de la BD, quelles que soient les MAJs, ainsi que sa pérennité - la cohérence).

-----------------------------------------------------

## Propriétés **ACID** pour les transactions (séquences d'opérations/requêtes) :

- **Atomicité** : Une transaction s’effectue entièrement ou pas du tout
- **Cohérence** : Le contenu d’une base doit être cohérent au début et à la fin d’une transaction
- **Isolation** : Les modifications d’une transaction ne sont visibles/modifiables que quand celle-ci a été validée
- **Durabilité** : Une fois la transaction validée, l’état de la base est permanent (non affecté par les pannes ou autre)

----------------------------------------

Néanmoins, l'écriture en base SQL est un goulot d'étranglement ("**bottleneck**") insurmontable. Elles ne peuvet pas supporter un grand nombre d'écritures concurrentes. 

#### Solution_1 _ARBRE_B_ : 

L’index le plus utilisé est l’arbre B (ou BTree), il adopte une structure arborescente pour chercher toute valeur indexée. Les feuilles de cet arbre contiennent des liens vers les pages contenant la valeur. 

#### Solution_2 _SHARDING_: 

Répartir les lignes de la TABLE sur différents serveurs. Mais cela rend l'administration (ajout/maj) plus complexe  et source de bogues.

Une _shard_ : est une partie de la table.

#### Solution_3 _Stockage semi-structurées_:

- Fichier semi-structurées : Xml, Jason ;
- Peu coûteux, à condition de compresser les fichiers ;
- Ne permettent pas l'évolution du schéma des données.

-------------------------------------------------------

# Big Data = Mégadonnées

    1941 : Explosion de données
    1950 : Alain Turing
    1980 : Loi de Parkingson (la capacité de stocage augmente exponentiellement)
    1990 : La démocratisation d'internet

Big Data, Désigne :

- La production de données massives
- Le développement de technologies capables de les traiter afin d’en extraire des corrélations ou du sens.

Il définit par les 3V : 
 
- **Volume**   : Stockage de données (dû à la numérisation)
- **Velocity** : Visualisation, traitement des données en temps réel
- **Variety** : Données hétérogènes et variées
        - Structured : Xml
        - Semi Structured : E-mails
        - Ustractured : Video files
        
> Un problème est dit Big data, si une caractéristique est présente!

    ##  Google File System

    GFS splits data into chuncks, wich are distributed an duplicated to different nods in a cluster
    > Distrtibution and replication protect against data lose  

    ## Bigtble(database)
    
    A database that use GFS to store and treat data 
    ###  MapReduce + GFS (pagerank)
   
----
Solution __NoSQL__ : 

- Le **passage à l'échelle** via la **réplication** et la **distribution** des données
- Nouvelle structure de données
- Plus de relationnel
- Une nouvelle manière d'**interroger** les données et de 
les **stocker**
- La **réplication** **empêche** la gestion **concurrentielle** de transactions et la distribution de calcul lourd est propre à Map/Reduce et non les langages de plus haut niveau utilisés dans les solutions NoSQL.
- Une base NoSQL **relâche** certaines **contraintes**, telles que la **synchronisation** des réplicas, pour favoriser l'efficacité. 

----
## Propriétés **BASE** des BDs NoSQL :  

- **Basically Available** : quelle que soit la charge de la base de données (données/requêtes), le système **garantie** un taux de **disponibilité** de la donnée
- **Soft-state** : La base peut changer lors des mises à jour ou lors d'ajout/suppression de serveurs. La base NoSQL **n'a pas à être cohérente** à tout instant
- **Eventually consistent** : **À terme**, la base atteindra **un état cohérent
**
----

## Famille NoSQL 
Les besoins de stockage et de manipulation sont variables. Il existe différentes familles de bases NoSQL et chacune répond à des besoins très spécifiques 

----

### 1. **Clé/Valeur**

La clé           | La valeur 
-----------------|-----------------
Identifie et gère la donnée de manière unique | Contient n'importe quel type de données.

- Un système clé-valeur agit comme **table de hachage** distribuée sur le réseau. 

- Les seules opérations de type CRUD peuvent être utilisées :
    - Create (key,value)
    - Read (key)
    - Update (key,value)
    - Delete (key) 

- Très simple, ni de schéma, ni de structure pour le stockage

- Aucune possibilité d'exploiter et de contrôler la structure des données (pas de langage SQL). Ce n'est pas un problème, si vous savez ce que vous cherchez (la clé) et que vous manipulez directement la valeur

- *Applications* : détection de fraude en temps réel, IoT, e-commerce, gestion de cache, transactions rapides, fichiers de logs, chat.

- *Utilisation* : 
    - Redis (VMWare) : Vodafone, Trip Advisor, Nokia, Samsung, Docker
    - Memcached (Danga) : LiveJournal, Wikipédia, Flickr, Wordpress
    - Azure Cosmos DB (Microsoft) : Real Madrid, Orange tribes, MSN, LG, Schneider Electric
    - SimpleDB (Amazon) 
    - Cassandra, Riak

----

### 2. **Des lignes vers les colonnes**

![Stockage_orienté_Colonnes.png](./Big_data/Stockage_orienté_Colonnes.png)

- Chaque **attribut est représenté par une table** (distribué).
- Adaptée à de gros calculs analytiques
- Traiter l'information par colonne et omettre les informations inutiles (les autres colonnes).
- Moins appropriée pour la lecture de données spécifiques comme pour les clés/valeurs.
- Application : Comptage (vote en ligne, compteur, etc), journalisation, recherche de produits dans une catégorie, reporting à large échelle.
- Utilisation : 
    - BigTable (Google)
    - HBase (Apache, Hadoop)
    - Spark SQL (Apache)
    - Elasticsearch (elastic) 
----

### 3. **La gestion de documents**

![Stockage_orienté_document](./Big_data/Stockage_orienté_document.png)

- Les bases orientées documents ressemblent aux BDs classiques pour des requêtes complexes. 

- Il repose sur le principe du clé/valeur, mais avec une extension sur les champs qui composent ce document.

- Approche structurée de chaque valeur (Complexe: types, listes, imbrications), formant ainsi un document. 

- Langages d'interrogation riches permettant de faire des manipulations complexes sur chaque attribut du document (et sous-documents).

- *Application* : gestion de contenu (bibliothèques numériques, collections de produits, dépôts de logiciels, collections multimédia, etc.), framework stockant des objets, collection d’événements complexes, gestion des historiques d’utilisateurs sur réseaux sociaux.

- *Utilisation* :
    - MongoDB (MongoDB) : ADP, Adobe, Bosch, Cisco, eBay, Electronic Arts, Expedia, Foursquare
    - CouchBase (Apache, Hadoop) : AOL, AT&T, Comcast, Disney, PayPal, Ryanair
    - DynamoDB (Amazon) : BMW, Dropcam, Duolingo, Supercell, Zynga
    - Cassandra (Facebook -> Apache) : NY Times, eBay, Sky, Pearson Education

----

### 4. Dans la base orientée graphe

- Les données stockées sont : 
    - les nœuds; 
    - les liens et des propriétés sur ces nœuds et ces liens. 
- Les requêtes que l'on peut exprimer sont basées sur la gestion de chemins, de propagations, d'agrégations, voire de recommandations. 
- Application : réseaux sociaux (recommandation, plus court chemin, cluster...), réseaux SIG (routes, réseau électrique, fret...), web social (Linked Data).
- Utilisation : 
    - Neo4j : eBay, Cisco, UBS, HP, TomTom, The National Geographic Society
    - OrientDB (Apache) : Comcast, Warner Music Group, Cisco, Sky, United Nations, VErisign
    - FlockDB (Twitter) : Twitter

Inconvenients de la solution Nosql :
- Les ropriétés ACID ne sont pas applicables dans un contexte distribué (NoSQL)
- LOG - l'historique des opérations très complexes.
- N'est pas à l'abri d'une erreur de programmation
> les bases NoSQL sont indispensables au big data, mais ne sont qu'**une partie de la solution**


# Théorème de Brewer dit "théorème de CAP" (2000)

![Théoreme_CAP](./Big_data/Théoreme_CAP.png)

Repose sur 3 propriétés fondamentales pour caractériser les bases de données (relationnelles, NoSQL et autres) :

- Consistency (Cohérence) : Une donnée n'a qu'un seul état visible quel que soit le nombre de réplicas

- Availability (Disponibilité) : Tant que le système tourne (distribué ou non), la donnée doit être disponible

- Partition Tolerance (Distribution) : Quel que soit le nombre de serveurs, toute requête doit fournir un résultat correct

 Le théorème de CAP dit :

Dans toute base de données, vous ne pouvez respecter au plus que 2 propriétés parmi la cohérence, la disponibilité et la distribution.


## Caractéristiques des bases NoSQL : 

![HDSM](./Big_data/Recap_nosql.png) 

- **Elasticité** : C’est la capacité du système à s’adapter automatiquement en fonction du nombre de serveurs qu’il dispose et de la quantité de données à répartir. L’élasticité va permettre de répartir uniformément les données sur les 2000 serveurs (déplacement de la moitié des données)

- **Sharding** : **Technique qui permet de découper en bloc** (_chunks_)de 64 Mo, qu'on va répartir intelligemmmet sur le réseau.

    - HDFS (basé sur la distribution)
    - le clustere index (basé sur le BTree)
    - le consistent hashing (basé sur les tables de hachage)

----

## Hadoop Distributed File System (HDFS)

![HDSM](./Big_data/HDSM.png)

Hadoop Distributed File System (HDFS) : Créé pour **Hadoop**, qui est un outil extrèmement populaire pour réaliser des calculs **distribués** et basé sur l'algorithme Map-Reduce.

Au sens du théorème CAP, HDFS n'est pas un système disponible : c'est un système **cohérent et tolétent au partition**. Cela signifie que Jules n'est pas certain d'obtenir une réponse à sa requête, mais s'il en obtient une alors cette réponse contiendra bien les données les plus récentes. Par ailleurs, un cluster HDFS distribué va continuer à être cohérent en cas de partition du réseau.

Le **namenode** constitue un point **unique de défaillance** (SPOF): si le namenode devient indisponible, tout le cluster l'est également. HDFS n'est pas considéré comme un système pouvant assurer 100% de disponibilité.

Il existe des librairies pour manipuler des données dans HDFS depuis n'importe quel langage de programmation ; Python.

Avantages :
 - Une forte puissance de calcul.
 - Une bonne tolérance aux pannes. 

- HDFS replicates data three times by default

Utilisation : Architecture orientées colonnes : HBase, PigLatin, Spark.

![HDSM](./Big_data/HDFS_User.png)

--------------------------------------------------------------------------------
> Google does not let this 3V stop them, they create : 
    Google File System, Bigtble, MapReduce 

Repose sur BTree non-dense, il s'agit de l'arbre dont les données sont triées. 

![HDSM](./Big_data/arbre_distribué.png)

Utilisatin : MongoDB


## Table de hachage distribuée (DHT)

![HDSM](./Big_data/DHT.png)

Basée sur les tables de hachage, on distribue l’intégralité des informations dont on dispose : à la fois la donnée et la table de hachage. 

La particularité de cette technique est que chaque nœud est à la fois client et serveur. Imaginez un anneau virtuelle contenant 264 serveurs (soit 1,8×1019 serveurs !), la fonction de hachage place chaque donnée sur cet anneau, considéré comme un angle dans un cercle trigonométrique. Un nœud s’occupe de toutes les données dont l’angle est compris entre lui-même et le nœud suivant (portion du cercle), un peu comme une part de gâteau.

- Avantages :

    - une architecture totalement distribuée capable de s’auto-gérer

    - une élasticité simplifiée, même s’il est difficile d’identifier les zones en surcharge (pas de structure de contrôle).

    - Non centraliser

![HDSM](./Big_data/DHT_user.png)


## les critères à respecter par une bonne architecture: 

- La tolérance aux pannes : la loi de Murphy stipule que la probabilité qu'un composant tombe en panne tend vers 1 avec le temps. Il faut donc que votre architecture soit prête à supporter la panne d'un ou plusieurs composants.

- Une bonne maintenabilité : minimiser la dette technique que vous allez laisser à vos successeurs. Et minimiser la dette technique (produire une architecture facile à maintenir et à modifier).

- Un coût faible : facilité d’administration/exploitation/déploiement/composants simples (DynamoDB n’est disponible que chez Amazon)

- La disponibilité du système 

- La cohérence des données : La cohérence des données est un critère fondamental pour des applications reposant sur des données « fraiches » ou des applications reposant sur des décisions critiques.

-----

## Logical storage  vs Physical storage 
-----

- Logical storage refers to how your operating system organizes your data. This includes the topology of your file system, and how data is partitioned across nodes.

- Physical storage refers to the actual real-world location of your data. This might be several racks of servers in a data warehouse. 

# Système de stockage :

Une question se pose pour le stockage des données : de manière normalisée ou dénormalisée ? 

- Donnés dénormalisées : dupliquent certains champs
- Données normalisées : évitent toute duplication en utilisant des IDs. 
    - Méthode de normalisation : 
        - 1 formes normales
        - 2FN
        - 3FN

Exemple :
```SQL 
Dénormalisée :{username: "Régis", car: "Peugeot 405 Style"}dans la liste "users"

Normalisée :{username: "Régis", car_id: 843}dans la liste "users", et dans une autre liste "cars" :{id: 843, model: "Peugeot 405 Style"}
```

1. Système de fichiers semi-structuré : Jason, Xml
2. Système de fichiers distribué : 
    - Elle respecte :
        - Passage à l'échelle horizontal à bas coût
        - Lecture et écriture séquentielles rapides

Exemple | Supt de stockage | Garanti | Avantage 
--------|--------------------|--------|--------| 
HDFS, NTFS, ext4, ZFS | Plusieurs machines (cluster-disque dure) | Ecriture + la lecture séquentielles + Système de permissions qui control la modification et la supression | peu coûteux (disque dure) + Passage à l'échelle


Commentaires : 

1. Data Lake/Master dataset : contient des données de natures très variées (des fichiers de logs, des images, des fichiers binaires, etc). 
    Caractériques :
    - Write once : Les données ne seront écrites une seule fois ;
    - Append-only : Le master dataset ne subira que des ajouts ;
    - Read many times : Le master dataset sera lu de nombreuses fois ;
    - Sequential reads : Les opérations de lecture seront séquentielles.

    <!> Le master dataset n'est pas stockée dans une base de données relationnelle (RDBMS), type *MySQL* ou *PostgreSQL*, jugées trop coûteuses, supportent mal l'évolution du format des données et trop contraignantes pour stocker des données dans un format arbitraire. 

    Les RDBMS sont particulièrement adaptées pour les accès aléatoires aux données ainsi que pour la modification de données existantes.

1. Systeme de gestion de Base de Données relationnelles (SGBDR/ RDBMS) : IBM System R, Oracle, DB2 ou MySQL. 

1. Petit rappel 

Terme    | Définition
---------|--------------------------------------------------------------------
Relation | Table
n-uplet  | Tuple/Enregistrement/Vecteur/Ligne d'une table/représente un objet
Attribut | Colonne
Schéma   | Ensemble des attributs d'une relation
Domaine  | Ensemble des valeurs que peuvent prendre les attributs

4. Data Architect : Responsable de la conception, du déploiement et de l'administration de plateformes de calculs distribués et de stockage de données massives (passer à l'échelle l'exploitation des données).

1. L'indexation : Permet d’accéder directement à l’information recherchée

1. MongoDB (Première): 
    - Est une solution fortement utilisée par les développeurs. 
    - Son est langage puissant et facilement intégrable dans toute application gérant des documents/objets.

1. Cassandra (Deuxième) :
    - Son langage est inspiré de SQL, il s'avérer assez décevant en raison de ses fortes contraintes ; 
    - Bonne solution pour l’élasticité ; 
    - Le temps de réponse et des fonctionnalités basiques.

1. Redis et Elasticsearch (coude à coude avec Cassandra):
    - gére du cache temps réel pour le premier, et des gros volumes de documents textes pour le second.
    - Redis est connu pour sa simplicité, même si la gestion des « facettes » doit être bien pensées.
    - Elasticsearch est en particulier utilisé pour faire de la visualisation temps réel et de l’analyse sur des recherches textuelles.

1. le passage à l'échelle horizontale : ajouter des nœuds au cluster pour augmenter sa capacité de calcul

1. Dans le modèle parallèle, on passe à l'échelle de manière verticale, en augmentant la puissance des processeurs. Mais avec le ralentissement de la loi de Moore, ce dernier modèle est remis en question.
1. Volume des données
Megabyte (1,000 kilobytes) -> Gigabyte (1,000 megabytes) -> Terabyte (1,000 gigabytes) -> Petabyte (1,000 terabytes) ->
Exabyte  (1,000 petabytes) ->
Zettabyte (1,000 exabytes)

1. A small cluster in Hadoop can mesure in Terabytes.


1. Json (JavaScript Object Notation): Constitue le standard actuel pour les échanges de données sur le Web.
# Frameworks big data

## 1. Hadoop 

> The Hadoop ecosystem is a set of tools for ingesting and processing data
- Apache Zookeeper
- YARN

- Apache Flume (build Dataarehouse)
- Apache Sqoop
- Apache Oozie

> Hadoop de la fondation Apach

    2002 : Hadoop, écrit en Java. Hadoop s'inspire de Google Labs avec le Google File System (GFS) et MapRedue.
    2008 : Rejoint la fondation Apach en 2008.


Un framework Java libre, distribue les grandes quantités de données collectées à travers plusieurs *nœuds*, un cluster de serveurs x86, (il n’est donc pas nécessaire d’acquérir et de maintenir un hardware spécifique et coûteux). Hadoop est également **capable d’indexer** et de **suivre** **ces** **données** big data, ce qui facilite grandement leur traitement et leur analyse par rapport à ce qui était possible auparavant.
Il se compose de système de stockage **HDFS** (Hadoop Distributed File System), et d'un outil de traitement appelé **MapReduce**.

Hadoop est **résilient** aux pannes ou aux défaillances du système, car les _données sont écrites sur le disque après chaque opération_.

Hadoop Streaming. C'est un outil distribué avec Hadoop qui permet l'exécution d'un programme écrit dans d'autres langages, comme par exemple Python, C, C++...


Incovenient :

- Ecrire sur disque entre deux étapes (map ou reduce) 
jeu d'instruction limité.


 ## Le socle technique d'Haddop (HDFS + MapReduce): 
 ------

 ![HDSM](./Big_data/socle_Hadoop.png)

#### 1. MapReduce : 

Proposé par Google pour le calcul matriciell de PageRank. C'est un modèle de conception d'algorithme qui fournit un cadre pour automatiser le calcul **parallèle** sur des données massives. MapReduce s'inspire de de _Diviser pour regner_ et de la programmation fonctionnelle (des opérateurs de listes _Map_ et _Reduce_).

 ![HDSM](./Big_data/general_idea_MapR.png)


    Map (Opération pour transformer) : prend en entré des données (list) et transforme en liste de paire (clé, valeur) 'Lot'.

    Reduce (Opération pour aggréger) : 
        - Prend en entré une paire (clé, [valeur1, valeur2]), résultant d'un et d'un regroupement 
        - Applique une opération d'aggrégation sur les valeurs sur une même clé.

- Ordonnancement des traitements,
- Localisation des fichiers,
- La distribution de l’exécution.
- Fonctionne en étapes 
    - Lit les données au niveau du cluster
    - Il exécute une opération
    - Il écrit les résultats au niveau du cluster
    - Il lit à nouveau les données mises à jour au niveau du cluster, il exécute l’opération suivante, il écrit les nouveaux résultats au niveau du cluster, etc. 


Exemple - Programmation Fonctionnelle :
```Python
# map consiste à appliquer une même fonction à tous les éléments de la liste;

map(f)[x0, ..., xn] = [f(x0, ...,f(xn)]
map(*4)[2, 3, 6] = [8, 12, 24]

# reduce applique une fonction récursivement à une liste et retourne un seul résultat;

reduce(f)[x0, ..., xn] = f(x0, f(x1, f(x2, ...)))
reduce(+)[2, 3, 6] = (2 + (3 + 6)) = 11
```
Exemple - Ptyhon :

```Python

import numpy as np
from functools import reduce

file_name = "test_scala.txt"
file_ob   = open(file_name, "r", encoding='utf-16')
data      = file_ob.readlines()[0][: -1] # To remove '\n' at the end of the sentence 

key_value = list(map(lambda x: {x : 1}, data.split()))
key_value = sorted(key_value, key=lambda x: x.keys())

print(key_value)
print(type(key_value))

# [{'hello': 1}, {'hello': 1}, {'word': 1}, {"I'm": 1}, {'Celia': 1}]
# <class 'list'>

# reduce(lambda a,b : a + b,[1, 2, 8]) ==> 11
group = reduce(lambda a,b : {list(a.keys())[0] : list(b.values())[0] + list(a.values())[0]} \
                                if list(a.keys())[0] == list(b.keys())[0] \
                                    else dict(a, **b), key_value) 
print(group)
print(type(group))
# {'hello': 2, 'word': 1, "I'm": 1, 'Celia': 1}
# <class 'dict'>

group["Celia"], group["word"] = 17, 5
# {'hello': 2, 'word': 5, "I'm": 1, 'Celia': 17}
group1 = sorted(group.items(), key = lambda kv : (kv[1], kv[0]), reverse=-1)
```

![HDSM](./Big_data/MapReduce_composant.png)

Traitement : Opération sur les matrices et jointure de table.

Mapreduce permet le passsage à l'echelle. Mais pour cela, il faut lui associé une infrastructure dédiée (qui gène les contraintes du calcul distribuées) qui permette d'éxécuter le shéma MR de manière massivement distribuée sr un cluster de machines 

Les contraintes du calcul distribué :
- Equilibrage de la charge 
- Tolérence aux pannes
- Optimisaion des transferts (disque et web)



### Map
Les données d'entrée sont divisées en blocs plus petits. Chaque bloc est ensuite assigné à un Mapper pour traitement.
Par exemple, si un fichier contient 100 enregistrements à traiter, 100 Mappers peuvent s'exécuter ensemble et traiter un enregistrement chacun, ou 50 Mappers peuvent s'exécuter ensemble et traiter deux enregistrements chacun, et ainsi de suite. Le framework Hadoop décide du nombre de Mappers à utiliser en fonction du volume de données à traiter et de la taille des blocs de mémoire disponibles sur chaque serveur Mapper.


### Reduce
Lorsque tous les Mappers ont terminé leur traitement, le framework mélange et trie les résultats avant de les transmettre aux Reducers (les Reducers ne peuvent pas démarrer avant que tous les Mappers aient terminé leur traitement). Les valeurs de sortie map affectées de la même valeur key sont assignées à un seul Reducer, qui agrège les valeurs map pour cette key.

### Combine et Partition
Il existe deux étapes intermédiaires entre Map et Reduce : Combine et Partition.

1. Combine est un processus facultatif. Un Combiner est en fait un Reducer complémentaire qui fonctionne séparément sur chaque serveur Mapper. Le Reducer poursuit la réduction des données de chaque Mapper sous une forme simplifiée avant de les transmettre en aval – ce qui facilite et accélère les opérations de mélange et le tri, dans la mesure où le volume de données à traiter a été réduit. Dans bien des cas, en raison des actions cumulatives et associatives exécutées par la fonction Reduce, la classe du Combiner est celle du Reducer (si nécessaire, le Combiner peut être associé à une classe distincte).
2. Partition est le processus qui traduit les paires <key, value> générées par les Mappers en d'autres paires <key, value> qui sont injectées dans le Reducer. Partition définit le mode de présentation des données au Reducer et assigne ce mode à un Reducer donné.
Le Partitioner par défaut détermine la valeur de hachage de clé transmis par le Mapper et assigne une partition en fonction de cette valeur. Il y a autant de partitions que de Reducers. Lorsque le partitionnement est terminé, les données de chaque partition sont transmises à un Reducer donné.


#### 2. Un système de fichiers :

- Distribué : les données sont réparties sur les machines du cluster.
- Répliqué : en cas de panne, aucune donnée n'est perdue.
- Optimisé pour la colocalisation des données et des traitements.
    
 **Framework Yet Another Ressource Negociator (Yarn)** d'Hadoop Apach allège les responsabilité du JOB TRACKER 

 
## 2. Apache Spark
Ne sait pas faire du stockage distribué. Il a donc besoin de s’appuyer sur un système de stockage distribué (soit HDFS, soit celui d’une autre plate-forme de données dans le cloud)

> Spark a été conçu pour Hadoop, et la plupart des gens s'accordent pour dire qu’ils fonctionnent mieux ensemble.


- Spark : 
    - Il peut travailler sur la totalité des données en une seule fois.
        - Exécute la totalité des opérations d'analyse de données en mémoire et en temps quasi réel : « Spark lit les données au niveau du cluster, effectue toutes les opérations d’analyses nécessaires, écrit les résultats au niveau du cluster, et c’est tout.
    - Spark offre la résilience intégrée du fait que les objets de données sont stockés dans des ensembles de données distribués résilients (RDD) répartis sur le cluster de données. « Ces objets de données peuvent être stockés dans la mémoire ou sur les disques, et les ensembles RDD permettent une récupération complète après panne ou défaillance.

> Spark est jusqu'à 10 fois plus rapide que MapReduce pour le traitement en lots et jusqu'à 100 fois plus rapide pour effectuer l'analyse en mémoire 

Spark a été conçu pour Hadoop, et la plupart des gens s'accordent pour dire qu’ils fonctionnent mieux ensemble.

Hadoop, initié en 2006. Il rejoint la fondation Apache en 2008

Google File System, un système de fichiers distribués propriétaire developpé par Google et permettant de stocker de gros volumes de données de manière fiable sur des clusters.


 # Autre Framework BIG DATA:


- Giraph: une solution pour faire des calculs sur graphes.

- HBase : une base de données NoSQL reposant sur HDFS. Nous détaillerons aussi ce type de base de données dans un prochain cours.

- Tez : un cadre pour l'écriture et l'exécution de traitements modélisés sous la forme de graphes dirigés acycliques (DAG) et qui facilite l'enchaînement des traitements.




Spark stock les données en RAM 


### Data Pipline (work flow for Hadoop)

Ingestion | processing | Analyse
---|---|----|
Flame | Spark, Pig (etl), Hbase | Hive, Drill,Mahout

DataWarehouse --> ETL 

Collaborative filtering is the machine learning algorithm behind many recommendation engines
