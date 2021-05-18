# ARG Software Architecture 

This repository is provides a brief guide on of the software architecture to be followed during the execution of the projects of the Automation and Robotics Research Group (ARG). If all of us follow this architecture we can have a standardized rules for developing, managing and executing workspaces and most of the developed code can be reutilized between different projects.

## How Do I Start?

### Create Github Account

Firstly, if you dont have a github account create one and also setup the ssh keys for your computer and add them to your github account. SSH keys are useful for faster and secure pulling and pushing of your code. See [this guide](https://www.inmotionhosting.com/support/server/ssh/how-to-add-ssh-keys-to-your-github-account/) for setting up your ssh keys.

### Repository Management

Each project will have a parent repo named as *project_ws*. For example in case of the project stugalux, the parent repo is called as *stugalux_ws*. We will use ros [vcs-tools](http://wiki.ros.org/vcstool) for repository management. The instructions below are used for creating a parent repository for the project *5G_sky*. 

#### Create a new repo on github as shown in the image below:
<img src="images/github_repo.png" width="" height=""> 

####   Clone the repo locallly in your workspace folder:   
    ``` 
    mkdir -p ~/workspace/ros/ && cd ~/workspace/ros/
    git clone git@github.com:snt-robotics/5G_sky_ws.git
    cd 5G_sky_ws/ && curl -O  https://github.com/hridaybavle/.gitignore/blob/master/.gitignore
    git add .gitignore && git commit -m 'added .gitignore' && git push
    ```

#### Create the folder structure:
```
cd ~/workspace/ros/5G_sky_ws && mkdir src && cd src
mkdir -p drivers/real &&  mkdir -p drivers/simulation
mkdir generic && mkdir navigation && mkdir utils
```

In the above commands we created a folder structure for our algorithm repos inside src folder. There will be four main folders namely: **drivers**, **generic**, **navigation**, **utils**. Note: More folders can be added based on the requirements of each projects, but try to keep the folder structure as compact as possible.

**drivers** : This folder would contain all the necessary packages for which provide necessary drivers for running the simulation environments as well as the real robot along with its on-board sensors. For example drivers can have sub-folders such as *real* and *simulation* which contain the packages for executing the real world robot and the robot in simulation respectively. 

**generic** : This folder contains all the relevant packages for launching all the processes required for successully executing a relevant task/mission for the project. It can be sub-divided into bringup and desciption packages. Example `5G_sky_ws` will have `5G_sky_bringup` and `5G_sky_description`. In the section below we will explain in detail the creation of these repositories. 

**navigation** : This folder would contain all the packages required for navigation of the robot. It can be divided into sub-folders such as *slam*, *localization*, *planning* and *perception*. 

**utils** : This folder should contain all the additional packages required but are not available in the form of binaries.

#### Create the Bringup and Description:

#### Clone all Remaining Required Repos:

#### Upload the Workspace Management File:

#### Maintain the Workspace
    
    *  Push the Repos in the workspace

    * Tag the Repos in the workspace

    * Update the Repos in the workspace

