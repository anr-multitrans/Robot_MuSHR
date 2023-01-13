---
noteId: "01c34620934311ed80cf874835c8bf87"
tags: []
layout: default
title: Foxglove
parent: Noetic version of MuSHR
nav_order: 3
---

# Foxglove

![](../../assets/images/foxglove.jpg)

{: .note }
This tutorial is for MacOS or Linux users only.

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
