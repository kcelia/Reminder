## Shell BASH

### Programmation shell : 
- **Minilangage** de programmation intégré à tous les systèmes **Linux**.
- Il gère et automatise des tâches répétitives et de gèrer l'invite de commandes.
- Rien à installer, rien à compiler. Toutes les commandes que l'on utilise dans les scripts shell sont des commandes du système (ls, cut, grep, sort…).
- Toutefois, pour programmer, il va vous falloir **utiliser** un __*éditeur de texte*__ (nano, __Vim__, emacs)

## Vim

**Vim** est une version améliorée de l'un des plus anciens éditeurs en console : **Vi**

On débute avec le mode **interactif** avec _Vim_.

Le mode interactif ne permet pas de rentrer du texte mais de faire des opérations sur du texte. Appuyez sur "i" pour passer en mode insertion et rentrer ainsi du texte.

Exit without saving: `:q!`

Exit with saving :  `INSET` + ... + `ECHAP` + `:wq`

Supprimer 3 lignes dans Vim : 3dd

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
Pour indiquer que le script est écrit en bash, appelée le *sha-bang*.

**!#** : Un signal qui indique avec quel interpréteur de shell il faut lire le script.

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

En bash, les bariables sont des chaînes de carcatères. Pour manipuler des nombres, il faut utiliser des commandes (let...).

```bash
let "a = 5"
let "b = 5"
let "c = a + b"

echo "$a + $b = $c"
```
#### Variables d'environement/Globales 

Les variables d'environnement peuvent être utilisées dans n'importe quel programme/script.

```bash 
$ env

ORBIT_SOCKETDIR=/tmp/orbit-mateo21
GLADE_PIXMAP_PATH=:/usr/share/glade3/pixmaps
TERM=xterm
SHELL=/bin/bash # Indique quel type de shell est en cours d'utilisation (sh, bash, ksh…)
GTK_MODULES=canberra-gtk-module
USER=celia
PATH=/home/celia/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin: /usr/bin:/sbin:/bin:/usr/games
GDM_XSERVER_LOCATION=local # Une liste des répertoires qui contiennent des exécutables sans "./"
PWD=/home/celia # Le dossier dans lequel vous vous trouvez 
EDITOR=nano # L'éditeur de texte par défaut
SHLVL=1
HOME=/home/celia # La position de votre dossier home 
OLDPWD=/home/celia # Le dossier dans lequel vous vous trouviez auparavant

[ ... ]
```

#### Définir une nouvelle variable d'environnement 

```bash
export #dans le .bashrc.
```

#### Exécuter depuis n'importe quel répertoire sans "./"

Le PATH est une variable système qui indique où sont les programmes exécutables sur l'ordinateur. 

```bash
echo $PATH # lister de ces répertoires « spéciaux ».4
```

Ajouter le script à l'un de ces répertoires spéciaux puis l'exécuter sans le './'.

```bash
test_shell_bash.sh # Sans le './'
```

### Les tableaux 

```bash
tableau=(1 2 1)
echo "{tableau[2]} = ${tableau[2]}" # Il faut entourer la variable d'accolades
tableau[5]=727 # La numérotation n'a pas besoin d'être continue
echo ${tableau[*]} #Afficher l'ensemble du contenu du tableau 
```

### Les conditions 

```bash
read x 
# ./file.sh 5
# x=$1
if [ $x -gt 0 ] # [ test ] et non [test] 
                # -ge GreaterorEqual
then 
        echo "Nombre positif" # Après deux tablulations"
elif [ $x -lt 0 ] # le LowerorEqual
then 
        echo "Nombre negatif" 
else
        echo "Nombre égale à 0"
fi
```

```bash

echo "Fichier $0, Nombre de paramètres $#"

if [ $1 != $2 ] 
then
        echo "Les 2 paramètres sont identiques !" 
elif [ $1 == $2 ]  
then 
        echo "Les 2 paramètres sont différents !"
        # " « eq » : Vérifie si les nombres sont égaux"
        # " « == » : Compare deux chaînes de caractères"
elif [ -z $1 ]
then
        echo "Vérifie si la chaîne est vide"
elif [ -n $1 ]
then 
        echo "Vérifie si la chaîne est non vide"

fi
```

