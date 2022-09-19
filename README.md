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
  - In the param pos_file you must to add the drone name in the list of drones
  - In the param model_package you must to add the drone name in the list of drones
------------------------------------------------------------------------------------------------------------
Add drone name (in this case 'blue' ) into the spawner_params config
  - FILE: /home/USER/mrs_workspace/src/simulation/ros_packages/mrs_simulation/scripts/mrs_drone_spawner.py
  - In the variable VEHICLE_TYPES you must to add the drone name in the list of drones
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

