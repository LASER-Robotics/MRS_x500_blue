# MRS_x500_blue
Inserts the x500 (LASER) model, in mrs_simulation

## Inserting
* Add drone name (in this case 'blue' ) into the spawner_params config, for parameter model_package 
FILE: /home/USER/mrs_workspace/src/simulation/ros_packages/mrs_simulation/config/spawner_params.yaml
LINE: 56
```
model_package: ["mrs_simulation", 'package name for the UAV models', [f330, f450, f550, t650, x500, eaglemk2, brus, naki, blue]]
```
* Create a pixhawk airframe for the drone inside 
FOLDER: /home/USER/mrs_workspace/src/simulation/ros_packages/mrs_simulation/ROMFS/px4fmu_common/init.d-posix/airframes/ 
Simply copying the existing 4001_x500, and saving it as 4001_blue
* Add this package into your workspace/src, and build workspace with catkin build
* Spawn the drone by calling rosservice call /mrs_drone_spawner/spawn "1 blue --model_package blue" 
  NOTE: Example for this inside the start folder 
  
  !!!!!!!!!!!!!!!!!!!! WARNING THAT IF YOU MAKE THESE CHANGES, YOU'LL NOT BE ABLE TO USE ANOTHER TYPE OF UAV !!!!!!!!!!!!!!!!!!!!!!!!!!
