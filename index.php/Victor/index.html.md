# Victor 884

## From FIRSTwiki

(Redirected from [Victor](/index.php?title=Victor&redirect=no "Victor"))

Jump to: navigation, search

## Victor 884

[![](/media/thumb/a/a2/Victor-884.gif/180px-
Victor-884.gif)](Image:Victor-884.gif)

[![Enlarge](/skins/common/images/magnify-
clip.png)](Image:Victor-884.gif "Enlarge")

Manufacturer: | [Innovation FIRST](Innovation_FIRST "Innovation
FIRST")<br>
Product Page: | [Victor Speed Controller](http://www.vexrobotics.com/products/vexpro/victor-speed-
controller.html "http://www.vexrobotics.com/products/vexpro/victor-speed-
controller.html")<br>
Data Sheet: | [884 Users' Manual](http://content.vexrobotics.com/docs/ifi-v884
-users-manual-9-25-06.pdf "http://content.vexrobotics.com/docs/ifi-v884-users-
manual-9-25-06.pdf")<br>
The [Control System](Control_system "Control system")

**[Logic of a Control System](Logic_of_a_control_system "Logic of a control system")**

- [Closed loop](Closed_loop "Closed loop")

  - [PID controller](PID_controller "PID controller")

- [Open loop](Open_loop "Open loop")

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

- [Input](Input "Input")

  - [Operator Interface](operator-interface)
  - [Joystick](joystick)

- [Output](Output "Output")

  - **Victor 884**
  - [Spike](spike-relay)
  - [Jaguar](Jaguar "Jaguar")

- [Sensors](sensor)

  - [Encoder](Encoder "Encoder")
  - [Accelerometer](Accelerometer "Accelerometer")
  - [Light sensor](/index.php?title=Light_sensor&action=edit "Light sensor")
  - [IR sensor](IR_sensor "IR sensor")
  - [Gyro](gyro)
  - [CMUcam2](CMUcam2 "CMUcam2")

--------------------------------------------------------------------------------

The **Victor 884** is a [speed controller](Speed_Controller "Speed
Controller") developed by [Innovation FIRST](Innovation_FIRST "Innovation FIRST") as an improved version of the [Victor 883](victor-883). The Victor 884 works by reading a [PWM](pwm) signal from a [robot controller](robot-controller), and adjusting the effective voltage supplied to the motors accordingly. The Victor 884 was the only FIRST legal speed controller allowed in the [2005](triple-play) [control system](Control_system "Control system").

## Contents

- 1 Technical

  - 1.1 Use
  - 1.2 Coast/Brake

- 2 Connections

  - 2.1 Data
  - 2.2 Input

- 3 Programming

--------------------------------------------------------------------------------

## Technical

[![The Victor 884 Speed Controller. Image source: Innovation
FIRST](/media/thumb/a/a2/Victor-884.gif/180px-
Victor-884.gif)](Image:Victor-884.gif "The Victor 884 Speed
Controller. Image source: Innovation FIRST")

[![Enlarge](/skins/common/images/magnify-
clip.png)](Image:Victor-884.gif "Enlarge")

The Victor 884 Speed Controller. Image source: [Innovation FIRST](Innovation_FIRST "Innovation FIRST")

The Victor 884 is part of the FIRST [control system](Control_system "Control system"). The Victor 884 works by recieving a [PWM signal](PWM_signal "PWM signal") input from a [robot controller](robot-controller), which may include the (full) [Robot Controller](Robot_Controller "Robot
Controller"), the [Robovation](robovation) controller or a [Vex](Vex "Vex") Controller. Depending on the range of the [PWM](pwm) signal - with 0 being full reverse, 127 being neutral, and 254 being full forward - the Victor 884 adjusts the output of the motor accordingly. This achieves a variable speed control for such applications as [drivetrains](Drive_trains "Drive trains"), arms, or elevators.

The operating voltage of the Victor 884 ranges from 6V to 15V DC, with a maximum operating current of 40 amps. The variable output from the Victor 884 ranges from 3% to 100% of full throttle. A cooling fan operated by the input voltage of the speed controller insures that the Victor 884 is continously cooled.

### Use

Although some motors may be run on a [Spike](spike-relay) if desired, the [CIM motors](CIM_motor "CIM motor") must use a Victor 884 speed controller. The Victor 884 Speed Controllers may be wired into either a 30 Amp or 40 Amp [fuse](/index.php?title=Fuse&action=edit "Fuse") on the [breaker panel](Breaker_panel "Breaker panel") depending on the motor being used. Each additional motor on a FIRST Competition Robot needs to have a Victor 884 or [Spike relay](Spike_relay "Spike relay").

### Coast/Brake

A small jumper on the Victor 884 determines whether the Victor will 'coast' or 'brake' when it stops recieving signal. In 'coast' mode, momentum of the spinning motor will enable the motor to coast to a stop when it stops recieving signal. In 'brake' mode, the Victor will short the output terminals together, providing a resistance to the momentum of the spinning motor. As such, the motor will come to a stop much more quickly.

Typically, a robot will use 'coast' mode on most drive motors, as abrupt stops can cause tipping issues. Turrets, arms, and other manipulators should usually use 'brake' mode, both to help hold a load at its desired position and to aid in controllability.

## Connections

### Data

A 3-pin [PWM cable](PWM_cable "PWM cable") connects the Victor 884 to the [robot controller](robot-controller). On the Robot Controller, the PWM cable destined for the Victor 884 speed controller should be connected to the "[PWM output](/index.php?title=PWM_output&action=edit "PWM output")" set of ports. A [relay extension cable](/index.php?title=Relay_extension_cable&action=edit "Relay extension cable") or a [Y-cable](/index.php?title=Y-cable&action=edit "Y-cable") may be used if the Victor is mounted far away from the Controller or if one wants a single PWM output port on the Controller to control multiple Victors.

### Input

The two [input](Input "Input") terminals on the Victor supply the power needed to run the speed controller, the cooling fan, and the motor output. The cooling fan on the Victor 884 should be wired into the two input terminals. This insures that the speed controller stays cool whenever the Victor is on. If wired incorrectly to the output terminals, the cooling fan will only work when the output motor is being driven, which will lead to over heating and the possible release of [magic smoke](Magic_smoke "Magic smoke").

The two input wires must be correctly wired to match their polarity. If the polarity of the input wires is switched, the speed controller may cease to function. Sparks, arcing, fire, burning smells, or [magic smoke](Magic_smoke "Magic smoke") may indicate that a Victor 884 was wired incorrectly, and hence has also been destroyed.

## Programming

The [PWM outputs](/index.php?title=PWM_outputs&action=edit "PWM outputs") on the [Robot Controller](robot-controller) can be set across the normal hobby servo range, 1 to 2 ms. The 8-bit PWM channels used on the PIC microprocessor of the Robot Controller (and Vex controller) has a resolution of 256 values, which fit in an `unsigned char`. Zero commands full reverse, 127 commands stop, and 254 commands full forwards. The command 255 should be avoided on older RCs because it acts as a special signal command when transmitted between the Robot Controller and OI. Newer versions of the RC seem to have no issue with a 255 command. However, for code portability, 254 should be the maximum value used (besides, using 254 results in symmetric forward and reverse resolutions).

Note that a neutral PWM command to a factory calibrated Victor consists of a pulse of about 1.5 ms duration. As such, when no PWM input is applied, the Victor will detect this and flash it's LEDs yellow.
