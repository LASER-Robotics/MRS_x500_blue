# MRS_x500_blue
Inserts the x500 (LASER) model, in mrs_simulation
* !!!!!!!!!! WARNING THAT IF YOU MAKE THESE CHANGES, YOU'LL NOT BE ABLE TO USE ANOTHER TYPE OF UAV !!!!!!!!!!
## Installing
Install ros packages:
```
sudo apt-get install ros-noetic-control*
```
```
sudo apt-get install ros-noetic-ros-control*
```
------------------------------------------------------------------------------------------------------------
Add drone name ( in this case 'blue' ) into the parameter model_package 
  - FILE: /home/USER/mrs_workspace/src/simulation/ros_packages/mrs_simulation/config/spawner_params.yaml
  - PARAM: pos_file
```
pos_file: [None, 'Load positions and ids from .csv file with format: [id, x, y, z, heading] or .yaml file with format: [uav_name: \n id: (int) \n x: (float) \n y: (float) \n z: (float) \n heading: (float)]', [f330, f450, f550, t650, x500, eaglemk2, brus, blue]]
```
  - PARAM: model_package
```
model_package: ["mrs_simulation", 'package name for the UAV models', [f330, f450, f550, t650, x500, eaglemk2, brus, naki, blue]]
```
------------------------------------------------------------------------------------------------------------
Add drone name (in this case 'blue' ) into the spawner_params config
  - FILE: /home/USER/mrs_workspace/src/simulation/ros_packages/mrs_simulation/scripts/mrs_drone_spawner.py
  - LINE: 28
```
VEHICLE_TYPES = ['f450', 'f550', 't650', 'x500', 'eaglemk2', 'f330', 'brus', 'blue']
```
------------------------------------------------------------------------------------------------------------
- TO USE ANOTHER TYPE OF DRONE, YOU MUST REMOVE THIS CHANGES, INTO SPAWNER_PARAMS AND MRS_DRONE_SPAWNER FILES.
------------------------------------------------------------------------------------------------------------
Create a pixhawk airframe for the drone inside 
  - FOLDER: /home/USER/mrs_workspace/src/simulation/ros_packages/mrs_simulation/ROMFS/px4fmu_common/init.d-posix/airframes/ 
  - Simply copying the existing 4001_x500, and saving it as 4001_blue
------------------------------------------------------------------------------------------------------------
Add this package into your workspace/src, and build workspace with catkin build

------------------------------------------------------------------------------------------------------------
Spawn the drone by calling rosservice call /mrs_drone_spawner/spawn "1 blue --model_package blue" 
  - NOTE: Example for this https://github.com/LASER-Robotics/mrs_x500_blue/blob/main/start/session.yml#L21
  - ALWAYS USE UAV_TYPE X500
  
## Grip controller
* Example for launch https://github.com/LASER-Robotics/mrs_x500_blue/blob/main/start/session.yml#L38
* Service: rosservice call /UAV_NAME/control_manager/controller_gripper "stance: ' ' "
  - Stance can be 'open' and 'close'

