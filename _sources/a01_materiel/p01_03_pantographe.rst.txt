************
Pantographe
************

La figure ci-dessous montre la maquette utilisée pour le projet. 

.. figure:: img/pantographe.png
    :align: center
    :width: 100%
    :alt: Raspberry Pi 5

    Système réel utilisé pour le projet

==================================
CAO du modèle 3D du pantographe
==================================

Le modèle CAO du pantographe est disponible au format step et téléchargeable ci-dessous.

:download:`maquette-5-barres_asm.stp <cad/maquette-5-barres_asm.stp>`

Afin de le recréer en URDF, il faut le modèle 3D de chaque corps. Il faut renseigner la géométrie visuelle de chaque corps ainsi que la géométrie utiilsée pour calculer les collisons du modèle. La première est obtenue avec un fichier STEP et la seconde avec un fichier dont la géométrie est simplifiée (une enveloppe cylindrique incluant tout un coprs sans être une reproduction fidèle de la réalité) est disponible au format DAE.

**Ci-dessous les fichiers STEP des différents corps du pantographe, à des fins de visualisation:**
   
   #. :download:`base.stp <cad/base.stp>`
   #. :download:`link1.stp <cad/link1.stp>`
   #. :download:`link2.stp <cad/link2.stp>`
   #. :download:`link3.stp <cad/link3.stp>`
   #. :download:`link4.stp <cad/link4.stp>`

**Ci-dessous les fichiers DAE des différents corps du pantographe, à des fins de calcul de collisons:**

   #. :download:`base.dae <cad/base.dae>`
   #. :download:`link1.dae <cad/link1.dae>`
   #. :download:`link2.dae <cad/link2.dae>`
   #. :download:`link3.dae <cad/link3.dae>`
   #. :download:`link4.dae <cad/link4.dae>`

En cas de problème de téléchargement, les fichiers sont disponibles sur ce `dépôt GitHub <https://github.com/yguel/informatique_industrielle_avec_ROS2>`_.