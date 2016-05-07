# Drive train

### From FIRSTwiki

(Redirected from [Drive Systems](/index.php?title=Drive_Systems&redirect=no
"Drive Systems" ))

Jump to: navigation, search

[![](/media/thumb/1/10/FIRST_logo.gif/50px-
FIRST_logo.gif)](/index.php/Image:FIRST_logo.gif "" )

| **Please help [improve this article or
section](http://www.firstwiki.net/index.php?title=Drive_train&action=edit
"http://www.firstwiki.net/index.php?title=Drive_train&action=edit" ) by
expanding it.**  
Further information might be found on the [talk
page](/index.php/Talk:Drive_train "Talk:Drive train" ) or at [requests for
expansion](/index.php/FIRSTwiki:Requests_for_expansion "FIRSTwiki:Requests for
expansion" ).  
---|---  
  
  

A [robot](/index.php/Robot "Robot" )'s **drive train** consists of all of the
components used to make the robot move around the field. Most drive trains use
[motors](/index.php/Motor "Motor" ) to spin [wheels](/index.php/Wheel "Wheel"
) or drive [treads](/index.php/Tread "Tread" ) (belts). Some innovative teams
also incoporate [pneumatics](/index.php/Pneumatics "Pneumatics" ) and
[servos](/index.php/Servo "Servo" ) to allow shifting of
[gears](/index.php?title=Gears&action=edit "Gears" ).

The drivetrain is by far the most important and crucial part of a robot. It
may have other features, but without a functioning drive train those features
are useless. Drive Trains can come in many different forms, each one having
its own strengths and weaknesses. This overview will attempt to give an
general synopsis of drive train do's and don'ts, as well as touch on the most
common drive train incarnations.

  

## Contents

  * 1 The Basics
  * 2 Types of Drive Trains
    * 2.1 Two wheel drive
    * 2.2 Four Wheel Drive
    * 2.3 Six Wheel Drive
    * 2.4 Car Drive
    * 2.5 Swerve Drive
    * 2.6 Crab Drive
    * 2.7 Holonomic Drive
    * 2.8 Mecanum Drive
    * 2.9 Tank Tread Drive
    * 2.10 Other Drive Types
  * 3 See also  
---  
  

## The Basics

The optimum drive train for a robot is one that finds the correct balance of
speed, maneuverability, and pushing power to fit within a team's strategy.
Speed and pushing power are, in most cases, inversely proportional to one
another. Adjusting the balance between speed and pushing power is accomplished
by adjusting the gearing ratios between the input (motors) and the output
(wheels).

Maneuverability can be defined as the acceleration the robot can achieve in
various directions. In the case of a [skid steer](/index.php/Skid_steer "Skid
steer" ) robot maneuverability would probably be defined as the speed and the
precision with which the robot can rotate. Maneuverability is much trickier to
manipulate as it is the result of not only a robots speed and available
torque, but of the drive train's geometry as well. A high level of
maneuverability is very important in robot design, although it can be just as
much a curse as it is a blessing if not correctly understood. A robot that is
both extremely fast and extremely maneuverable will be almost impossible to
control without a certain level of sophistication within its controls, this
can take the form of either genuine closed loop software control (e.g. [PID
feedback loop](/index.php/PID_feedback_loop "PID feedback loop" )), or an
extensive [open loop](/index.php/Open_loop "Open loop" ) control system.


## Types of Drive Trains


### Two wheel drive

The _two-wheel drive_ (aka "casterbot") is undeniably the easiest one to make.
It offers high maneuverability while maintaining a very low level of
complexity. It can also be the most difficult to use. A casterbot turns with
such ease because there is virtually no side friction working against the
wheels of the robot as it turns. However, that same ease of turning can be a
nightmare - with no friction regulating the bot's speed of turning, its
inertia will always want to continue turning even after the motors have
stopped. This results in a robot that is extremely difficult to control using
basic control methods - it is a rare casterbot that can drive in a straight
line without the use of internal sensors or gyros. Furthermore, the unpowered
surfaces in contact with the floor detract from available pushing power, and
significantly lower a robot's ability to maintain its position when hit.

The design, for all its shortcomings, is nevertheless viable if correctly put
to use. When designing a two-wheel drive train, the powered wheels should be
in the center. This allows the robot's pivot point to remain close to its
center of mass, minimizing the area through which it must travel in order to
turn. Also, placing the powered wheels along the 30" sides of the robot will
further slow its rate of turn, making it more controllable (helpful, but not
necessary). A good example is [95](/index.php/95 "95" )'s 2002 'bot.


### Four Wheel Drive

The _four-wheel drive_ system is probably the most common drive train used in
FIRST. It offers a number of advantages and disadvantages over the more basic
two wheel drive. With the addition of two extra driven wheels, a four wheel
drive robot has more traction and control over a two wheel drive robot. The
trade-off is the increased wheel base can cause problems turning (when the
wheel base exceeds the wheel width.) A good example is [587](/index.php/587
"587" )'s '05 bot.


### Six Wheel Drive

The _six-wheel drive_ robot is a moderately common type of drivetrain. It
offers a good compromise between traction and maneuverability. Most teams
choose to lower the center wheels by approximately 1/8 - 3/16", allowing the
robot to turn more easily because normally it has a shortened wheel base but
at the same time, can tip over slightly, and enjoy the benefits of a full
length wheel base.

Some six wheel drive robots are in fact four wheel drive robots with an
unpowered pair of extra wheels that just act to increase the wheel base for
stability. When tipped to the unpowered set, some of its weight is diverted to
unpowered wheels and traction is therefore reduced.

A good example of this kind of drivetrain is the [418](/index.php/418 "418" )
'05 bot.

If you hear any reference to a "West Coast drive" it is commonly refering to a
Six Wheel Drive


### Car Drive

A _car drive_ (aka Ackerman Steering) robot has a steering system much like
what you would find on a standard automotive vehicle. Usually, the drive train
system has four wheels, with the two wheels in the back providing power, and
the two wheels in the front providing steering, though there are designs with
power and steering to all wheels. While the design gives increased speed and
pushing power and reduces the learning curve for the driver, it is not a very
common choice due to its lack of maneuverability. Generally, the large turning
radius makes it very difficult to maneuver in a corner.

A good example of this type of drivetrain is the [612](/index.php/612 "612" )
'05 bot.


### Swerve Drive

A _swerve drive_ robot has the ability to rotate its wheels, allowing the
robot to travel with three degrees of freedom. Several types exist, such as
the _crab drive_, in which all four wheels are linked such that they always
have the same angle as each other (generally requires one drive motor per
wheel plus two angling motors). A _2+2_ configuration has two pairs of wheels
which share angles (typically requiring four drive motors plus two angle
motors), and a _full omni_ system allows each wheel to be independently angled
(requires four drive motors and four angle motors - generally very time-,
labor-, part-, and weight-intensive, though it has been done before; examples
include Team [1810](/index.php/1810 "1810" )'s 2007 robot).

The main advantage of a swerve drive is a great increase in maneuverability.
The trade-offs are that swerve drives are much more complex to build and
consume much more resources (time, money, weight) than most other drivetrains.
Some forms of swerve drive are also known to have less power for pushing other
robots around on the field. However, increased maneuverability is gained to
make up for it. A good example is the [95](/index.php/95 "95" ) 2003 robot.


### Crab Drive

A _crab drive_ allows the robot to strafe at any angle, but turning involves a
great deal of skidding, sometimes even more than a typical four-wheel _tank
drive_ system (in which the power to the right and left wheels can be
independently adjusted). A _2+2_ configuration allows smoother turning
(similar to a car drive system but with two sets of independently angled
wheels) and the same omnidirectional strafing as a _crab drive_, but it cannot
turn and strafe at the same time (the reasons for this are a bit complicated).
Finally, a _full omni_ system allows for any combination of strafing and
turning simultaneously, as well as point turning. However, the increasing
weight and complexity of the latter two designs leads many teams to use the
simpler _crab drive_.


### Holonomic Drive

A _holonomic drive_ (aka omni drive) also allows a robot to travel with three
degrees of freedom rather than two. The difference is that a holonomic drive
allows a robot to instantly change direction without having to turn the wheels
to a different position. The major benefit of using a holonomic drive is a
great increase in maneuverability without having to add an entirely new
mechanism to turn the wheels. The major trade-off is that the robot isn't very
good when it comes to a pushing and shoving. Holonomic wheels have poor
traction, as they can't be made inflatable or with treads. They also demand
individual, speed controlled motors for each wheel.

An example of this type of drivetrain is team [2047s '07
bot](/media/0/09/2047_holonomic.jpg "2047 holonomic.jpg" ).

[Here](http://www.youtube.com/watch?v=CTlAf0c9KfA
"http://www.youtube.com/watch?v=CTlAf0c9KfA" ) is a video of team
[1418's](/index.php/1418 "1418" ) 2007 holonomic drive in action. Note the
slight listing when the chassis is supposed to be driving straight; this was
caused by asymmetries in the power outputs of the [Victor speed
controllers](/index.php/Victor_884 "Victor 884" ). This problem was
successfully fixed by using a lookup table to force individual joystick
positions to map to a linear set of power outputs.


### Mecanum Drive

A _[mecanum drive](/index.php/Mecanum_wheel "Mecanum wheel" )_ is another
omnidirectional drive system. It consist of wheels with their rollers angled
in a conventional four wheel drive layout. With an independent
motor/transmission on each wheel, omni driving can be achieved by varying
speeds. Mecanum is hard to understand without a picture, so
[here](http://wiki.chiefdelphi.com/Image:2006iFRC1595.jpg
"http://wiki.chiefdelphi.com/Image:2006iFRC1595.jpg" ) is a picture of the
[1595](/index.php?title=1595&action=edit "1595" ) robot in its incomplete
state, showing the drivetrain quite clearly.


### Tank Tread Drive


### Other Drive Types


##  See also

  * [Wikipedia:Floorplan](http://www.wikipedia.org/wiki/Floorplan "wikipedia:Floorplan" )
  * [Wikipedia:Robotic navigation](http://www.wikipedia.org/wiki/Robotic_navigation "wikipedia:Robotic_navigation" )

