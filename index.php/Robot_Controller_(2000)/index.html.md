# Robot Controller (2000)

### From FIRSTwiki

Jump to: navigation, search

The 2000 RC was a big upgrade from the older system. It used a
[BS2sx](/index.php/BS2sx "BS2sx" ) to replace the [BS2](/index.php/BS2 "BS2"
). This was also the first one designed and manufactured by
[InnovationFIRST](/index.php/InnovationFIRST "InnovationFIRST" ). It was used
for the 2000-2002 seasons (and with minor modifications for the 2003 season).

The 2000-2003 Robot Controller systems consisted of three processors. The
[Operator Interface](/index.php/Operator_Interface "Operator Interface" ) used
a [PIC16F877](/index.php/PIC16F877 "PIC16F877" ) microcontroller to collect
data from all the digital and analog inputs and communicate with the Robot
Controller via a radio or tether. The second processor was the user processor,
a Basic Stamp 2SX. The User Processor was the only user-programmable CPU in
the entire system. The third processor, the Master Processor, was a PIC16
microcontroller, which controlled the outputs for all relays, speed
controllers, and other output devices. The General-purpose IO pins of the
BS2SX were not accessible as they were connected to LEDs on the controller
itself. The only direct connection available to the BS2SX was the "programming
port", two pins on the Stamp normally dedicated to RS232 communication with
the host programming PC.

The 2000-2003 Robot Controllers were programmed in [PBASIC](/index.php/PBASIC
"PBASIC" ), a [Parallax](/index.php/Parallax "Parallax" )-dialect of
[BASIC](http://www.wikipedia.org/wiki/BASIC "wikipedia:BASIC" ). Program flow
was very similar to the current [C](/index.php/PIC_C "PIC C" )-based code,
with a main loop and similar timing characteristics involved. Code would first
have to declare all variables used, which were bits, nibbles, bytes, or words.
Then initialization of the master processor would occur. The Stamp would use
SHIFTOUT to establish communication with the Master Processor and bring the
entire stack online. Then, the main loop would start. In the main loop, a long
SERIN instruction would collect all input data from the Input microprocessor.
The user code would manipulate the data as it saw fit, and then would use
SEROUT to pipe the data to the Master microprocessor. This is roughly
analogous to the current GetData() and Put_Data() in the modern control
system. Even the timing is nearly identical--both systems were required to
output data ever 26.2 ms.

  


## External links

  * [InnovationFirst.com](http://innovationfirst.com "http://innovationfirst.com" )
  * [Documentation for 2001 through 2003 Control Systems](http://innovationfirst.com/FIRSTRobotics/documentation-legacy.htm "http://innovationfirst.com/FIRSTRobotics/documentation-legacy.htm" ). 

Retrieved from
"<http://www.firstwiki.net/index.php/Robot_Controller_%282000%29>"

##### Views

  * [Article](/index.php/Robot_Controller_%282000%29)
  * [Discussion](/index.php?title=Talk:Robot_Controller_%282000%29&action=edit)
  * [Edit](/index.php?title=Robot_Controller_%282000%29&action=edit)
  * [History](/index.php?title=Robot_Controller_%282000%29&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Robot_Controller_\(2000\))

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

  * [What links here](/index.php/Special:Whatlinkshere/Robot_Controller_%282000%29)
  * [Related changes](/index.php/Special:Recentchangeslinked/Robot_Controller_%282000%29)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Robot_Controller_%282000%29&printable=yes)
  * [Permanent link](/index.php?title=Robot_Controller_%282000%29&oldid=76708)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 04:54, 21 June 2010.
  * This page has been accessed 2,036 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

