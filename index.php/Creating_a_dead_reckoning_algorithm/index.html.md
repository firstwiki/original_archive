# Creating a dead reckoning algorithm

### From FIRSTwiki

Jump to: navigation, search

A [dead reckoning](/index.php/Dead_reckoning "Dead reckoning" ) algorithm is
the simplest and quickest to implement type of autonomous control for a robot
to implement. The robot does not use any sensory input and simply follows a
predefined set of "directions" stored as hardcoded (or in
[ROM](http://www.wikipedia.org/wiki/ROM "wikipedia:ROM" )) values. This is a
good, simple autonomous program for novice robot programmers to start with
because of its simplicity.

## Contents

  * 1 Intoduction
    * 1.1 Functional requirements
    * 1.2 Mechanical systems
    * 1.3 Controller quirks
  * 2 The code begins
    * 2.1 Aliases
    * 2.2 Autonomous code
      * 2.2.1 The basic setup
      * 2.2.2 Moving Forward
      * 2.2.3 Spinning Clockwise
    * 2.3 Incrementing timer
    * 2.4 Timing
  * 3 Next Steps
    * 3.1 Adding other mechanism usage to this dead reckoning program
    * 3.2 Limitations
  * 4 Conclusion  
---  
  

## Intoduction

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=2 "Edit section: Functional requirements" )]

### Functional requirements

The very first thing to do when creating a Dead Reckoning Algorithm is to
decide exactly what the robot should do. Often, it is easy to sum this up as a
short list of commands. Here is the list that we will use for the example
program:

  * Go forward fifteen feet 
  * Turn left 45 degrees 
  * Go forward for eight seconds 
  * Spin clockwise pi radians (180 degrees) 

This is a fundamental step in the creation of your dead reckoning algorithm.
The goal of this excercise is to make your dead reckoner match these steps as
closely as possible. Unless you already know *exactly* how fast your robot
will be able to accelerate, what it's top speed is, etc. these steps will
almost certainly end up being altered later, but for now they will give us our
baseline for the program.

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=3 "Edit section: Mechanical systems" )]

### Mechanical systems

FIRST Robots are very diverse, meaning that control algorithms are never
universal. The most common drive train system, however, is what is known as
the [skid steer](/index.php/Skid_steer "Skid steer" ). Essentially, this means
that each side of the robot (left and right) are independently controlled. You
have one or more motors driving the left side, and a mirror system driving the
right side.

For this algorithm we will be working with a setup that only includes one
motor per side.


### Controller quirks

The [Victor 884](/index.php/Victor_884 "Victor 884" ) receive signals from the
[Robot Controller](/index.php/Robot_Controller "Robot Controller" ) via [PWM
signals](/index.php/PWM_signal "PWM signal" ). These allow the Robot
controller to pass values between 0 and 254 to the speed controller. PWM
values are stored in 8-bit `unsigned char` so they are limited to values from
0-255, but note that using value of 255
["resets"](/index.php?title=Resetting_Victors&action=edit "Resetting Victors"
) the Victor and should not be used.

Also note that on the victor 884 controllers, 0-37 is full reverse, 123-136 is
neutral, and 227-254 is full forward.

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=5 "Edit section: The code begins" )]

## The code begins

**Note:** From this point forward I will be assuming that the reader has basic familiarity with the C Language. Anyone on the team can develop the functional requirements, but the programmers job really takes off here. 


### Aliases

Aliases should probably be placed at the beginning of the `user_routines.h`
file. Note that they _should not_ be in `ifi_aliases.c` as it always
recommended _not_ to touch the required IFI code.

