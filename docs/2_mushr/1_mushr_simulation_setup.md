---
noteId: "ba8ab0608d1e11ed8656897383d7b310"
tags: []
layout: default
title: MuSHR simulation setup
parent: MuSHR
nav_order: 1
---

# MuSHR simulation setup
Learn how to simulate the MuSHR Car.

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
- For running the MuSHR racecar, when ask “Are you installing on robot and need all the sensor drivers? (y/n)” respond “y” so that the sensor drivers are installed.

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
```$ mushr_noetic``` will generate a new container, and if you want to use the same container, you can run ```$ docker exec -it [CONTAINER_ID] bash```. View Container ID run ```$ docker ps```.

In the same terminal (within the Docker container), build the MuSHR software stack. (First run or when there is an update.)
```$ source .bashrc && cd catkin_ws && catkin build```

---