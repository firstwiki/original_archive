# Pressure switch

### From FIRSTwiki

Jump to: navigation, search

A **pressure switch** is a [pneumatics](Pneumatics "Pneumatics" )
switch whose state changes depending on the pressure.

[![A pressure
switch.](/media/6/6f/PressureSwitch.PNG)](Image:PressureSwitch.PNG
"A pressure switch." )

[![Enlarge](/skins/common/images/magnify-
clip.png)](Image:PressureSwitch.PNG "Enlarge" )

A pressure switch.

## Contents

  * 1 Data
  * 2 Connections
    * 2.1 Air
    * 2.2 Signal
  * 3 Current Product Info
    * 3.1 Supplier
    * 3.2 Model Number
  * 4 Programming
    * 4.1 Default Code
    * 4.2 easyC PRO
    * 4.3 MPLAB  
---  
  

## Data

Sends a digital signal. The two terminals are shorted together when the
pressure is greater than 95psi after hitting a peak of 115psi. The terminals
are disconnected when the pressure is less than 115psi after dropping below
95psi.


## Connections


### Air

Connects to the system via a 1/8" NPT thread on the bottom.


### Signal

Two terminals on the top that are connected to a digital input on the robot
controller, connecting on the black and white wires.


## Current Product Info


### Supplier

Supplied by [[The Nason Company](http://www.nasonptc.com
"http://www.nasonptc.com" )].


### Model Number

SM-2B-115R


## Programming

The Robot Controller needs to check the pressure switch and react accordingly
by applying power to the compressor when needed.


### Default Code

Note that if you have not modified the code in your Robot Controller, you may
connect the pressure switch to digital input 1, with the signal wire connected
to one terminal of the switch and the black ground wire connected to the other
terminal. Connect the Spike Relay with compressor attached to relay output 8.
The controller should turn the compressor on when needed, and off when not.


### easyC PRO

[![The configuration window for the Pressure Switch block in
easyC.](/media/thumb/e/eb/PressureSwitchConfiguration.PNG/180px-PressureSwitch
Configuration.PNG)](Image:PressureSwitchConfiguration.PNG "The
configuration window for the Pressure Switch block in easyC." )

[![Enlarge](/skins/common/images/magnify-
clip.png)](Image:PressureSwitchConfiguration.PNG "Enlarge" )

The configuration window for the Pressure Switch block in easyC.

Use the "Pressure Switch" block under "Outputs". When you drag the block into
your code, a window will pop up asking which input the pressure switch is on.
Also in this window is the relay output you connect the compressor to. Select
the correct channels in this window. It will only allow you to use pins that
are configured as inputs; to configure others, go to the Main function of your
project and double-click Config. Under "DIGITAL IN/OUT", click the desired
pin's arrow--it should point to the pin for an input. Once you have placed the
Pressure Switch block, the code automatically checks the pressure switch every
500 milliseconds (1 millisecond = 0.001 second; 500 milliseconds = 1/2 second)
and switches the relay on if needed.


### MPLAB

First, you need to make sure the digital IO pin you want to use is configured
as an input. If you are using the IFI base code, inside the user_routines.c
file, there is a function called User_Initialization(). At the top of that
function, there is a series of lines setting the port direction of each
digital input. Make sure that the pin you wish to use is being set equal to
INPUT--if you are using digital input 5, for example, you need to be sure
digital_io_05 is set to INPUT.

Once the port direction has been set to input, you need to put a line of code
in a function that is called repeatedly; Process_Data_From_Master_uP() would
be an OK place. The compressor output relay needs to be set to the opposite of
the input--the pressure switch reads "1" when the tanks are full, and "0" when
the tanks are low/empty. So the line of code would look like

relay#_fwd = !rc_dig_in##;

where the # signs are replaced with the appropriate channel numbers.

The compressor should then turn on when it is needed, and off when it is not.

_**[Pneumatics](Pneumatics "Pneumatics" ) Parts:**_  
[Cylinder](Cylinder "Cylinder" ) | [Solenoid](Solenoid
"Solenoid" ) | [Compressor](Compressor "Compressor" ) | [Storage
tank](Storage_tank "Storage tank" ) | [Rotary
actuator](Rotary_actuator "Rotary actuator" ) | [Pressure
regulator](Pressure_regulator "Pressure regulator" ) | **Pressure
switch**  
---  
  
