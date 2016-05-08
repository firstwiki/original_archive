# Using interrupts

### From FIRSTwiki

Jump to: navigation, search

## Contents

  * 1 Hardware Events
  * 2 Polling vs Interrupts
  * 3 Event Latency
  * 4 Interrupt Latency
  * 5 Interrupt Vectors
  * 6 Interrupt Priority Levels
  * 7 Controlling Interrupts
  * 8 Interrupt Service Routines
  * 9 Interrupt Context
    * 9.1 Hardware Context
    * 9.2 Software (Compiler) Context
  * 10 Accessing Shared Variables
  * 11 PIC18F Interrupts - How They Work
  * 12 PIC18F Hardware Events
  * 13 Example: Timer Interrupts
    * 13.1 Config
    * 13.2 Start
    * 13.3 Stop
    * 13.4 Read
    * 13.5 Write
    * 13.6 ISR
  * 14 Interrupt worthy resources on PIC  
---  
  

## Hardware Events

An executing program often reads input, processes data, and generates output.
It wouldn't be much of a program if it didn't read input or generate output.
On FRC robots, inputs can include pressure switches, gryos, wheel encoders,
and the like. Robot outputs include the motor PWM values, relay controls, etc.
Also, sometimes during program execution unwanted or unexpected things -- like
call stack overflow -- happen. The reading, writing, and unexpected things are
all hardware events that need to be handled in some fashion by the program.

In some cases these hardware events are synchronous with program execution and
other times not.

Overflowing the call stack is an example of a **synchronous event**. The
overflow can only occur while the current instruction stream is attempting to
push yet another return address onto the call stack. The event is synchronous
with the execution of a specific instruction or instruction sequence.

Arrival of the next byte on a serial port is an example of an **asynchronous
event**. The next byte arriving isn't coupled with any specific sequence of
program instructions -- the data arrives when it arrives. Asynchronous events
may be predictable in periodicity, for example the baud rate of the serial
port dictates when the next byte is likely to arrive. However a programmer
while writing the program doesn't know "aha, right here the serial port will
have the next byte available for me so I'll go ahead and read the byte from
the serial port's hardware buffer".

The key concept is that there are hardware events, both synchronous and
asynchronous, that the program needs to service in order for the program to
work well.

_Note:_ some architectures support software event generation such as from
BREAK (breakpoint) or illegal instructions. These software events still are
rooted in the hardware executing the intstruction stream.


##  Polling vs Interrupts

There are two methods of a program servicing events, either by polling or via
interrupts.

`

    
    
    Envision a classroom.  The teacher cannot see very well, so cannot tell when a student
    raises their hand to ask a question.  In order to find out if there is a question, 
    the teach must stop every once in a while and **poll** the class by asking "Any questions?"
    
    Same classroom, but the school has hired an aid.  Part of the aid's job is upon noticing
    that a student has raised their hand to **interrupt** and notify the teacher that there is
    a question pending.
    
    _[Editor] ok, this is a contrived example... but until someone comes up with a better one..._
    

`

One way of dealing with the synchronous stack overflow event is to add code to
check on how full the stack is before doing every function or routine call. It
is easy to see that doing so slows down the execution of the system by
constantly checking for a condition that might occur, but seldom or hopefully
never does.

This is **polling**. Adding code into the program to check for specific
conditions at specific points within the execution flow. In some cases polling
makes sense as it is the most efficient method available. The master processor
on the 2008 robot controller uses polling to service all hardware events. If
fact, the main loop of the master processor is just a small polling loop that
checks the various hardware devices it utilizes to do its job. So, polling
isn't necessarily always bad. It has its place and uses. It is typically used
when

  * the program is always event driven and is idle when not processing a hardware event, or 
  * the program is small enough to be well understood in terms of the program's execution timing and how it dovetails with the various hardware events it needs to handle in order to perform its job, or 
  * the hardware event doesn't happen very often or can wait long periods of time before the event gets handled, or 
  * the hardware event, as in the ADC example below, occurs as a result of some action kicked off by the program and the program is willing to wait for the event. 

  
Another polling example is the standard Microchip analog to digital conversion
(ADC) code.

`

    
    
      ADCON0 = ((channel >> 1) & 0b00111100) | (ADCON0  & 0b11000011);  // select channel to convert
      ADCON0bits.GO = 1                                                 // start conversion
      **while(ADCON0bits.GO)**;                                             // while busy, wait
      adc_result.lo = ADRESL;                                           // Get low byte of ADC result
      adc_result.hi = ADRESH;                                           // Get high byte
      return( adc_result.data );                                        // return 16 bits of result
    

`

