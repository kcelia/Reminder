## Git (Logiciel de gestion de versions):

* Un logiciel de contrôle de version distribué, qui est chargé de suivre les modifications apportées au conten (code source).
* Local.
* Outil de ligne de commande.	
* Installer git ⇒ Installe deux paquages : 
    * git-core (interface graphique)
    * gitk (facultatif)

## GitHub (Service):

* Un service qui héberge sur un site Web des dépôts Git.
* Crée un espace de stockage centralisé où les utilisateurs peuvent stocker et accéder à leurs projets.
* Fournit une interface graphique.
* L'entreprise concurrent est GitLab.

#### Configuration Git:

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

1. Init (Depuis la console, se placer dans le dossier souhaité): 

    ```  
    $ git init         // Init le versionning
    $ git clone URL    // Cloner un dépôt existant: ou Créer un nouveau dépôt
    ```
    
2. Add:

    ```
    $ git add fic1 fic2 
    $ git add --all      // Recommader à : git add folder/*
    $ git add *.html        
    ```

3. Commit 

    ```
    $ git commit -m         // Commit est local
                            // m: commentaires 
                            // Commiter tous les fichiers listés dans _git status_ dans les colonnes 
                            // «Changes to be committed» et «Changed but not updated» (vert ou rouge)

    $ git commit fic1 fic2  // Pour indiquer lors du commit quels fichiers précis doivent être «commités»
    ```

4. Push:

    ```
    $ git push origin master_                             // Les envoyer sur le serveur
    $ git branch --set-upstream-to=origin/master master_
    $ git push
    ```

5. Pull:

    `$ git pull   // Récupérer du serveur`

6. Affichage:

    ```
    $ git status      // Etat du repertoire
    $ git log -n 2    // Lister les 2 derniers commits
    $ git log --stat  // Résumer plus court des commits
    $ git diff        // Affiche un diff etre le (working directory) et l’index (staging area) ou dans le repository. 
                      // Dès qu’on fait _git add_ sur un fichier modifié, il n’apparait plus dans le diff
    ```
