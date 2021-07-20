# Optitrack Documentation

## Version
The current version of the OptiTrack is 1.10.3 

## Installation
For the installation process, you may consult [the optitrack website](https://v22.wiki.optitrack.com/index.php?title=Installation_and_Activation)

## Setup
The OT-PC needs to be connected to the OptiTrack cameras via Ethernet to the OptiTrack switch, which is in the Electrical cabinet. The ROS-PC, is then connected to a second network, used to stream the information.

[Here will go the diagram of the connection]

## Networks
### Robonet
This netwok is for the internet connection.
**Password**: Procrob@2016

### OptiTrack
This network is for the OptiTrack data
**Password**: 

### robotics.snt.uni.lu - Ethernet3
This network is a local network for the robots communication
**Password**: control4uav

##  Calibration
### Camera calibration
1. New project
2. Hide the calibration wand (know by the program)
3. Click on Mask Visible (We choose where to save it)
4. Click on start Wanding and start moving around with the wand 
5. Click on Calculate and Apply the results

### Ground Plane calibration
1. Put the calibration triangle (from the box) in the center on the X and Y axes 
2. Click on Set Ground Plane and apply 

### When adding a robot
To create a rigid body for streaming, select the markers of the object (at least three) and right-click in Motive and select Rigid Body -> Create From Selected Markers
1. Select the markers / robot 
2. Right Click and choose Rigid Body
3. Click on Create From Selected Markers
- The name of the robot could be changed and we can see the User ID.





