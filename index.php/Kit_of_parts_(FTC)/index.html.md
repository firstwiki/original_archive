# Kit of parts (FTC)

## From FIRSTwiki

Jump to: navigation, search

[![ ](/media/thumb/1/10/FIRST_logo.gif/50px-
FIRST_logo.gif)](Image:FIRST_logo.gif " ") | **This article or section needs to be updated.**<br>
Parts of this article or section have been identified as no longer being up to date.<br>
Please update the article to reflect recent events, and remove this template when finished. | [![ ](/media/thumb/5/5f/600px-Nuvola_apps_important.svg.png
/50px-600px-Nuvola_apps_important.svg.png)](Image:600px-
Nuvola_apps_important.svg.png " ")<br>
---|---|---

[![The Vex Robotics Design System line of parts. Image source: VexLABS
\[1\]](/media/thumb/7/79/Vex-Robotics-Design-System.gif/280px-Vex-Robotics-
Design-System.gif)](Image:Vex-Robotics-Design-System.gif "The Vex
Robotics Design System line of parts. Image source: VexLABS \[1\]")

[![Enlarge](/skins/common/images/magnify-clip.png)](Image:Vex-
Robotics-Design-System.gif "Enlarge")

The Vex Robotics Design System line of parts. Image source: VexLABS [[1]](http://www.vexlabs.com "http://www.vexlabs.com")

Several weeks before the [2005 FIRST Championships](Championship_Event_%282005%29 "Championship Event
\(2005\)"), [RadioShack](/index.php?title=RadioShack&action=edit "RadioShack") (the official sponsor of Vex) unveiled the Vex kits at their stores. Dubbed Version 0.5, the main kit, which sells for $300 USD, contains everything to make a simple Vex robot. Additional parts, such as spare motors, servos, wheels, and gears were available in Version 0.5\. The entire line of parts (Version 1.0), including a programming module and advanced sensors, was released in August 2005.

In addition to standard Vex parts, [VexLabs](/index.php?title=VexLabs&action=edit "VexLabs") (a subcompany of [Innovation First, Inc.](Innovation_First%2C_Inc. "Innovation
First, Inc.")) is credited with developing new beta components for possible inclusion into the standard Vex kits. Some of these new mechanical pieces include new/longer 1x1 and 2x2 angle pieces, 1x2x1 and 1x5x1 C-Channel, Linear Bearings, and more. [[3]](http://www.vexlabs.com "http://www.vexlabs.com")

## Contents

- 1 Line of Parts
- 2 Vex Controller

  - 2.1 Inputs / Output Ports

    - 2.1.1 Analog / Digital Ports
    - 2.1.2 Interrupt Ports
    - 2.1.3 Motor Ports

- 3 VEX Motors and Servos

  - 3.1 Motors
  - 3.2 Servos

- 4 Sensors
- 5 Pneumatics
- 6 VexLabs Beta Parts

--------------------------------------------------------------------------------

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=1 "Edit
section: Line of Parts")]

### Line of Parts

- Starter Kit (v0.5)
- Extra Gears Kit (v0.5)
- Sprocket and Chain Set (v1.0)
- Vex Motor (v0.5)
- Vex Servo (v0.5)
- Extra Metal Components (v0.5)
- Extra Wheel Set (v0.5)
- Omni-Directional Wheel Kit (v1.0)
- Tank Tread Kit (v1.0)
- Additional R/C Transmitter/Reciever (v0.5)
- Additional R/C Radio Crystal Packs (v0.5)
- Vex Rechargeable Batteries (v0.5)
- Programming Module (v1.0)
- Limit Switches (v0.5)
- Bumper Switches (v0.5)
- Line-Following Sensor (v1.0)
- Light Sensor (v1.0)
- Ultra-Sonic Sensor (v1.0)

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=2 "Edit
section: Vex Controller")]

## Vex Controller

[![The Vex Micro-Controller. Image source: VexLABS \[2\]](/media/thumb/0/0f
/Vex-micro-controller-module.jpg/220px-Vex-micro-controller-
module.jpg)](Image:Vex-micro-controller-module.jpg "The Vex Micro-
Controller. Image source: VexLABS \[2\]")

[![Enlarge](/skins/common/images/magnify-clip.png)](Image:Vex-
micro-controller-module.jpg "Enlarge")

The Vex Micro-Controller. Image source: VexLABS [[2]](http://www.vexlabs.com "http://www.vexlabs.com")

The Vex controller uses two PIC18F8520 micro controllers, a Master and User which are uses to execute tasks. Vex robots can be driven by R/C or by an [autonomous mode](autonomous-mode). A stock autonomous mode is available, but users can modify and change their autonomous mode by using the Vex Programming Module and either [EasyC](/index.php?title=EasyC&action=edit "EasyC") or [MPLAB](MPLAB "MPLAB"). The Vex Controller runs off 7.2 volts, and is compatibly with both Vex rechargeable battery packs and standard 7.2V hobby batteries.

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=3 "Edit
section: Inputs / Output Ports")]

### Inputs / Output Ports

The Vex Controller has 16 [Analog](Analog "Analog")/[Digital](digital) [Input](input)/[Output](output) Ports, one RX and one TX port, 8 [Pulse-Width-Modulation](pwm) Motor Ports, and 8 [Interrupt](Interrupts "Interrupts") Ports. There are also two (RX1 and RX2) Radio Modem/Tether ports and one Serial Port on the side of the controller.

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=4 "Edit
section: Analog / Digital Ports")]

#### Analog / Digital Ports

In addition to the official VEX sensors, custom sensors (ex. [Potentiometers](Potentiometer "Potentiometer"), [Infrared Range Sensors](/index.php?title=Infrared_Range_Sensors&action=edit "Infrared Range
Sensors"), etc.) may be used with the Vex controller. Devices such as a [Spike Relay](spike-relay), a pneumatic [solenoid](Solenoid "Solenoid"), or a [LED](/index.php?title=LED&action=edit "LED") may be controlled via the Digital Outputs of the Vex Controller

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=5 "Edit
section: Interrupt Ports")]

#### Interrupt Ports

These ports are used to 'Interrupt' the main user program, in the case that a certain sensor has a much higher frequency than the main program loop. The Vex Ultrasonic and Optical Shaft Encoders both utilize Interrupt Ports.

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=6 "Edit
section: Motor Ports")]

#### Motor Ports

The eight Motor Ports on the Vex Controller use [Pulse-Width- Modulation](pwm) to control the Vex Motors and Servos. Standard hobby [Servos](servo) and the [Speed Controllers](speed-controller) used on full- size FRC robots may also be controlled via the Vex Motor ports.

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=7 "Edit
section: VEX Motors and Servos")]

## VEX Motors and Servos

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=8 "Edit
section: Motors")]

### Motors

The standard Vex motors are continuous-rotation, geared, Futaba servo-motors. They have a maximum speed of 100 RPM. There is no discernible difference in clockwise and counter-clockwise rotation speeds.

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=9 "Edit
section: Servos")]

### Servos

The Standard Vex servos are limited-rotation, geared, Futaba servo-motors. They have a maximum rotation of slightly under 180 degrees. The only discernable difference between a Vex Servo and a standard Futaba servo motor is merely cosmetic differences.

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=10 "Edit
section: Sensors")]

## Sensors

In the current line of Vex parts, there are six official Vex [sensors](sensor). These six sensors, include [limit switches](Limit_switch "Limit switch"), bumper switches, [light sensors](/index.php?title=Light_sensor&action=edit "Light sensor"), [line following](line-following) sensors, [ultrasonic range finders](/index.php?title=Ultrasonic_range_finder&action=edit "Ultrasonic range finder"), and optical [shaft encoders](encoder). The Vex limit and bumper switches report a <digital> [signal](/index.php?title=Signal&action=edit "Signal"), while the light sensor and line follower use a <analog> signal. The Ultrasonic and Optical Shaft Encoders both utilize Interrupt ports when being programmed. The Ultrasonic part also needs a digital output port to create the ping pulse.

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=11 "Edit
section: Pneumatics")]

## Pneumatics

Although not legal in the 2006 FIRST Vex Challenge, [VexLabs](/index.php?title=VexLabs&action=edit "VexLabs") sells [pneumatics](pneumatics) kits for the Vex Robotics System. These consist of a [accumulator](/index.php?title=Accumulator&action=edit "Accumulator"), [regulator](/index.php?title=Regulator&action=edit "Regulator"), [solenoids](Solenoid "Solenoid"), and single and double acting cylinders. The solenoids can be controlled via the [digital output](/index.php?title=Digital_output&action=edit "Digital output") ports on the Vex Controller. The maximum recommended pressure for the accumulator is 120 PSI. The cylinders have a bore diameter of 10 millimeters, and a bore stroke of 200 millimeters. (Source: VexLabs [[4]](http://www.vexlabs.com/vex-
robotics-pneumatic-parts.shtml "http://www.vexlabs.com/vex-robotics-pneumatic-
parts.shtml"))

The Vex pneumatics kits do not contain a onboard [compressor](Compressor "Compressor"), which means that the accumulator has to be recharged by an external source of compressed air (such as a bicycle pump or a FRC compressor). Regulated to the correct pressure, the accumulator can last for up to 45 cycles of the pneumatic cylinders. (If double acting cylinders or a higher pressure are used, the maximum number of cycles drops significantly).

[[edit](/index.php?title=Kit_of_parts_%28FTC%29&action=edit&section=12 "Edit
section: VexLabs Beta Parts")]

## VexLabs Beta Parts

To expand the line of available mechanical parts in the Vex kits, [VexLabs](/index.php?title=VexLabs&action=edit "VexLabs") (a subcompany of [Innovation First, Inc.](Innovation_First%2C_Inc. "Innovation
First, Inc.") began to produce alpha and beta stage prototype mechanical pieces for possible inclusion into the standard Vex Robotics System kits. These new pieces include:

- Linear Slide Pack
- 1x1 Left and Right Angle (With Slots)
- 1x1 Angle (Without Slots)
- 2x2 Angle
- 3x3 Angle
- 1x2x1 C-Channel
- 1x5x1 C-Channel
- 2x1 Chassis Rails
- 3x2 Chassis Rails
- New Chassis Kits
- New Threaded Beam Sizes
- Threaded Beam Couplers
- Longer 8/32 Screws
