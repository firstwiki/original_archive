# IR sensor

### From FIRSTwiki

Jump to: navigation, search

The [Control System](Control_system "Control system" )

**[Logic of a Control System](Logic_of_a_control_system "Logic of a control system" )**

  * [Closed loop](Closed_loop "Closed loop" )
    * [PID controller](PID_controller "PID controller" )
  * [Open loop](Open_loop "Open loop" )

**[Parts of a Control System](Parts_of_a_control_system "Parts of a control system" )**

  * [Computer](Computer "Computer" )
    * [Robot Controller](robot-controller)
      * [2010 RC](Robot_Controller_%282010%29 "Robot Controller \(2010\)" )
      * [2009 RC](Robot_Controller_%282009%29 "Robot Controller \(2009\)" )
      * [2006 RC](Robot_Controller_%282006%29 "Robot Controller \(2006\)" )
      * [2004 RC](Robot_Controller_%282004%29 "Robot Controller \(2004\)" )
      * [2003 RC](Robot_Controller_%282003%29 "Robot Controller \(2003\)" )
      * [2000 RC](Robot_Controller_%282000%29 "Robot Controller \(2000\)" )
      * [1996 RC](/index.php?title=Robot_Controller_%281996%29&action=edit "Robot Controller \(1996\)" )
      * [1993 RC](/index.php?title=Robot_Controller_%281993%29&action=edit "Robot Controller \(1993\)" )
    * [Robovation](robovation)
  * [Input](Input "Input" )
    * [Operator Interface](operator-interface)
    * [Joystick](joystick)
  * [Output](Output "Output" )
    * [Victor 884](victor-884)
    * [Spike](spike-relay)
  * [Sensors](sensor)
    * [Encoder](Encoder "Encoder" )
    * [Accelerometer](Accelerometer "Accelerometer" )
    * [Light sensor](/index.php?title=Light_sensor&action=edit "Light sensor" )
    * **IR sensor**
    * [Gyro](gyro)
    * [CMUcam2](CMUcam2 "CMUcam2" )  
---  
  
The **Vishay TSOP34840 IR sensor**, or simply **IR sensor**, is used to detect
infra-red signals. In [FIRST Robotics](first), this sensor
is primarily used during the [autonomous mode](Autonomous_mode
"Autonomous mode" ). It was introduced in 2004, for the game [FIRST Frenzy:
Raising the Bar](FIRST_Frenzy:_Raising_the_Bar "FIRST Frenzy:
Raising the Bar" ), and during [kickoff](Kickoff "Kickoff" ) [Dean
Kamen](Dean_Kamen "Dean Kamen" ) and [Woodie
Flowers](Woodie_Flowers "Woodie Flowers" ) strongly hinted at its
continued importance. The most common setup works by connecting the sensors to
[interrupt](Interrupts "Interrupts" ) pins, and detecting a certain
frequency and pulse-width that the [IR beacons](IR_beacon "IR
beacon" ) were known to emit.


## Use in 2004

The 2004 game [FIRST Frenzy](FIRST_Frenzy:_Raising_the_Bar "FIRST
Frenzy: Raising the Bar" ) saw the first use of the IR sensor. During the
autonomous mode, there was a ball that had to be knocked over. The robots
could not simply stick an apendage out and follow the wall, because bars
prevented this. [Dead reckoning](Dead_reckoning "Dead reckoning" )
and [line following](Line_following "Line following" ) were still
alternatives, -- but the new method available was IR tracking. On each side of
the field above the ball, IR beacons emitted a specified signal, such that
they could be differentiated. Not many teams decided to use the sensors,
choosing instead more simple methods, and those that did were not always
successful. See [Autonomous techniques
(2004)](/index.php?title=Autonomous_techniques_%282004%29&action=edit
"Autonomous techniques \(2004\)" ) for more information in this regard.


## Future use (speculation)

At kickoff for the 2004 season, it was strongly hinted that the IR sensors
would be back next year, and that it might be necessary to use them. Keep in
mind that the following is pure speculation, something the [FIRST
community](FIRST_community "FIRST community" ) seems to love, --
even given their track record. However, possible ideas for why this might be
the case include this. The robot will have to track a moving target, and since
it is not static, [dead reckoning](Dead_reckoning "Dead reckoning"
) simply won't work. For more on this discussion, see these
[ChiefDelphi](ChiefDelphi "ChiefDelphi" ) threads
([[1]](http://www.chiefdelphi.com/forums/showthread.php?t=28435
"http://www.chiefdelphi.com/forums/showthread.php?t=28435" ),
[[2]](http://www.chiefdelphi.com/forums/showthread.php?t=26774
"http://www.chiefdelphi.com/forums/showthread.php?t=26774" )).


## Resources

  * [Kevin Watson's](Kevin_Watson "Kevin Watson" ) excellent [beacon tracking code](http://kevin.org/frc/ "http://kevin.org/frc/" ) and more. A copy of the data sheet for the sensor is also available at this site. 