In the above example, the **while...** is polling the ADC done flag and is
waiting for the hardware operation to complete. If the program is not time
sensitive or does not perform a lot of analog to digital conversions then
polling can be a viable alternative to interrupts.

The alternative to polling is **interrupts**: the automatic hardware
notification that an event has occurred that needs to be serviced. The results
of this notification is to change the execution flow by re-vectoring the
processor to an appropriate interrupt service handler for that hardware event.

The ADC example helps illustrate why interrupts are often preferred over
polling. While the program is executing the **while...** above, it cannot do
anything else. Its wasting valuable execution time that could be used for
doing other useful work.

The alternative to spinning and waiting for the event to occur is to continue
to do other work and occassionally check back on the ADC done flag to see if
the results are ready yet. This works well for things like ADC hardware where
only one conversion will be performed until the program chooses to start
another one. But this type of polling behavior doesn't work well for some
hardware such as serial ports. For this type of hardware event, if the program
doesn't service the event quickly enough then data associated with the event
can be lost. With a serial port, the next arriving byte can overwrite the
previous byte if the program doesn't service the event quickly enough. The
time span between hardware events is sometimes refered to as **event latency**
\- how long can the event sit there not being serviced before information
associated with the event is lost or corrupted.


## Event Latency

The latency of an event is the minimum time between two hardware events from
the same hardware. The event latency for serial port set to 115k baud, with 1
start bit and 1 stop bit is about 90usec. The event latency for the Gear Tooth
Sensor from 2007 was less than 40usec. The inverse of event latency is the
maximum number of interrupts per second possible for a given piece of
hardware.


## Interrupt Latency

Interrupt latency is the time it takes between when notification of a hardware
event has occurred until the program is able to service that event. If
interrupt latency is too long, then data associated with the interrupt may be
lost. For example, the gear tooth sensor from 2007 has 45usec pulse when the
gears were turned one way and a 90usec pulse the other way. If interrupt
latency was too long, then the code servicing the hardware event could not
reliably tell which way the robot was moving.

Interrupt latency is comprised of several components:

  * external hardware notification delays, nominally close to 0us for most hardware, 
  * processor hardware delays, 
  * interrupt vector code, 
  * interrupt service program context save/restore, 
  * determination of which interrupt to service, and 
  * interrupt servicing code. 

The PIC18F processor hardware delay is 2-3 instruction cycles. This latency is
independent upon whether a one or two cycle instruction is being executed.

The nominal interrupt latency is measured when no interrupt is currently being
serviced. The worse case latency often will occur as a result of an interrupt
already being serviced. This is because the interrupts are turned off while
the current hardware event causing the interrupt is being serviced.

The interrupt vector code latency (execution path length), is normally 3
instruction cycles -- the amount of time needed to execute a two instruction
cycle GOTO. On FRC robots however, a double jump is required because the first
0x800 instruction locations hold the boot loader code. Therefore on FRC robots
the interrupt vector code latency is typically 6 instruction cycles.

`

    
    
     0000: GOTO 0x800               // reset vector
     :
     0008: GOTO 0x808               // high priority interrupt vector
     :
     0018: GOTO 0x818               // low priority interrupt vector
     :
     .
     0800: GOTO _startup            // C startup, initialization before calling main()
     :
     0808: GOTO InterruptHandlerHigh
     :
     0818: GOTO InterruptHandlerLow
    

`

Since the hardware is shared between the user code and interrupt code, the
interrupt service routines must save and restore processor context. If you
didn't do this, then the user code will fail in unusual and spectacular ways.
The amount of latency contributed by this context save can be as little as
1-2usec or as much as 100us or more.

The interrupt dispatching code (code that polls all the hardware events to see
which one is requesting service), can take between 1us-10us depending on how
many different hardware events are polled and how they are polled.

The interrupt servicing code that deals with the specific hardware event can
be as few as .1us to as much as several 100us depending on the device
complexity. The majority of hardware "drivers" have an average code path of
10-20 instructions or 1-2us.


## Interrupt Vectors

Most processors have multiple interrupt vectors. An interrupt vector is either
assigned to a particular piece of hardware or hardware event as part of the
architecture or assigned via software. The processor then "vectors" through
that location to the event service routine.

