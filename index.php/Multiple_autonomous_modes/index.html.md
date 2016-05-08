# Multiple autonomous modes

### From FIRSTwiki

Jump to: navigation, search

**Multiple autonomous modes** can sometimes be better than a single [autonomous mode](Autonomous_mode "Autonomous mode" ). Having a variety of options gives the robot the ability to change its strategy based on who the [alliance partner](/index.php?title=Alliance_partner&action=edit "Alliance partner" ) and [opposing alliance](/index.php?title=Opposing_alliance&action=edit "Opposing alliance" ) are. For instance, in the 2004 game [FIRST Frenzy: Raising the Bar](FIRST_Frenzy:_Raising_the_Bar "FIRST Frenzy: Raising the Bar" ), a robot might have an autonomous mode to track the [IR beacon](IR_beacon "IR beacon" ) and knock down the "10 point ball" and another mode to travel forward at full speed and block the opposing alliance member from knocking over the ball. Both modes, obviously, would be useful depending on the circumstances of the match. There are disadvantages to having multiple autonomous modes, however. It means more code, which will take longer to [program](Programming "Programming" ), and it means less time to test each individual autonomous mode. Both of these introduce the chance for more errors. But, despite the disadvantages, there are certainly many circumstances where having multiple autonomous modes is extremely useful. 

The main tasks involved with creating muliple autonomous modes are:

  * Selecting which autonomous mode to run 
  * Creating each autonomous mode 

This article will focus on the infrastructure involved to select and run
multiple autonomous modes, and leaves the programming of each autonomous mode
up to you.

## Contents

  * 1 Selecting which autonomous mode to run
    * 1.1 Read and evaluate the input
    * 1.2 Differentiate between autonomous modes
  * 2 Resources  
---  
  
[[edit](/index.php?title=Multiple_autonomous_modes&action=edit&section=1 "Edit
section: Selecting which autonomous mode to run" )]

## Selecting which autonomous mode to run

Having multiple autonomous modes is useless if there is no method to select
between them. This can be as simple as a
[switch](/index.php?title=Switch&action=edit "Switch" ) or
[potentiometer](Potentiometer "Potentiometer" ) on either the
[RC](RC "RC" ) or [OI](OI "OI" ). Since the OI sends
data to the RC before a match starts (while still
[disabled](Disabled "Disabled" )) it is usually the most attractive
choice. This article assumes the selecting mechanism is on the OI. In order to
implement this in the code, follow the following steps.

  1. Read and evaluate the input 
  2. Differentiate between autonomous modes based on input 

[[edit](/index.php?title=Multiple_autonomous_modes&action=edit&section=2 "Edit
section: Read and evaluate the input" )]

### Read and evaluate the input

First, declare the variable and set it to some default value. In
User_Routines_Fast.c, add the following code in the custom variables section.

    
    
     char AutoSelect = 0;  //  Sit still unless some other mode is selected (default action)
    

Next, put the following statement in the files you want to reference the above
variable (e.g., User_Routines.h).

    
    
     extern char AutoSelect;  // This allows the files which include this header to use AutoSelect
    

Now that you have the variable to select between autonomous modes, the next
step is to select the appropriate autonomous mode. In User_Routines.c, add the
following code in the function Process_Data_From_Master_uP().

    
    
     if (!autonomous_mode)
         AutoSelect = SELECT_AUTO_MODE;
    

Remember that the OI does not send any data while in autonomous mode.
SELECT_AUTO_MODE is just a [macro](/index.php?title=Macro&action=edit "Macro"
), defined elsewhere. In some header file that User_Routines.c has access to,
make sure to define SELECT_AUTO_MODE based on how it is selected in your
particular setup. E.g.,

    
    
     #define SELECT_AUTO_MODE (char)((p4_sw_trig<<3) | (p4_sw_top<<2) |  \
         (p4_sw_aux1<<1) | p4_sw_aux2)
    

What this example does is it takes each bit, bit-shifts it up the appropriate
amount, and ORs it with the other bits, generating a number (in this case, 0
to 15 (2^4 - 1). It is designed for a 4 switch setup (ie, there are 4 switches
hooked up to the OI in a custom box. To select a mode, you convert it to
binary, and set the swtiches to a corresponding bit).

Alternately, you can use a function rather than a macro to handle putting the
data into a single variable:

    
    
     if (!autonomous_mode)
         AutoSelect = selectAutoMode();
    

and

    
    
     char selectAutoMode()
     {
          return ((p4_sw_trig<<3) | (p4_sw_top<<2) |  (p4_sw_aux1<<1) | (p4_sw_aux2));
     }
    

[[edit](/index.php?title=Multiple_autonomous_modes&action=edit&section=3 "Edit
section: Differentiate between autonomous modes" )]

### Differentiate between autonomous modes

This can be accomplished in a variety of ways. The simplest is just to have a
[switch](/index.php?title=Switch&action=edit "Switch" ) statement, as follows.
In User_Routines_Fast.c in the function User_Autonomous_Code(), add this code.

    
    
       switch (AutoSelect)
       {
       case 0: 	//  Sit still in auto mode (default action)
            break;
       case 1:
           Auto1();
           break;
       case 2:
           Auto2();
           break;
    

...

    
    
       case N:
           AutoN();
           break;
       default:
           // This shouldn't be reached.  Some error message or action
           // appropriate for your code should go here
       }
    

It is trivial to add as many cases to the switch statement above as is
desired. Obviously, replace _case N:_ with the highest number the code
demands. Again, you'll have to write the various autonomous functions (e.g.,
Auto1()). This is where the action occurs.

_See also:_ [Extern keyword](/index.php?title=Extern_keyword&action=edit
"Extern keyword" ), [Programming](Programming "Programming" ),
[Input](Input "Input" )

[[edit](/index.php?title=Multiple_autonomous_modes&action=edit&section=4 "Edit
section: Resources" )]

## Resources

  * Various [ChiefDelphi](ChiefDelphi "ChiefDelphi" ) discussions ([[1]](http://www.chiefdelphi.com/forums/showthread.php?t=28211 "http://www.chiefdelphi.com/forums/showthread.php?t=28211" ), [[2]](http://www.chiefdelphi.com/forums/showthread.php?t=23519 "http://www.chiefdelphi.com/forums/showthread.php?t=23519" ), [[3]](http://www.chiefdelphi.com/forums/showthread.php?t=28237 "http://www.chiefdelphi.com/forums/showthread.php?t=28237" ) ...) 

Retrieved from
"<http://www.firstwiki.netMultiple_autonomous_modes>"

[Categories](/index.php?title=Special:Categories&article=Multiple_autonomous_m
odes "Special:Categories" ): [How-to](Category:How-to "Category
:How-to" ) | [Programming](Category:Programming
"Category:Programming" )

##### Views

  * [Article](Multiple_autonomous_modes)
  * [Discussion](Talk:Multiple_autonomous_modes)
  * [Edit](/index.php?title=Multiple_autonomous_modes&action=edit)
  * [History](/index.php?title=Multiple_autonomous_modes&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Multiple_autonomous_modes)

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

  * [What links here](Special:Whatlinkshere/Multiple_autonomous_modes)
  * [Related changes](Special:Recentchangeslinked/Multiple_autonomous_modes)
  * [Upload file](Special:Upload)
  * [Special pages](Special:Specialpages)
  * [Printable version](/index.php?title=Multiple_autonomous_modes&printable=yes)
  * [Permanent link](/index.php?title=Multiple_autonomous_modes&oldid=39102)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 01:46, 16 June 2004.
  * This page has been accessed 1,393 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