`&&` : signifie « et »

`||` : signifie « ou »

Inverser un test : `if [ ! -e fichier ] # -e si le fichier existe`

#### Case

```bash
case $1 in
        "Chien" | "Chat" | "Souris")
                echo "C'est un mammifère"
                ;;
        "Moineau" | "Pigeon")
                echo "C'est un oiseau"
                ;;
        *)
                echo "Je ne sais pas ce que c'est"
                ;;
esac
```

### Boucles

For :
```bash 
for fichier in $tableau 
# for fichier in `ls`
# for name in $(ls ${dir_input}.txt)
do
        echo "Fichier trouvé : $fichier"
done
```
While :
```bash 
while [ -z $reponse ] || [ $reponse != 'oui' ]
do
        read -p 'Dites oui : ' reponse
done

```
Séquence:

```bash
for i in `seq 1 10`;
do
        echo $i
done
```

### Grep

Chercher un mot dans un fichier.
`grep -c $mot $file` retourne `1` si le fichier contient le mot. Sinon, 0.

### Awk

**awk** est une commande très puissante, qui permet une recherche de chaînes et l'exécution d'actions sur les lignes sélectionnées, de récuperer de l'information, générer des rapports, transformer des données entre autres. 

Un programme awk possède la structure suivante: **Critère de sélection d'une chaîne {action}**. Quand il n'y a pas de critère c'est que l'action s'applique à toutes les lignes du fichier. 


> Syntaxe : `awk [-F] [-v var=valeur] -f fichier-config fichier`

L'argument | description | exemple
---|---| ---
-F | suivi du séparateur de champ | **-F:** (":" comme séparateur de champ)
-f | suivi du nom du fichier de configuration de awk | 
-v | définit une variable, qui sera utilisée par la suite dans le programme | ***var***  

#### Variable **awk**

Variable | Description 
---------|------------
$0 | l'enregistrement complet (une ligne d'un fichier) est référencé par $0
$1, $2, ..., $NF | dans un enregistrement les champs sont référencés par $1, $2, ..., $NF (dernier champ)
ARGC | nombre d'arguments de la ligne de commande néant 
ARGIND | index du tableau ARGV du fichier courant 
ARGV | tableau des arguments de la ligne de commande néant 
CONVFMT | format de conversion pour les nombres "%.6g" 
ENVIRON | tableau contenant les valeurs de l'environnement courant 
ERRNO | contient une chaîne décrivant une erreur "" 
FIELIWIDTHS | variable expérimentale à ne pas utiliser 
FILENAME | nom du fichier d'entrée néant 
FNR | numéro d'enregistrement dans le fichier courant néant 
FS | contrôle le séparateur des champs d'entrée " " 
IGNORECASE | contrôle les expressions régulières et les opérations sur les chaînes de caractères 0 
NF | nombre de champs dans l'enregistrement courant néant 
NR | nombre d'enregistrements lus jusqu'alors néant 
OFMT | format de sortie des nombres (nombre après la virgule) "%.6g" 
OFS | séparateur des champs de sortie " " 
ORS | séparateur des enregistrements de sortie 
RLENGTH | néant longueur de la chaîne sélectionnée par le critère "\n" 
RS | contrôle le séparateur des enregistrements d'entrée "\n" 
RSTART | début de la chaîne sélectionnée par le critère néant 
SUBSEP | séparateur d'indiçage "\034"

#### Les actions
1. Traitement des numériques:
    - **cos(x), exp(x), int(x), log(x), sqr(x)**
