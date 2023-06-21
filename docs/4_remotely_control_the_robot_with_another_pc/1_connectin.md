---
noteId: "17d0e8c00f8811eea038e3eb8b9b08a3"
tags: []
layout: default
title: Connecting
parent: Remotely control the robot with another PC
nav_order: 1
---

# Connecting
## 1. Check the IP address on the robot
```
$ ifconfig
```

{: .warning}
Trying to connect your robot to a wifi with a static IP address, so that you don’t have to connect the screen, mouse, and keyboard to the TX2 to check the IP address every time you boot the robot, and it may changes often which is very inconvenient.

## 2. On other workstations
On other workstations, connect to the robot and the container.

{: .note}
For this to work your computer needs to be connected to the same wifi as the car.

There are two ways to connect:

**With the terminal:**

1. ```$ ssh [robot_name]@[IP_address]```
2. In the same window, run ```$mushr_noetic``` Or ```$ docker start [container_ID]```

If you want to open multiple terminals, you also have two ways:
- you can use TMUX
- Or open a new terminal and do steps i and ii again.

**with the VS code:**

1. **open VS code, attach to the remote with SSH**:
Take the remote extension on Visual studio code, chose the remote explorer as remote, and check the ssh list if there is no IP address you want, move your Cursor on the ‘SSH’ and click “+”, print ssh robot@[IP address] and enter until it finished. Flash the ssh list and you will see the IP address you just added. Move the cursor to the IP address you want and attach to it the current window or a new window **(suggest)**.
![](../assets/images/vs1.png)
![](../assets/images/vs2.png)

2. **In the VS window connected to the robot remotely**:
Take the remote extension on Visual Studio code and switch the remote explorer to the **Dev container**, if there is no container name you want or you want to start a new container, open a terminal and run $ mushr_noetic. Then back to the container list and chose the one you want to attach and attached it with a new window (we suggest keeping the vs code window which is attached to the robot to be able to shut down the robot at the end).
![](../assets/images/vs3.png)

{: .note}
If there is an error about connection, most probably you connect to a wifi with a dynamic IP address and the ID has changed. You have to find the new one with ```$ ifconfig``` on the robot again, then redo all the connect steps above to connect it.
