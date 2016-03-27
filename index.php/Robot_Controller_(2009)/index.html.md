# Robot Controller (2009)

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
      * **2009 RC**
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
    * [IR sensor](/index.php/IR_sensor "IR sensor" )
    * [Gyro](/index.php/Gyro "Gyro" )
    * [CMUcam2](/index.php/CMUcam2 "CMUcam2" )  
---  
  
[![](/media/thumb/1/10/FIRST_logo.gif/50px-
FIRST_logo.gif)](/index.php/Image:FIRST_logo.gif "" )

| **Please help [improve this article or section](http://www.firstwiki.net/ind
ex.php?title=Robot_Controller_%282009%29&action=edit "http://www.firstwiki.net
/index.php?title=Robot_Controller_%282009%29&action=edit" ) by expanding it.**  
Further information might be found on the [talk
page](/index.php?title=Talk:Robot_Controller_%282009%29&action=edit
"Talk:Robot Controller \(2009\)" ) or at [requests for
expansion](/index.php/FIRSTwiki:Requests_for_expansion "FIRSTwiki:Requests for
expansion" ).  
---|---  
  
  

The FIRST Robotics Competition (FRC) has adopted the CompactRIO (cRIO) control
system for advanced robotics for its 2009 season and beyond. The cRIO from
National Instruments can be programmed in LabVIEW or C.

## Contents

  * 1 Programming
    * 1.1 LabVIEW
    * 1.2 C++
    * 1.3 C
  * 2 Hardware
  * 3 Modules
    * 3.1 Digital I/O Module (NI 9403) and Sidecar
    * 3.2 Digital Output/Solenoid Module (NI 9472) and Solenoid Breakout
    * 3.3 Analog Input Module (NI 9201) and Analog Breakout
  * 4 Key features
  * 5 External Links  
---  
  
[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=1
"Edit section: Programming" )]

##  Programming

Code is cross-compiled on a seperate computer then uploaded over the network
by the programming environment.

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=2
"Edit section: LabVIEW" )]

###  LabVIEW

The cRIO will be programmable from National Instrument's own environment,
LabVIEW. A demonstration of how LabVIEW will be used with the FIRST Robotics
Competition robots has been provided by NI [FIRST Robotics Competition:
Joystick Motor Control in 10
Minutes](http://zone.ni.com/devzone/cda/tut/p/id/7977
"http://zone.ni.com/devzone/cda/tut/p/id/7977" )

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=3
"Edit section: C++" )]

###  C++

In addition, the cRIO will be programmable in C or C++ with a library
developed by [Worcester Polytechnic Institute](http://first.wpi.edu/
"http://first.wpi.edu/" ) called WPILib. Generated API documentation under
very active development (subject to change) can be previewed: [WPI Robotics
Library
Documentation](http://users.wpi.edu/~bamiller/WPIRoboticsLibrary/index.html
"http://users.wpi.edu/~bamiller/WPIRoboticsLibrary/index.html" ).

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=4
"Edit section: C" )]

###  C

Wrappers around the C++ library will be provided.
[[1]](http://forums.usfirst.org/showpost.php?p=18063&postcount=1
"http://forums.usfirst.org/showpost.php?p=18063&postcount=1" )

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=5
"Edit section: Hardware" )]

##  Hardware

The Compact Rio contains a PowerPC processor and reprogramable FPGA processor
which will be programmed by FIRST for the events. It runs
[VxWorks](http://www.wikipedia.org/wiki/VxWorks "wikipedia:VxWorks" ) [![Image
:Extlinkwikipedia.GIF](/media/c/cb/Extlinkwikipedia.GIF)](/index.php/Image:Ext
linkwikipedia.GIF "Image:Extlinkwikipedia.GIF" ), a POSIX certified, real-time
operating system.

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=6
"Edit section: Modules" )]

##  Modules

The cRIO has slots for eight interchangeable modules. New modules will be
supplied each year to teams. The modules by themselves only have a D-Sub
connector, so PWM or other wiring connections are made available through a
breakout board that either that screws into the module, or a sidecar that is
seperate from the module and connected by a cable.

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=7
"Edit section: Digital I/O Module \(NI 9403\) and Sidecar" )]

