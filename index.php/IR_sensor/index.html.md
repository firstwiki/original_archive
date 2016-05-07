# IR sensor

### From FIRSTwiki

Jump to: navigation, search

The [Control System](/index.php/Control_system "Control system" )

**[Logic of a Control System](/index.php/Logic_of_a_control_system "Logic of a control system" )**

  * [Closed loop](/index.php/Closed_loop "Closed loop" )
    * [PID controller](/index.php/PID_controller "PID controller" )
  * [Open loop](/index.php/Open_loop "Open loop" )

**[Parts of a Control System](/index.php/Parts_of_a_control_system "Parts of a control system" )**

  * [Computer](/index.php/Computer "Computer" )
    * [Robot Controller](/index.php/Robot_Controller "Robot Controller" )
      * [2010 RC](/index.php/Robot_Controller_%282010%29 "Robot Controller \(2010\)" )
      * [2009 RC](/index.php/Robot_Controller_%282009%29 "Robot Controller \(2009\)" )
      * [2006 RC](/index.php/Robot_Controller_%282006%29 "Robot Controller \(2006\)" )
      * [2004 RC](/index.php/Robot_Controller_%282004%29 "Robot Controller \(2004\)" )
      * [2003 RC](/index.php/Robot_Controller_%282003%29 "Robot Controller \(2003\)" )
      * [2000 RC](/index.php/Robot_Controller_%282000%29 "Robot Controller \(2000\)" )
      * [1996 RC](/index.php?title=Robot_Controller_%281996%29&action=edit "Robot Controller \(1996\)" )
      * [1993 RC](/index.php?title=Robot_Controller_%281993%29&action=edit "Robot Controller \(1993\)" )
    * [Robovation](/index.php/Robovation "Robovation" )
  * [Input](/index.php/Input "Input" )
    * [Operator Interface](/index.php/Operator_Interface "Operator Interface" )
    * [Joystick](/index.php/Joystick "Joystick" )
  * [Output](/index.php/Output "Output" )
    * [Victor 884](/index.php/Victor_884 "Victor 884" )
    * [Spike](/index.php/Spike "Spike" )
  * [Sensors](/index.php/Sensor "Sensor" )
    * [Encoder](/index.php/Encoder "Encoder" )
    * [Accelerometer](/index.php/Accelerometer "Accelerometer" )
    * [Light sensor](/index.php?title=Light_sensor&action=edit "Light sensor" )
    * **IR sensor**
    * [Gyro](/index.php/Gyro "Gyro" )
    * [CMUcam2](/index.php/CMUcam2 "CMUcam2" )  
---  
  
The **Vishay TSOP34840 IR sensor**, or simply **IR sensor**, is used to detect
infra-red signals. In [FIRST Robotics](/index.php/FIRST "FIRST" ), this sensor
is primarily used during the [autonomous mode](/index.php/Autonomous_mode
"Autonomous mode" ). It was introduced in 2004, for the game [FIRST Frenzy:
Raising the Bar](/index.php/FIRST_Frenzy:_Raising_the_Bar "FIRST Frenzy:
Raising the Bar" ), and during [kickoff](/index.php/Kickoff "Kickoff" ) [Dean
Kamen](/index.php/Dean_Kamen "Dean Kamen" ) and [Woodie
Flowers](/index.php/Woodie_Flowers "Woodie Flowers" ) strongly hinted at its
continued importance. The most common setup works by connecting the sensors to
[interrupt](/index.php/Interrupts "Interrupts" ) pins, and detecting a certain
frequency and pulse-width that the [IR beacons](/index.php/IR_beacon "IR
beacon" ) were known to emit.

[[edit](/index.php?title=IR_sensor&action=edit&section=1 "Edit section: Use in
2004" )]

## Use in 2004

The 2004 game [FIRST Frenzy](/index.php/FIRST_Frenzy:_Raising_the_Bar "FIRST
Frenzy: Raising the Bar" ) saw the first use of the IR sensor. During the
autonomous mode, there was a ball that had to be knocked over. The robots
could not simply stick an apendage out and follow the wall, because bars
prevented this. [Dead reckoning](/index.php/Dead_reckoning "Dead reckoning" )
and [line following](/index.php/Line_following "Line following" ) were still
alternatives, -- but the new method available was IR tracking. On each side of
the field above the ball, IR beacons emitted a specified signal, such that
they could be differentiated. Not many teams decided to use the sensors,
choosing instead more simple methods, and those that did were not always
successful. See [Autonomous techniques
(2004)](/index.php?title=Autonomous_techniques_%282004%29&action=edit
"Autonomous techniques \(2004\)" ) for more information in this regard.

[[edit](/index.php?title=IR_sensor&action=edit&section=2 "Edit section: Future
use \(speculation\)" )]

## Future use (speculation)

At kickoff for the 2004 season, it was strongly hinted that the IR sensors
would be back next year, and that it might be necessary to use them. Keep in
mind that the following is pure speculation, something the [FIRST
community](/index.php/FIRST_community "FIRST community" ) seems to love, --
even given their track record. However, possible ideas for why this might be
the case include this. The robot will have to track a moving target, and since
it is not static, [dead reckoning](/index.php/Dead_reckoning "Dead reckoning"
) simply won't work. For more on this discussion, see these
[ChiefDelphi](/index.php/ChiefDelphi "ChiefDelphi" ) threads
([[1]](http://www.chiefdelphi.com/forums/showthread.php?t=28435
"http://www.chiefdelphi.com/forums/showthread.php?t=28435" ),
[[2]](http://www.chiefdelphi.com/forums/showthread.php?t=26774
"http://www.chiefdelphi.com/forums/showthread.php?t=26774" )).

[[edit](/index.php?title=IR_sensor&action=edit&section=3 "Edit section:
Resources" )]

## Resources

  * [Kevin Watson's](/index.php/Kevin_Watson "Kevin Watson" ) excellent [beacon tracking code](http://kevin.org/frc/ "http://kevin.org/frc/" ) and more. A copy of the data sheet for the sensor is also available at this site. 

