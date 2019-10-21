## Shell BASH

### Programmation shell : 
- **Minilangage** de programmation intégré à tous les systèmes **Linux**.
- Il gère et automatise des tâches répétitives et de gèrer l'invite de commandes.
- Rien à installer, rien à compiler. Toutes les commandes que l'on utilise dans les scripts shell sont des commandes du système (ls, cut, grep, sort…).
- Toutefois, pour programmer, il va vous falloir **utiliser** un __*éditeur de texte*__ (nano, __vim__, emacs)

**vim** : est une version améliorée de l'un des plus anciens éditeurs en console : **vi**

Exit without saving: `:q!`

Exit with saving :  `:wq`

Deux environnements très différents sont disponibles sous Linux :

1. Environnements console 
(appelés, les shells)
1. Environnement graphique (Unity, KDE, XFCE).

- La différence est moins tape-à-l'œil que dans le mode graphique (différent menus)
- Les fonctionnalités offertes par l'invite de commandes peuvent varier en fonction du shell que l'on utilise (eg. tabulation, définir des alias, gérer les processus, chainer les commandes ‘|’).

Mode Console
-------------
shell | Description
--|---
sh (Bourne Shell) | L'ancêtre de tous les shells.
bash (Bourne Again Shell) | Une amélioration du Bourne Shell, disponible par défaut de la plupart des distriutions Linux et Mac OS X.
ksh (Korn Shell) | Un shell puissant assez présent sur les Unix propriétaires, mais aussi disponible en version libre, compatible avec bash.
csh (C Shell) | Un shell utilisant une syntaxe proche du langage C.
tcsh (Tenex C Shell) | Amélioration du C Shell.
zsh (Z Shell) | Shell assez récent reprenant les meilleures idées de bash, ksh et tcsh.


> `.bashrc` est le fichier de configuration du bash que linux utilise par défaut.


### Créer un **script shell** :
Extension *.sh* par convention, certain scripts shell n’ont pas d’extension du tout)

`$ vim test_shell_bash.sh`

Ajouter à la première ligne: 
```bash 
#!/bin/bash/
``` 
Pour indiquer que le shell est executable. 

**!#** : Le hashtag, est appelé *sha-bang*.

**/bin/bash** : peut être remplacé par */bin/sh* ou */bin/ksh*/

#### Rendre le script executable : 

```bash
$ chmod +x test_shell_bash.sh
```

#### Executer le script : 

```bash
 ./test_shell_bash.sh
 ```

#### Debug : 

```bash
bash -x test_shell_bash.sh
```

#### Téléchargement 
`wget` ou `curl`

#### Unzip: 

```bash
tar -xvzf /path/to/yourfile.tgz
```

Option |  Description 
-------|  ----------
x      | extract
v      | verbose
z      | gnuzip
f      | file (should come at last)

#### Compter le nombre de fichier dans un répertoire 

`ls | wc -l`

***<!> ls -l ajoute la ligne total …***

### Nombre de mot par fichier 
```bash
wc -w file.txt
wc -w * 
```

#### Definir une variable

`message="Il n\'a pas d\'espace entre le nom de la variable et sa valeur"`

#### Affichage 

```bash
echo $message
echo "Le message contient: $message" # Il faut utiliser les doubles quotes
```

```bash
message_exec=`pwd`
echo "Les back quotes `` demandent à bash d\'executer ce qui se trouve a l'interieur de la variable : $message_exec"
```

#### Opérations mathematiques 

En bash, les bariables sont des chaînes de carcatères. Pour manipuler des nombres, il faut utiliser des commandes.

```bash
let "a = 5"
let "b = 5"
let "c = a + b"

echo "$a + $b = $c"
```
#### Variable d'environement

Les variables d'environnement peuvent être utilisées dans n'importe quel programme.

```bash 
$ env
```
