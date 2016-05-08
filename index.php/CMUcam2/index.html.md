# CMUcam2

## From FIRSTwiki

Jump to: navigation, search

[![](/media/thumb/1/10/FIRST_logo.gif/50px-
FIRST_logo.gif)](Image:FIRST_logo.gif)

| _This article is currently a stub (a short article without much content)._

[Please add more content](http://www.firstwiki.net/index.php?title=CMUcam2&action=edit "http://www.firstwiki.net/index.php?title=CMUcam2&action=edit") to make a significant article. _See more [stubs](Special:Shortpages "Special:Shortpages")._

---|---

The [Control System](control-system)

**[Logic of a Control System](Logic_of_a_control_system "Logic of a control system")**

- [Closed loop](closed-loop)

  - [PID controller](PID_controller "PID controller")

- [Open loop](open-loop)

**[Parts of a Control System](Parts_of_a_control_system "Parts of a control system")**

- [Computer](Computer "Computer")

  - [Robot Controller](robot-controller)

    - [2010 RC](Robot_Controller_%282010%29 "Robot Controller \(2010\)")
    - [2009 RC](Robot_Controller_%282009%29 "Robot Controller \(2009\)")
    - [2006 RC](Robot_Controller_%282006%29 "Robot Controller \(2006\)")
    - [2004 RC](Robot_Controller_%282004%29 "Robot Controller \(2004\)")
    - [2003 RC](Robot_Controller_%282003%29 "Robot Controller \(2003\)")
    - [2000 RC](Robot_Controller_%282000%29 "Robot Controller \(2000\)")
    - [1996 RC](/index.php?title=Robot_Controller_%281996%29&action=edit "Robot Controller \(1996\)")
    - [1993 RC](/index.php?title=Robot_Controller_%281993%29&action=edit "Robot Controller \(1993\)")

  - [Robovation](robovation)

- [Input](input)

  - [Operator Interface](operator-interface)
  - [Joystick](joystick)

- [Output](output)

  - [Victor 884](victor-884)
  - [Spike](spike-relay)

- [Sensors](sensor)

  - [Encoder](encoder)
  - [Accelerometer](accelerometer)
  - [Light sensor](/index.php?title=Light_sensor&action=edit "Light sensor")
  - [IR sensor](tsop34840)
  - [Gyro](gyro)
  - **CMUcam2**

--------------------------------------------------------------------------------

The **CMUcam2** is a vision system given to teams in the [kit of parts](kit-of-parts), starting in [2005](triple-play).

The camera communicates with the [full robot controller](Full_robot_controller "Full robot controller") via the [TTL](/index.php?title=TTL&action=edit "TTL") port, with an TTL/RS-232 converter and buffer provided by [Innovation First](Innovation_First%2C_Inc. "Innovation First, Inc."). The camera is commonly mounted to two servos in order to locate objects.

## Contents

- 1 Purpose
- 2 Camera Mount

  - 2.1 Assembly

- 3 Problems

  - 3.1 Backup Battery
  - 3.2 Wire Connections
  - 3.3 Status Lights

--------------------------------------------------------------------------------

## Purpose

The camera is used to track a colored object.

In [2005](triple-play), colored pieces of plastic were used. These did not work too well, as the camera was very sensitive to their angle, and the amount of light.

In [2006](aim-high), the camera has a green target that is lit by six lights. This ensures that the lighting conditions do not effect the ability of the camera too much.

## Camera Mount

The camera came with a pan and tilt mount powered by servos that could be used to allow the robot to "look around". The mount also made it easy for teams to mount the camera on their robot.

### Assembly

When assembling the camera mount, it should be noted that the lens goes on the bottom of the mount. When assembled correctly, it is very close to the center of the pan and tilt servos.

## Problems

Here are a few things to try if the camera is not operating properly.

### Backup Battery

Is the backup battery charged? The camera and it's servos are powered off of the blue backup battery, not the main battery. This should be the first thing to check if the camera is not operating properly.

### Wire Connections

Were any wires pulled loose? The camera itself has two PWM cables going into it. One powers the camera, and is plugged into any free PWM port on the [robot controller](robot-controller). The other is plugged into the small TTL/RS-232 converter, which is then plugged into the [robot controller](robot-controller).

### Status Lights

Are any lights on? The camera itself has three lights. When the camer is in use, two are lit:

- A green light in the bottom right of the camera board indicates that the camera itself is recieving power.
- A red light in the same place indicates that the camera is locked onto the color it is tracking.
