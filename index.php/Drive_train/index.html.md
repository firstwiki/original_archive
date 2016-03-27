As we organize getting the site's software updated, feel free to submit any
suggestions you have on how we can improve the wiki
_**_[here!](/index.php/User:Hallry/Suggestions "User:Hallry/Suggestions"
)_**_. Thanks for all of your support!

If you are an administrator, it would be greatly appreciated if you could help
patrol [Recent Changes](/index.php/Special:Recentchanges
"Special:Recentchanges" ) to combat spam.

# Drivetrain

### From FIRSTwiki

(Redirected from [Drive train](/index.php?title=Drive_train&redirect=no "Drive
train" ))

Jump to: navigation, search

A **drivetrain** consists of all of the components used to make the robot move
around the field and is a crucial part of a robot. Most drivetrains use
[motors](/index.php/Motor "Motor" ) to spin [wheels](/index.php/Wheel "Wheel"
) or drive [treads](/index.php/Tread "Tread" ) (belts). Some innovative teams
also incoporate [pneumatics](/index.php/Pneumatics "Pneumatics" ) and
[servos](/index.php/Servo "Servo" ) to allow shifting of
[gears](/index.php/Gear "Gear" ) or changing which wheels are in contact with
the ground.

Drivetrains can come in many different forms, each one having its own
strengths and weaknesses. This overview will attempt to give an general
synopsis of drivetrain do's and don'ts, as well as touch on the most common
drivetrain variations.

## Contents

  * 1 Overview
    * 1.1 Maneuverability
  * 2 Types of Drivetrains
    * 2.1 Two Wheel Drive
    * 2.2 Four Wheel Drive
    * 2.3 Six Wheel Drive
    * 2.4 Car Drive
    * 2.5 Swerve Drive
    * 2.6 Crab Drive
    * 2.7 Holonomic Drive
    * 2.8 Mecanum Drive  
---  
  
[[edit](/index.php?title=Drivetrain&action=edit&section=1 "Edit section:
Overview" )]

## Overview

The optimum drivetrain for a robot is one that finds the correct balance of
speed, maneuverability, and pushing power to fit within a team's strategy.
Speed and pushing power are, in most cases, inversely proportional to one
another and can be adjusted by modifying the gearing ratios between the input
(motors) and the output (wheels).

[[edit](/index.php?title=Drivetrain&action=edit&section=2 "Edit section:
Maneuverability" )]

### Maneuverability

Maneuverability can be defined as how easily it is for a robot to maneuver
across a surface such as the game field. Maneuverability is much trickier to
manipulate as it is the result of not only a robots speed and available
torque, but of the drivetrain's geometry as well.

A high level of maneuverability is very important in robot design, although it
can be just as much a curse as it is a blessing if not correctly understood. A
robot that is both extremely fast and extremely maneuverable would be almost
impossible to control without a certain level of sophistication within its
controls which can take the form of either a closed loop software control
(e.g. [PID feedback loop](/index.php/PID_feedback_loop "PID feedback loop" )),
or an extensive [open loop](/index.php/Open_loop "Open loop" ) control system.

[[edit](/index.php?title=Drivetrain&action=edit&section=3 "Edit section: Types
of Drivetrains" )]

## Types of Drivetrains

[[edit](/index.php?title=Drivetrain&action=edit&section=4 "Edit section: Two
Wheel Drive" )]

### Two Wheel Drive

The _two wheel drive_ (aka "casterbot") is undeniably the easiest one to make.
A two-wheel drive consists of having two powered wheels at one end of the
robot and a unpowered surface that slides on the other end of the robot.

The two wheel drive offers high maneuverability while maintaining a very low
level of complexity. It can also be the most difficult to use. A casterbot
turns with such ease because there is virtually no side friction working
against the wheels of the robot as it turns. However, that same ease of
turning can be a nightmare - with no friction regulating the bot's speed of
turning, its inertia will always want to continue turning even after the
motors have stopped. This results in a robot that is extremely difficult to
control using basic control methods - it is a rare casterbot that can drive in
a straight line without the use of internal [sensors](/index.php/Sensor
"Sensor" ) or [gyros](/index.php/Gyro "Gyro" ). Furthermore, the unpowered
surfaces in contact with the floor detract from available pushing power, and
significantly lower a robot's ability to maintain its position when hit.

The design, for all its shortcomings, is nevertheless viable if correctly put
to use. When designing a two-wheel drivetrain, the powered wheels should be in
the center. This allows the robot's pivot point to remain close to its center
of mass, minimizing the area through which it must travel in order to turn.
Placing the powered wheels along the 30" sides of the robot will further slow
its rate of turn, making it more controllable (helpful, but not necessary).

[[edit](/index.php?title=Drivetrain&action=edit&section=5 "Edit section: Four
Wheel Drive" )]

### Four Wheel Drive

The _four wheel drive_ system is probably the most common drivetrain used in
[FIRST](/index.php/FIRST "FIRST" ). It offers a number of advantages and
disadvantages over the more basic two wheel drive. With the addition of two
extra driven wheels, a four wheel drive robot has more traction and control
over a two wheel drive robot. The trade-off is the increased wheel base can
cause problems turning (when the wheel base exceeds the wheel width).

[[edit](/index.php?title=Drivetrain&action=edit&section=6 "Edit section: Six
Wheel Drive" )]

### Six Wheel Drive

The _six wheel drive_ (also called "west coast drive") is a moderately common
type of drivetrain. It offers a good compromise between traction and
maneuverability. Most teams choose to lower the center wheels by approximately
1/8 - 3/16", allowing the robot to turn more easily because normally it has a
shortened wheel base but at the same time, can tip over slightly, and enjoy
the benefits of a full length wheel base.

Some six wheel drive robots are in fact four wheel drive robots with an
unpowered pair of extra wheels that just act to increase the wheel base for
stability. When tipped to the unpowered set, some of its weight is diverted to
unpowered wheels and traction is therefore reduced.

[[edit](/index.php?title=Drivetrain&action=edit&section=7 "Edit section: Car
Drive" )]

### Car Drive

A _car drive_ (aka [Ackerman
Steering](http://en.wikipedia.org/wiki/Ackermann_steering_geometry
"http://en.wikipedia.org/wiki/Ackermann_steering_geometry" )) robot has a
steering system much like what would be found on a standard automotive vehicle
with front wheel steering.

Usually, the drivetrain system has four wheels, with the two wheels in the
back providing power, and the two wheels in the front providing steering,
though there are designs with power and steering to all wheels. While the
design gives increased speed and pushing power and reduces the learning curve
for the driver, it is not a very common choice due to its lack of
maneuverability. Generally, the large turning radius makes it very difficult
to maneuver in a corner or tight space.

[[edit](/index.php?title=Drivetrain&action=edit&section=8 "Edit section:
Swerve Drive" )]

### Swerve Drive

A _swerve drive_ robot has the ability to rotate its wheels, allowing the
robot to travel with three degrees of freedom.

Several types exist, such as the _crab drive_, in which all four wheels are
linked such that they always have the same angle as each other (generally
requires one drive motor per wheel plus two angling motors). A _2+2_
configuration has two pairs of wheels which share angles (typically requiring
four drive motors plus two angle motors), and a _full omni_ system allows each
wheel to be independently angled (requires four drive motors and four angle
motors.

The main advantage of a swerve drive is a great increase in maneuverability.
The trade-offs are that swerve drives are much more complex to build and
consume much more resources (time, money, weight, space) than most other
drivetrains. Some forms of swerve drive are also known to have less power for
pushing other robots around on the field. However, increased maneuverability
is gained to make up for it.

[[edit](/index.php?title=Drivetrain&action=edit&section=9 "Edit section: Crab
Drive" )]

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

[[edit](/index.php?title=Drivetrain&action=edit&section=10 "Edit section:
Holonomic Drive" )]

### Holonomic Drive

A _holonomic drive_ (aka "omni drive") also allows a robot to travel with
three degrees of freedom rather than two. The difference is that a holonomic
drive allows a robot to instantly change direction without having to turn the
wheels to a different position. The major benefit of using a holonomic drive
is a great increase in maneuverability without having to add an entirely new
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

[![Example of a mecanum drive from 1595.](/media/thumb/7/71/2006iFRC1595.jpg
/150px-2006iFRC1595.jpg)](/index.php/Image:2006iFRC1595.jpg "Example of a
mecanum drive from 1595." )

[![Enlarge](/skins/common/images/magnify-
clip.png)](/index.php/Image:2006iFRC1595.jpg "Enlarge" )

Example of a [mecanum drive](/index.php/Mecanum_wheel "Mecanum wheel" ) from
[1595](/index.php?title=1595&action=edit "1595" ).

[[edit](/index.php?title=Drivetrain&action=edit&section=11 "Edit section:
Mecanum Drive" )]

### Mecanum Drive

A [mecanum drive](/index.php/Mecanum_wheel "Mecanum wheel" ) is another
omnidirectional drive system. It consist of wheels with their rollers angled
in a conventional four wheel drive layout. With an independent
motor/transmission on each wheel, omni driving can be achieved by varying
speeds.

Retrieved from "<http://www.firstwiki.net/index.php/Drivetrain>"

[Category](/index.php?title=Special:Categories&article=Drivetrain
"Special:Categories" ): [Robot
components](/index.php/Category:Robot_components "Category:Robot components" )

##### Views

  * [Article](/index.php/Drivetrain)
  * [Discussion](/index.php/Talk:Drivetrain)
  * [Edit](/index.php?title=Drivetrain&action=edit)
  * [History](/index.php?title=Drivetrain&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Drivetrain)

[](/index.php/Main_Page "Main Page" )

##### Navigation

  * [Main Page](/index.php/Main_Page)
  * [Community portal](/index.php/FIRSTwiki:Community_portal)
  * [Current events](/index.php/Current_events)
  * [Recent changes](/index.php/Special:Recentchanges)
  * [Random page](/index.php/Special:Random)
  * [Help](/index.php/FIRSTwiki:Help)
  * [Donations](/index.php/FIRSTwiki:Site_support)

##### Search



##### Toolbox

  * [What links here](/index.php/Special:Whatlinkshere/Drivetrain)
  * [Related changes](/index.php/Special:Recentchangeslinked/Drivetrain)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Drivetrain&printable=yes)
  * [Permanent link](/index.php?title=Drivetrain&oldid=80763)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 23:04, 11 July 2011.
  * This page has been accessed 30,553 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

