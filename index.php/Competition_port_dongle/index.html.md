# Competition port dongle

### From FIRSTwiki

Jump to: navigation, search

A **competition port dongle** is a device built by most teams for testing and
practicing with their robot. It connects to the [competition
port](Competition_port "Competition port" ) on the [Operator
Interface](Operator_Interface "Operator Interface" ).

[[edit](/index.php?title=Competition_port_dongle&action=edit&section=1 "Edit
section: What a dongle does" )]

## What a dongle does

A dongle can be built to do the following things:

  * Allow teams to [disable](Disabled "Disabled" ) the robot safely 
  * Allow teams to start [autonomous mode](Autonomous_mode "Autonomous mode" )
  * Enables access to channels 4, 13, 22, and 31 in addition to the normal channel 40 on the 900 mhz band 

[[edit](/index.php?title=Competition_port_dongle&action=edit&section=2 "Edit
section: Building a dongle" )]

## Building a dongle

To build a competition port dongle, you'll need the following things:

  * One DB15 solder cup connector and housing 
  * Two ON/OFF switches, which function according to taste 
  * A container to hold everything (optional--some teams fit everything on the connector housing) 
  * Wire 
  * Soldering equipment 
  * Basic tools. (A drill may be needed, depending on your container.) 

**WARNING:** _Be careful when soldering, as it can burn. Also be extra careful about short circuits, as they can permanently damage or destroy your Operator Interface._

The circuitry is fairly simple to [solder](Soldering "Soldering" ).
By grounding pin 6 to pin 8, the robot will be disabled. Grounding pin 5 to
pin 8 will start the robot's autonomous mode. Grounding pin 12 to pin 8 will
enable access to the channels mentioned above. (The channel access does not
require a switch.) Make sure to read the _Competition Port Pin-out Guide_ from
[Innovation First's documentation
page](http://innovationfirst.com/FIRSTRobotics/documentation.htm
"http://innovationfirst.com/FIRSTRobotics/documentation.htm" ).

Once the circuits are made, simply package the switches and wire in the
container or secure the switches to the connector housing.

[[edit](/index.php?title=Competition_port_dongle&action=edit&section=3 "Edit
section: Suggestions for customizing your dongle" )]

## Suggestions for customizing your dongle

Different teams build their dongles in different fashions to suit their
tastes. The main source of difference is in switches. Some teams use push-
button ON/OFF switches in order to quickly activate or deactivate a feature.
Others use momentary switches to act as a "dead man's switch," requiring a
person to hold down the button for the feature to remain engaged. (In this
case, the disable switch would have the robot enabled while depressed.)

One other change that can be used is to use a long wire between the controls
and the connector, to allow a person to be further away from the driver while
controlling. This is extremely useful when letting non-team members drive the
robot, or when the robot is being driven in a location without barriers.
Standard RJ11 (or telephone) wire works well, is very inexpensive (roughly ten
to fifteen cents per foot), and is available in many places.

