# Modifying a servo

### From FIRSTwiki

Jump to: navigation, search

**Modifying a servo** is useful if you want to use a [servo](/index.php/Servo "Servo" ) as a small motor, without restrictions on rotation and without sending a [PWM signal](/index.php/PWM_signal "PWM signal" ). [Servos](/index.php/Servo "Servo" ) are small geared [motors](/index.php/Motor "Motor" ) that usually have low power outputs. Their [RPM](/index.php?title=RPM&action=edit "RPM" ) is reduced and their rotational range of motion is limited to, usually, a full rotation or even less. 

Servos are very useful for rotating small parts in small angles. However, one
often wants to have full rotation.

The modifications listed will allow you to power the servo using direct
voltage, instead of a PWM signal and allow the horn to rotate infinitely in
either direction.

## Contents

  * 1 Why Modify the Servo?
  * 2 Theory
  * 3 Modifying the Servo
    * 3.1 Before you Work
    * 3.2 Electrical Modifications
    * 3.3 Mechanical Modifications
    * 3.4 Putting it All Together
  * 4 How to Use the Modified Servo  
---  
  
[[edit](/index.php?title=Modifying_a_servo&action=edit&section=1 "Edit
section: Why Modify the Servo?" )]

## Why Modify the Servo?

If you want to use a [servo](/index.php/Servo "Servo" ) as a small motor,
without restrictions on rotation and without sending a [PWM
signal](/index.php/PWM_signal "PWM signal" ), modify the servo as follows.

[[edit](/index.php?title=Modifying_a_servo&action=edit&section=2 "Edit
section: Theory" )]

## Theory

Servos are very useful for rotating small parts in small angles. However, one
often wants to have full rotation.

The modifications listed below will:

  1. Allow you to power the servo using direct voltage, instead of a PWM signal. 
  2. Allow the horn to rotate infinitely in either direction. 

[[edit](/index.php?title=Modifying_a_servo&action=edit&section=3 "Edit
section: Modifying the Servo" )]

## Modifying the Servo

[[edit](/index.php?title=Modifying_a_servo&action=edit&section=4 "Edit
section: Before you Work" )]

### Before you Work

First, some basic engineering precautions:

  * Keep all screws removed in one step together. They are normally interchangeable. However, screws from different steps are not interchangeable. 
  * Some modifications are irreversable. 
  * Use caution when [soldering](/index.php/Soldering "Soldering" ). 
  * Clean up any pieces of wire to avoid [short circuiting](/index.php/Short_circuit "Short circuit" ). 

Some [PWM cables](/index.php/PWM_cable "PWM cable" ) might have brown, red,
and yellow wires instead of black, red, and white wires. In that case "black"
means "brown," and "white" means "yellow." The red wire remains the same.

Do the following pre-modification steps:

  1. Remove the servo from any external attachments. 
  2. Disconnect the servo from any power or output ports. 
  3. Remove the [servo horn](/index.php?title=Servo_horn&action=edit "Servo horn" ), if any. 
  4. Remove the 4 long screws in the corners of the servo. 
  5. Carefully remove the back plastic cover (the side with the PWM cable). 

[[edit](/index.php?title=Modifying_a_servo&action=edit&section=5 "Edit
section: Electrical Modifications" )]

### Electrical Modifications

  1. Loosen the [PWM cable](/index.php/PWM_cable "PWM cable" ) holder (a rubber piece). 
  2. Cut the black, white, and red wires. Be sure to cut very close to the solder connections. 
  3. Pull the PWM cable holder back. 
  4. Pull the black, white, and red wires apart. 
  5. [Strip](/index.php/Wire_stripping "Wire stripping" ) the red and black wires approximately 1/4 inch. 
  6. Examine the side of the circuit board that is farthest from the location that the PWM cable holder used to be. There should be two solder connections. 
  7. Solder the red wire to one of the connections. 
  8. Solder the black wire to another connection. 

[[edit](/index.php?title=Modifying_a_servo&action=edit&section=6 "Edit
section: Mechanical Modifications" )]

### Mechanical Modifications

  1. Hold the servo with the circut board side up. 
  2. Pull the front (the side with the [output shaft](/index.php?title=Output_shaft&action=edit "Output shaft" )) plastic cover off. Make sure that the gears don't fall out. 
  3. Remove the brass-colored ring in the gears. 
  4. Holding the servo as before, put the plastic cover, with gears, back on. 

[[edit](/index.php?title=Modifying_a_servo&action=edit&section=7 "Edit
section: Putting it All Together" )]

### Putting it All Together

  1. Put the PWM cable holder on the plastic side. 
  2. Put the 4 long screws back in. 

[[edit](/index.php?title=Modifying_a_servo&action=edit&section=8 "Edit
section: How to Use the Modified Servo" )]

## How to Use the Modified Servo

The servo will now run on power supplied directly through the red and black
wires. You can ignore the white wire.

[![Image:LinkFA-star.png](/media/6/60/LinkFA-star.png)](/index.php/Image
:LinkFA-star.png "Image:LinkFA-star.png" )

