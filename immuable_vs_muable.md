
## Mutable

Un objet mutable est un objet modifiable, tel que : List, Dict et instances de nos propres classes.

## Immutable

Un object immutable est un object non modifiable, tel que : bool, int, str, bytes, tuple, range et frozenset. Pour créer un object immutable, il faut hériter d'un object immutable de base.

<!> modification != réassignation.

1. Modification:

Une fois un object mutable instancié, il est possible d’y insérer de nouveaux éléments, contrairement aux objects immutables.

List
```Python
>>> values = [0, 1, 2]
>>> id(values)
4340729544
>>> values.append(3)
>>> id(values)
4340729544
```
Fonction with List
```Python
# List has a specific function that allows us to modify it
>>> def append_42(values):
...     values.append(42)
...     return values

>>> v = [1, 2, 3, 4]
>>> append_42(v)
[1, 2, 3, 4, 42]
>>> v
[1, 2, 3, 4, 42]
```

Tuple 
```python 
# Can't modify a tuple !
# We do the same thing with a tuple instead of a list.
a = ("apples", "bananas", "oranges")
>>> a[0] = "berries"
Traceback (most recent call last):
  File "", line 1, in 
TypeError: 'tuple' object does not support item assignment
```
Int
```Python
>>> a = 60
>>> id(a)

>>> a = 66
>>> id(a)

```
Function with Tuple 
```python 
# Tuple hasn't a specific function that allows us to modify it
>>> def append_42(values):
...     return values + (42,)

>>> v = (1, 2, 3, 4)
>>> append_42(v)
(1, 2, 3, 4, 42)
>>> v
(1, 2, 3, 4)
```

Principe de mutabilité : En Python, il est possible d’avoir plusieurs noms (étiquettes) sur une même valeur. 

List
```python
>>> values = [0, 1, 2]
>>> id(values)
123456
>>> othervalues = [0, 1, 2]
>>> id(othervalues)
123456
# values et othervalues référencent un même objet.
>>> values.append(3)
>>> othervalues
[0, 1, 2, 3]
```
String/int
```
>>> a = "Karim"
>>> b = "Karim"
>>> id(a)
4364823608
>>> id(b)
4364823608
```

Tuple
```Python
>>> a = (1, 2, 3)
>>> id(a)
4364823608
>>> b = (1, 2, 3)
>>> id(b)
43648236545

```
2. réassignation 
``` Python
>>> values = othervalues = [0, 1, 2]
>>> values = [0, 1, 2, 3] # réassignation de values
```

Tuple
```Python
>>> a = (1, 2, 3)
>>> id(a)
4340765824
>>> a = (1, 2, 3, 4)
>>> id(a)
4340764557
# The old value is lost
```


3. Égalité et identité

- Egalité - == : Deux valeurs qui partagent un même état (même objet en mémoire), surchargeable en Python, via la méthode spéciale __eq__.
- Identité - is : Deux objets sont d'une même instance, ils seront toujours égales car les modifications seront perçues sur les deux variables. Il n’est bien sûr pas possibe de le surcharger.
```Python
>>> values1, values2 = [1, 2, 3], [1, 2, 3]
>>> values1 == values2
True
>>> values1 is values2
False

>>> values1 is values1
True

>>> values1 = values2 = [1, 2, 3]
>>> values1 == values2
True
>>> values1 is values2
True
```

4. Hashage

Hash == Condensat => object immutable.

Les objets hashables vont notamment servir pour les clefs des dictionnaires. Deux valeurs égales partageront un même hash.
Le condensat est généralement un nombre de taille fixe (64 bits par exemple), il existe donc un nombre limité de hashs pour un nombre infini de valeurs. Les collisions dépendent des algorithmes de hashage. 



```Python
>>> hash(10)
>>> hash('toto')
>>> hash((1, 2, 3))

# les listes ne sont pas hashables. Car le hash doit correspondre à une valeur. Or, en modifiant une liste, le condensat calculé auparavant deviendrait invalide. Il est donc impossible de hasher les listes (de même pour les dictionnaires et les ensembles (set)).

>>> hash([1, 2, 3])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'

# Les types immutables peuvent contenir des mutables et inversement ==> Non hashable.
>>> hash((12, [1, 2])
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'list'

# Les Dict ne sont pas hashables
>>> hash({{'foo': 'bar'}})
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unhashable type: 'dict'
```


Mutable Vs Immutable 

1. Mutable - Appending Performance
Les objects mutables sont plus efficace lorsque l'object est fréquemment modifié (iterable object)

List 

```python
L  = []
for item in x:
    L.append(item)
```    
Tuple 

```python
# Memory crush
T  = ()
for item in x:
    T = T + (item,)
```    
2. Immutable - Easiness of Debugging (modification et assignation)
    
    
    
    



