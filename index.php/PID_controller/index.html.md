As we organize getting the site's software updated, feel free to submit any
suggestions you have on how we can improve the wiki
_**_[here!](/index.php/User:Hallry/Suggestions "User:Hallry/Suggestions"
)_**_. Thanks for all of your support!

If you are an administrator, it would be greatly appreciated if you could help
patrol [Recent Changes](/index.php/Special:Recentchanges
"Special:Recentchanges" ) to combat spam.

# PID controller

### From FIRSTwiki

Jump to: navigation, search

The [Control System](/index.php/Control_system "Control system" )

**[Logic of a Control System](/index.php/Logic_of_a_control_system "Logic of a control system" )**

  * [Closed loop](/index.php/Closed_loop "Closed loop" )
    * **PID controller**
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
    * [Jaguar](/index.php/Jaguar "Jaguar" )
  * [Sensors](/index.php/Sensor "Sensor" )
    * [Encoder](/index.php/Encoder "Encoder" )
    * [Accelerometer](/index.php/Accelerometer "Accelerometer" )
    * [Light sensor](/index.php?title=Light_sensor&action=edit "Light sensor" )
    * [IR sensor](/index.php/IR_sensor "IR sensor" )
    * [Gyro](/index.php/Gyro "Gyro" )
    * [CMUcam2](/index.php/CMUcam2 "CMUcam2" )  
---  
  
A **Proportional-Integral-Derivative controller** is a [closed
loop](/index.php/Closed_loop "Closed loop" )
[feedback](/index.php?title=Feedback&action=edit "Feedback" ) control. It is
used to get some device to reach a _setpoint_ by reacting based on the
[error](/index.php/Error "Error" ) of the system. The
[program](/index.php/Programming "Programming" ) reads in
[input](/index.php/Input "Input" ) from a [sensor](/index.php/Sensor "Sensor"
) and reacts based on the difference between the sensor reading and the
setpoint (the desired sensor reading) in three ways.

  * The error is multiplied by a **proportional** constant P. This handles the present, basing the output proportionally on the error. 
  * The error is integrated (or summed) over a time period and then multiplied by an **integral** constant I. This handles the past, basing the output on how long the error has persisted. 
  * The first derivative of the error (its rate of change, often the difference between the current and previous error is used) is calculated with respect to time and then multiplied by a **derivative** constant D. This handles the future, basing output on how quickly the error is changing. 

The sum of these calculations is then added to the last
[output](/index.php/Output "Output" ) of the PID loop.

## Contents

  * 1 Theory
  * 2 Application
  * 3 Tuning
  * 4 Going open loop
  * 5 Positive Feedback
  * 6 Safety Mechanisms
  * 7 Schematic
  * 8 See also
  * 9 External Links  
---  
  

## Theory

_Control_ refers to applying input (e.g., sensor readings) to cause a certain
system to conform to desired values (e.g, having an "arm" move to some
position). [Open loop](/index.php/Open_loop "Open loop" ) control does not use
feedback, meaning it does not continuously update its input. [Closed
loop](/index.php/Closed_loop "Closed loop" ) control continuously measures the
system variables and corrects the output based on this feedback. Closed loop
control adjusts to a dynamic environment where everything is not known
exactly. PID control is a specific type of closed loop control, and adjusts
the output using proportional, integral, and derivative terms. It is based on
control theory, heavy in mathematics (it is actually a differential equation),
and is a widely used filter mechanism. For most applications related to
[FIRST](/index.php/FIRST "FIRST" ), simplified results of control theory can
be used without needing to know advanced mathematical equations.

The general equation for proportional control is

Pout=Kerr*Kp where Pout is the output, Kerr= Target value-Current value, and
Kp is the gain value.


## Application

PID control is very useful in robotics. It is a way to make sure that what is
supposed to happen actually happens, despite a changing environment that can't
be controlled. For instance, PID control might be applied to driving the
robot, to compensate for wheel slippage and running into obstacles that offer
resistance or it might be applied to an "arm" to make it move to the desired
position and then resist backdrive due to gravity. There is no shortage of
applications. Almost wherever a sensor is used, a PID loop _could_ add for
additional control. However, it is not always desirable. It increases the
code's complexity and creates at least three constants that must be finely
tuned (see below). Also, if the sensor fails, called "going open loop," very
undesirable results can happen, depending on how the sensor failed (see
below). Despite these disadvantages, though, a PID control can be beneficial
to a wide variety of applications. For something that cannot be known fully
beforehand [dead reckoning](/index.php/Dead_reckoning "Dead reckoning" ) does
not work well; but, this is exactly where PID control shines. If, for
instance, a robot has a tendency to veer toward some direction besides
straight, using [wheel encoders](/index.php?title=Wheel_encoders&action=edit
"Wheel encoders" ) and PID control would be able to correct the problem.