These lines begin with a hash sign (#). This marks them as
[preprocessor](http://www.wikipedia.org/wiki/preprocessor
"wikipedia:preprocessor" ) directives. Note that these lines do not end with a
semi-colon like normal C code.

    
    
    #define pwm1 LMotor
    #define pwm2 RMotor         /* PWM switchboard; Change aliases to match your setup */
     
    #define FullForward 254
    #define Neutral 127
    #define FullReverse 0          /* Basic Constants */
    


### Autonomous code

The default Autonomous routine is found in `user_routines_fast.c` and looks
like this:

    
    
    void User_Autonomous_Code(void)
    {
      while (autonomous_mode)   /* DO NOT CHANGE! */
      {
        if (statusflag.NEW_SPI_DATA)      /* 26.2ms loop area */
        {
            Getdata(&rxdata);   /* DO NOT DELETE, or you will be stuck here forever! */
            /* Add your own autonomous code here. */
            Putdata(&txdata);   /* DO NOT DELETE, or you will get no PWM outputs! */
        }
      }
    }
    

Things to notice:

  * Don't change the name of the autonomous code function itself unless you plan to change it in main.c also. This is _not_ recommended. 
  * Autonomous mode occurs inside it's own while loop. The input and output has to be run inside this loop, or you will stay in autonomous mode forever. If GetData(&amp;rxdata) is never called, the autonomous_mode flag will never be unset! By the same token, one can adjust PWM values, but if Putdata(&amp;txdata) is never called, then updated PWM values will not be sent to the [master processor](/index.php/Master_processor "Master processor" ) and consequently not be outputted on the PWM pins. Make sure you don't remove those two statements! 

Now on to the really interesting part!

    
    
     /* Add your own autonomous code here. */
    

Time to start making the autonomous mode!

The basic design of a simple autonomous mode is this: Each step in the code
detailed in your functional requirements translates to a step of the program.
We will start by working exclusively with the drive train, not any other
mechanisms (arms, flippers, etc.) So, our list of directions might be
something like this:

  * Step 0: Forward 10 feet 
  * Step 1: Spin Clockwise 45 degrees 
  * Step 2: Forward 6 feet 
  * Step 3: Spin counter-clockwise 90 degrees 
  * Step 4: Forward 8 feet 
  * Step 5: Stop 

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=8 "Edit section: The basic setup" )]

#### The basic setup

We'll need a few variables:

    
    
    unsigned int step = 0;    /* This holds data indicating which step of the routine we are in. */
    unsigned long timer = 0;  /* This holds data indicating how many cycles the processor has run in the current step. 
                             Note that these are processor cycles, or roughly 26.2ms */
    

These are probably best inserted into the default code in user_routines_fast.c
file, just after the line

    
    
    /*** DEFINE USER VARIABLES AND INITIALIZE THEM HERE ***/
    

You also need to initialize them every time you go into autonomous. So scroll
down to

    
    
    void User_Autonomous_Code(void)
    

And right under the brace (`{`), but before the while, insert the lines

    
    
     step = 0;
     timer = 0;
    

This way, they are initialized every time you go into autonomous.

The basic control structure we want to use is the `switch` statement.

    
    
    switch (step)
    {
      case 0:
       // Step 0: Go forward
       break;
     
      case 1:
       // Step 1: turn clockwise
       break;
     
      case 2:
       // Step 2: Go forward
       break;
     
      //...
      //... etc...
      //...
    }
    

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=9 "Edit section: Moving Forward" )]

#### Moving Forward

So, on the first run through of this code, the _step_ variable is zero, so it
will execute commands in case zero. We want it to go forward, so, according to
the [skid steer](/index.php/Skid_steer "Skid steer" ) model, we need to set
both the left motor and right motor to full forwards. In C code, that is...

    
    
     LMotor = FullForward;
     RMotor = FullForward;
    

That's it! Now your robot is going forward! There is, of course, one problem.
It doesn't stop. At least, not while autonomous mode is on. It's time to use
that _timer_ variable we made. The intended result: After a certain time
period, go on to the next step. As long as we're at it, we can reset the timer
so that it starts out at zero for the next step. With this added, the code for
step 0 starts to look like this:

    
    
      case 0:
       /*Step 0: Go forward */
       LMotor = FullForward;
       RMotor = FullForward;
       if (timer >= 400)
       {
        step++;
        timer = 0;
       }
       break;
    


#### Spinning Clockwise

Let's spin clockwise! With skid steering, to spin clockwise, or to the right,
with a minimum turning radius, the left motor should be directed forward while
the right motor should be reversing with the same power. In C...

    
    
       LMotor = FullForward;
       RMotor = FullReverse;
    

Next, we give this the same treatment that we gave step zero, and it comse out
looking like...

    
    
      case 1:
       /*Step 1: Spin Clockwise */
       LMotor = FullForward;
       RMotor = FullReverse;
       if (timer >= 400)
       {
        step++;
        timer = 0;
       }
       break;
    

Put it together, and you get

    
    
    switch(step)
    {
      case 0:
       /*Step 0: Go forward */
       LMotor = FullForward;
       RMotor = FullForward;
       if (timer >= 400)
       {
        step++;
        timer = 0;
       }
       break;
     
      case 1:
       /*Step 1: Spin Clockwise */
       LMotor = FullForward;
       RMotor = FullReverse;
       if (timer >= 400)
       {
        step++;
        timer = 0;
       }
       break;
     
    ... etc. ...
    }
    

