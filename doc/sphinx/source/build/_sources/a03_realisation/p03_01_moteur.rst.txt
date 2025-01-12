**************************
Actionnement des moteurs
**************************

Afin de piloter les moteurs de notre maquette, nous avons suivis le turoriel suivant jusqu'à la minute 1:15 :

.. raw:: html

   <iframe width="640" height="360" src="https://www.youtube.com/embed/E8XPqDjof4U" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Nous allons maintenant décrire les étapes suivantes pour piloter les moteurs de notre maquette.

################################################
Détails des commandes pour piloter les moteurs
################################################

==============================
Préparation de l'environnement
==============================

Nous utilisons ROS Jazzy sur notre machine nous devons donc modifier le clonage du dépôt et ainsi utiliser la commande suivante pour forcer l'utilisation d'Humble:

.. code-block:: bash

   git clone -b humble-devel https://github.com/ROBOTIS-GIT/DynamixelSDK



Après s'être déplacé dans le répertoire ``robotis_ws``, nous devons vérifier si la commande ``ros2`` est reconnue. Si ce n'est pas le cas, nous devons ajouter la ligne suivante à la fin du fichier ``.bashrc`` :

.. code-block:: bash

   source /opt/ros/jazzy/setup.bash


Une fois la vérification du package ROS effectuée, nous devons configurer et construire le projet en exécutant les commandes suivantes dans le Workspace:

.. code-block:: bash

   source install/setup.bash
   colcon build --symlink-install


==============================
Exécution du programme
==============================

Afin de pouvoir communiquer via les ports série, nous devons ajouter notre utilisateur au groupe ``dialout``.

.. code-block:: bash

   sudo usermod -aG dialout <linux_account>

Où ``<linux_account>`` est le nom d'utilisateur Linux. La commande ``whoami`` permet de connaître le nom d'utilisateur. Redémarrez ensuite l'ordinateur pour enregistrer les changements.

Le code source doit être modifié pour correspondre à notre situation. Il faut donc modifier le fichier ``read_write_node.cpp`` situé dans le dossier ``src > DynamixelSDK > dynamixel_sdk_examples > src``. Les lignes 42 à 46 doivent être remplacées par le code suivant :

.. code-block:: bash

   // Control table address for X series (except XL-320)
   #define ADDR_OPERATING_MODE 255
   #define ADDR_TORQUE_ENABLE 24
   #define ADDR_GOAL_POSITION 30
   #define ADDR_PRESENT_POSITION 36

Les moteurs utilisés communiquent avec un baude rate de ``115200``. Il faut donc modifier la ligne 49 du fichier ``read_write_node.cpp`` pour correspondre à cette valeur :

Pour terminer, il faut reconstruire, sourcer à nouveau et exécuter le programme. Dans le dossier ``robotis_ws``, exécutez les commandes suivantes :

.. code-block:: bash

   colcon build --symlink-install
   source install/setup.bash

Et enfin  :

.. code-block:: bash

   ros2 run dynamixel_sdk_examples read_write_node

====================
Pilotage des moteurs
====================

Les moteurs seront controlés en position. Pour cela dans ``robotis_ws``, exécutez la commande suivante :

.. code-block:: bash

   source install/setup.bash

La commande suivante permet de publier un message pour changer la position du moteur :

.. code-block:: bash

   ros2 topic pub -1 /set_position dynamixel_sdk_custom_interfaces/msg/SetPosition "{id: 1, position: 500}"

Comme deux moteurs sont utilisés, il faut changer l'identifiant du moteur pour le second moteur enchangeant ``id: 1`` par ``id: 2``.

La position de chaque moteur est comprise en ``0`` et ``1023``. Il est possible de changer la position en modifiant la valeur de ``position: 500``.