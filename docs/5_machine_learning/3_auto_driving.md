---
noteId: "7a5307000f8611eea038e3eb8b9b08a3"
tags: []
layout: default
title: Auto-driving
parent: Machine Learning
nav_order: 3
---

# Auto-driving
1. Modify the Python file with your model
_[path]/catkin_ws/src/imredd_pkg/src/FollowRoad_node.py_

2. compile the Python files you need to run if you just add it to catkin_ws

3. Launch road following node:
```
$ roslaunch mushr_base teleop.launch
$ roslaunch imredd_pkg follow_road.launch
```
Stop it with ```control+c```
	
{: .note}
only when your controller is disconnected, the command messages published by follow_road will work.