1. Traitement des chaines de caractères
    - **gsub(expression-régulière,nouvelle-chaine,chaine-de-caractères)** dans chaine-de-caractères tous les caractères décrits par l'expression régulière sont remplacés par nouvelle-chaine. gsub et équivalent à gensub. 

    - **gsub(/a/,"ai",oi")** Remplace la chaine oi par ai 
index(chaine-de-caractères,caractère-à-rechercher) donne la première occurence du caractère-à-rechercher dans la chaine chaine-de-caractères 

    - **n=index("patate","ta")** n=3 
    - **length(chaine-de-caractères)** renvoie la longueur de la chaine-de-caractères 

    - **n=length("patate")** n=6 

    - **match(chaine-de-caractères,expression-régulière)** renvoie l'indice de la position de la chaîne chaine-de-caractères, repositionne RSTART et RLENGTH 

    - **n=match("PO1235D",/[0-9][0-9]/)** n=3, RSTART=3 et RLENGTH=4 

    - **printf(format,valeur)** permet d'envoyer des affichages (sorties) formatées, la syntaxe est identique de la même fonction en C 

    - **printf("La variable i est égale à %7,2f",i)** sortie du chiffre i avec 7 caractères (éventuellement caractères vides devant) et 2 chiffres après la virgule. 
    - **printf("La ligne est %s",$0) > "fichier.int"** Redirection de la sortie vers un fichier avec >, on peut utiliser aussi la redirection >>. Veillez à ne pas oublier les "" autour du nom du fichier. 
    - **split(chaine-de-caractères,tableau,séparateur)** scinde la chaîne chaine-de-caractères dans un tableau, le séparateur de champ est le troisième argument 
    - **n=split("zorro est arrivé",tab," ")** tab[1]="zorro", tab[2]="est", tab[3]="arrivé", n=3 correspond au nombre d'éléments dans le tableau 
    - **sprintf(format,valeur)** printf permet d'afficher à l'écran alors que sprintf renvoie la sortie vers une chaîne de caractères. 
    - **machaine=sprintf("J'ai %d patates",i)** machaine="J'ai 3 patates" (si i=3) 
    - **substr(chaine-de-caractères,pos,long)** Extrait une chaine de longueur long dans la chaîne chaine-de-caractères à partir de la position pos et l'affecte à une chaîne. 
    - **machaine=substr("Zorro est arrivé",5,3)** machaine="o e" 
    - **sub(expression-régulière,nouvelle-chaine,chaine-de-caractères)** idem que gsub sauf que seul la première occurence est remplacée (gsub=globale sub) 
    - **system(chaine-de-caractères)** permet de lancer des commandes d'autres programmes 
    - **commande=sprintf("ls | grep toto")** Exécution de la commande UNIX "ls |grep toto" 
system(commande) 
    - **tolower(chaine-de-caracteres)** retourne la chaîne de caractères convertie en minuscule 
    - **toupper(chaine-de-caracteres)** retourne la chaîne de caractères convetie en majuscule


Exemple: 

```bash 
echo `awk -F":" '{print $NF}' /etc/passwd`
```

Il n'y a pas de critères, donc l'action s'applique à toutes les lignes du fichier /etc/passwd. L'action consiste à afficher le dernier de champ du fichier.

### Critères de sélection

Un critère peut être une expression régulière, une expression ayant une valeur chaîne de caractères, une expression arithmétique, une combinaison des expressions précédentes. 

Le critère est inséré entre les chaînes BEGIN et END, avec la syntaxe suivante: 
> `awk -F":" 'BEGIN{instructions} critères END{instructions}'`

- BEGIN peut être suivi d'instruction comme une ligne de commentaire ou pour définir le séparateur. 
    > BEGIN { print"Vérification d'un fichier"; FS=":"}

- END indiquera que la commande a achevé son travail. Le END n'est pas obligatoire, de même que le BEGIN. 
    > END {print "travail terminé"} 

1. Expression réguliere 

> expression ~ /expression régulière/{instructions}

> expression !~/expression régulière/ {instructions}

Soit le fichier "adresse":

gwenael | 0298452223 | 0638431234 | 50 

marcel  | 0466442312 | 0638453211 | 31 

judith  | 0154674487 | 0645227937 | 23 

L'exemple suivant vérifie que dans le fichier le numéro de téléphone domicile (champ 2) et le numéro de portable (champ 3) sont bien des nombres. 

> 
    # Instruction d'affichage + définition du séparateur de champ
    awk 'BEGIN { print "On vérifie les numéros de téléphone; 
                FS="|"} 

            # Si succès, on affichera un msg d'erreur
            # $2 = 2° champ d'une ligne (enregistrement)
            # On recherche ceux qui ne contiennent pas de chiffre "!"
            $2 !~ /^[0-9][0-9]*$/ { print "Erreur, ligne n°"NR":\n"$0} 

            $3 !~ /^[0-9][0-9]*$/ { print "Erreur, ligne n°"NR":\n"$0} 
            
            # END indiquant la fin du travail
            END { print "Vérification terminé"} 
    
    ' adresse 

            

