---
noteId: "a7634d508d2611ed8656897383d7b310"
tags: []
layout: default
title: Flashing Jetson TX2
parent: The race rebot
nav_order: 2
---

# [](#header-1)Jetson TX2 Driver Installation
## 1. Flash TX2 with your laptop
First, download the user guidebook from [TX2 user guide][def3], and go to the "**how to install jetpack**" part and follow the instructions.

{: .note }
Supported host operating systems are: Ubuntu Linux x64 Version 18.04 or 16.04

TX2 connecting system layout
![](/home/li/GitHub/anr-multitrans/Robot_MuSHR/assets/images/jetson_tx2_scan-2.jpg)

<!-- TODO: (Rem1: In the second part, use only the USB Micro-B to USB A to connect the car and the computer, and the AC adapter)
(Rem2: Which are the Power and Force Recovery buttons ? pictures ?) -->

You will be asked to make an account before downloading NVIDIA SDK Manage.

Install Jetson Software with SDK Manager with this [link][def2] 
```
Username: robot
Password: prl_robot
```

<!-- TODO: Do we have to do step 4 ? -->

## 2. Connect TX2
Once done the step 1, connect TX2 with the screen, the mouse, and the keyboard. Now you can do anything such as:

**Update ubuntu software**
```
$ sudo apt-get update 
$ sudo apt-get upgrade
```
A window will pop up and there will be a question about configuring docker.io : “Automatically restart Docker deamon” ? -> the answer is YES 
![][def]


[def]: ../../assets/images/tx2_flashing_docker.jpg
[def2]: https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html
[def3]: https://developer.nvidia.com/embedded/downloads#?search=developer%20kit%20user%20guide&tx=$product,jetson_tx2

