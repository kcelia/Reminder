# Shell BASH

## Shell programming: 

Mini programming language integrated in all Linux systems. So, no configuration is required for installation or compilation. All commands used in shell scripts are system commands. You just need an editor (Vi, Vim, emacs,...).

In shell scripts, the shell acts as an interpreter and executes the commands sequentially.

**DRY** stands  for _Don't Repeat Yourself_.

## Different _shells_ 

Shells | Stands for         | Descriptions
-------|--------------------|-------------
sh     | Bourne Shell       | The ancestor of all shells
bash   | Bourne Again Shell | An improved version of the Bourne Shell, available by default in all distributions
ksh    | Korn Shell         | A powerful shell, more present on proprietary Unix, also available in free version and compatible with bash
csh    | C Shell            | Close to C syntax language tcsh   | Tenex C Shell      | An uplift version of cshell
zsh    | Z Shell            | Fairly new shell with the best ideas of bash, ksh and tcsh


## Vim

**Vim** is an enhanced version of **Vi**.

vim has 2 main mode: 
- **I**nsert mode: `ESC + i` you type text 
- Command: undo, redo, find and replace, quit, etc.


```bash
vimtuto fr       ## Open tutorial in french

ESC + :q!        ## Exit without saving
ESC + :wq        ## Exit with saving

dd               ## Delete an entire line  
d4w              ## Delete 4 words  
4dd              ## Delete 4 lines

dd + p           ## Cut + copy before the cursor
dd + P           ## Cut + copy after the cursor

u                ## CTR+Z
U                ## Undo all your changes

gg               ## Beginning of the script
G                ## End of the script

/beau            ## Searche for the word beau
n                ## Go to the next found word
N                ## Go to the previous found word 

:5               ## Go to line 5
```

Deux environnements sont diponibles sous Linux :

1. Environnements console 
(appelés, les shells)
1. Environnement graphique (Unity, KDE, XFCE)

### VcXsrv - Deport your terminal in an interactive server X

```bash
## Enable the connexion to the server X
nano .bashrc 
CTRL + o
export DISPLAY=:0
# <!> Close your terminal to apply the new changes

## Install vim + interface
sudo apt-get vim-gtk

### Lunch vim
gim
``` 
## Let's get started

### 1. Shebang "#!"

What follows the _she-bang_ is the interpreter path, it could be :

```bash
#!/bin/bash
#!/bin/csh
#!/bin/ksh
#!/bin/zsh
#!/usr/bin/python3.8
```

If a script doesn't contain a shebang the commands are executed using you shell.

The default extension is *.sh*. But, some shell scripts may not have extension.


### 2. Make your script executable:

```bash
chmod 755 script.sh

# Or
chmod +x script.sh
```


### 3. script.sh

```bash
#!/bin/bash

## By default all variables are global 
MY_SHELL="bash"
HALF_WORD="bash"
SERVER_NAME=$(hostname)   # Cmmand
MESSAGE="There is no space between the name of the variable and its value"

## Prints
echo "My interpreter if $MY_SHELLL shell"
echo "Again, my interpreter if ${MY_SHELLL} shell"
echo "I'm ${HALF_WORD}ing on my keyboard"
echo "You are running this script on ${SERVER_NAME}"

## Display the previous execution or exit status of previous commad
ls *.sh
echo "$?"

## All the txt files that have 2 characters
ls ??.txt

## List of files that end with digit
ls *[[:digit:]]

## Lowercase
echo $X | tr [a-z] [A-Z]

## Calendar
cal [ [ month ] year] 
cal 2 1995

## Number of words per file
wc -w file.txt
wc -w * 
```

## File operators 

Operator | Meaning
---------|-----------
-d FILE  | True if the file is a directory
-e FILE  | True if the file exists
-f FILE  | True if the file exists and is a regular file
-r FILE  | True if the file is readable by you
-s FILE  | True if the file is not empty
-w FILE  | True if the file is writable by you
-x FILE  | True if the file is executable by you

## String operators

