---
noteId: "7756e8900f8711eea038e3eb8b9b08a3"
tags: []
layout: default
title: Control robot with a PS4 controller
parent: The race rebot
nav_order: 4
---

# Control robot with a PS4 controller
## 1. Connect the PS4 controller to the TX2, for the first time
[Build Instructions - MuSHR: The UW Open Racecar Project](https://mushr.io/hardware/build_instructions/#:~:text=Note%20the%20column,dialog.%20(Fig.%2015.7)) 

**i.** Press the “P” and “share” buttons of the PS4 controller at the same time, and the light will flash with high frequency, and the ps4 controller will on a pairing mode

**ii.** On TX2, go to the blue tooth setting.

{: .note }
If there already is a “wireless controller”, remove them first, because all the controllers use the same name.

**iii.** search for “Wireless Device”, you can choose the device type as input to specify the right devices.
![](../assets/images/wiless_control.png)

**vi.** When the controller is detected, click it to connect.
Once you connected your control, next time you only need to turn on the controller and it will be auto-connect to the TX2.

## 2. Contro the race robot with a PS4 controller
[Build Instructions - MuSHR: The UW Open Racecar Project](https://mushr.io/hardware/build_instructions/#:~:text=Once%20all%20of%20the%20robot%E2%80%99s%20nodes%20have%20been%20brought%20up%2C%20you%20can%20drive%20the%20car%20with%20the%20wireless%20controller.%20The%20LB%20button%20acts%20a%20deadman%E2%80%99s%20switch%20that%20you%20must%20hold%20down%20in%20order%20to%20make%20the%20car%20move.%20The%20left%20joystick%20controls%20the%20robot%E2%80%99s%20throttle%2C%20and%20the%20right%20joystick%20controls%20its%20steering).

{: .note }
Push L1 to use it
