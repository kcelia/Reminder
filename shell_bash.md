## Shell BASH

### Programmation shell : 
- **Minilangage** de programmation intégré à tous les systèmes **Linux** et qui permet d'automatiser des tâches répétitives et de gèrer l'invite de commandes.
- Rien à installer, rien à compiler. Toutes les commandes que l'on utilise dans les scripts shell sont des commandes du système (ls, cut, grep, sort…).
- Toutefois, pour programmer, il va vous falloir **utiliser** un __*éditeur de texte*__ (nano, vil, emacs)

**Vim** : est une version améliorée de l'un des plus anciens éditeurs en console : **Vi**

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
`$ vim essai.sh`

#### Téléchargement 
`wget` ou `curl`

#### Unzip: 

`tar -xvzf /path/to/yourfile.tgz`
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
```
wc -w file.txt
wc -w * 
```