The PIC18F only has three interrupt vectors,

  * processor reset vector, address 0x000 
  * high priority interrupt vector address 0x008, and 
  * low priority interrupt vector, address 0x018. 

The processor upon power up, is forced to start execution at location 0x000.

The high priority interrupt vector is reserved for the FRC robot's interrupt
routine that is in charge of exchanging data with the master processor.

The low priority interrupt vector is available for team use on the FRC robot
platform.

  


## Interrupt Priority Levels

Most hardware events can be assigned to one of several interrupt priority
levels. Typical systems have 8, 16, or more interrupt priority levels.
Different events have different priorities and as assigned to higher or lower
priority levels depending on a number of factors. If while executing an event
at a specific interrupt priority and another higher priority event occurs,
then the higher priority event handler is run.

On the FRC robot, only the low priority interrupt vector is available to
teams. The high priority interrupt routine is assigned to the interprocessor
housekeeping service routine. This routine uses the SPI serial bus as the
hardware communication pathway between the master and user processors within
the robot. While the team written low priority interrupt service handler is
running, the high priority interrupt routine can suspect it and take the
processor over.

Although there is only 1 priority level interrupt available for general team
use, it is possible to simulate other interrupt levels through the use of
software.


## Controlling Interrupts

To control interrupts on the PIC18F, the following three hardware control
flags are utilized for each hardware event:

  * IP, interrupt priority (must be set to low priority for all team hardware serviced events), 
  * IE, interrupt enable which enables notification of an interrupt, and 
  * IF, interrupt flag which is set requesting service for some specific piece of hardware. 

Note that the IF associated with a hardware event is ALWAYS set, indepent of
whether the IE is set or not. This allows polling of service requests. If the
IE is set, then the IF must be cleared within the interrupt service routine
otherwise once interrupts are turned back on at the end of current interrupt
processing another interrupt delivery will occur.

Not clearing the IF flag within the service routine is a common cause of the
RLOD.


## Interrupt Service Routines

Interrupt service routines (ISR) are the routines and functions that handle a
given hardware event request for service. For example, a serial port recieve
ISR might copy the new input byte into a circular fifo that the user program
can read, if or when needed.

If there are multiple hardware events assigned to the same interrupt vector,
as in the PIC18F, then the first portion of code that must be executed is code
that polls all the different hardware devices to see which one or ones
requested servicing. Both the interrrupt enable (IE) and interrupt flag (IF)
must be set to indicate that this particular hardware device requested
service. It is possible that the user code was polling the same interrupt and
happened to be clearing the IF at the same time as it was being set. The
result could be "phantom" interrupts. That is, the interrupt dispatch code
that polls all the hardware events find no pending service requests. This is
unusual, but not necessarily unexpected.

The ISR for a particular hardware device can also be referred to as the
hardware driver.


## Interrupt Context

The interrupt service routine and user code share the same hardware as well as
ram (variable) space. The ISR is essentially executed asychronously as needed
and often is referred to as executing in the **background**. The user code, in
this type of model, is said to be running in the **foreground**. The point is
that the ISR execution is on the same hardware that is running the user code.

There are both hardware and software information in registers and/or ram that
must not be changed by the ISR. If these registers were to change, upon
returning to the interrupted user code erroneous operation could occur and
cause the dreaded red-light-of-death (RLOD) that halts the robot. The way for
ISRs to peacefully coexist with the user code that is running is to save
processor registers when the ISR is started, and to restore the processor
registers before exiting the ISR. This saving and restoring of registers is
called saving/restoring **context**.

But what is context?

` Context example:

    
    
     You are making yourself a PBJ sandwich.  In the middle of putting peanut butter on the bread, you are gently 
     reminded - again - to take out the garbage.  Not wanting yet another reminder later and afraid you will forget
     again you stop and take out the garbage.  Upon returning to making the sandwich, you continue where you left off.
    

`

The context in the above example is all the materials you had for your
sandwich and where in the process you were in making the sandwich. If you
hadn't "saved context", then you would start the whole process of making a
(new) sandwich over again. If as part of taking out the garbage you had to
make sure all the kitchen counters were clean and you did just that --
including throwing away the partially made sandwich and putting the knife in
the dishwasher -- this would certainly seem like an unreasonable thing to do.
Yet the same thing can and does happen on the processor since it is sharing
the equivalent of PBJ, bread, knife, etc. with the user code.

