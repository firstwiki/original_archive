As we organize getting the site's software updated, feel free to submit any
suggestions you have on how we can improve the wiki
_**_[here!](/index.php/User:Hallry/Suggestions "User:Hallry/Suggestions"
)_**_. Thanks for all of your support!

# Programming the Robot Controller

### From FIRSTwiki

Jump to: navigation, search

**Programming the FRC** is necessary to get the most out of the [control system](/index.php/Control_system "Control system" ). For simple [robots](/index.php/Robot "Robot" ), the [default code](/index.php/Default_code "Default code" ) will be sufficient. But for more advanced control, custom code must be added. This article attempts to explain how to begin modifying the default code to meet your specific purposes. The article assumes a familiarity with the C programming language (see [Resources for C programming](/index.php/Resources_for_C_programming "Resources for C programming" )), and primarily focuses on that. 

Note that prior to 2004, a the a [BASIC stamp](/index.php/BASIC_stamp "BASIC
stamp" ) was used, which was programmed in [PBASIC](/index.php/PBASIC "PBASIC"
). 2004 marked a major switch in the [Robot
Controller](/index.php/Robot_Controller "Robot Controller" ), making [PIC
C](/index.php/PIC_C "PIC C" ) the programming language of choice (along with
[assembly](/index.php/Assembly "Assembly" )).

