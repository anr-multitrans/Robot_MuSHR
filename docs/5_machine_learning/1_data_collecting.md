---
noteId: "5b5734200f8611eea038e3eb8b9b08a3"
tags: []
layout: default
title: Data Collecting
parent: Machine Learning
nav_order: 1
---

# Data Collecting
## 1. [Connect to PS4 controller](https://docs.google.com/document/d/1G0I589q59IySPdlj8d79lRL1SR4P4d3J7_3MFj95dLM/edit#heading=h.5cx2hg4drf6m)

## 2. Check all the sensors needed are working
```
$ rostopic list
```

Topics we may need:

```
/car/[camera_name]/color/image_raw: RBG image from camera_name
/car/[camera_name]/color/image_rect_raw: RBG image from camera_name with frequency less than default as image raw so that the latency is less. 
/car/[camera_name]/depth/image_raw: Depth image from camera_name
/car/[camera_name]/depth/image_rect_raw: Depth image from camera_name with frequency we defined.
/car/scan/: data from lidar
```

## 3. Connecting data by Rosbag
[rosbag/Commandline - ROS Wiki](http://wiki.ros.org/rosbag/Commandline)

Run the below commands:
- If you want to choose the name of the files (“bag_name”) yourself you can do this instead:
```
$ rosbag record -O path/[bag_name].bag [topic_name_1] [topic_name_2] …
```

Ex.
```
$ rosbag record -O /home/…./test_data.bag /car/[camera_name]/depth/image_raw /car/[camera_name]/color/image_raw
```

The bag file is normally big a few G. Suggest saving the bag in an SD card with more space.  Be careful, the car doesn’t have a lot of memory and it can crash.

- If you only do 
```
$ rosbag record [topic]
```
it will gives a bag_name automatically (date + hour)

{: .note}
We can redo the same command to obtain more topics but we have to use the new ‘bag_name’, otherwise it will cover the old one

{: .warning}
We strongly recommend that you record the bag file on SD and try to transfer it to your own computer after that.

## 4. [Contro the race robot with a PS4 controller](https://anr-multitrans.github.io/Robot_MuSHR/docs/3_the_race_rebot/4_control_robot_w_a_ps4_controller/)



