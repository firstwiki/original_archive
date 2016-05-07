# Potentiometer

### From FIRSTwiki

Jump to: navigation, search

A **potentiometer**, also called a **pot**, is an [analog](/index.php/Analog
"Analog" ) [sensor](/index.php/Sensor "Sensor" ) that changes resistance in
proportion to the position of its shaft. Potentiometers can found in rotary or
linear varieties. In a rotary potentiometer, the shaft rotates and causes the
change in resistance. In a linear (or slide) potentiometer, the shaft moves in
a straight line. Potentiometers can also come in audio or linear tapers. The
audio taper means that the output varies logarithmically with the position of
the shaft, and is usefull for volume knobs in audio equipment. In linear taper
pots, the output varies linearly. The concept of tapers and shaft arrangments
are independent, a linear potentiometer can have a audio taper, and vice
versa.

In [FIRST Robotics](/index.php/FIRST "FIRST" ), when
[wiring](/index.php?title=Wiring&action=edit "Wiring" ) the pot, one end of
the potentiometer is connected to 5V and the other end to ground. The sense
line is connected to the analog [input](/index.php/Input "Input" ) on the
[Robot Controller](/index.php/Robot_Controller "Robot Controller" ). Thus, the
potentiometer acts as a voltage divider, where the values of the two resistors
can be varied.

Potentiometers are used, therefore, to determine where specific moving parts
are in their range of travel on the robot, or to provide analog input to the
[Operator Interface](/index.php/Operator_Interface "Operator Interface" ).

Note that when working with analog values on the [2004 Robot
Controller](/index.php/Robot_Controller_%282004%29 "Robot Controller \(2004\)"
), the function Get_Analog_Value must first be called. This is not necessary
when the pot is connected to the Operator Interface.

[[edit](/index.php?title=Potentiometer&action=edit&section=1 "Edit section:
See also" )]

##  See also

  * [Programming the Robot Controller](/index.php/Programming_the_Robot_Controller "Programming the Robot Controller" )
  * [Electronics and circuitry](/index.php/Electronics_and_circuitry "Electronics and circuitry" )
  * [Electronics rules](/index.php?title=Electronics_rules&action=edit "Electronics rules" )

[[edit](/index.php?title=Potentiometer&action=edit&section=2 "Edit section:
Resources" )]

##  Resources

  * [Documentation page](http://innovationfirst.com/FIRSTRobotics/documentation.htm "http://innovationfirst.com/FIRSTRobotics/documentation.htm" ) from [Innovation First, Inc.](/index.php/Innovation_First%2C_Inc. "Innovation First, Inc." )

