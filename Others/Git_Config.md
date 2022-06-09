# Les modèles de gestion
1. Un serveur central
- Contrôle toute la base de code du logiciel.
- Les developpeurs recupèrent une version à la fois.
- Exemple: cvs, svn
2. Modèle distribué:
- Tous les acteurs du projet on une copie de la base de code.
- Pas besoin d'être connecté au serveur pour travailler.
- Example: git, mercurial

# Git (Logiciel de gestion de versions)

* Un logiciel de contrôle de **version distribué** or **décentralisée**. Il n'est pas nécessaire de disposer des accès à un serveur maître pour l'utiliser. Chacun des utilisateurs possèdent une copie des sources et de l'historique en local.
* Permet d'avoir un historique des modifications du code source.
* Permet de travailler plus facilement en équipe.
* Outil de ligne de commande.	

Installer git ⇒ Installe deux paquages: 
    * git-core (interface graphique)
    * gitk (facultatif)

# GitHub (Service)

* Un service qui héberge sur un site Web des dépôts Git.
* Crée un espace de stockage centralisé où les utilisateurs peuvent stocker et accéder à leurs projets.
* Fournit une interface graphique.
* L'entreprise concurrent est GitLab.

### GitLab (Service)

* Même chose que Github, mais propose d'héberger le code dans son propre serveur.

### Bitbucket

*  Crée par l'enreprise Altassian.

### Gists

* Permet de partager un morceau de code.

### Adding new collaborators

`Setting > Collaborators`.

### Accès aux dépôts Github 

Il existe 2 modes de communications sécurisés avec un server:

1. SSH 
2. HTTPS:
   - Moins sécurisé que le SSH
   - Accès via Login/PassWord or Login/Token
         + Le token est généré aléatoirement 

## Configuration Git

```
sudo apt install git-all

git help config

git config --global color.diff auto
git config --global color.status auto
git config --global color.branch auto
git config --global user.name "kcelia"
git config --global use.email "kherfallah_celia@hotmail.fr
git config --list    # What has been done so far
git remote -v        # Connaitre l'URL
```

# Basic commands 

## Init

- Depuis la console, se placer dans le dossier souhaité.
- `git init` transforme votre _dossier classique_ en un _repository git_ en y ajoutant un _.git_.
- _.git_ contient:
   * Historique
   * Zone d'index 
         + Indexer une modification ⇒ `git add` 
         + Désindexer une modification ⇒ `git reset`
   * Autres informations pour la gestion

```  
git init                                                              # Init le versionning
git clone URL                                                         # Cloner un dépôt publique existant: ou Créer un nouveau dépôt
git clone https://username:githubmdp@github.com/username/project.git  # Cloner un dépôt privé
```

If you have a special character in your password, replace it with values from this website : https://support.brightcove.com/special-characters-usernames-and-passwords. Example: p@ssword --> p%40ssword
  
