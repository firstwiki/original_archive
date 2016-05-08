# Default code (2004)

### From FIRSTwiki

Jump to: navigation, search

The **default code** provides pre-programmed functionality to the [Robot
Controller](robot-controller). This can allow
teams to spend more time on [fabricating](Fabrication "Fabrication"
) their [robot](Robot "Robot" ), so long as they don't need more
complicated control. But the default code also provides the starting point for
[programming](Programming "Programming" ) the FRC, and it is
necessary to understand the code before you decide to change it.

[InnovationFIRST](InnovationFIRST "InnovationFIRST" ) provides a
detailed description of the pre-programmed functionality of the default code
(see [Default Code Reference Guide](http://innovationfirst.com/FIRSTRobotics/p
dfs/FRC_RC_Default_Software_Ref_Guide_2004-1-7.pdf "http://innovationfirst.com
/FIRSTRobotics/pdfs/FRC_RC_Default_Software_Ref_Guide_2004-1-7.pdf" )). This
article does not strive to repeat that information here. Rather, the article
will attempt to explain the important features of the default code, and, to a
degree, how a team might go about customizing the code for its own needs (for
more on this, see [programming the Robot
Controller](Programming_the_Robot_Controller "Programming the Robot
Controller" )).

The default code consists of 12 header and c program files, only 3 of which
IFI recommends the user edit (although you are certainly allowed to create
your own files). Generally speaking, it is wise to stay within these
guidelines. Only edit files like _main.c_ or _printf_lib.c_ if you really know
what you are doing (and only edit files like _ifi_startup.c_ if you really,
really know what you are doing). Consider yourself warned.

The default code comes with the following files:

C files (.c extension) |  Header files (.h extension)  
---|---  
ifi_startup.c |  ifi_aliases.h  
ifi_utilities.c |  ifi_default.h  
main.c |  ifi_picdefs.h  
printf_lib.c |  ifi_utilities.h  
user_routines.c |  printf_lib.h  
user_routines_fast.c |  user_routines.h  
  
_ifi_aliases.h_ provides some useful aliases, and is worth looking at.
_printf_lib.c_ and _printf_lib.h_ provide a stripped down printf function, and
are useful for debugging purposes. Other than that, you should only need to be
concerned with _user_routines.c_, _user_routines.h_, and
_user_routines_fast.c_. This is the heart of the program -- the other files do
bookkeeping, and set things up for you.

Before explaining these individual files, it is helpful to examine the control
flow of the program. The program starts out by doing two initialization
routines, one from IFI and a custom one for the user. It then enters into the
main loop (which happens to be infinite). Basically, the loop involves reading
data, processing it, and then outputting data -- and then starting all over
again. In the [2004 Programming Reference Guide](http://innovationfirst.com/FI
RSTRobotics/pdfs/2004_Programming_Reference_Guide_12-Apr-2004.pdf "http://inno
vationfirst.com/FIRSTRobotics/pdfs/2004_Programming_Reference_Guide_12-Apr-200
4.pdf" ), [IFI](InnovationFIRST "InnovationFIRST" ) provides a
visual representation of this.

[![Default code structure
diagram](/media/thumb/d/da/Default_code_structure_diagram.png/180px-Default_co
de_structure_diagram.png)](Image:Default_code_structure_diagram.png
"Default code structure diagram" )

[![Enlarge](/skins/common/images/magnify-
clip.png)](Image:Default_code_structure_diagram.png "Enlarge" )

Default code structure diagram

## Contents

  * 1 user_routines.h
  * 2 user_routines.c
    * 2.1 User_Initialization
    * 2.2 Process_Data_From_Master_uP
    * 2.3 Default Routine
  * 3 user_routines_fast.c
    * 3.1 Interrupts
    * 3.2 User_Autonomous_Code
    * 3.3 Process_Data_From_Local_IO
  * 4 Resources  
---  
  
[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=1 "Edit
section: user_routines.h" )]

## user_routines.h

This is a [header file](/index.php?title=Header_file&action=edit "Header file"
), which is an appropriate place for
[macro](/index.php?title=Macro&action=edit "Macro" ) declarations, including
[aliases](/index.php?title=Aliases&action=edit "Aliases" ) and
[constants](/index.php?title=Constants&action=edit "Constants" ),
[typedef](/index.php?title=Typedef&action=edit "Typedef" ) declarations, and
[function prototypes](/index.php?title=Function_prototypes&action=edit
"Function prototypes" ). Nothing eventful happens in this file in the default
code, though it is a useful file to edit.

[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=2 "Edit
section: user_routines.c" )]

## user_routines.c

This is a c file, which is the heart of the normal operations. It contains the
default mappings of inputs to outputs on the RC. It defines useful functions,
such as Limit_Mix () which keeps the joystick control in the correct range.
This is where the action begins to happen.

[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=3 "Edit
section: User_Initialization" )]

### User_Initialization

This function starts out by setting which [I/O
pins](/index.php?title=I/O_pins&action=edit "I/O pins" ) will be used as
inputs and which will be used as outputs. It initializes the output, and sets
the [PWM](pwm) values to neutral (127). It then tells the
processor to take control of PWMs 13-16 (this can be changed to provide more
customization). The function then intializes the serial communications and
tells the master processor that it is ready.

[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=4 "Edit
section: Process_Data_From_Master_uP" )]

### Process_Data_From_Master_uP

This function is your connection to the main control loop. It runs every
26.2ms. The function gets fresh data, then sends it off to Default_Routine,
where the main action of the default code takes place. It then does some
important behind-the-scenes work that shouldn't be tampered with.

[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=5 "Edit
section: Default Routine" )]

### Default Routine

And now we get to the meat of the program. First, the function maps analog
inputs to PWM outputs. So if you had a
[potentiometer](Potentiometer "Potentiometer" ) connected to
p4_wheel, for instance, it would control pwm12, which might be connected to a
[speed controller](victor-884) and therefore control
a [motor](Motor "Motor" ). By default, port 1 is assumed to have a
[joystick](joystick) connected to it, and pwm13-16 are
assumed to control the drive motors. The function then maps the joystick
buttons to specific relay outputs. It causes certain PWM outputs to be limited
by [limit switches](Limit_switch "Limit switch" ). And finally, it
controls the robot feedback LEDs on the [OI](OI "OI" ).

[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=6 "Edit
section: user_routines_fast.c" )]

## user_routines_fast.c

This is another C file, which is the heart of the autonomous operations. It
also contains a place to put code that must be executed every loop, hence the
name _user_routines_fast_. It includes a section to define custom variables.

[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=7 "Edit
section: Interrupts" )]

### Interrupts

The file begins by providing the framework from which to build
[interrupts](Interrupts "Interrupts" ). These are not used by
default, however, and require special care and advanced knowledge of how the
processor works.

[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=8 "Edit
section: User_Autonomous_Code" )]

### User_Autonomous_Code

This is the function that executes when the robot is in [autonomous
mode](Autonomous_mode "Autonomous mode" ). It starts by
initializing all PWMS and relays. Then, it sets up a loop for you to add the
autonomous code. There is no autonomous action by default.

[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=9 "Edit
section: Process_Data_From_Local_IO" )]

### Process_Data_From_Local_IO

There is nothing at all in this function in the default code. It is useful for
code that must execute every loop and does not need to have fresh data every
time through.

_See also:_ [Programming](Programming "Programming" ), [Programming
the Robot Controller](Programming_the_Robot_Controller "Programming
the Robot Controller" )

[[edit](/index.php?title=Default_code_%282004%29&action=edit&section=10 "Edit
section: Resources" )]

## Resources

  * [Robot Controller Documentation](http://www.ifirobotics.com/rc.shtml "http://www.ifirobotics.com/rc.shtml" ) from [InnovationFIRST](InnovationFIRST "InnovationFIRST" ) (IFI) 
  * [2004 Programming Reference Guide](http://www.ifirobotics.com/docs/legacy/2004-programming-reference-guide-12-apr-2004.pdf "http://www.ifirobotics.com/docs/legacy/2004-programming-reference-guide-12-apr-2004.pdf" ) (pdf) from IFI 
  * [2004 Default Software Reference Guide](http://www.ifirobotics.com/docs/legacy/frc-rc-default-software-ref-guide-2004-1-7.pdf "http://www.ifirobotics.com/docs/legacy/frc-rc-default-software-ref-guide-2004-1-7.pdf" ) (pdf) from IFI 
  * [2007 FRC Default/User and Master code](http://www.ifirobotics.com/docs/frc-code-2007-8722.zip "http://www.ifirobotics.com/docs/frc-code-2007-8722.zip" ) (zip) from IFI (the old 2004 code no longer available) 

