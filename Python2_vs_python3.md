Python : Un langage "portable" et "interprété"

- Prtable : Un script écrit sous Linux Ubuntu avec une installation Python 3.7 et exécuté sous Windows 10 avec une installation Python 3.7 et fournira le résultat attendu.
- Interpreté : Un processus "l'interpréteur" exécute le code les lignes par lignes. Mais, un script écrit en Python 3.x peut poser des problèmes avec un interpréteur de version antérieure 3.y 

Il y a une rupture de compatibilité entre la branche Python 2 et Python 3. En voici quelques exemples :

- Print devient une fonction 

Python 2 | Python 3 
---------|----------
Print "a"| print("a") 
print "\n".join([x, y]) | print(x, y, sep="\n")
print "une ligne " | print("une ligne", end="")

- Python3 dissocie la division réelle et division entière

Code |Python 2 | Python 3 
-----|---------|---------
3/2| 1 | 1.5 
3//2| 1 | 1 

- Range 

Code |Python 2 | Python 3 
-----|---------|----------
Range(1000000)| Prend beaucoup de place| Range est implémenté sous forme d'itérateur
xrange(10000000) | OK | Erreur
type(range(7))| list | range | le nouveau type range (itérateur) apparaît

- Opérateur : Les opérateurs douteuses sont impossibles.

Code | Python 2 | Python 3 
------|---|---------
1 <> 2 | OK | Erreur (1 =! 2)
1 < '124' | Résultat quelconque | Erreur 

- Round : Python3 utilise 'l'arrondu du banquier'. Il arrondi pair le plus proche pour avoir une moyenne correcte sur l'ensemble.

Code |Python 2 | Python 3 
-----|---------|---------
round(16.5)| 16 | 16
round(17.5)|17 | 18

- List de compréhension : En python3, les variables de LdC ne fuient pas.

Code |Python 2 | Python 3 
-----|---------|---------
i = 1; [i for i in range(4)]; print(i)| 4 | 1 



