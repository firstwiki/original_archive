# PBASIC

### From FIRSTwiki

Jump to: navigation, search

[![BASIC Stamp manual](/media/thumb/d/d0/Basic_stamp_manual_small.png/180px-
Basic_stamp_manual_small.png)](Image:Basic_stamp_manual_small.png
"BASIC Stamp manual" )

[![Enlarge](/skins/common/images/magnify-
clip.png)](Image:Basic_stamp_manual_small.png "Enlarge" )

BASIC Stamp manual

**PBASIC** is the language that was used to [program](Programming "Programming" ) the [Robot Controller](Robot_Controller "Robot Controller" ) for the 2003 season and before. The 2004 season marked a significant switch to the much more sophisticated [C programming language](PIC_C "PIC C" ). While PBASIC is a more simple language, with its limitations, complex robots could still be created. The simple language proved easier for [rookie](/index.php?title=Rookie&action=edit "Rookie" ) teams to learn, and also provided a challenge for [veteran](/index.php?title=Veteran&action=edit "Veteran" ) teams because of the limitations. PBASIC is [Parallax's](Parallax "Parallax" ) version of the Basic programming language, designed for the [BASIC stamp](BASIC_stamp "BASIC stamp" ) (specifically the [BS2sx](BS2sx "BS2sx" ) was used in 2000 and after, while the [BS2](BS2 "BS2" ) was used prior to that). 


## Code Structure

The code structure is markedly different from the [PIC C](PIC_C
"PIC C" ) language. Most important is that the program is a single file, and
only rudimentary functions are possible. Also, basic control structures
produce what is known as _spaghetti code_, due largely to the required use of
_GOTO_ (see below). The basic structure of the program was this: define the
BS2SX, define variables, define aliases, define constants, initialization;
then, loop over the data input, custom code, and data output.

The use of variables was very different on the Stamp. Only 26 bytes of ram
were available (see "Limitations"), and so an elaborate procedure of declaring
certain constants and a long SERIN statement were necessary to read input.
That is, not all the variables in the program could be used, and so the user
had to manually decide which were the most important and then alter the SERIN
statement to meet the specifics of the program.

Also available to the Stamp was 64 bytes of scratchpad memory.

Below is a code sample from the Programming Reference Guide from
[InnovationFIRST](InnovationFIRST "InnovationFIRST" ). It
demonstrates how code typically had to be written.

    
    
    
    '========== PERFORM OPERATIONS ==============================================================
    '---------- Button to Relay -----------------------------------------------------------------
    relay1_fwd = p1_sw_trig 'Port 1 Trigger = Relay 1 Forward
    'relay1_fwd is an Alias to the relayA byte
    '---------- Roller Code ---------------------------------------------------------------------
    if rc_sw1 = 1 then turn_roller_on: 'sw1 = 1 when activated, so goto turn_roller_on
    Roller_Out = 127 'sw1 must be 0, so turn Roller_Out Off (127 is Off)
    Goto exit_roller
    turn_roller_on:
    Roller_Out = rollerSpeed
    exit_roller:
    
    

Midway through the 2003 season, a significant change occurred to the PBASIC
language. Prior, teams were using PBASIC 2.0. Eventually, Parallax released a
long promised alpha and then beta version of PBASIC 2.5, which provided more
advanced features. Most importantly, it provided an _if ... else_ structure,
and allowed for pre-processor directives.


## Limitations

Aside from the nature of the language itself, there were several limitations
that programmers had to deal with. The processor is relatively primitive.
Signed math could not be done, as the processor could not handle negative
numbers (hence the carry over in the 2004 season of using an unsigned int
value from 0 to 254). Further, the processor had no order of operations; so
parentheses had to be used, or unexpected and dangerous errors would occur
(which did sometimes during late night coding sessions). Also, there was only
a limited amount of memory available. The actual code could only occupy 8
blocks of 2k, which meant that programs could only grow so big. The user could
only alter 26 bytes of ram, -- meaning, effectively, that tricks had to be
used, such as [Boolean algebra](/index.php?title=Boolean_algebra&action=edit
"Boolean algebra" ), to minimize the use variables. The careful programmer
could utilize unused switch combinations to decrease the amount of memory
necessary, overload certain bytes to have different uses at different places
in the code, and swap variable values without a temporary variable. However,
it was not for the faint of heart -- and these limitations, though
challenging, caused the switch to the [C programming
language](PIC_C "PIC C" ) for the [2004 Robot
Controller](Robot_Controller_%282004%29 "Robot Controller \(2004\)"
). It was simply too primitive to easily handle advanced [autonomous
modes](Autonomous_mode "Autonomous mode" ), which were introduced
during the 2003 season. Though some teams created quite effective autonomous
modes, they almost always used a secondary processor.

  
The [BS2sx](BS2sx "BS2sx" ) was just an extension to the
[BS2](BS2 "BS2" ). The BS2 was about 4x slower and didn't have any
scratchpad or seperate code banks (so you were limited to 2k).


## Resources

  * [IFI Legacy documentation](http://innovationfirst.com/FIRSTRobotics/documentation-legacy.htm "http://innovationfirst.com/FIRSTRobotics/documentation-legacy.htm" )
  * [RoboEmu](http://www.robbayer.com/software.htm "http://www.robbayer.com/software.htm" ) and other software by [Rob Bayer](/index.php?title=Rob_Bayer&action=edit "Rob Bayer" )

[![Image:LinkFA-star.png](/media/6/60/LinkFA-star.png)](Image
:LinkFA-star.png "Image:LinkFA-star.png" )

