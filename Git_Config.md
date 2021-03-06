# Git (Logiciel de gestion de versions):

* Un logiciel de contrôle de version distribué, qui est chargé de suivre les modifications apportées au conten (code source).
* Local.
* Outil de ligne de commande.	
* Installer git ⇒ Installe deux paquages : 
    * git-core (interface graphique)
    * gitk (facultatif)

# GitHub (Service):

* Un service qui héberge sur un site Web des dépôts Git.
* Crée un espace de stockage centralisé où les utilisateurs peuvent stocker et accéder à leurs projets.
* Fournit une interface graphique.
* L'entreprise concurrent est GitLab.

# GitLab (Service):

* Même chose que Github, mais propose d'héberger le code dans son propre serveur.

# Bitbucket

*  Crée par l'enreprise altassian


## Configuration Git:

```
$ git config --global color.diff auto
$ git config --global color.status auto
$ git config --global color.branch auto
$ git config --global user.name "kcelia"
$ git config --global use.email "kherfallah_celia@hotmail.fr
$ git help config
$ git config --list    // Savoir ce qui a été configuré
$ git remote -v        // Connaitre l'URL
```

# Steps

1. Init (Depuis la console, se placer dans le dossier souhaité): 

    ```  
    $ git init         // Init le versionning
    $ git clone URL    // Cloner un dépôt existant: ou Créer un nouveau dépôt
    ```
    
1. Add:

    ```
    $ git add fic1 fic2 
    $ git add --all      // Recommader à : git add folder/*
    $ git add *.html        
    ```

1. Commit 

    ```
    $ git commit -m         // Commit est local
                            // m: commentaires 
                            // Commiter tous les fichiers listés dans _git status_ dans les colonnes 
                            // «Changes to be committed» et «Changed but not updated» (vert ou rouge)

    $ git commit fic1 fic2  // Pour indiquer lors du commit quels fichiers précis doivent être «commités»
    ```

1. Push:

    ```
    $ git push origin master_                             // Les envoyer sur le serveur
    $ git branch --set-upstream-to=origin/master master_
    $ git push
    ```

1. Pull:

    `$ git pull   // Récupérer du serveur`

1. Affichage:

    ```
    $ git status      // Etat du repertoire
    $ git log -n 2    // Lister les 2 derniers commits
    $ git log --stat  // Résumer plus court des commits
    $ git diff        // Affiche un diff etre le (working directory) et l’index (staging area) ou dans le repository. 
                      // Dès qu’on fait _git add_ sur un fichier modifié, il n’apparait plus dans le diff
    ```

## Branch 

```
   $ git checkout -b my_branch  // Création de la branche et on se met dessus
   // ou 
   $ git branch my_branch       // Création de la branche
   $ git branch 
   * master                     // Branche intiale sur laquelle on se trouve
     my_branch
   
   $ git checkout my_branch     // Se déplacer sur la branche
   Switched to branch 'my_branch'
   $ git branch 
     master     
   * my_branch
```

## Merge 

```
// il va souvent vous arriver de vouloir ajouter  dans une branche A les mises à jour que vous avez faites dans une autre branche B. Pour cela, on se place dans la branche A

// Résolution du conflit en supprimant des lignes...

<<<<<<<<<<< HEAD      // Balise -> La branche master
Ligne rouge           // Version dans la branche actuelle
------------          // Séparation avec une ligne
Ligne bleu            // Version dans une autre branche 
>>>>>>>>>>> my_branch // Balise fermante 

   $ git add . 
   $ git commit            // Sans -m, on peut prendre le message par défaut de merge

// Scénario: Des motifications ont été apportées à la branche my_branch
  
   $ git branch master     // On se place sur la branche master
   $ git merch my_branch   // Commit se fait automatiquement 
   
// Conflict --> A regler manuellement 
   
   $ git add .
   $ git commit -m "fix conflict"
```

## Git Checkout 

```
$ ls
   File.txt
$ vim File.txt

$ git status
   Modified File.txt

$ git checkout File.txt

$ git status
   Nothing to commit
```   

```Bash
$ git add file.txt
// Sans le commit 
$ git reset HEAD file.txt
// Retour à la version précédente 

$ git add file.txt
$ git commit -m "commit"
$ git reset HEAD~1 // Revient à la version t-1

// CASE:
$ git reset --hard HEAD~1
$ git status
   Nothing to commit
   
```
