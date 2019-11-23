## Notion de machine virtuelle 
**Contexte** : 

On a besoin de serveurs physiques avec une quantité définie de CPU, de mémoire RAM ou de stockage sur le disque.

Pendant les pics d'utilisation, on peut utiliser : la machine virtuelle (**virtualisation lourde**). 

On recrée un système complet dans le **système hôte** (isolation totale), pour qu’il ait ses propres ressources.

**Inconvénients** :
- une VM prend du **temps à démarrer**.
- une VM **réserve les ressources** (CPU/RAM) sur le **système hôte**.

**Avantages** : 
- une VM est totalement **isolée du système hôte**.
- les ressources attribuées à une VM lui sont totalement réservées.
- vous pouvez installer **différents OS** (Linux, Windows, BSD, etc.).

**Problème** : Il arrive très souvent que l'application qu'elle fait tourner ne **consomme pas l'ensemble des ressources disponibles sur la VM**. Ainsi, est né un nouveau **système de virtualisation plus léger** : **les conteneurs**.

## Notion de conteneur 

Un ***conteneur Linux*** est un processus ou un ensemble de processus isolé du reste du système, tout en étant légers.

Le **conteneur** permet de faire de la **virtualisation légère**, c'est-à-dire qu'il ne **virtualise pas les ressources** (Le conteneur partage donc les ressources avec le système hôte), il ne crée qu'une **isolation des processus**.

Technologies de conteneur : OpenVZ, LXC, Docker.

**Avantages** :
- Ne réserve que les ressources nécessaires.
- Démarrage rapide (Les conteneurs n'ayant pas besoin d'une **virtualisation** des ressources mais seulement d'une **isolation**, ils peuvent démarrer beaucoup plus rapidement et plus fréquemment qu'une VM sur nos serveurs hôtes).
- Donne plus d'autonomie aux développeurs (travailler dans un  environnement local).

**Pourquoi utiliser des conteneurs ?** 

Les conteneurs permettent de **réduire les coûts**, d'**augmenter la densité de l'infrastructure**, tout en **amélioran**t le **cycle de déploiement**.


# Docker:

Docker a été créé pour les besoins d'une société de __Platform as a Service (PaaS)"__ - **DotCloud**. 
En mars 2013, l'entreprise crée une nouvelle structure nommée __Docker Inc__.

**Docker** est un **logiciel** de **conteneurisation** qui permet la création et l'utilisation de conteneurs Linux®.

Avec la technologie DOCKER, les conteneurs sont des VM très légères et modulaires, flexibiles. On peut les créer/déployer/copier/les déplacer d'un environnement à un autre, ce qui permet l'optimisation des applications par le cloud.

## Statless/Immuatabilité
Les conteneurs Docker vous apportent aussi les **notions** de **stateless** (isolé du système hôte) et d'**immutabilité** (créer un volume de stockage).

Example : Les conteneurs de BdD (MySQL, PostgreSQL, etc.) sont des conteneurs stateful (leur bon fonctionnement dépend d'un état. Il faudra donc pérenniser leurs données afin qu'ils fonctionnent correctement). Un serveur comme Nginx est stateless, son fonctionnement ne dépend pas d'autre chose que du conteneur lui-même.


**Docker Hub** un service fourni par Docker Inc ; vous pouvez le comparer à GitHub, mais spécialisé dans le stockage d'image pour Docker.


Rappel : 
- On peut faire tourner des **images équivalent** à des **systèmes d'exploitation Linux (Debian et Ubuntu par exemple)**, mais pas **Windows ou macOS** !
- On utilise des **conteneurs** pour **réduire les coûts de l’infrastructure** (grâce à leur légèreté, ils permettent de faire tourner **plus de serveurs sur une même machine**). 
- Ils n'offrent pas d'isolation des ressources. Au contraire, l'utilisation des ressources se fait de manière flexible, contrairement à une machine virtuelle qui les réserve.
- Docker est idéal pour créer des environnements de développement, ainsi que pour déployer une application reposant sur plusieurs services.
- Docker convient bien moins à des systèmes très largement distribués et nécessitant du stockage persistant, à cause de leur aspect statefull.
- Un conteneur léger prendra moins de temps pour être récupéré de la Registry Docker. Ainsi, il démarrera bien plus rapidement. Le stockage et la vitesse d'arrêt des conteneurs ne sont pas des critères de valeur.



### Une registry
Est un logiciel qui permet de partager des images à d'autres personnes.

## Prise ne main avec Docker 

Trick : `CMD ["ifconfig"]` pour connaitre l'adresse IP.

```docker
# Docker va chercher si l'image "hello-world" est disponible en local. Dans le cas contraire, il va la récupérer sur la registry Docker officielle.

docker run hello-world

# Sur l'adresse  http://127.0.0.1:8080 ou http://192.168.99.100:8080/, se trouve la page par défaut de Nginx. 

# Transférer le trafic du port 8080 vers le port 80 du conteneur.
docker run -d -p 8080:80 nginx
```