_This article follows the structure of the [2004 Programming Reference Guide](
http://innovationfirst.com/FIRSTRobotics/pdfs/2004_Programming_Reference_Guide
_12-Apr-2004.pdf "http://innovationfirst.com/FIRSTRobotics/pdfs/2004_Programmi
ng_Reference_Guide_12-Apr-2004.pdf" )._

The [PICmicro](/index.php/PICmicro "PICmicro" ) can be programmed in C or
assembly. [MPLAB](/index.php/MPLAB "MPLAB" ) IDE is the name of the free
Windows program used to edit, compile, and debug programs. To
[download](/index.php/Downloading_a_program "Downloading a program" ) a
program, [IFI loader](/index.php/IFI_loader "IFI loader" ) must be used. This
software is included in the [kit of parts](/index.php/Kit_of_parts "Kit of
parts" ), and is availalbe on the [Innovation
FIRST](/index.php/Innovation_FIRST "Innovation FIRST" ) website (see Resources
below).

## Contents

  * 1 About C
    * 1.1 Comments
    * 1.2 Variables
    * 1.3 Macros as Aliases
    * 1.4 Macros as Constants
    * 1.5 Macros as Functions
  * 2 About the default code
    * 2.1 Initialization
    * 2.2 Main loop
    * 2.3 Process_Data_From_Master_uP  
---  
  
[[edit](/index.php?title=Programming_the_Robot_Controller&action=edit&section=
1 "Edit section: About C" )]

## About C


### Comments

Comments are text within a program that the compiler ignores, but is present
for the benefit of the programmer and others reading the code. Comments are
used to explain what a specific piece of code does, or how it fits in the
larger structure of the program. They do not affect in any way how the program
runs. The C-style comment is deliminated with _/* */_, with text going in
between. Comments can span multiple lines, but **may not** be nested. For
example:

    
    
     /* This is
          allowed. */
     /*  but  /* this */ is most distinctively not */
    

When commenting, it is important to remember that what seems obvious at the
time will become archaic in a few months. It is also important to remember
that other people will often be examining the code, some which are trying to
learn from it. Therefore, it is generally considered good practice to heavily
comment program code. A good rule of thumb is that if you ever had to look at
code and wonder "What does that do again?" then you need to comment. Keep in
mind, however that comments should be high level code like this, for instance:
x = y + z; /* adds y and z and puts the sum in x */ adds nothing. Finally, be
concise.

Also allowed by the [compiler](/index.php/MCC18 "MCC18" ), but not documented,
are what are known as C++ style comments (so called because they were added in
C++ and are not in the original C). They begin with 2 slashes and end at the
end of the line.

    
    
    //This is a comment
    This_isnt_a_Comment();
    

There are several advantages to this:

  * Can be placed within a /* */ comment (aka a muliline comment) 
  * You can use multi-line comments to comment out code w/o having to go through each line and add /* at the beginning 


### Variables

C is a heavily typed language. What this means is that when a variable is
created, it must be a specific data type -- e.g., it could be an integer, or
maybe a floating point number. (See [List of data
types](/index.php/List_of_data_types "List of data types" ) for more
information.) Variables are declared like this:

    
    
     unsigned int loop_counter_for_function_x = 0;
    

Note that it is possible to intialize variables when they are declared (set to
0 above), but this is not necessary. Also note that it is important to
establish some sort of naming convention, preferably with less verbose names
than above -- a general rule of thumb is that variables that are used most
often should be shorter variable names, since they are typed out more, but
less frequently used variables can have more informative, and hence longer,
names.

It is possible to share variables between files, and is often quite important.
For instance, if the variable _arm_pos_ represents the position of the robot's
arm, it might be useful to have in both _user_routines.c_ and
_user_routines_fast.c_ (this way in can be used in normal control as well as
autonomous mode). To do this, declare the variable in _user_routines.c_ and
then put the following statement in _user_routines_fast.c_:

    
    
     extern unsigned int arm_pos;
    


### Macros as Aliases

Macros provide alternate and often shorter names for constants, variables, and
sub-divisions of variables. This is significant because it can save on typing,
and also allows for a certain layer of abstraction. Aliases are used
extensively in the [default code](/index.php/Default_code "Default code" ) to
provide convenient names for [analog
inputs](/index.php?title=Analog_inputs&action=edit "Analog inputs" ), [digital
i/o](/index.php?title=Digital_i/o&action=edit "Digital i/o" ), [relay
outputs](/index.php?title=Relay_outputs&action=edit "Relay outputs" ),
[solenoid outputs](/index.php?title=Solenoid_outputs&action=edit "Solenoid
outputs" ), and [PWM outputs](/index.php?title=PWM_outputs&action=edit "PWM
outputs" ). Aliases used by the default code are located in _ifi_aliases.h_;
custom aliases might be placed in _user_routines.h_. Note that aliases are
taken care of by the pre-processor by simple text substitution, and do not
require any additional memory -- therefore they may be used liberally with
little consequence. They are defined like this:

    
    
     #define AUTO_SEL_POT p2_wheel
    

Note that no semicolon is used -- if a semicolon is placed at the end of the
line, it will be substituted when the alias is used, typically causing errors.
Aliases can be useful because they allow for a bit of abstraction. For
instance, if a [potentiometer](/index.php/Potentiometer "Potentiometer" ) in
p2_wheel is changed to p3_wheel, the rest of the code does not care -- only
the alias has to be changed (this is preferred, of course, as opposed to
changing many references).


### Macros as Constants

Aside from aliases, macros also prove useful as standing for constants. They
make the code more readable, that is, more understandable to the human. It
also aids in adjusting the code for future use. For instance, if the program
makes use of the value pi, rather than putting 22/7 in all the locations it is
used, a macro would allow simply saying PI. Then, if more accuracy is desired,
the define statement can be altered. E.g.,

    
    
     #define PI 22/7    
             /* first go */
    

**NOTE:**  

    Avoid putting comments on the same line as a #define. These lines have no punctuation. They are commands directly to the compiler. You are telling the compiler to use the following information whenever you use the macro in the c-code. The compiler will then stuff any comments into the code along with the defined variable. This can lead to strange reported errors. 
    
    
     #define PI 3.14     
            /* more accurate */
     #define PI 3.14159  
            /* every milimeter counts! */
    

Also, imagine that for the autonomous mode, the robot needs to travel at a
certain forward speed during a particular stage. Having that speed defined in
an easily accessible location with other adjustable parameters makes changing
it much easier. In general, macros aid in the development process.


### Macros as Functions

Macros may also take arguments. Examples:

    
    
     #define SGN(Value) (((Value) < 0) ? -1 : (((Value) > 0) ? 1 : 0))
     #define ABS_DIF(Num1,Num2) (((Num1) > (Num2)) ? ((Num1) - (Num2)) : ((Num2) - (Num1)))
    

  * Don't put spaces between arguments, as that will cause it to end the name at the space (eg _ABS_DIF(Num1,_) 
  * If an expresion is given as an argument, it is still compiled as a string replace. eg: 
    
    
    ABS_DIF(foo + bar, bar - foo)
    

would be compiled as

    
    
    (((foo + bar) > (bar - foo)) ? ((foo + bar) - (bar - foo)) : ((bar - foo) - (foo + bar)))
    

[[edit](/index.php?title=Programming_the_Robot_Controller&action=edit&section=
7 "Edit section: About the default code" )]

## About the default code


### Initialization

Initialization takes place in _main.c_. First, the function IFI_Initialization
is called. This should not be tampered with, as it is important for setting up
the processor to handle the rest of the code. Next, however, the function
User_Initialization is called. This function is in _user_routines.c_. Often
there are things that the program only needs to execute the first time
through. It is not necessary to create a variable and a conditional statement
to handle this anymore, as the code can simply be placed in
User_Initialization. For instance, it might be necessary to read in a sensor
value, assign that to a setpoint, and then react in some way if it is in a
certain range. In general, it is good practice to intialize most variables in
this function that need initialization, rather than when they are declared, so
that they are easy to get to and change when necessary.


### Main loop

In _main.c_ there is a while loop with the condition of 1. In C, 1 is always
true, meaning that it is in effect, an infinite loop. It is important to
understand this concept when programming the FRC. The program reads in data,
processes it, then outputs other data, then repeats. For this reason, custom
code will almost never include additional looping structures, and alogirthms
must be adopted to this.


### Process_Data_From_Master_uP

_See also:_ [MPLAB](/index.php/MPLAB "MPLAB" ), [Downloading a
program](/index.php/Downloading_a_program "Downloading a program" ), [Robot
Controller](/index.php/Robot_Controller "Robot Controller" ), [Electronics and
circuitry](/index.php/Electronics_and_circuitry "Electronics and circuitry" )

Retrieved from
"<http://www.firstwiki.net/index.php/Programming_the_Robot_Controller>"

[Categories](/index.php?title=Special:Categories&article=Programming_the_Robot
_Controller "Special:Categories" ):
[Programming](/index.php/Category:Programming "Category:Programming" ) | [How-
to](/index.php/Category:How-to "Category:How-to" )

##### Views

  * [Article](/index.php/Programming_the_Robot_Controller)
  * [Discussion](/index.php/Talk:Programming_the_Robot_Controller)
  * [Edit](/index.php?title=Programming_the_Robot_Controller&action=edit)
  * [History](/index.php?title=Programming_the_Robot_Controller&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Programming_the_Robot_Controller)

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

  * [What links here](/index.php/Special:Whatlinkshere/Programming_the_Robot_Controller)
  * [Related changes](/index.php/Special:Recentchangeslinked/Programming_the_Robot_Controller)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Programming_the_Robot_Controller&printable=yes)
  * [Permanent link](/index.php?title=Programming_the_Robot_Controller&oldid=69039)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 02:29, 27 September 2008.
  * This page has been accessed 5,954 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

