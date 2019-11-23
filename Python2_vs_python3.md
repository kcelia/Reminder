Python : Un langage "portable" et "interprété"

- Prtable : Un script écrit sous Linux Ubuntu avec une installation Python 3.7 et exécuté sous Windows 10 avec une installation Python 3.7 et fournira le résultat attendu.
- Interpreté : Un processus "l'interpréteur" exécute le code les lignes par lignes. Mais, un script écrit en Python 3.x peut poser des problèmes avec un interpréteur de version antérieure 3.y 

Il y a une rupture de compatibilité entre la branche Python 2 et Python 3. En voici quelques exemples :

Code | Python 2 | Python 3 | Explication
-----|----------|----------|------------
Print| print "a" | print("a") | print devient une fonction 
Print| print "\n".join([x, y])| print(x, y, sep="\n")| -
Print| print "une ligne " | print("une ligne", end="") | -
3/2| 1 | 1.5 | Python3 dissocie la division réelle et division entière
3//2| 1 | 1 | -