A real example. The user code is using the PRODH/PRODL (multiplier product
high/low results registers) as part computing the index into a data array.
After the multiplication, but before the user program is able to retrieve the
results an interrupt occurs. The interrupt service routine calls an often
called function that returns an _int_ value. The C compiler uses the
PRODH/PRODL hardware registers for returning _int_ return values from a
function. If the interrupt routine didn't save this set of hardware registers,
then upon returning to user code... the user code continues (it doesn't know
its been interrupted). It retrieves the value from PRODH/PRODL register and
adds it to the base of the data array. It writes information to that data
array location. Where it actually wrote the data is anyone's guess as the
PRODH/PRODL essentially had random data in it left over from the interrupt
service routine.

There are two types of context that must be saved; hardware and software. Not
all of the context must be saved all the time. The amount of context
information is variable depending on what is needed or used by the various
hardware drivers in the system. Some systems such as EasyC which can accept
any driver, must save a full context. The full context can add 100usec or more
to interrupt latency.

Analysis of the drivers and other ISR code that will be run is often needed to
craft the minimum set of registers to include within the context save/restore.

_NOTE:_ Optionally saved context is done by the C compiler via use of the
#pragma statement. See the MCC C18 manuals for more details. The V2.4 compiler
requires users to specify which registers to **ADD** to the saved context. The
V3.0+ versions of the compiler requires users to specify which registers to
**REMOVE** from the saved context.