I leave filling in the remainder of the code as an excercise for the reader.
(YOU do steps 2-5)

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=11 "Edit section: Incrementing timer" )]

### Incrementing timer

While this is small, it is vital. With out incrementing `timer`, your code
would never go anywhere!

Don't worry, it's quite simple. This is the `if` block

    
    
        if (statusflag.NEW_SPI_DATA)      /* 26.2ms loop area */
        {
            Getdata(&rxdata);   /* DO NOT DELETE, or you will be stuck here forever! */
            switch(step)
            {
             //A whole lot of stuff here
            }
            timer++; //VERY VERY IMPORTANT!!!
            Putdata(&txdata);   /* DO NOT DELETE, or you will get no PWM outputs! */
        }
    

You can see where the increment was inserted.

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=12 "Edit section: Timing" )]

### Timing

There's still one thing fundamentally wrong with our autonomous code. So far,
for the timer values, we've just thrown in the value 400. This is, in almost
absolute certainty, not going to make the robot go forward anything near 10
feet or spin clockwise 45 degrees.

It's time for an application of the classic problem solving technique of
_Guess &amp; Check_. Put any values that you think are reasonable into place
instead of those 400s. Download the code into your robot, set it into
autonomous mode with a [Competition port
dongle](/index.php/Competition_port_dongle "Competition port dongle" ), and
see what it does. If it goes too far, take some cycles off the appropriate
timer. If it doesn't spin enough, on that spin timer add a few extra cycles.
The idea here is to just play with it until you get it right!


## Next Steps

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=14 "Edit section: Adding other mechanism usage to this dead reckoning
program" )]

### Adding other mechanism usage to this dead reckoning program

Coming Soon!

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=15 "Edit section: Limitations" )]

### Limitations

The dead reckoning algorithm described in this article has a few severe
limitations.

  * Lack of Consistency - There are a number of things that make this type of program inconsistent. The most major is battery voltage. A DC Motor's speed is proportional to the voltage given, thus as the voltage of the battery decreases, the motors spin slower, and you don't move as far in each cycle. One way to limit this effect is to do all autonomous testing and competing using a battery that is fully charged at the start of the autonomous mode. Other mechanical factors can influence consistency also, such as chain tension and tire pressure. The other major factor is playing field surface. If the carpet you tested on in your build facility isn't exactly the same as the carpet FIRST uses (or isn't layed down the same way), you will need to tweak your algorithm at the competition (and sometimes between competitions). 
  * Lack of Sensor Input - This is a 'dead reckoner' in the extreme. It doesn't use any kind of sensor to assist in guidance. Sensors help validate that the robot is, in fact, where it is supposed to be, and allow it to correct its behavior accordingly. 
  * Portability Issues - Sure, you could put your program onto another teams robot, but even a slight difference in drive train construction can lead to an autonomous mode disaster! If you are going to put it into a second robot, you are going to have to do all that tedious fine tuning over again. 

[[edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit&secti
on=16 "Edit section: Conclusion" )]

## Conclusion

This is an easy algorithm for a rookie team or a team with limited computer
programming expertise to write and implement, but with it's huge flaws, it is
almost certainly better to use a [line
tracker](/index.php?title=Line_tracker&action=edit "Line tracker" ) or
[infrared](/index.php?title=Infrared&action=edit "Infrared" ) following robot
instead. A [copycat](/index.php?title=Copycat&action=edit "Copycat" ) system
is an improvement on this design, while a guidance system involving
[accelerometers](/index.php/Accelerometer "Accelerometer" ) would be a true
boon to those teams who are capable of implementing it.

Retrieved from
"<http://www.firstwiki.net/index.php/Creating_a_dead_reckoning_algorithm>"

##### Views

  * [Article](/index.php/Creating_a_dead_reckoning_algorithm)
  * [Discussion](/index.php/Talk:Creating_a_dead_reckoning_algorithm)
  * [Edit](/index.php?title=Creating_a_dead_reckoning_algorithm&action=edit)
  * [History](/index.php?title=Creating_a_dead_reckoning_algorithm&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Creating_a_dead_reckoning_algorithm)

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

  * [What links here](/index.php/Special:Whatlinkshere/Creating_a_dead_reckoning_algorithm)
  * [Related changes](/index.php/Special:Recentchangeslinked/Creating_a_dead_reckoning_algorithm)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Creating_a_dead_reckoning_algorithm&printable=yes)
  * [Permanent link](/index.php?title=Creating_a_dead_reckoning_algorithm&oldid=42416)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 03:59, 14 January 2006.
  * This page has been accessed 3,390 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

