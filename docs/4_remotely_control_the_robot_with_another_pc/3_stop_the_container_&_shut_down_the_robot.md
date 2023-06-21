---
noteId: "38d954800f8811eea038e3eb8b9b08a3"
tags: []
layout: default
title: Stop the container and shut down the robot
parent: Remotely control the robot with another PC
nav_order: 3
---

# Stop the container and shut down the robot
## 1. first stop the container:
- In the bash of the container, run
```
$exit
```
- Or in the bash of the robot, run 
```
$docker stop [container_ID]
```
You will lose the connection in a few seconds.
## 2. Then shut down the TX2(robot), In the bash of the robot:
```
$ sudo shutdown -P now
```
You will lose the connection in a few seconds too.
