---
noteId: "11efda300f8611eea038e3eb8b9b08a3"
tags: []
layout: default
title: Install ROS1
parent: MuSHR
nav_order: 2
---

# Install ROS1
We are using the latest version of ROS1 - Noetic.

## For Ubuntu
Follow the official tutorial: [noetic/Installation/Ubuntu - ROS Wiki](http://wiki.ros.org/noetic/Installation/Ubuntu)

{: .note }
The ROS 1 - Noetic only supports ubuntu 20. [REP 3 -- Target Platforms (ROS.org)](https://www.ros.org/reps/rep-0003.html#noetic-ninjemys-may-2020-may-2025) 

For Windows users who are using Ubuntu VM, don’t forget to choose the right version of Ubuntu (Ubuntu 20) in the settings:
![](../assets/images/windows_ubuntu_vm.png)

## For Windows Users
Follow the official tutorial: [noetic/Installation/Windows - ROS Wiki](http://wiki.ros.org/noetic/Installation/Windows). 

-> for Visual Studio: download Visual Studio 2019 (Community is enough) at [Downloads - Visual Studio Subscriptions Portal](https://my.visualstudio.com/Downloads?q=Visual%20Studio%202019).

Note: Choose a ROS python environment on Visual Studio to be able to execute the files, and you have to re-install the package you need (scipy, torch, torchvision, torchaudio) on the Visual Studio terminal.

You have also a video tutorial about how to install ROS1 on Windows 11 : [How to Install ROS On Windows Natively](https://www.youtube.com/watch?v=mO_ilabG63I&ab_channel=SvenzvaRobotics).
