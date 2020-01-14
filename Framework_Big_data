

# Frameworks big data

## 1. Hadoop 

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