>
    awk 'BEGIN { print "test de l'absence de mot de passe";                     
                FS=":"}

        # Pour toutes les lignes contenant 7 champs 
        NF==7 {
        if ($2=="") 
        # Si 2° champ = vide, on affiche ($1=login) qui n'a pas de mdp 
        { print $1 "n'a pas de mot de passe"} 

        else # Sinon, on affiche le nom de l'user possédant un mdp 
        { print $1 " a un mot de passe"} 
        }
        END{ print"C'est fini") 
    
    ' /etc/passwd

Quand l'une des variables de champ est modifée, $0 est modifié. ATTENTION le séparateur ne sera pas celui définit par FS mais celui définit par OFS (output field separator). 
> 
    awk 'BEGIN { print"les user de GID 22 basculeront vers GID 24"; 
                FS=":"; 
                OFS=":"} 

        # Si le groupe n'est pas users on fait rien 
        $4 != 22 {print $0} 

        # Si le groupe est 22, on lui réaffecte 24 
        $4 ==22 {$4=24; print $0} 

        END {print" C'est fini"}
    ' /etc/passwd > passwd.essai


> 
    awk 'BEGIN { print "Verification du fichier /etc/passwd pour ...";
                print "- les utilisateurs avec UID = 0 " ;
                print "- les utilisateurs avec UID >= 60000" ;
                FS=":"}
        $3 == 0 { print "UID 0 ligne "NR" :\n"$0 }
        $3 >= 60000  { print "UID >= 60000 ligne "NR" :\n"$0 }
        END { print "Fin" }
    ' /etc/passwd 

> 
    awk 'BEGIN { print "Verification du fichier /etc/group";
                print "le groupe 20 s'appelle t-il bien users ? " ;
                FS=":"}
        $1 == "users" && $3 ==20 { 
            print "groupe "$1" a le GID "$3" !" }
        END { print "Fin" }
    ' /etc/group 



## Bashrc
Le shell (bash ou autre) est personnalisable via un fichier de configuration, lu à chaque ouverture de console par l'utilisateur $USER.

***shell BASH*** ==> ***.bashrc*** situé dans le dossier /home/$USER/.bashrc. 

***shell CSH***  ==> ***.cshrc*** situé dans le dossier /home/$USER/.cshrc. 

S'il n'est pas lu, vérifier que le fichier soit exécutable, et vérifier aussi la présence de **.bash_profile** qui doit contenir :

```bash
# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
        . "$HOME/.bashrc"
    fi
fi
```
Accéder au bashrc : `vim ~/.bashrc`

Après modification du fichier **.bashrc**, il faut relancer bash ou recharger le fichier :
`source ~/.bashrc`

### Alias

```bash 
alias nom_de_votre_alias='commande de votre alias'
```

Exemple: 
```bash 
alias agu='sudo apt-get update'
alias agg='sudo apt-get upgrade'
alias agd='sudo apt-get dist-upgrade'
alias miseàjour='agu && agg && agd'
```


## Environnement bash
Le fichier /etc/bash.bashrc est lu au démarrage de votre terminal.

Modifiez le fichier /etc/bash.bashrc
```
export http_proxy=http://"proxy_ip":"port_number"
```
où "proxy_ip" et "port_number" seront adaptés à votre situation

## Pour désactiver le proxy http/https:

```
$ unset http_proxy
$ unset https_proxy
```
ou

```
$ export http_proxy=''
$ export https_proxy=''
```
vérifier avec 

`$ printenv` ou `$ printenv https_proxy`

More [proxy_terminal](https://doc.ubuntu-fr.org/proxy_terminal)