## Add and Reset
- Zone index.
- Add pour Indexer une modification.
 ```
 git add fic1 fic2 
 git add --all      # Recommader à `git add folder/*`
 git add .          # Tout
 git add *.html        
 ```
- Reset pour désindexter une modification.

```
 git reset fic1      

git add file.txt        # Sans le commit 
git reset HEAD file.txt # Retour à la version précédente 

git add file.txt
git commit -m "commit"
git reset HEAD~1        # Revient à la version t-1

git reset --hard HEAD~1
git status
   Nothing to commit
```
 
## Tag
- Permet de naviguer facilement et identifier clairement des versions bien précises
- Le tag master se positionne toujours sur le dernier commit
- Les custom tags restent attacher au commit lors de leur création

```
git log 
git checkount SHA-1
git tag version1 -m "V1"

git tag --delete version1

git tag # Lister les tags
```

## Commit
- Zone dépôt local (le commit est local).
- SHA-1: Idenfiant unique de 40 caractères
- Une fois que les modifications sont dans la *Zone d'Index*, il faut les enregistrer dans le dépôt local via `git commit`.
- Informations sur l'auteur, date de création, commentaire décrivant le commit _-m_
- Liste SHA-1 de ses parents

```
git commit -m  "Message" # Commiter tous les fichiers listés dans _git status_
git commit fic1 fic2     # Quels fichiers doivent êtres commités
 ```

**Comment naviger dans l'historique des commits ?**

```
git log            # Lister tous les commits
git checkout SHA-1 # Deplacer le head -> master sur le commit souhaité

git log            # N'afficher plus les commits effectués après le SHA-1 selectionné

git checkout master # Revenir à la branche master
git log
```

## Push

```
git push --tags    # Push all the tags
git push origin V1 # Push the tag V1

git push origin master 
git branch --set-upstream-to=origin/master master_
git push
 ```

## Pull

`git pull   # Récupérer du serveur`

## Stash 
- Isoler des modifications

```
git checkout V1

git stack save " isolate thse modifications" 

git stash list     # Display all the index
git stash show 0   # Get more details about index 0

git checkout V0

git checkout V1
git stash pop 0    # Bring back the modifications
git add .
git commit -m "Update"
git push
```

## Affichage

```
git status        # Etat du repertoire

git log            # List des commits
git log V2         # List des commits de la branche V2
git log -n 2       # Lister les 2 derniers commits
git log --stat     # Résumer plus court des commits    

git show SHA-1     # Afficher les modifications d'un commit particulier
git show mastet    # utiliser le tag au lieu du SHA-1
            
git diff --cached  # Visualiser les modifications avant le commit
git diff           # Visualiser les modifications après le commit

git blame hello.html           # Display more details
git blame -L 10,20 hello.html
git blame -L 10.+4 hello.html
```

## Branch

Une branche est un ensemble de commits.
```
   git checkout -b my_branch  // Création de la branche et on se met dessus
   // ou 
   git branch my_branch       // Création de la branche
   git branch 
   * master                     // Branche intiale sur laquelle on se trouve
     my_branch
   
   git checkout my_branch     // Se déplacer sur la branche
   Switched to branch 'my_branch'
   git branch 
     master     
   * my_branch
```

## Merge

- Resoudre des conflits lors de la fusion de branches

```
<<<<<<<<<<< HEAD       # Balise -> La branche master
Ligne rouge            # Version dans la branche actuelle
------------           # Séparation avec une ligne
Ligne bleu             # Version dans une autre branche 
>>>>>>>>>>> my_branch  # Balise fermante 
```

- Scenario: Conflict entre 2 commits avec Stash
```
git stash save "Saving the changes in stash because we have a conflict" 

git pull 

git stash pop  # Auto-merging CONFLICT
               # You need to solve the merge manually 
    
git add file.txt
git commit -m "Solving conflict"
git push
```

- Scenario: Conflict entre 2 commits avec Merge

Le soucis avec solution, pollue l'historique.

```
git pull # Then, update your file manually
git add file.twt
git commit -m "merge the changes" # Sans -m, on prend le message par défaut de merge
git push 

git merge --abort # Undo, the previous pull
```

- Scenario: Conflict entre 2 commits avec pull --rebase

Pour ne pas polluer l'historique, deplacer le commit
```
git add file.txt
git commit -m "Updating"
git pull --rebase
git push
```
## Branch

```
git branch BRANCH_A_MERGE
git branch                                    # Lister les branches

git checkout BRANCH_A_MERGE

git add file.txt
git commit -m"commit 1"

git push --set-upstream origin BRANCH_A_MERGE  # Créer un lien entre notre branche et le dépôt distant

git add file.txt
git commit -m"commit 2"

git push                                       # Once the link is established, we can use the pull command

git pull                                       # Récupérer la branch
git branch -a
git checkout  BRANCH_A_MERGE

git add file.txt
git commit -m"commit 3"
git push 
```

### Merge Branches

1. Methode 1:
```
git merge BRANCH_A_MERGE # Fix the conflict manually
git add file.txt
git commit -m "merge branch BRANCH_A_MERGE with master branc"
```
- Merging using rebase

```
git merge BRANCH_A_MERGE # Fix the conflict manually
git add file.txt
git commit -m "merge branch BRANCH_A_MERGE with master branc"
```

1. Methode 2:

```
git checkout SHA-1 # SHA-1 du commit souhaité 
git checkout -b BRANCH2

git add file.txt
git commit -m "commit1"

git rebase master # Edit the conflicts manually
git add file.txt # Indiquer à git que le conflit a été réglé manuellement
git rebase --continue

git checkout master
git merge BRANCH2
```

### Delete branch

```
git branch BRANCH_A_MERGE 
git checkout BRANCH_A_MERGE

git add fichier.txt
git commit -m "commit"
git push --set-upstream origin BRANCH_A_MERGE  

git checkout master
git branch -d BRANCH_A_MERGE               # Delete la branche en local
git branch -a
git push origin --delete BRANCH_A_MERGE    # Delete la branch en remote
git branch -a
```

## Cherry-pick

- Mettre le commit de la branche BRANCH_A_MERGE dans la branche master
```
git log BRANCH_A_MERGE
git cherry-pick SHA-1
git log                    # Logs of master branch
git push
```

## Create a folder via graphical interface:

`Create_file > my_folder/.gitkeep > Create_file`

*.gitkeep* is not a feature of Git. To add an empty directories in Git, people have created the convention of putting files called *.gitkeep* in these directories. 

The file could be called anything. Git assigns no special significance to this name.
Adding a .gitignore file to the empty directories is possible, but some people see this as confusing since the goal is to keep the empty directories, not ignore them.
