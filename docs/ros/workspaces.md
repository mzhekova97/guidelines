# Workspaces

Each project should have its own ROS workspace named as `<project_name>_ws`. For project "Foo", for instance, we would have a workspace named `foo_ ws`.

[vcstool](http://wiki.ros.org/vcstool) should be used for managing workspace repositories.

Although workspaces are versioned, their repository should not contain any code. Instead, they should contain the following elements:

```
    |- .gitignore
    |- .rosinstall
    |- requirements.txt
    |- Dockerfile
    |- README.md
    |- setup.sh
```

The `.rosinstall`file points to one or more ROS package repositories that are required by the project, and is used by `vcstool` to fetch these dependencies.

 Similarly, the `requirements.txt` file should contain a list of required Python modules, whereas the `Dockerfile` specifies how to build a Docker container for the project.

 Finally, `setup.sh` is a script that calls automates the setup of the workspace e.g., calling `vcstool`, `pip`, and so on.
 
 Note that except for the `.rosinstall`, all other files are optional.

### Starting a new project

When starting a new project, create new repository on GitHub, as shown in the image below:
    
<img src="assets/github-repo.png" width="" height=""> 

Then clone this new repository:

``` 
mkdir -p ~/workspace/ros/ && cd ~/workspace/ros/
git clone git@github.com:snt-robotics/5G_sky_ws.git
cd 5G_sky_ws/ && curl -O https://raw.githubusercontent.com/hridaybavle/.gitignore/master/.gitignore
git add .gitignore && git commit -m 'Add .gitignore' && git push
```

Next, scaffold the workspace:
    
```
cd ~/workspace/ros/5G_sky_ws & \
mkdir -p src/generic src/navigation src/utils src/drivers/real src/drivers/simulation
```

In the above commands we created an opinionates layout under the `src` directory to keep our projects's packages organized. 

This layout comprises four main folders, namely: `/drivers`, `/generic`, `/navigation`, and `/utils`. 

> [!Warning] Other directories can be added depending on the requirements of each project, but try to keep the folder structure as compact as possible.

Below is a description of what should be inside each of these directories.

* `/drivers` : This folder contains all packages providing drivers for running both simulations and the real robot. The `/drivers` directory can have sub-folders such as `/real` and `/simulation`, containing packages for executing the real world robot and the robot in simulation, respectively. 

* `/generic` : This folder contains all relevant packages for launching the processes required for successully executing a given task/mission for the project. It can be further divided into `/bringup` and `/description`. As an example, the `5G_sky_ws` workspace could have both the `5G_sky_bringup` and `5G_sky_description` subdirectories.

* `/navigation` : This folder contains all packages required for navigation. It can be divided into sub-folders such as `/slam`, `/localization`, `/planning` and `/perception`. 

* `/utils` : This folder contains all packages that are required but not available in the form of binaries.

* #### Create the Project Bringup and Project Description:

    Each project will have a bringup repository and a description repository, these repos will be named as project_bringup and project_description.

    * **project_bringup** : The project_bringup as the name suggests is responsible for bringing up all the processes responsible for proper execution of the robot and its sensors, where it be in a simulated environment or in real world. Basically it has all the launch and config files of the different packages which are grouped together to launch an entire mission of the robot. How to create a bringup repo (example: `5G_sky_bringup`):
        
        ```
        cd ~/workspace/ros/5G_sky_ws/src/generic && catkin_create_pkg 5G_sky_bringup roscpp rospy 
        cd 5G_sky_bringup && mkdir launch && mkdir config
        ```    

        The above command creates a ros repo, it also adds `launch` and `config` folders. You have to push this created ros repo to github. 

    * **project_description** : As the name suggests the project description contains the description files the projects. The description file contains the urdfs, meshes, worlds etc for the robots and the environment of the robot. 
        
        ```
        cd ~/workspace/ros/5G_sky_ws/src/generic && catkin_create_pkg 5G_sky_description
        cd 5G_sky_description && mkdir launch && mkdir config && mkdir urdf && mkdir worlds
        ```    

        The above command will create a ros repo which will have `launch`, `config`, `urdf` and `worlds` folders. 


* #### Clone all Remaining Required Repos: 

    You should also clone all the relevant ros packages that do not have binaries and need to installed in the project_ws in the relevant folders. For example if we need a ros package of `hdl_graph_slam` inside our `5G_sky_ws` you can clone it inside the folder navigation/SLAM

* #### Upload the Workspace Management File:

    Once you have all the repos cloned just perform the command below to create a `.rosinstall` file which will contain the entire repository management. 

    ```
    cd ~/workspace/ros/5G_sky_ws && touch .rosinstall
    vcs export src > .rosinstall
    git add .rosinstall && git commit -m 'added .rosinstall'
    git push 
    ```

* #### Maintain the Workspace

    * Update the Repos in the workspace: If the repos in the workspace have been updated in the remote, you simply need to follow the command to update them locally:
        ```
        cd ~/workspace/ros/5G_sky_ws  
        vcs import src < .rosinstall    
        ``` 

    * Tag the Repos in the workspace: Instead of using master branch in your.rosinstall file you can take advantage of git tags. For example, instead of using `master` branch in your `.rosinstall` file for the `5G_sky_bringup` repo, you can use a specific version or a commit. You can create a version for a repo like `5G_sky_bringup` using the following commands:
        ```
        roscd 5G_sky_bringup 
        catkin_prepare_release 
        ```
