
## The Key Difference between a List and a Tuple


+ **Lists** are **mutable** objects which means you **can modify** a list object **after** 
it has been **created**. 
+ **Tuples** on the other hand are **immutable** objects 
which means you **can't modify** a tuple object **after** it's been **created**.


### 


```python 
# Let’s create a list and assign it to a variable.
>>> a = ["apples", "bananas", "oranges"]
>>> a[0] = "berries"
>>> a
['berries', 'bananas', 'oranges']
```
```python 
# We do the same thing with a tuple instead of a list.
a = ("apples", "bananas", "oranges")
>>> a[0] = "berries"

Traceback (most recent call last):
  File "", line 1, in 
TypeError: 'tuple' object does not support item assignment
```
But 

```python

>>> a = ("apples", "bananas", "oranges")
>>> a = ("berries", "bananas", "oranges")
>>> a
('berries', 'bananas', 'oranges')
