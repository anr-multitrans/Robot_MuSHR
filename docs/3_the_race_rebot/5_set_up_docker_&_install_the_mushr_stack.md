---
noteId: "fd58beb00f8611eea038e3eb8b9b08a3"
tags: []
layout: default
title: Set up Docker & Install the MuSHR stack
parent: The race rebot
nav_order: 5
---

# Set up Docker & Install the MuSHR stack
We will work directly on TX2. Here are the essential steps for us.

## Setup Docker
[REF](https://mushr.io/tutorials/noetic_first_steps/#:~:text=Setup%20Docker%20%26%20Install%20MuSHR%20stack)

### 1. [Install the Compose plugin](https://docs.docker.com/compose/install/linux/#install-using-the-repository)

{: .warning }
never install the docker engine already installed on Jetson TX2 default.

**Step 1:** Set up the repository. Find distro-specific instructions in the link below for your system. Perform the steps at **Set up the repository**. 

{: .warning }
Do not continue to Install Docker Engine!

Back to the [Install the Compose plugin](https://docs.docker.com/compose/install/linux/#install-using-the-repository) and continue with step 2.
![](../assets/images/plugin.png)

**Step 2:** run the commands depending on your system.

**Step 3:** Verify that docker-compose is installed correctly. **You can always check with this command if needed.**


### 2. Manage docker as a non-root user 
Following the tutorial - [Linux post-installation steps for Docker Engine](https://docs.docker.com/engine/install/linux-postinstall/). **Reboot TX2 after this.** Otherwise, before you reboot, you need to run 
```
$ newgrp docker
```
every time when you launch a new terminal, otherwise, you won’t run docker commands without sudo.


## Install MuSHR stack
### 1. Clone mushr stack
Suggest cloning it to your SD card because TX2 doesn’t have too many memories.
```
$ mkdir -p [your_path]/catkin_ws/src 
$ cd catkin_ws/src 
$ git clone --branch noetic https://github.com/prl-mushr/mushr.git
```
You can also download it from our [GitHub](https://github.com/Lilly-yang/catkin_imredd)


### 2. Docker setting
**a. Suggest using our docker image**

Go to the file _[your_path]/catkin_ws/src/mushr/mushr_utils/install/docker-compose-robot.yml_, modify the parameter **image**: 
```
...
services:
  mushr_noetic:
    image: pdaelm/imredd_mushr:02_2023 # mushr/mushr:${MUSHR_OS_TYPE}
...
```

**b. Attaches the catkin_ws volume so you can edit code outside or inside the docker container**

Got to the file _[your_path]/catkin_ws/src/mushr/mushr_utils/install/docker-compose-robot.yml_, add below to the Volumes parameter:
```
...
volumes:
      ...
      - ${MUSHR_WS_PATH}/catkin_ws:/root/catkin_ws
...
```


**c. Run the installation script** 
```
$ [path]/catkin_ws/src/mushr/mushr_utils/install/mushr_install.bash
```
It will prompt you with two questions. **For running the MuSHR robot, the answer should be [yes] and [no].** This will install a series of necessary packages, and create a script mushr_noetic in /usr/local/bin which initializes a docker container with all of the mushr configs installed.

{: .warning}
**Watch out for the log:**

**Warnings of git are ok** because you may already have the directories and don’t need to update them.

**Failure is not ok:** _“failure to make file /usr/local/bin/mushr_noetic”_ may cause the failure to run the command ```$ mushr_noetic```. Normally it becaus there is already a _mushr_noetic_ file exit. You should:
1. delete it with root authority
```
$ sudo rm /usr/local/bin/mushr_noetic
```
2. And run the install _.bash_ file again
```
$ [path]/catkin_ws/src/mushr/mushr_utils/install/mushr_install.bash
```

**d. Launch mushr_noetic docker continar**

Close the terminal and open a new one, start a container: 
```
$ mushr_noetic 
```
(The first time running this command will take some time to download the Docker image.) 


{: .note}
if you run the mushr_noetic before and you want to start the same container, try:```$ docker start [container_ID] && docker exec -it [container_ID] bash```.


**e. catkin build**

In the container(same terminal), run catkin build: 
```
$ cd catkin_ws && catkin build 
$ cd && source .bashrc 
```
(you only do it for the first time when you start a new container or you add new files in catkin_ws)


**f. Modify the parameters of ros_ip in _.bashrc_:** 

```$ export ROS_HOSTNAME=localhost ``` **[sugesst]** 

or 

```$ export ROS_IP=[IP]```

when your IP is static, otherwise you need to modify it every time when your IP changes, you can check it with ```$ ifconfig``` and **wlan0:…inet:[IP]…**
![](../assets/images/ip.png)

**To check the .bashrc file in the container, you have two ways:**
1. In the container bash terminal:
```$ vim .bashr```
2. In the VS code attached to the container:
Directly click the file .bashrc under the /root/

You can also use these two ways above to modify the .bashrc file.

{: .note}
```.bashrc``` is a file in the docker container, you have to commit to persist it. But sometimes it may doesn’t work. If you wait too long and you see the error below when you launch a ```.launch``` file, most probably the IP address is incorrect, run the ```$ export ROS_HOSTNAME=localhost``` again.
![](../assets/images/ip_error.png)

**g. Launch ROS teleop** 

```$ roslaunch mushr_base teleop.launch``` 

Make sure no errors are reported. **[control + c]** to stop it.


**More sensors(cameras) setting:**
- Depth image data: set the parameters: **depth from false to true** in _[path]/catkin_ws/src/mushr/mushr_hardware/mushr_hardware/launch/racecar-uw-tx2/sensor.launch_ or _[path]/catkin_ws/src/mushr/mushr_hardware/realsense/realsense2_camera/launch/rs_camera.launch_ 
- Set the parameters of **fisheyes from false to true** in _rs_camera.launch_ 


Now you can [control the robot with a PS4 controller](https://anr-multitrans.github.io/Robot_MuSHR/docs/3_the_race_rebot/4_control_robot_w_a_ps4_controller/).


**h. Exit the container bash**
Just run:

```$ exit```


**Supplements:**

1. Check container ID and image_name:
 ```$ docker ps -a (to check the container info)```
 ![](../assets/images/contianr_id.png)

2. **[do it every time you make changes in the container]** The files made inside the docker container will only persist if you commit. Re-open a new terminal:
```$ docker commit [container_ID] [image_name] ```

3. If you need more terminal windows in the container, there are three ways to reach it:

    i. Open a new terminal, check the container ID, and go to its bash:
    ```$ docker exec -it [container ID] bash```

    ii. Tmux: [Getting Started · tmux/tmux Wiki · GitHub](https://github.com/tmux/tmux/wiki/Getting-Started)

    iii. VS code **[suggestion]**:
    
        a. (if on another PC) connect vs code to remote: ssh robot@[IP address]

        b. Launch the container if you don’t have one, and connect vs code to the container

        c. Open the terminal in VS code as much as you want

	We suggest using this on your own PC because launching VS code also costs the memories of TX2 which is not too much.
