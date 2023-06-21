---
noteId: "837be2f0104b11eea038e3eb8b9b08a3"
tags: []
layout: default
title: Applying deep learning on MuSHR
parent: MuSHR
nav_order: 4
---

# Applying deep learning on MuSHR
This tutorial is all about knowing how you can accomplish the task of deep learning on mushr.

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

---

## Data connection (manualy)
- The race car is powered on.

- Connect PS4 joystick. Refer to the [Connect the bluetooth controller](https://anr-multitrans.github.io/Robot_MuSHR/docs/noetic/noetic_robot_software_setup/#connect-the-bluetooth-controller).

- Launch teleop.launch.
```$ roslaunch mushr_base teleop.launch```
Make sure the sensor you need is active. And check the topic of relevant data.

{: .highlight }
Here are some key topics

**Intel® RealSense™ Tracking Camera T265**

```/car/camera/accel/sample```: IMU accelerate data

```/car/camera/fisheye1/image_raw```: Image data from one of the fisheye cameras

```/car/camera/fisheye2/image_raw```: Image data from the other one of the fisheye cameras

```/car/camera/gyro/sample```: IMU ayro data

```/car/camera/odom/sample```: IMU odom data


**Intel® RealSense™ Depth Camera D435i**

```/car/cameraD435i/color/image_raw```: Image data


**LiDAR**

```/car/scan```: LiDAR point cloud data


**VESC&Mux**

```/car/vesc/commands/motor/speed```: Motor speed

```/car/vesc/commands/servo/position```: Rotation angle of the servo

```/car/mux/ackermann_cmd_mux/output```: Output of speed and angle information
```yaml
header:  
  seq: 34296 
  stamp:  
    secs: 0 
    nsecs: 0 
  frame_id: '' 
drive:  
  steering_angle: -0.32584002614 #Steering angle, interchangeable with Servo position
  steering_angle_velocity: 0.0 
  speed: 0.0 # Speed, interchangeable with Motor speed
  acceleration: 0.0 
  jerk: 0.0 

```

- Select the topics related to the data to be collected and run the bag record:

```rosbag record [topic1] [topic2] [topic3]```

- Now, use ps4 to steer your car around the track to collect data.

{: .warning }
The image and point cloud data is large, so pay attention to the memory capacity or you will have lag and other problems.

- When you think you're almost done collecting data, in the window running rosbag record exit with a Ctrl-C. Now examine the contents of the directory where the terminal is running. You should see a file with a name that begins with the year, data, and time and the suffix .bag.

{: .note }
we can examine it and play it back using the commands ```rosbag info <your bagfile>``` and ```rosbag play <your bagfile>```.
