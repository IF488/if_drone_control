# if_drone_control
TP Drone et Application

Note: Pour chaque nouveau terminal, il faut faire:
```
source devel/setup.bash
```
depuis votre catkin workspace

## Partie 1: Installer le simulateur
[Suivez les instructions](https://github.com/IF488/hector-quadrotor)  
Une fois installer, lancer le simulateur avec:

```
roslaunch hector_quadrotor_demo outdoor_flight_gazebo.launch
```

Faite source devel dans votre catkin ws, et activer les moteurs avec:

```
rosservice call /enable_motors "enable: true"
```

## Partie 2: Régulation en altitude
Cette partie à pour but de crée un service qui modifiera l'altitude du drone.  
Cloner le package dans le fichier src de votre catkin workspace:  

```
cd catkin_ws/src
git clone https://github.com/IF488/if_drone_control.git
catkin_make
cd ..
source devel/setup.bash
```

Dans un premier terminal, éxecuter le noeud:  

```
rosrun if_drone_control takeoff.py
```

Dans un deuxième terminal, faites appels au service:

```
rosservice call /altitude_service "a:
 data: '10'"
```

## Partie 3: Régulation en position
Cette partie à pour but de créer un service qui transmettra un waypoint au drone.  
Dans un premier terminal, éxecuter le noeud: 

```
rosrun if_drone_control waypoint.py
```

Dans un deuxième terminal, faites appels au service:

```
rosservice call /waypoint_service "x:
 data: '-5'
y:
 data: '-5'
z:
 data: '10'"
```

## Partie 4: Planification de mission
Executer le noeud avec:

```
rosrun if_drone_control Final_project.py
```