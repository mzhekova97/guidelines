# Stream position of the robot

## Robots  
**DJI Diekirch:**  
IP: 192.168.30.14  
Password: control4uav

## Steps
Before continuing with the following steps, please make sure that the [callibration](/docs/optitrack/) has been done when creating a new project.  

**Optitrack-PC**  
1. In the Motive software, go to `View-> Data Streaming` and verify that the local interface is set to the IP of the Optitrack-PC, in our case is `192.168.10.10`.
2. Then click on `Select rigid body-> Properties` in order to view the userID and position of the robot.

**ROS-PC** 
1. Make sure that the user id matches with the config file `snt_mocap_optitrack`  in mocap_optitrack node. If the configuration of the robot/object is not in the file, create a new one and give different ID and topic name.
2. On another terminal execute `roslaunch snt_mocap_optitrack -name-`, echo the topic with `rostopic echo /-robot name-/pose` to receive the position. Make sure that this position is correct.  

You will need to install [chrony](/docs/optitrack/chrony) if it is not yet installed.

In order to test your settings, we provide a demo.

**Demo preparation steps**  
1. Go to your workspace source code `~catkin_ws/src` and clone our [repository](https://github.com/snt-robotics/obstacle_avoidance_project)
2. Enter your project folder `~catkin_ws/src/obstacle_avoidance_project` and execute the following:
    ```
    # for the update
    git submodule update --init --recursive
    ```
3. Go back to the workspace `~catkin_ws` and execute
    ```
    catkin_make 
    ```
4. Add the following alias in your `.bashrc`file:
    ```alias robosource='source ~/catkin_ws/src/obstacle_..../setup.bash
    ```
5. Save and execute
    ```source bashrc
    ```

**Demo Steps**
1. On your computer ping the robot and wait so that the ping gets a stabilized value bellow 2 or 3 
    ```ping 192.168.30.14
    ```
2. Access the robot with `ssh`.
3. Verify if the date matches with [chrony](/docs/optitrack/chrony) 
4. Type each of the following commands in different window.
    ```
    source $OBSTACLE_AVOIDANCE_PROJECT/setup.zsh 192.168.30.14 && tmux
    roscore
    sdk
    client
    ```
5. Make sure that the alias is added `alias robosource source $OBSTACLE_AVOIDANCE_PROJECT/setup.bash 192.168.30.14`
6. If you are using the ROS computer and not your own, access via `ssh` the ROS computer and type the following. If you are using your own, you can type it on your computer.
    ```
    robosource && roslaunch snt_mocap_optitrack mocap-m100-humans.launch

7. On your computer, execute the following commands on different windows.

    ```
    robosource && roslaunch drone_mpc_controller drone_mpc_dji_m100.launch
    robosource && rosservice call /dji_m100_diekirch/state_estimation_ekf/set_state_estimation_enabled "data: true"
    robosource && roslaunch drone_mpc_controller multi_human_ekf_obstacle_estimation.launch # if this one provokes errors in those before -> repeat the 2 lines before

    robosource && roscd drone_mpc_controller/rviz/ && rviz -d drone.rviz
    robosource && rqt #drone_mpc_controller/rviz/drone.perspective
    ```
8. Go to the `RQT` window which popped up from the robot and change accordingly the positions as explained bellow.
- In `Plugins->Topics->Message Publisher`
- Select as Topic: `/dji_m100_diekirch/drone_mpc_controller/refernce/state`
- Select the box and set the position to : 
    x = 0.0  
    y = 0.0  
    z=1.5  
9. Use `Rviz` to visualize the position
10. Have fun :) 
