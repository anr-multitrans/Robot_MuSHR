---
noteId: "ba8ab0608d1e11ed8656897383d7b310"
tags: []
layout: default
title: Quickstart with Foxglove
parent: Noetic version of MuSHR
nav_order: 1
---

# Quickstart with Foxglove
Learn how to simulate the MuSHR Car with Foxglove visualizations.

![](../../assets/images/foxglove.jpg)

{: .note }
This tutorial is for MacOS or Linux users only.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## MuSHR Docker Container

### Installing Docker
First, install [Docker](https://docs.docker.com/get-docker/) and [Docker Compose](https://docs.docker.com/compose/install/) for your machine.

|                | Version |
|:---------------|:--------|
| Docker         | 20+     |
| Docker Compose | 1.29+   |

{: .warning }
> Check your [JetPack version](https://developer.nvidia.com/embedded/jetpack-archive), if it comes with Docker (e.g. version 4.6.1), do not reinstall the Docker, just install Docker-Compose.

{: .note }
If on Linux, follow the [post install](https://docs.docker.com/engine/install/linux-postinstall/) steps to make sure you can run Docker without root privileges.

### Installing MuSHR Docker Container
#### Clone the MuSHR repository at catkin_ws/src

```
$ mkdir -p catkin_ws/src
$ cd catkin_ws/src
$ git clone --branch noetic https://github.com/prl-mushr/mushr.git
```
#### Run the installation script

```
$ ./mushr/mushr_utils/install/mushr_install.bash
```
It will prompt you with two questions.

- For running the MuSHR simulator, the answers should be no, no.
- For running the MuSHR racecar, the answers should be ?, ?.

---

{: .note }
You can edit code outsideor inside the docker container. Other files made inside the docker container will not persist unless you commit.

### Run the MuSHR Docker Container
open a new terminal and run:
```
$ mushr_noetic
```
The first time running this command will take some time to download the Docker image. If the prefix switches to root, the installation was successful.

{: .note}
```$ mushr_noetic``` will generate a new container, and if you want to use the same container, you can run ```$ docker start [container ID]```. View Container ID run ```$ docker ps```.

In the same terminal (within the Docker container), build the MuSHR software stack. (First run or when there is an update.)
```$ source .bashrc && cd catkin_ws && catkin build```

## Foxglove Studio
We can use Foxglove Studio to visualize our robot and map.

### Downloading Foxglove Studio
{: .note }
Make sure [foxglove](https://foxglove.dev/download) is the latest version.

### Import layout
Open Foxglove Studio, and click the “Layouts” button on the left panel (second from top) and then click Import layout button pictured below.
![](../../assets/images/foxglove_layout (1).png)

Import the preset layout from: ```mushr/mushr_utils/foxglove/foxglove_layout.json```.

### MuSHR panel extension
Navigate to the Extensions tab (bottom icon on the left panel) and install the MushrTeleop extension from the Marketplace.
![](../../assets/images/foxglove_extention.jpg)

### Connecting to Data With Foxglove Studio
Start the Docker container. In the same terminal (within the Docker container), start up the simulator with the command:
```
$ roslaunch mushr_sim teleop.launch
```
After starting up, the simulator should print out a line similar to ```Rosbridge WebSocket server started at ws://0.0.0.0:9090```

In Foxglove, click the top button in the sidebar, labeled Data source. Then select the Plus button in the left panel. This should open up an interface to connect to data. Click the Open Connection button. 
![](../../assets/images/import_data.png)

Select Rosbridge (ROS 1 & ROS 2) as shown below.
![](../../assets/images/new_connection.png)
Fill out the WebSocket URL with the url and port that the simulator output before.
Then, click Open in the bottom right corner.

---