It is worth mentioning that many systems are simple enough that a full PID
loop is not needed. Often a simple P loop (based soley on proportional
control, where I=D=0) is sufficient. Factors such as the speed that the system
can respond, the granularity of input, and the expected amount of disturbances
affect this, and if these are changed, more advanced control may then be
needed. A general rule of thumb in all of engineering is to start out simple,
and only add complexity where it is absolutely necessary. Complex things are
hard to fix and tend to break more easily. Simple things are much easier to
devlop.


## Tuning

A PID loop is useless without the correct constants. If these are too high or
too low, the system might overshoot drastically, leading to an uncontrolled
oscillation. The constants (P, I, and D) may be determined empirically, or
calculated if a system model is available for the controlled system. Tuning of
a PID loop is an art or skill, which is generally acquired through practice.
One suggestion is to start with just P control (I = D = 0). Observe the system
response to a small input step command. Increase P until the system just
starts to oscillate, meaning it reaches the target (setpoint), overshoots,
returns, undershoots and repeats this process; this is so-called _underdamped_
behaviour. Increase D until this oscillation stops; the control should be
smoother now, but if increased too far may cause sluggish system response
(i.e. the system is _overdamped_). Ideally, step response should have some
overshoot, and undershoot, but should settle into the desired setpoint
quickly. This may be achieved by repeatedly adjusting P &amp; D until the
desired step response is acheived. Integral gain (the I constant) is required
if there is some following error in the system; that is, if the controlled
variable has a constant difference from desired setpoint. Integral gain should
only be used sparingly since it tends to destabilize a system.


## Going open loop

"Going open loop" refers to a closed loop control that loses its input. This
might happen because the sensor becomes jostled out of the input slot on the
[Robot Controller](/index.php/Robot_Controller "Robot Controller" ), wear and
tear (aided by walls and opposing robots many times), the [PWM
cable](/index.php/PWM_cable "PWM cable" ) fails, or some other problem. If the
sensor is damaged and the system is not at the setpoint, it will try to reach
the setpoint as per the control, but the computer will never think it has
reached the setpoint since it is getting an incorrect and non-updated value.
This is mentioned because it can be a **safety risk** on certain systems,
causing an arm, for instance, to flail about wildly, damaging the robot,
passers-by, or both. If strange behaivor is observed on a previously working
control loop, check the sensors to make sure the correct values are being
read, and that the sensor is functioning.


## Positive Feedback

A common mistake when impementing a closed-loop controller is to use the
"wrong sign" when subtracting the feedback signal from the setpoint signal. We
want negative feedback; i.e. the error signal (setpoint minus the feedback)
times the PID gains should lead to a further reduction in the error. Positive
feedback will cause a runaway condition that can be very violent, causing
damage to people or equipment.


## Safety Mechanisms

In light of the above mentioned issues, a control system designer must always
consider the possibility of a sensor failure or other potential fault
condition. Steps should be taken in the control system design to limit the
motion (or other controlled variable), i.e. position, speed, accleration of a
controlled system. Such controls may be implemented in hardware (e.g. limit
switches) or software ("soft" limits). If only software limits are available,
there should be a watchdog circuit with safe shutdown implemented, since the
sanity of the control software cannot be depended upon.


## Schematic

[![Schematic for a PID closed loop system](/media/e/ec/Pidclosedloopsystem.JPG
)](/index.php/Image:Pidclosedloopsystem.JPG "Schematic for a PID closed loop
system" )


## See also

  * [Sensors](/index.php/Sensors "Sensors" )
  * [Feedback](/index.php?title=Feedback&action=edit "Feedback" )
  * [Open loop](/index.php/Open_loop "Open loop" )
  * [Closed loop](/index.php/Closed_loop "Closed loop" )


## External Links

  * [PIDlab.com](http://www.pidlab.com "http://www.pidlab.com" ) \- PID controller laboratory - free Java applets for PID tuning 
  * See [PID controller](http://www.wikipedia.org/wiki/PID_controller "wikipedia:PID_controller" ) for more information 
  * [Larry Barello](/index.php?title=Larry_Barello&action=edit "Larry Barello" ) gives a description of various robots he has worked on, and an overview of [PID control](http://www.barello.net/Papers/Motion_Control/index.htm "http://www.barello.net/Papers/Motion_Control/index.htm" ) (scroll down, code included) 
  * Several [ChiefDelphi](/index.php/ChiefDelphi "ChiefDelphi" ) threads related to this issue: ([[1]](http://www.chiefdelphi.com/forums/showthread.php?t=24340 "http://www.chiefdelphi.com/forums/showthread.php?t=24340" ), [[2]](http://www.chiefdelphi.com/forums/showthread.php?t=27978 "http://www.chiefdelphi.com/forums/showthread.php?t=27978" )) 

[![Image:LinkFA-star.png](/media/6/60/LinkFA-star.png)](/index.php/Image
:LinkFA-star.png "Image:LinkFA-star.png" )

