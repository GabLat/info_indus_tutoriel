************************
Création du modèle URDF
************************

La description d'un modèle URDF s'appuie sur des balises. Ces balises permettent de décrire les différents éléments du robot.
Comme expliqué dans la section :doc:`../a01_materiel/p01_03_pantographe`, nous utilisons les fichiers STEP pour créer la géométrie de chaque corps du pantographe. 
Cette description s'inscrit dans la balise ``<visual>`` qui permet de décrire la géométrie du corps.
La balise ``<collision>`` permet de décrire la géométrie du corps pour les calculs de collision. Afin de simplifier les calculs nous utilisons un maillage en format DAE correspondant à un volume simple qui contient le corps.
Ceci permet en plus de simplifier le calcul d'assurer que le robot ne rentre pas en collision car son enveloppe sera plus grande que sa géométrie réelle.

Les fichiers ont été regroupés dans un fichier URDF.

.. code-block:: json

   {
        <?xml version="1.0"?>
        <robot name="Pentograph">

        <!-- Fixation du robot à 'base_link' -->
        <link name="map"/>

        <!-- Base Link -->
        <link name="base">
            <visual>
            <geometry>
                <mesh filename="base.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.025"/>
            </visual>
            <inertial>
            <mass value="1" />
            <origin xyz="0 0 0.025" rpy="0 0 0" />
            <inertia ixx="1" ixy="0" ixz="0" iyy="1" iyz="0" izz="1" />
            </inertial>
            <collision>
            <geometry>
                <mesh filename="base.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.025"/>
            </collision>
        </link>

        <joint name="base2world" type="fixed">
            <parent link="map"/>
            <child link="base"/>
        </joint>

        <!-- Revolute Joint 1 -->
        <link name="link1">
            <visual>
            <geometry>
                <mesh filename="link1.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.225"/>
            </visual>
            <inertial>
            <mass value="0.5" />
            <origin xyz="0 0 0.05" rpy="0 0 0" />
            <inertia ixx="0.5" ixy="0" ixz="0" iyy="0.5" iyz="0" izz="0.5" />
            </inertial>
            <collision>
            <geometry>
                <mesh filename="link1.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.225"/>
            </collision>
        </link>

        <joint name="joint1" type="revolute">
            <parent link="base"/>
            <child link="link1"/>
            <origin xyz="0 0 0.05"/>
            <limit effort="1000.0" lower="-1.57" upper="1.57" velocity="0.5"/>
            <axis xyz="0 0 1"/>
            <dynamics damping="0.2" friction="0.1" />
        </joint>

        <!-- Revolute Joint 2 -->
        <link name="link2">
            <visual>
            <geometry>
                <mesh filename="link2.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.225"/>
            </visual>
            <inertial>
            <mass value="0.5" />
            <origin xyz="0 0 0.05" rpy="0 0 0" />
            <inertia ixx="0.5" ixy="0" ixz="0" iyy="0.5" iyz="0" izz="0.5" />
            </inertial>
            <collision>
            <geometry>
                <mesh filename="link2.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.225"/>
            </collision>
        </link>

        <joint name="joint2" type="revolute">
            <parent link="link1"/>
            <child link="link2"/>
            <origin xyz="0 0 0.05"/>
            <limit effort="1000.0" lower="-1.57" upper="1.57" velocity="0.5"/>
            <axis xyz="0 0 1"/>
            <dynamics damping="0.2" friction="0.1" />
        </joint>

        <!-- Revolute Joint 3 -->
        <link name="link3">
            <visual>
            <geometry>
                <mesh filename="link3.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.225"/>
            </visual>
            <inertial>
            <mass value="0.5" />
            <origin xyz="0 0 0.05" rpy="0 0 0" />
            <inertia ixx="0.5" ixy="0" ixz="0" iyy="0.5" iyz="0" izz="0.5" />
            </inertial>
            <collision>
            <geometry>
                <mesh filename="link3.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.225"/>
            </collision>
        </link>

        <joint name="joint3" type="revolute">
            <parent link="link4"/>
            <child link="link3"/>
            <origin xyz="0 0 0.05"/>
            <limit effort="1000.0" lower="-1.57" upper="1.57" velocity="0.5"/>
            <axis xyz="0 0 1"/>
            <dynamics damping="0.2" friction="0.1" />
        </joint>

        <!-- Revolute Joint 4 -->
        <link name="link4">
            <visual>
            <geometry>
                <mesh filename="link4.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.225"/>
            </visual>
            <inertial>
            <mass value="0.5" />
            <origin xyz="0 0 0.05" rpy="0 0 0" />
            <inertia ixx="0.5" ixy="0" ixz="0" iyy="0.5" iyz="0" izz="0.5" />
            </inertial>
            <collision>
            <geometry>
                <mesh filename="link4.dae" scale="1 1 1" />
            </geometry>
            <origin xyz="0 0 0.225"/>
            </collision>
        </link>

        <joint name="joint4" type="revolute">
            <parent link="base"/>
            <child link="link4"/>
            <origin xyz="0 0 0.05"/>
            <limit effort="1000.0" lower="-1.57" upper="1.57" velocity="0.5"/>
            <axis xyz="0 0 1"/>
            <dynamics damping="0.2" friction="0.1" />
        </joint>

        </robot>

   }