Argument | Signification 
--|--
-t | `--tag` nom de l'image.
-d | pour détacher le conteneur du processus principal de la console. Il vous permet de continuer à utiliser la console pendant que votre conteneur tourne sur un autre processus.
-p | `--publish` pour définir l'utilisation de ports. 
-ti | permet d'avoir un shell bash pleinement opérationnel.
stop | --detach : `docker stop ID_RETOURNÉ_LORS_DU_DOCKER_RUN` puis rm.
rm | détruire le conteneur et son contenu : `docker rm ID_RETOURNÉ_LORS_DU_DOCKER_RUN`.
pull | téléchargez une image directement depuis le Docker Hub : `docker pull hello-world`.
ps | affiche l'ensemble des conteneurs existants.
system prune | supprimer l'ensemble des conteneurs Docker qui ne sont pas en status running ; l'ensemble des réseaux créés par Docker qui ne sont pas utilisés par au moins un conteneur ; l'ensemble des images Docker non utilisées ; l'ensemble des caches utilisés pour la création d'images Docker : `docker system prune`.
search | rechercher une image sur votre registry.

### Dockerfile
- Dockerfile  : Un ensemble d'instruction  décrivant l'image Docker dont le projet a besoin.
	- Chaque instruction crée une nouvelle layer correspondant à chaque étape de la construction de l'image.	

```Dockerfile

### Code source + les dépendances du conteneur

# l'image que vous allez utiliser comme base.
# *alpine* pour linux.

From debian:9

# RUN pour exécuter une commande dans votre conteneur.
# Limitez au maximum le nombre d'instructions RUN, afin de limiter le nombre de layers créées (réduire la taille de notre image Docker).
RUN apt-get update -yq \
&& apt-get install curl gnupg -yq \
&& curl -sL https://deb.nodesource.com/setup_10.x | bash \
&& apt-get install nodejs -yq \
&& apt-get clean -y

# ADD permet d'ajouter/copier/télécharger des fichiers dans votre conteneur.
ADD . /app/

# WORKDIR permet de définir votre répertoire de travail (L'ensemble des commandes qui suivront seront toutes exécutées depuis le répertoire défini).
WORKDIR /app

### Fin Code source + les dépendances du conteneur

# EXPOSE permet d'indiquer le port sur lequel votre application écoute.
EXPOSE 2368

# VOLUME permet d'indiquer quel répertoire vous voulez partager avec votre host.
VOLUME /app/logs

# CMD permet à notre conteneur de savoir quelle commande il doit exécuter lors de son démarrage.
CMD npm run start
```
### .dockeringore
Créez un fichier .dockeringore : permet de ne pas copier certains fichiers et/ou dossiers dans notre conteneur lors de l’exécution de l'instruction ADD.

### Lancer Docker

`docker build -t name_docker .`

Argument | Signification 
--|--
-t | permet de donner un nom à votre image Docker.
. | le répertoire où se trouve le Dockerfile.

`docker run -d -p 2368:2368 name_docker`

Accéder via l'URL http://127.0.0.1:2368 ou http://192.168.99.100:2368/

- Optimisation Docker :

	Après la commande docker build, Docker crée un **conteneur** pour **chaque instruction**, et le **résultat** sera sauvegardé dans une **layer**. Le résultat final étant un ensemble de layers qui construisent une **image Docker complète**. Si une layer ne bouge pas entre deux builds, Docker ne la reconstruira pas. 


### Partager une image 
1. Partagez votre fichier Dockerfile à chacun de vos collègues, et vous leur demandez de créer eux-mêmes leur propre image avec un docker build ( peut prendre beaucoup de temps). 
1. Envoyez votre image sur votre propre registry Docker.
	-  https://hub.docker.com/ 

	- Cliquez sur Create Repository, saisissez le nom de votre image ici : "ocr-docker-build", ainsi qu'une description.
	- `docker tag ocr-docker-build:latest YOUR_USERNAME/ocr-docker-build:latest` ou `docker tag id_du_conteneur openclassrooms/ocr-docker-build:latest` : va créer un lien entre notre image ocr-docker-build:latest créée précédemment et l'image que nous voulons envoyer sur le Docker Hub YOUR_USERNAME/ocr-docker-build:latest.
	- Envoyer votre image vers le Docker Hub :`docker push YOUR_USERNAME/ocr-docker-build:latest`


	### Docker Compose 
	- Permet d'orchestrer vos conteneurs, et ainsi de simplifier vos déploiements sur de multiples environnements. 
	
	- DC est un outil écrit en Python qui permet de décrire, dans un fichier YAML, plusieurs conteneurs comme un ensemble de services. 