# Optitrack Documentation

## Version and Licence
The current version of the OptiTrack is 1.10.3.  
Device Serial | Hardware Key: #104477  
Valid From: 31.03.2015  
Update & Support Until: 30.03.2019  
Licence Hash: 9280-1132-1549-7C8A  

* Initial License: MVCL1782
* Update Licence: MVCL1060 [Duration 1 Year]
* Update Licence: MVCL1061 [Duration 1 Year]
* Update Licence: MVCL1062 [Duration 1 Year]

## Installation
For the installation process, you may consult [the optitrack website](https://v22.wiki.optitrack.com/index.php?title=Installation_and_Activation)

>[!Warning] If the Optitrack computer is changed, please copy all the available licences from the Licence folder of the current Optitrack computer and paste them in the Licence folder of the new Optitrack computer! This solves licence issues.

## Setup
The Optitrack-PC needs to be connected to the OptiTrack cameras via Ethernet to the OptiTrack switch, which is in the Electrical cabinet. The ROS-PC, is then connected to a second network, used to stream the information.

For networks connection, please consult the [Networks section](/docs/aerolabNetworks/).

##  Calibration
### **Camera calibration**
1. Create a new project
2. The calibration wand, known by the program should not be in the flight arena.
3. Click on `Mask Visible` and choose where to save the project.
4. Click on `Start Wanding`.
5. Go inside the flight arena and start moving around with the wand in order to allow the cameras to capture as many motions as possible.
6. When done, click on `Calculate` and Apply the results

### **Ground Plane calibration**
1. Put the calibration square from the markers box in the center on the X and Y axis. It should be aligned so that it references the desired axis orientation.
2. Select the calibration square.
3. Click on `Set Ground Plane` 

### **When adding a robot**
1. Put the robot inside the nets and verify its position. If needed correct the `Capture Volume Rotation` information of <span style="color: red">X</span>, <span style="color: green">Y</span> and <span style="color: blue">Z</span>. Sometimes it is better to first check the `rostopic echo` (in [ROS setup](/docs/optitrack/optitrackToRos))  because the rotation could be done.
2. To create a rigid body for streaming, select the markers of the object (at least three) and right-click in Motive and select `Rigid Body -> Create From Selected Markers`
3. Check axes on robots. Make sure that `Properties -> Display -> Orientation=True`
