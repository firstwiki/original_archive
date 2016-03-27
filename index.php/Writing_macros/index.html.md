# Writing macros

### From FIRSTwiki

Jump to: navigation, search

Macros are simple text replacements made by the C preprocessor. They allow
constants to be defined in one place where they can easily be edited and are
also used to rename cryptic variable names to be more understandable. Using
macros wisely in a program can increase code readability and maintainability.

## Contents

  * 1 Syntax
  * 2 Uses of Macros
    * 2.1 Constants
    * 2.2 Renaming
  * 3 External Links  
---  
  
[[edit](/index.php?title=Writing_macros&action=edit&section=1 "Edit section:
Syntax" )]

## Syntax

Macros are written using the C preprocessor statement #define using the
following syntax:

    
    
    #define TEXT_TO_REPLACE   TextToBeInserted
    

Unless the text to be inserted is a complete statement, the line should not
end in a semi-colon. The text to be inserted in a macro can be split into
multiple lines by ending the line with a “\” (no quotes). Having multi-line
statements is not recommended for beginners except for simple string
replacements. Including multiple lines of code in a macro can produce errors
that are very difficult to understand because syntax errors can occur after
preprocessor has replaced text, making error messages hard to follow. Also,
including complex macros can make the code more difficult to understand for
other programmers.

There is also a function-like notation for macros with parameters inside
parenthesis. Using a macro instead of a normal function benefits the speed of
a program because calculations are done by the compiler, not during runtime,
but this shouldn’t be used for the same reasons multi-line macros are not
recommended. To achieve the same effect without using macros, a function can
be preceded with the keyword "inline" in any modern compiler.

[[edit](/index.php?title=Writing_macros&action=edit&section=2 "Edit section:
Uses of Macros" )]

## Uses of Macros

Macros can make a program more readable and maintainable by having all
constants named in one place, as well as providing reasonable names for
input/output variables.

[[edit](/index.php?title=Writing_macros&action=edit&section=3 "Edit section:
Constants" )]

### Constants

One use for macros is defining constants. For example, constant values used
for PWM outputs can be defined in one place.

    
    
    #define PWM_NEUTRAL_SPEED 127
    #define PWM_MAX_FORWARD   254
    #define PWM_MAX_REVERSE     0
    

Then 254 will replace every instance of PWM_MAX_SPEED by the preprocessor.
This allows programmers to change the value 254 to a lower value, should they
decide that 254 is too fast later on. It also removes any confusion a future
programmer might have about what the value means because it is written in
plain English, rather than an obscure number.

[[edit](/index.php?title=Writing_macros&action=edit&section=4 "Edit section:
Renaming" )]

### Renaming

Macros don't just define constants, they can also be used to assign aliases
for global variables, such as PWM outputs and joystick inputs. This provides
the same benefits as using a macro for constants: the code is more readable
and maintainable. A team's define list for a tank-like drive system could look
like the following:

    
    
    #define LEFT_MOTOR_PWM        pwm01
    #define RIGHT_MOTOR_PWM       pwm02
    
    #define LEFT_MOTOR_CONTROL    p1_y
    #define RIGHT_MOTOR_CONTROL   p2_y
    

This could then be used in the user_routines.c file with the following
function:

    
    
    void Process_Data_From_Master_uP(void)
    {
      Getdata(&rxdata);   /* Get fresh data from the master microprocessor. */
      
      LEFT_MOTOR_PWM = LEFT_MOTOR_CONTROL;
      RIGHT_MOTOR_PWM = RIGHT_MOTOR_CONTROL;
      
      Generate_Pwms(pwm13,pwm14,pwm15,pwm16);
      
      Putdata(&txdata);     /* DO NOT CHANGE! */
    }
    

By using macros, any programmer reading this function can easily tell that the
left motor is being assigned to the left motor controller, and the right motor
is being assigned to the right motor controller.

In addition to being easier to understand and more readable, this code is also
more maintainable. For example, if a team wanted to change the primary input
device from two joysticks to one XBox 360 controller using a [USB
chicklet](/index.php?title=USB_chicklet&action=edit "USB chicklet" ), normally
the programmers would need to change every instance of p2_y to p1_x in the
code, but using macros, they would only need to change one line of code in the
defines list:

    
    
    #define RIGHT_MOTOR_CONTROL   p2_y
    

would change to

    
    
    #define RIGHT_MOTOR_CONTROL   p1_x
    

[[edit](/index.php?title=Writing_macros&action=edit&section=5 "Edit section:
External Links" )]

## External Links

  * [Wikipedia Entry](http://en.wikipedia.org/wiki/C_preprocessor "http://en.wikipedia.org/wiki/C_preprocessor" )

Retrieved from "<http://www.firstwiki.net/index.php/Writing_macros>"

##### Views

  * [Article](/index.php/Writing_macros)
  * [Discussion](/index.php/Talk:Writing_macros)
  * [Edit](/index.php?title=Writing_macros&action=edit)
  * [History](/index.php?title=Writing_macros&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Writing_macros)

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

  * [What links here](/index.php/Special:Whatlinkshere/Writing_macros)
  * [Related changes](/index.php/Special:Recentchangeslinked/Writing_macros)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Writing_macros&printable=yes)
  * [Permanent link](/index.php?title=Writing_macros&oldid=60352)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 02:51, 10 May 2007.
  * This page has been accessed 1,442 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

