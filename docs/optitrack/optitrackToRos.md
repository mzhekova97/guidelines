# Stream position of the robot

## Steps
Before continuing with the following steps, please make sure that the [callibration](/docs/optitrack/) has been done when creating a new project.  

**Optitrack-PC**  
1. In the Motive software, go to `View-> Data Streaming` and change the local interface to the IP of the Optitrack-PC, in our case is `192.168.10.10`.
2. Then click on `Select rigid body-> Properties`.  

**ROS-PC** 
1. Make sure that the user id matches with the config file `snt_mocap_optitrack`  in mocap_optitrack node.
2. On another terminal execute `roslaunch mocap_optitrack mocap-only-m100.launch`, echo the topic to receive the position and have fun.