###  Digital I/O Module (NI 9403) and Sidecar

The Digital Sidecar and module providing general purpose input/output. 32
channels of data are sent to the Digital Sidecar. A digital output can output
a maximum of 5.2V.

[Module](http://first.wpi.edu/FRC/digital.html
"http://first.wpi.edu/FRC/digital.html" )
[Sidecar](http://first.wpi.edu/FRC/digitalsidecar.html
"http://first.wpi.edu/FRC/digitalsidecar.html" )

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=8
"Edit section: Digital Output/Solenoid Module \(NI 9472\) and Solenoid
Breakout" )]

###  Digital Output/Solenoid Module (NI 9472) and Solenoid Breakout

The Solenoid module will allow for connections to a pneumatics relay.
Connections are provided through the Solenoid Breakout. This module can
provide a maximum output of 30V.

[Module and Breakout](http://first.wpi.edu/FRC/solenoid.html
"http://first.wpi.edu/FRC/solenoid.html" )

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=9
"Edit section: Analog Input Module \(NI 9201\) and Analog Breakout" )]

###  Analog Input Module (NI 9201) and Analog Breakout

The Analog Input module allows eight inputs of analog data with 12-bit
resolution.

[Module and Breakout](http://first.wpi.edu/FRC/analog.html
"http://first.wpi.edu/FRC/analog.html" )

  

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=10
"Edit section: Key features" )]

## Key features

  * 32-bit real-time processor 
  * 802.11 pre-n wireless ethernet 
  * FPGA I/O control 
  * Programmable in C, C++, and LabVIEW 
  * Wireless debugging 
  * Laptop dashboard 
  * Intelligent robotics algorithms 
  * Real-time vision processing 
  * 50G shock rating 
  * Easier connectivity 
  * More sensor choices 
  * More I/O lines 
  * Customizable I/O possible in future years 

[[edit](/index.php?title=Robot_Controller_%282009%29&action=edit&section=11
"Edit section: External Links" )]

## External Links

  * [FIRST Documentation](http://www.usfirst.org/community/frc/content.aspx?id=10934 "http://www.usfirst.org/community/frc/content.aspx?id=10934" )
  * [NI FIRST community](http://decibel.ni.com/content/community/first "http://decibel.ni.com/content/community/first" )
  * [WPIlib resources, C and C++ programming](http://first.wpi.edu/FRC/ "http://first.wpi.edu/FRC/" )

  

[![](/media/thumb/1/10/FIRST_logo.gif/50px-
FIRST_logo.gif)](/index.php/Image:FIRST_logo.gif "" )

|  _This article is currently a stub (a short article without much content).
[Please add more content](http://www.firstwiki.net/index.php?title=Robot_Contr
oller_%282009%29&action=edit "http://www.firstwiki.net/index.php?title=Robot_C
ontroller_%282009%29&action=edit" ) to make a significant article. If you'd
like to add to more stubs, look at the list of [short
articles](/index.php/Special:Shortpages "Special:Shortpages" )._  
---|---  
  
Retrieved from
"<http://www.firstwiki.net/index.php/Robot_Controller_%282009%29>"

[Categories](/index.php?title=Special:Categories&article=Robot_Controller_%282
009%29 "Special:Categories" ): [Articles to be
expanded](/index.php/Category:Articles_to_be_expanded "Category:Articles to be
expanded" ) | [Stubs](/index.php/Category:Stubs "Category:Stubs" )

##### Views

  * [Article](/index.php/Robot_Controller_%282009%29)
  * [Discussion](/index.php?title=Talk:Robot_Controller_%282009%29&action=edit)
  * [Edit](/index.php?title=Robot_Controller_%282009%29&action=edit)
  * [History](/index.php?title=Robot_Controller_%282009%29&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Robot_Controller_\(2009\))

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

  * [What links here](/index.php/Special:Whatlinkshere/Robot_Controller_%282009%29)
  * [Related changes](/index.php/Special:Recentchangeslinked/Robot_Controller_%282009%29)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Robot_Controller_%282009%29&printable=yes)
  * [Permanent link](/index.php?title=Robot_Controller_%282009%29&oldid=69991)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 01:31, 19 November 2008.
  * This page has been accessed 1,842 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

