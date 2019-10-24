### Tensorflow: (ancienne version)

* Un outil open source d’apprentissage automatique développé par Google Brain en 2015.
* API front-end de développement d’applications.
* Repose sur le langage de programmation Python, tandis que l’exécution de ces applications s’effectue en C++ haute-performance.

### Pytorch:

* Un outil open source d’apprentissage automatique développé par Facebook en 2016. 

   

#### Différences:

* La manière dont on définit les graphiques de calcul. 
    * Tensorflow crée un graphique statique (définir l’ensemble du graphe de calcul du modèle, puis exécuter votre modèle ML).
    * PyTorch croit en un graphique dynamique (vous pouvez définir / manipuler votre graphique à tout moment. Ceci est particulièrement utile lorsque vous utilisez des entrées de longueur variable dans les RNN).
* Plus difficile d'apprendre Tensorflow que PyTorch.
* TensorBoard: un outil qui permet de visualiser vos modèles ML directement dans votre navigateur. 
* Production:
    * Tensorflow: Développer des modèles pour la production.
    * Pytorch: Faire des recherches ou construction de prototypes rapides.