Operator            | Meaning
--------------------|-----------
-z STRING           | True if string is empty
-n STRING           | True if string is not empty
STRING1 == STRING2  | True if strings are equal
STRING1 != STRING2  | True if strings are not equal

## Arithmetic operators

Operator | Meaning
---------|-----------
x -eq y  | True if x is equal to y
x -ne y  | True if x is not equal to y
x -lt y  | True if x is less than y
x -le y  | True if x is less or equal to y
x -gt y  | True if x is greater than y
x -ge y  | True if x is greater or equal to y

By default, variables are strings. To manipulate numbers, you have use the commands _let_:

```bash
let "a = 5"
let "b = 5"
let "c = a + b"

echo "$a + $b = $c"
```

## If statement

Syntax:

```bash
if [ condition-to-test-for ]
then 
   command 1
elif [ condition-to-test-for ]
   command 2
else 
   command 3
fi 
```

**Example 1:**

```bash
X="bash"

if [ "$X" = "bash" ]
then 
  echo "you seem to like the bash shell"
fi
```
**Example 2:**

```bash
# If the file doesn't exist, then...
if [ ! -e fichier ] 
```

## For loop

**Syntax**
```bash
for VARIABLE_NAME in ITEM_1 ITEM_N
do
    command1
    commnd2
done
```

**Example 1:**

```bash
#!/bin/csh

for COLOR in red green blue
do 
    echo "COLOR: $COLOR"
done
```

**Example 2:**

```bash
#!/bin/csh

COLORS="red green blue"

for COLOR in $COLORS
do 
    echo "COLOR: $COLOR"
done
```

**Example 3:**

```bash
#!/bin/csh
for i in `seq 1 10`;
do
        echo $i
done
```

## Positional Parameters

Sign  | Meaning | Example: ./test.sh 1 2 3
------|---------|--------------------------
$0    | Name of the file            | test.sh
$1    | First argument              | 1
${10} | 10th argument               | 
$@    | What parameters were passed | $$1 \; 2 \; 3$$ ```<!> un param par arg -> for param in "$@" do echo -e " Paramètre : $param" done```
$#    | Number of arguments         | 3 
$?    | was last comand successful  | 0 
$*    | L'ensembles des paramètres sous la forme d'un seul argument | ```for param in "$*": do echo "liste des paramètres en 1 seul argument: $param" done```
`$$`    | Le PID su shell qui exécute le script | 165165
$!    | Le PID du dernier processus lancé en arrière-plan

## User input (STDIN)

`read -p "PROMPT" VARIABLE`

## && and ||
`cm1 && cm1` --> cm2 is executed only if cm1 succeeded

`cm1 || cm2` --> cm2 is executed only if cm1 failed

## Functions 

**Example 1**: count .sh files in my present directory


```bash
function count_files () {
        if [ -d $1 ]
        then
                echo "Files list: $(ls *.sh)"
                echo "COUNT: $(ls *.sh | wc -l)"
                return $?
        else
                echo "$1 is not a directory"
        fi
}

count_files ./
```

**Example 2**: mv files in an other directory
```bash
function mouve () {
        [ -d $2 ] || mkdir -p $2 || echo "$2 couln't be created"
        if [ $? -eq 0 ]
        then
                echo "$2 is OK"
                #echo "$(ls $2)"
        fi

        for FILE in $1/*[[:digit:]]
        do
                echo "Copying $FILE to $2"
                cp -f $FILE $2
        done
}

mouve ./test1 ./test1/toto/
```

**Example 3**: backup file

```bash
function backup_file () {
        if [ -f $1 ]
        then
                ## .$$ -> PID of the processus of the script
                BACK="./test1/$(basename $1).$(date +%F).$$"
                echo "Backing up $1 to $BACK"
                ## Return the exist status of cp command
                cp $1 $BACK
                if [ $? -eq 0 ]
                then
                        echo "The file $1 exists"
                        echo "Backup succeeded!"
                fi
        else
                echo "The file $1 doesn't exist"
                echo "Backup failed"
                return 1
        fi
}

backup_file sleepy.sh
backup_file sleepu.sh
```
## Wildcards
- `*`: matches zeros or more characters.
- `?`: matches exactly one character. 
- `[]`: A character class, mataches any of the characters included between the brackets
- `[!]`: Matches any of the characters NOT included between the brackets.