[[edit](/index.php?title=Using_interrupts&action=edit&section=10 "Edit
section: Hardware Context" )]

### Hardware Context

The following table shows the typical hardware registers (SFR - special
function registers) that may need to be saved as part of interupt context:

`

    
    
     PC<24>        saved automatically on the 32 entry deep address stack
     W             working register, automatically saved in context save pre-amble by the C compiler
     BSR           bank select register, automatically saved in context save pre-amble created by the C compiler
     STATUS        status (zero result, etc.) register, automatically saved
     FSR0          ram register indirection (hold computed ram addresses), automatically saved
     FSR1          ram register indirection #1, used by the compiler for a variable stack - automatically saved
     FSR2          ram register indirection #2, used by the compiler for a frame pointer into the stack - automatically saved
     PRODH/PRODL   multiplier product (result) registers, optionally saved
     PCLATU/PCLATH program counter (PC) latch registers, used when computing jumps to dynamic functions (*function()), optionally saved
     TBLPTR        table pointer register, used for rom lookup and other program memory access, optionally saved
     TBLAT         table data latch, used for rom lookup and other program memory access, optionally saved
    

`

Let us say that the PCLAT registers are not saved, but one of the drivers
indirectly uses these due to a computed function invocation... say something
like *(registered_event_timer_1)(). These computed function calls occur very
infrequently in user code. The result is that most of the time the robot will
run just fine without problems, but eventually bad things will happen. The
timing window where bad things happen is small but will be hit eventually
given enough time. The problem occurs when the user is in the middle of a
computed function call and has loaded say PCLATH but not the final PCLAT byte
of the new program counter. An interrupt occurs, changes PCLATH, and returns.
The user code loads PCLAT and jumps... somewhere in code. Typically this
causes erratic robot behavior shortly before the RLOD or a robot reset (that
is execution ends up looping into the 0x0000 reset vector).

  

[[edit](/index.php?title=Using_interrupts&action=edit&section=11 "Edit
section: Software \(Compiler\) Context" )]

### Software (Compiler) Context

In addition to the hardware registers that need to be saved, there are
compiler temporary data variables that could need to be saved. The temporary
data is gathered into two named sections within ram, **.tmpdata** and
**MATH_DATA**. See the compiler manuals as to when and where these are used.
Both are optionally saved.

_NOTE:_ MCC V3.0+ supports creation of a separate .tmpdata section for
interrupt routines. See the compiler manuals for more details. This allows
code that uses .tmpdata to be used within an ISR without having to save the
user's separate .tmpdata variables.

[[edit](/index.php?title=Using_interrupts&action=edit&section=12 "Edit
section: Accessing Shared Variables" )]

## Accessing Shared Variables

Some data or data structures are by necessity shared between user code and
ISRs. For example, if the robot has an encoder driver installed then the
encoder counts are typically written/updated in the driver and read in user
code.

The PIC18F is has an 8 bit (byte) data path. If a shared variable is a single
byte, then reading or writing that variable is an **atomic** action. An atomic
action is one that cannot be interrupted and therefore maintains the variable
integrity. How can a shared variable not have integrity?

Assume we have user code that is reading a 4 byte encoder count variable. The
code reads low to high bytes. The current value is 0x000040FF. After reading
the lowest byte of 0xFF an encoder interrupt occurs. The interrupt code bumps
the counter value to 0x00004100 and returns to the user code. The user code
continues execution and reads the 2nd through 4th bytes. The encoder value it
has read is 0x000041FF - not even close to the real value.

This type of issue can occur when the user code is writing and the ISR is
reading the shared variables. So, variables requiring multiple instructions to
access -- essentially anything more than 1 byte -- probably needs addtional
code to force the access to be atomic. But how? The easiest way is to disable
interrupts, either all low priority interrupts or just the interrupt for the
driver that accesses the shared variable. In this way, the read or write
access becomes atomic -- no other code can run that will change the value in
mid-access.

**NOTE:** There is another method that is sometimes used. It doesn't create an atomic access, but recognizes when a shared access collision between user and interrupt code has occurred. It typically only works with counters that are monotonically increased and/or decreased. It is especially useful for functions that could be called in a tight loop waiting for a specific value to be reached by a multi-byte counter. What the code does is read the variable once, and then reads the lower byte one more time and compares it to the value of the lower byte previously read. If they are the same, then the read value should be ok. If the lower bytes differ, then an interrupt has occurred and the code needs to read the variable again. In the vast majority of cases, the variable will be fine and the code didn't have to turn off interrupts and thus didn't effect latency. 

  

[[edit](/index.php?title=Using_interrupts&action=edit&section=13 "Edit
section: PIC18F Interrupts - How They Work" )]

## PIC18F Interrupts - How They Work

When hardware sets the IF and the IE for the same hardware event has been
previously enabled, then the processor performs the following actions:

`

    
    
     1 -> IF                           ; a hardware event is signaled
     :                                 ; 2-3 instruction cycle processor hardware logic delay
     0 -> GIEL or GIEH                 ; turn off the appropriate interrupt
     push PC -> top of stack           ; save the current user program counter
     0x0008 | !IP<<4 -> PC             ; so for high priority, address 0x0008 / for low 0x0018
     0x00x8 GOTO executed              ; execute jump around boot block
     0x08x8 GOTO executed              ; execute jump to actual interrupt handler
    

`

This disregards the possible use of shadow registers associated with high
priority interrupts for simplification.

At the end of the ISR, a RETEI (return from exception interrupt) restores the
user's PC from the stack and re-enables interrupts.

An example of a typical low priority interrupt handler follows, including the
C compiler added code specific to ISRs:

`

    
    
     InterruptHandlerLow:
                                               ; context save...
          MOVFF STATUS, PREINC1                ; compiler added, STATUS -> +(SP)
          MOVFF BSR   , PREINC1                ; compiler added, BSR    -> +(SP)
          MOVWF         PREINC1                ; compiler added, W      -> +(SP)
          MOVFF FSR2  , PREINC1                ; compiler added, FP     -> +(SP)
          MOVFF FSR0  , PREINC1                ; compiler added, FSR0   -> +(SP)
          ...                                  ; compiler added, other pragma controlled context saved here
          
          if (<event>.IF && <event>.IE)
          {
              <event>.IF = 0;
              <event>ISR();
          }
          else if (event2.IF && <event>.IE)
          {
              <event>.IF = 0;
              <event>ISR();
          }
          else if ...
          
                                               ; context restore...
          ...                                  ; compiler added, other pragma controlled context restored here
          MOVFF FSR0  , PREINC1                ; compiler added, FSR0   -> (SP)-
          MOVFF FSR2  , PREINC1                ; compiler added, FP     -> (SP)-
          MOVWF         PREINC1                ; compiler added, W      -> (SP)-
          MOVFF BSR   , PREINC1                ; compiler added, BSR    -> (SP)-
          MOVFF STATUS, PREINC1                ; compiler added, STATUS -> (SP)-
          RETEI                                ; return to user, turn back on interrupts
    

`

[[edit](/index.php?title=Using_interrupts&action=edit&section=14 "Edit
section: PIC18F Hardware Events" )]

## PIC18F Hardware Events

The following table lists some of the most common hardware events that a team
might write a driver for. The INT0 and INT1 interrupts are currently reserved
for use witin the robot hardware. INT0 is used to synchronize the start of a
rx/tx data packet transmission between the master and user processors.

A few of the interrupts can configured to interrupt either on a leading
(lo-&gt;hi) or trailing (hi-&gt;lo) signal transitions as noted in the _EDGE_
column.

See the PIC18F reference manual for more information on each of these
interrupts.

_NOTE:_ EasyC &amp; WPILIB supports user written interrupt device drivers for
INT2, INT3, and INTB (INT4-7) only.

  
`

    
    
    Interrrupt	IP			IE		IF		EDGE
    INT0		<high>  		INTCON.INT0IE	INTCON.INT0IF	INTCON2.INTEDG0 
    INT1		INTCON3.INT1IP		INTCON3.INT1IE	INTCON3.INT1IF	INTCON2.INTEDG1 
    INT2		INTCON3.INT2IP		INTCON3.INT2IE	INTCON3.INT2IF	INTCON2.INTEDG2  
    INT3            INTCON2.INT3IP		INTCON3.INT3IE	INTCON3.INT3IF	INTCON2.INTEDG3
    INTB		INTCON2.RBIP		INTCON.RBIE	INTCON.RBIF	-
    TMR0		INTCON2.TMR0IP		INTCON.TMR0IE	INTCON.TMR0IF
    TMR1		IPR1.TMR1IP		PIE1.TMR1IE	PIR1.TMR1IF
    TMR2		IPR1.TMR2IP		PIE1.TMR2IE	PIR1.TMR2IF
    TMR3		IPR2.TMR3IP		PIE2.TMR3IE	PIR2.TMR3IF
    TMR4	        IPR3.TMR4IP		PIE3.TMR4IE	PIR3.TMR4IF
    ADC		IPR1.ADIP		PIE1.PSPIE	PIR1.ADIF
    RC1		IPR1.RC1IP		PIE1.RC1IE	PIR1.RC1IF
    TX1	    	IPR1.TX1IP		PIE1.TX1IE	PIR1.TX1IF
    RC2	    	IPR3.RC2IP		PIE3.RC2IE	PIR3.RC2IF	
    TX2		IPR3.TX2IP		PIE3.TX2IE	PIR3.TX2IF
    EEPROM		IPR2.EEIP		PIE2.EEIE	PIR2.EEIF
    PSP		IPR1.PSPIP		PIE1.PSPIE	PIR1.PSPIF
    SSP1		IPR1.SSP1IP		PIE1.SSP1IE	PIR1.SSP1IF
    BCL1		IPR2.BCL1IP		PIE2.BCL1IE	PIR1.BCL1IF
    SSP2		IPR3.SSP2IP		PIE3.SSP2IE	PIR3.SSP2IF
    BCL2		IPR3.BCL2IP		PIE3.BCL2IE	PIR2.BCL2IF
    CCP1		IPR1.CCP1IP		PIE1.CCP1IE	PIR1.CCP1IF
    CCP2		IPR2.CCP2IP		PIE2.CCP2IE	PIR2.CCP2IF
    CCP3		IPR3.CCP3IP		PIE3.CCP3IE	PIR3.CCP3IF
    CCP4		IPR3.CCP4IP		PIE3.CCP4IE	PIR3.CCP4IF
    CCP5		IPR3.CCP5IP		PIE3.CCP5IE	PIR3.CCP5IF
    OSC		IPR2.OSCFIP		PIE2.OSCFIE	PIR2.OSCFIF
    CMP		IPR2.CMIP		PIE2.CMIE	PIR2.CMIF
    HLVD		IPR2.HLVDIP		PIE2.HLVDIE	PIR2.HLVDIF
    

`

[[edit](/index.php?title=Using_interrupts&action=edit&section=15 "Edit
section: Example: Timer Interrupts" )]

## Example: Timer Interrupts

When a programmer writes a driver package for a piece of hardware, like one of
the PIC18F timers, the following functions in one form or another are
typically provided.

`

    
    
     Config                        ; configure/initialize/setup the hardware 
     Start                         ; start the hardware running so it generates interrupts
     Stop                          ; stop the hardware from generating interrupts
     Read                          ; read data back from the device
     Write                         ; write or preset variables associated with the device
     ISR                           ; the interrupt service routine that handles the device
    

`

The _config_ routine is used to setup and initialize the hardware. In some
drivers the hardware will be enabled as part of the configuration routine.
This makes sense for the timer1 example used as a system clock. It may not
make sense for something like quadrature encoders.

The _start_ routine is used to start the hardware running. The start routine
results in allowing the hardware device to generate interrupts. The key to
allowing interrupts is to turn on the associated IE for the hardware event.

The _stop_ routine is used to stop the hardware running. The stop routine
results in the hardware no longer being able to generate interrupts. In some
cases the hardware will continue to run and will set its associated IF flag.
This would be the case for quadrature encoders, there is no means to stop the
associated IF from not being set. In the other cases like the user of timer1,
it is possible to stop the IF from being set by turning off the hardware. The
key to disallowing further interrupts is to turn off the associated IE for the
hardware event.

The _read_ routine is used to retrieve data associated with the hardware. In
almost all cases this data with be shared access information. The program must
guarentee atomic access because it is shared access with the ISR routine. For
the timer1 example that is being used as a 1ms system clock, the read data
will be the milliseconds that have elapsed since starting the robot. For a
quadrature encoder, the read data would be the count value representing the
number of ticks that have occurred.

The _write_ routine is used to set or preset data associated with the
hardware. Again, the variables being accessed will almost always be shared
with the ISR so again atomic access must be guarenteed. For the timer1
example, the user may wish to reset the system clock to zero the first time
the robot is enabled as this might represent the start of the competition game
clock.

The final routine is the _ISR_. The ISR is the code that will be run to
service the hardware event.

The PIC18F has a number of different timers. They do not all operate the same
way so the PIC18F user manual should be read carefully. For this example,
timer1 will be used. Timer1 can be configured as either a 8 bit or 16 bit
timer. There are pre-scalers that can be applied and its input clock can be
selected. The timer is basically a counter. Everytime its input clock is
asserted, the timer's counter is incremented. When the timer overflows from
0xFF-&gt;0x00 in 8 bit mode and 0xFFFF-&gt;0x0000 in 16 bit mode, the timer
asserts its IF. Timer1 doesn't stop counting, it keeps counting after the
overflow and will create timer interrupt after timer interrupt everytime it
overflows.

[[edit](/index.php?title=Using_interrupts&action=edit&section=16 "Edit
section: Config" )]

### Config

In this example, timer1 is used as a 1ms system clock. The timer uses the
PIC18F's internal clock and prescales it so that 10,000 clock cycles represent
the passage of 1ms of time. To get an overflow condition after 10,000 cycles
the timer is preset with (0xFFFF-10,000)+1 or 0xD8F0. Since this timer will be
used as the system clock for the robot, the configuration code immediately
after setup, starts the timer. Other hardware devices may or may not immediate
allow the hardware to generate interrupts.

`

    
    
    void SysClock_Config( void )
    {
       T1CONbits.TMR1ON = 0;
       INTTMR1_IP       = 0;               // low priority interrupt assignment
       INTTMR1_IF       = 0;               // clear IF before starting
       
        // Start things up
        TMR1H           = 0xD8;
        TMR1L           = 0xF0;	        // max - 10,000 = overflow @ 1ms
        T1CON           = 0x80;	        // 16bitmode, 1:1 prescale, osc=off, internal clock, tmr disabled
       
        T1CONbits.TMR1ON= 1;		// start sysclock running now
        INTTMR1_IE      = 1;               // Enable interrupts for timer1
    }
    

`

[[edit](/index.php?title=Using_interrupts&action=edit&section=17 "Edit
section: Start" )]

### Start

The start routine is not needed for the system clock, but in case a user would
like to start/stop the system clock they are included to show how it would be
done for a timer.

`

    
    
    void SysClock_Start( void )
    {
        T1CONbits.TMR1ON= 1;	       // start sysclock running
        INTTMR1_IE      = 1;               // Enable interrupts for timer1
    }
    

`

[[edit](/index.php?title=Using_interrupts&action=edit&section=18 "Edit
section: Stop" )]

### Stop

The stop routine is not needed for the system clock, but in case a user would
like to start/stop the clock, an example is included.

`

    
    
    void SysClock_Stop( void )
    {
        T1CONbits.TMR1ON= 0;	       // stop sysclock running...
        INTTMR1_IE      = 0;               // Disable interrupts for timer1
    }
    

`

[[edit](/index.php?title=Using_interrupts&action=edit&section=19 "Edit
section: Read" )]

### Read

Read the current number of milliseconds from the system clock counter. Since
this is a multi-byte variable, interrupts associated with timer1 are disabled
to prevent the value from changing in the middle of this code accessing the
counter.

`

    
    
    unsigned long SysClock_GetMs( void )
    {
    unsigned long tmp;
        INTTMR1_IE      = 0;               // Disable interrupts for timer1
        tmp = sysclock_count;
        INTTMR1_IE      = 1;               // Enable interrupts for timer1
        return(tmp);
    }
    

`

[[edit](/index.php?title=Using_interrupts&action=edit&section=20 "Edit
section: Write" )]

### Write

This routine sets the current system clock to that specified by the user.
Since the counter variable is multiple bytes, interrupts are turned off/on to
guarentee atomic access.

`

    
    
     void SysClock_SetMs( unsigned long ms )
     {
        INTTMR1_IE      = 0;               // Disable interrupts for timer1
        sysclock_count  = ms;
        INTTMR1_IE      = 1;               // Enable interrupts for timer1
     }
    

`

[[edit](/index.php?title=Using_interrupts&action=edit&section=21 "Edit
section: ISR" )]

### ISR

The interrupt service routine handles the hardware event. The code that is
executed within the low priority interrupt handler would need to poll for
timer1 interrupts as follows:

`

    
    
     void InterruptHandlerLow()
     :
     .
     else if (INTTMR1_IF && INTTMR1_IE)
     {
          SysClock_ISR(void);
     }
     :
     .
    

`

The interrupt dispatcher polls all the hardware events. It is looking for
events that have the request service flag (IF) set **AND** have their
interrupt enable (IE) set. Both flags must be set in order for the processor
hardware to be interrupted.

The routine to service timer1 follows. The timer is turned off, the counter
value is reset to overflow-10,000, and the prescaler and other options are
reset including turning the timer back on so it starts the counting again.
Finally the counter associated with the system clock is incremented.

This routine is typical of most device drivers in that it consists of two
parts. The first part is code that services the hardware. It deals directly
with the physical nature of the hardware; reseting the counter and starting it
running again.

The 2nd part of the driver deals with the logical nature of how the device is
being used. In this case the driver is maintaining a counter which holds the
number of 1ms intervals that have elapsed while the timer has been running.

Overall the driver is of small size, which again is typical of most drivers.

`

    
    
    void SysClock_ISR( void )
    {
        INTTMR1_IF       = 0;                 // clear the interrupt flag for this device
        T1CONbits.TMR1ON = 0;                 // reset the timer and re-start it
        TMR1H            = 0xD8;
        TMR1L            = 0xF0;	        
        T1CON            = 0x81;	           // this also starts the timer running
        sysclock_counter++;
    }
    

`

Other logical functions could be added to this driver. For example, code could
be added that detects when the robot is first enabled and saves the current
sysclock_counter. A new _read_ routine could be added that returns the amount
of time since this event occurred.

The code could add software timers. If a software timer was enabled
(TimerStart(channel)), then the counter associated with the software timer
could also be incremented. Then these software timer counts could be available
to be read.

`

    
    
     :
     sysclock_counter++;
     if (sw_timer_1) sw_timer1_count++;
     if (sw_timer_2) sw_timer2_count++;
     :
    

`

[[edit](/index.php?title=Using_interrupts&action=edit&section=22 "Edit
section: Interrupt worthy resources on PIC" )]

## Interrupt worthy resources on PIC

  * Timers - some 8 &amp; 16 bit counters. Every clock beat is counted off by an active timer, no matter what the controller is concentrating on. When an active timer rolls over, the interrupt function runs. One example of that function - set a pin high and load the clock timer for 1.5ms. Return to main. _ Main loop resumes._ The timer runs out, and the timer function runs. This run, set your pin low, and reload the clock timer for 15ms. Return to main. You now have a servo signal! 
  * Serial port - nothing worth writing your own code for. The interrupt should just shovel more bytes to/from a string whenever the transiever runs low. 
  * Pin change - That's what those 6 interrupt ports on the VEX are, right? 

  
Only a few pre-made interrupts are available in EasyC v1. How about v2?

[![](/media/thumb/1/10/FIRST_logo.gif/50px-
FIRST_logo.gif)](Image:FIRST_logo.gif "" )

|  _This article is currently a stub (a short article without much content).
[Please add more
content](http://www.firstwiki.net/index.php?title=Using_interrupts&action=edit
"http://www.firstwiki.net/index.php?title=Using_interrupts&action=edit" ) to
make a significant article. If you'd like to add to more stubs, look at the
list of [short articles](Special:Shortpages "Special:Shortpages"
)._  
---|---  
  
