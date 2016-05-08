# Creating a PID controller

### From FIRSTwiki

Jump to: navigation, search

Programming a simple [PID controller](PID_controller "PID
controller" ) for a FIRST robot is a relatively easy task. Depending on its
use, PID controllers may make the robot much easier to control.

[[edit](/index.php?title=Creating_a_PID_controller&action=edit&section=1 "Edit
section: Software" )]

##  Software

[[edit](/index.php?title=Creating_a_PID_controller&action=edit&section=2 "Edit
section: Variable Declaration" )]

###  Variable Declaration

Three constants or variables that are the reciprocal of the ratio, derivative,
and integral constants of proportionality must be declared and given values
to. You may use `#define`.

[[edit](/index.php?title=Creating_a_PID_controller&action=edit&section=3 "Edit
section: PID Function" )]

###  PID Function

Arguments to the PID function:

  * An integer request value 
  * The actual value of the device from the current [frame](/index.php?title=Code_frame&action=edit "Code frame" )
  * A pointer to an integer denoting the actual value 1 [frame](/index.php?title=Code_frame&action=edit "Code frame" ) ago 
  * A signed integer value denoting running total of the error 

Preconditions for the PID function:

  * All of the above arguments are valid 
  * Three constants or variables with the reciprocals of the ratio, integral, and derivative constants of proportionality 

Postconditions for the PID function:

  * The value at the pointer to the last actual value now equals the current actual value 
  * The sum pointer's value has been incremented by the current error 
  * The return value is the output value for the device as determined by [PID controller](PID_controller "PID controller" ) logic. 

Steps taken in the PID function:

  1. Calculate the error (not absolute value of error) as difference between request and actual 
  2. Add to the requested value the error multiplied by the ratio constant of proportionality 
  3. Add to the running sum the current error 
  4. Add the running sum multiplied by the integral constant of proportionality to the requested value 
  5. Add the derivative constant of proportionality multiplied by the difference between the actual value this frame and the actual value last frame to the requested value 
  6. Return the requested value (it has been updated due to the previous steps) 

An example PID function is (from the now defunct [NRG Code Repository (Code
Package 1)](http://nrg.chaosnet.org/repository/viewcode?id=1
"http://nrg.chaosnet.org/repository/viewcode?id=1" ). Check
[frCoder](FrCoder "FrCoder" ) for updates.):

    
    
     #define PID_K_PROP 1
     #define PID_K_INT 1
     #define PID_K_DERIV 1
     
     int PID(int request, int actual, int *lastActual, signed int *sum){
     int pid=request;
     signed int error=request-actual;
     /* Add the "proportional" part of the error */
     pid += error/PID_K_PROP;
     
     /* Add the "integral" part of the error */
     (*sum)+=error;
     pid+=(*sum)/PID_K_INT;
     
     /* Add the "derivative" part of the error */
     pid+=(actual-(*lastActual))/PID_K_DERIV;
     (*lastActual)=actual;
     
     return pid;
     }

Retrieved from
"<http://www.firstwiki.netCreating_a_PID_controller>"

[Categories](/index.php?title=Special:Categories&article=Creating_a_PID_contro
ller "Special:Categories" ): [How-to](Category:How-to "Category
:How-to" ) | [Logic of a control
system](Category:Logic_of_a_control_system "Category:Logic of a
control system" )

##### Views

  * [Article](Creating_a_PID_controller)
  * [Discussion](/index.php?title=Talk:Creating_a_PID_controller&action=edit)
  * [Edit](/index.php?title=Creating_a_PID_controller&action=edit)
  * [History](/index.php?title=Creating_a_PID_controller&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Creating_a_PID_controller)

[](Main_Page "Main Page" )

##### Navigation

  * [Main Page](Main_Page)
  * [Community portal](FIRSTwiki:Community_portal)
  * [Current events](Current_events)
  * [Recent changes](Special:Recentchanges)
  * [Random page](Special:Random)
  * [Help](Help:Contents)
  * [Donations](FIRSTwiki:Site_support)

##### Search



##### Toolbox

  * [What links here](Special:Whatlinkshere/Creating_a_PID_controller)
  * [Related changes](Special:Recentchangeslinked/Creating_a_PID_controller)
  * [Upload file](Special:Upload)
  * [Special pages](Special:Specialpages)
  * [Printable version](/index.php?title=Creating_a_PID_controller&printable=yes)
  * [Permanent link](/index.php?title=Creating_a_PID_controller&oldid=39506)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 21:14, 16 February 2005.
  * This page has been accessed 1,652 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