## Case

**Example 1:**
```bash
case "$VAR" in
    pattern1)
        # Commands 
        ;;
    pattern2)
        # Commands
        ;;
    *) ## Else
        echo "Nothing matched"
esac
```

**Example 2:**
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


## Read file

```bash
LINE_NUM=1

while read LINE
do 
    echo "${LINE_NUM} : ${LINE}"
    ((LINE_NUM++))
done < /etc/fstab ## File path 

# Or

grep xfs /etc/fstab | while read LINE
do 
    echo "xfs: ${LINE}
done 
```
## Array


```bash
tableau=(1 2 1)

echo "{tableau[2]} = ${tableau[2]}"

tableau[5]=727 

# Displying all the array 
echo ${tableau[*]} 
```

## Debug

Flags | Meaning 
------|--------
x     | Debugs
e     | Exits on error
v     | Prints shell input line as they are read 

```bash
##### Method 1
#!/bin/bash -xe
X=1
echo "Debu $X"

##### Method 2
#!/bin/bash
X=1
set -x
echo "Debu $X"
set +x

#### Method 3
bash -x script.sh

#### Method 4: Prints file name : number line : line code
#!/bin/bash -xe
PS4='+ $BASH_SOURCE : $LINENO :' 
TEST_VAR="test"
echo "$TEST"


#### Method 4: Prints file name : number line : line code
#!/bin/bash -xe
PS4='+ ${BASH_SOURCE} : ${LINENO}: ${FUNCNAME[0]} ()'

debug()  {
    echo "Executing: $@"
    $@
}
debug ls 
```

### Verbose
```bash
DEBUG='echo'
$DEBUG ls 

$DEBUG=true
$DEBUG && echo "Bebug mode ON
$DEBUG || echo "Bebug mode OFF

$DEBUG=false
$DEBUG || echo "Bebug mode OFF
```


## Unzip: 

Syntax:

`tar -xvzf /path/to/yourfile.tgz`

Options | Descriptions 
--------|----------
x       | extract
v       | verbose
z       | gnuzip
f       | file (should come at last)

## Téléchargement 
`wget` ou `curl`

## Variables d'environement/Globales 

Les variables d'environnement peuvent être utilisées dans n'importe quel programme/script.

```bash 
$ env

ORBIT_SOCKETDIR=/tmp/orbit-mateo21
GLADE_PIXMAP_PATH=:/usr/share/glade3/pixmaps
TERM=xterm
# Indicates which shell is used (sh, bash, ksh...)
SHELL=/bin/bash 
GTK_MODULES=canberra-gtk-module
USER=celia
PATH=/home/celia/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin: /usr/bin:/sbin:/bin:/usr/games
# Une liste des répertoires qui contiennent des exécutables sans "./"
GDM_XSERVER_LOCATION=local 
# Le dossier dans lequel vous vous trouvez 
PWD=/home/celia 
# L'éditeur de texte par défaut
EDITOR=nano 
SHLVL=1
# La position de votre dossier home 
HOME=/home/celia
# Le dossier dans lequel vous vous trouviez auparavant
OLDPWD=/home/celia 

[ ... ]
```


## Bashrc

`/etc/bash.bashrc` est le fichier de configuration personnalisable du bash que linux utilise par défaut. Il est lu au démarrage de votre terminal.

***shell BASH*** $\to$ ***.bashrc*** situé dans le dossier /home/$USER/.bashrc. 

***shell CSH*** $\to$ ***.cshrc*** situé dans le dossier /home/$USER/.cshrc. 

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
### Amend Bashrc

```bash
## Access bashrc 
vim ~/.bashrc

## After any changes, reload .bashrc
source ~/.bashrc

## Alias
alias agu='sudo apt-get update'
alias agg='sudo apt-get upgrade'
alias agd='sudo apt-get dist-upgrade'
alias maj='agu && agg && agd'
```

