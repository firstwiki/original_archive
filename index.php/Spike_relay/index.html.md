# Spike

### From FIRSTwiki

(Redirected from [Spike relay](/index.php?title=Spike_relay&redirect=no "Spike
relay" ))

Jump to: navigation, search

The [Control System](/index.php/Control_system "Control system" )

**[Logic of a Control System](/index.php/Logic_of_a_control_system "Logic of a control system" )**

  * [Closed loop](/index.php/Closed_loop "Closed loop" )
    * [PID controller](/index.php/PID_controller "PID controller" )
  * [Open loop](/index.php/Open_loop "Open loop" )

**[Parts of a Control System](/index.php/Parts_of_a_control_system "Parts of a control system" )**

  * [Computer](/index.php/Computer "Computer" )
    * [Robot Controller](/index.php/Robot_Controller "Robot Controller" )
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
    * **Spike**
  * [Sensors](/index.php/Sensor "Sensor" )
    * [Encoder](/index.php/Encoder "Encoder" )
    * [Accelerometer](/index.php/Accelerometer "Accelerometer" )
    * [Light sensor](/index.php?title=Light_sensor&action=edit "Light sensor" )
    * [IR sensor](/index.php/IR_sensor "IR sensor" )
    * [Gyro](/index.php/Gyro "Gyro" )
    * [CMUcam2](/index.php/CMUcam2 "CMUcam2" )  
---  
  
## Contents

  * 1 Data
  * 2 Connections
    * 2.1 Motors
    * 2.2 Solenoids
    * 2.3 Air Compressor
    * 2.4 Pinout of Control Input
  * 3 Spike Red  
---  
  
[[edit](/index.php?title=Spike&action=edit&section=1 "Edit section: Data" )]

## Data

The [Robot Controller](/index.php/Robot_Controller "Robot Controller" ) sends
a Relay signal to the Spike. When it recieves a FWD signal, it applies +12v to
M+ and grounds M-. Likewise when it recieves a REV signal, it applies +12v to
M- and grounds M+. When both signals are recieved, +12v is applied to M+ and
M- and nothing is grounded.

[[edit](/index.php?title=Spike&action=edit&section=2 "Edit section:
Connections" )]

## Connections

[[edit](/index.php?title=Spike&action=edit&section=3 "Edit section: Motors" )]

### Motors

Spikes can be connected to a [motor](/index.php/Motor "Motor" ) that does not
need to move at a variable speed. The motor cannot draw more than 20A.

[[edit](/index.php?title=Spike&action=edit&section=4 "Edit section: Solenoids"
)]

### Solenoids

Spikes can be connected to one or two solenoids. To connect two solenoids
simply ground the negative ends of the [solenoid](/index.php/Solenoid
"Solenoid" ) to the grounding portion of the [breaker
panel](/index.php/Breaker_panel "Breaker panel" ) and the positive ends to M+
and M-.

[[edit](/index.php?title=Spike&action=edit&section=5 "Edit section: Air
Compressor" )]

### Air Compressor

The air compressor can also be connected to the Spike, but care should be
taken to always observe the proper polarity. The NEG output should never be
enabled. If the compressor is powered in reverse, it will appear to function,
but it will be drawing more current and producing more heat than it should for
the amount of air it moves.

[[edit](/index.php?title=Spike&action=edit&section=6 "Edit section: Pinout of
Control Input" )]

### Pinout of Control Input

The control input to the Spike relay is a three-pin receptacle where a three-
wire cable from the [Robot controller](/index.php/Robot_controller "Robot
controller" ) is connected to. The black wire is grounded.

When the white wire is at +5V and the red wire is at 0V, M+ receives the full
input voltage. When the red wire is at +5V and the white wire is at 0V, M-
receives the full input voltage.

[[edit](/index.php?title=Spike&action=edit&section=7 "Edit section: Spike Red"
)]

#  Spike Red

Occasionally you might see versions of the Spike relay floating around that
have red lettering. These are older editions of the relay and lack reverse
polarity protection on their inputs.

Retrieved from "<http://www.firstwiki.net/index.php/Spike>"

##### Views

  * [Article](/index.php/Spike)
  * [Discussion](/index.php?title=Talk:Spike&action=edit)
  * [Edit](/index.php?title=Spike&action=edit)
  * [History](/index.php?title=Spike&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Spike)

[](/index.php/Main_Page "Main Page" )

##### Navigation

  * [Main Page](/index.php/Main_Page)
  * [Community portal](/index.php/FIRSTwiki:Community_portal)
  * [Current events](/index.php/Current_events)
  * [Recent changes](/index.php/Special:Recentchanges)
  * [Random page](/index.php/Special:Random)
  * [Help](/index.php/Help:Contents)
  * [Donations](/index.php/FIRSTwiki:Site_support)

##### Search



##### Toolbox

  * [What links here](/index.php/Special:Whatlinkshere/Spike)
  * [Related changes](/index.php/Special:Recentchangeslinked/Spike)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Spike&printable=yes)
  * [Permanent link](/index.php?title=Spike&oldid=60461)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 17:23, 14 May 2007.
  * This page has been accessed 2,339 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )
