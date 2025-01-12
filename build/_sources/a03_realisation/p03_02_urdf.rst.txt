************************
Création du modèle URDF
************************

La description d'un modèle URDF s'appuie sur des balises. Ces balises permettent de décrire les différents éléments du robot.
Comme expliqué dans la section :doc:`../a01_materiel/p01_03_pantographe`, nous utilisons les fichiers STEP pour créer la géométrie de chaque corps du pantographe. 
Cette description s'inscrit dans la balise ``<visual>`` qui permet de décrire la géométrie du corps.
La balise ``<collision>`` permet de décrire la géométrie du corps pour les calculs de collision. Afin de simplifier les calculs nous utilisons un maillage en format DAE correspondant à un volume simple qui contient le corps.
Ceci permet en plus de simplifier le calcul d'assurer que le robot ne rentre pas en collision car son enveloppe sera plus grande que sa géométrie réelle.