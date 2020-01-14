# Qu'est ce qu'Apache ?

- Fondation
- C'est un serveur Web totalement modulaire
- Réalise l'affichage et traiter les requetes des clients "Navigateurs Web" 
Les modules : 
    - Langages de programmation : Pthon, Php, Perl
    - Serveur Proxy 
    - Event
    - Worker
- Open source 

# Histoire d'Apache 

- Evolution de NCSA
- Apparu en 1995

# Projets

- HTTP Serveur
- Hadoop
- Hbase (Processing)
- HTTP
- XML
- Drill (Analyse)
- Kafka
- River
- Perl
- Spark (Processing)
- Hive (Analyse)
- Mahout (Analyse)
- Pig (Processing)
- Giraph
- Tez
- Flame (Ingestion + build DataWarehouse)

...

## Hadoop

> The Hadoop ecosystem is a set of tools for ingesting and processing data
- Apache Zookeeper
- YARN
- Apache Flume (build Datawarehouse)
- Apache Sqoop
- Apache Oozie

> Hadoop de la fondation Apach

    2002 : Hadoop, écrit en Java. Hadoop s'inspire de Google Labs avec le Google File System (GFS) et MapRedue.
    2008 : Rejoint la fondation Apach.

Un framework Java libre, distribue les grandes quantités de données collectées à travers plusieurs *nœuds*, un cluster de serveurs x86, (il n’est donc pas nécessaire d’acquérir et de maintenir un hardware spécifique et coûteux). Hadoop est également **capable d’indexer** et de **suivre** **ces** **données** big data, ce qui facilite grandement leur traitement et leur analyse par rapport à ce qui était possible auparavant.
Il se compose de système de stockage **HDFS** (Hadoop Distributed File System), et d'un outil de traitement appelé **MapReduce**.

Hadoop est **résilient** aux pannes ou aux défaillances du système, car les _données sont écrites sur le disque après chaque opération_.

Hadoop Streaming. C'est un outil distribué avec Hadoop qui permet l'exécution d'un programme écrit dans d'autres langages, comme par exemple Python, C, C++...

A small cluster in Hadoop can mesure in Terabytes.

Incovenient :
- Ecrire sur disque entre deux étapes (map ou reduce)
- Jeu d'instruction limité.


### Data Pipline (Workflow for Hadoop)

Ingestion | processing | Analyse
----------|------------|----------|
Flame     | Spark, Pig (etl), Hbase | Hive, Drill,Mahout

## Tez

Un cadre pour l'écriture et l'exécution de traitements modélisés sous la forme de graphes dirigés acycliques (DAG) et qui facilite l'enchaînement des traitements.

## HBase (Framework BIG DATA)

Une base de données NoSQL reposant sur HDFS.

## Giraph (Framework BIG DATA)

Apache Giraph est une solution pour faire des calculs sur graphes.

## Hive (Framework BIG DATA)

Au départ, Hive est développé par FB, puis a été repris par la fondation Apache. Hive est un **open source data warehouse**, qui analyse et questionne avec le langage HiveQL ~ SQL, qui sont ensuite traduites comme des programmes MapReduce sur le cluster. 

Les données (structurées + schema) dans und BD-Relationnelle sont stockées sur HDFS.

## Pig (Framework BIG DATA)

Comme Hive (langage python, scala...)

## Drill (Framework BIG DATA)

Apache Drill est un framework logiciel, version open-source de Dremel de Google. Drill supporte les applications temps réel distribuées pour l'analyse interactive de jeux de données à grande échelle. Un objectif de conception indique qu'il est capable:
- Requeter sur des dépôts distincts
- Evoluer plus de 10.000 serveurs 
- Traiter des pétaoctets de données et des milliards d'enregistrements en quelques secondes
 
Drill supporte des bases NoSQL et des systèmes de fichiers distribués comme HBase, MongoDB, MapR-DB, HDFS, MapR-FS, Amazon S3, Azure Blob Storage, Google Cloud Storage, Swift, NAS et des fichiers locaux. 