### Définir une nouvelle variable d'environnement dans le .bashrc

`export`

### Exécuter depuis n'importe quel répertoire sans "./"

Le PATH est une variable système qui indique où sont les programmes exécutables sur l'ordinateur. 

```bash
echo $PATH # lister de ces répertoires « spéciaux ».4
```

Ajouter le script à l'un de ces répertoires spéciaux puis l'exécuter sans le './'.

```bash
test_shell_bash.sh # Sans le './'
```


## Data manipulation and text transformations with _SED_

### 1. Sed

Sed = Stream EDitor for filtering and transforming text.

A stream is data that travels from :
- One process to another through a pipe 
- One file to another as a redirect
- One device to another

### Enable sed
`$ type -a sed`

### Replace string

Syntax:

`sed 's/sear-pattern/replacement-string/flags'`

flags | Meaning
------|---
i     | case insensitive
I     | case insensitive
g     | global replace 
digit | replace digit occurence
w     | rediret the change to another file
-i    | create backup file 
/:#   | delimiters 
d     | delete 
f     | put the instructions in a sed file

**Example 1:** 

```bash
echo '# Private' > text.txt
echo "My name is Celia" >> text.txt
echo "I'm 26 years old" >> text.txt
echo >> text.txt
echo '# Pro' >> text.txt
echo "I'm a data scientist" >> text.txt
cat text.txt

## Replace only in line 2 
sed "2s/i'm/i m/i" text.txt
sed "2 s/i'm/i m/i" text.txt

## Replace only in line 1 to 2
sed "1,2 s/i'm/i am/i" text.txt

## Replace where the line contains the word old
sed "/old/ s/i'm/i am/i" text.txt

## Replace only if it's private section
sed "/# Private/ ,/^$/ s/i'm/i am/i" text.txt

## Amend and send the stream in another file
cat other_file.txt | sed "s/i'm/i m/i" text.txt 
sed "s/i'm/i m/iw other_file.txt" text.txt

## Create backup file
sed -i.bak "s/i'm/i am/ig" text.txt

# Find and replace
echo '/home/jason' | sed 's:/home/jason:/export/ceci:'

## Delete
sed '/Celia/d' text.txt
```

**Example 2:**

```bash
echo '#User to run service as.' > config
echo 'User apache' >> config
echo >> config ## Ampty line
echo '#Group to run service as.' >> config
echo 'Group apache' >> config
cat config 

## Delete comments & blank lines 
sed '/^#/d ; /^$/d' config 

## Save the commands in a sed file
echo '/^#/d' > config.sed
echo '/^$/d'>> config.sed
echo 's/apache/httpd/i' >> config.sed
cat config.sed
sed -f config.sed config
```

### 2. Grep

Chercher un mot dans un fichier.

`grep -c $mot $file` retourne `1` si le fichier contient le mot. Sinon, 0.

### 3. Awk

**awk** est une commande très puissante, qui permet une recherche de chaînes et l'exécution d'actions sur les lignes sélectionnées, de récuperer de l'information, générer des rapports, transformer des données entre autres. 

Un programme awk possède la structure suivante: **Critère de sélection d'une chaîne {action}**. Quand il n'y a pas de critère c'est que l'action s'applique à toutes les lignes du fichier. 

Syntaxe : 

`awk [-F] [-v var=valeur] -f fichier-config fichier`

Argument | Description | Exemple
---------|-------------|---------
-F       | suivi du séparateur de champ | **-F:** (":" comme séparateur de champ)
-f       | suivi du nom du fichier de configuration de awk      | 
-v       | définit une variable, qui sera utilisée par la suite dans le programme | ***var***  

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

### Critères de séléction

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


## Désactiver le proxy http/https:

```bash
unset http_proxy
unset https_proxy

## Or

export http_proxy=''
export https_proxy=''

## Check with 

printenv
## Or 
printenv https_proxy

```
More [proxy_terminal](https://doc.ubuntu-fr.org/proxy_terminal)