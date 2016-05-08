

# Spike

### From FIRSTwiki

Jump to: navigation, search

The [Control System](Control_system "Control system" )

**[Logic of a Control System](Logic_of_a_control_system "Logic of a control system" )**

  * [Closed loop](Closed_loop "Closed loop" )
    * [PID controller](PID_controller "PID controller" )
  * [Open loop](Open_loop "Open loop" )

**[Parts of a Control System](Parts_of_a_control_system "Parts of a control system" )**

  * [Computer](Computer "Computer" )
    * [Robot Controller](robot-controller)
      * [2010 RC](Robot_Controller_%282010%29 "Robot Controller \(2010\)" )
      * [2009 RC](Robot_Controller_%282009%29 "Robot Controller \(2009\)" )
      * [2006 RC](Robot_Controller_%282006%29 "Robot Controller \(2006\)" )
      * [2004 RC](Robot_Controller_%282004%29 "Robot Controller \(2004\)" )
      * [2003 RC](Robot_Controller_%282003%29 "Robot Controller \(2003\)" )
      * [2000 RC](Robot_Controller_%282000%29 "Robot Controller \(2000\)" )
      * [1996 RC](/index.php?title=Robot_Controller_%281996%29&action=edit "Robot Controller \(1996\)" )
      * [1993 RC](/index.php?title=Robot_Controller_%281993%29&action=edit "Robot Controller \(1993\)" )
    * [Robovation](robovation)
  * [Input](Input "Input" )
    * [Operator Interface](operator-interface)
    * [Joystick](joystick)
  * [Output](Output "Output" )
    * [Victor 884](victor-884)
    * **Spike**
    * [Jaguar](Jaguar "Jaguar" )
  * [Sensors](sensor)
    * [Encoder](Encoder "Encoder" )
    * [Accelerometer](Accelerometer "Accelerometer" )
    * [Light sensor](/index.php?title=Light_sensor&action=edit "Light sensor" )
    * [IR sensor](IR_sensor "IR sensor" )
    * [Gyro](gyro)
    * [CMUcam2](CMUcam2 "CMUcam2" )  
---  
  
## Contents

  * 1 Data
  * 2 Connections
    * 2.1 Motors
    * 2.2 Solenoids
    * 2.3 Air Compressor
    * 2.4 Pinout of Control Input
  * 3 Spike Red  
---  
  

## Data

The [Robot Controller](robot-controller) sends
a Relay signal to the Spike. When it recieves a FWD signal, it applies +12v to
M+ and grounds M-. Likewise when it recieves a REV signal, it applies +12v to
M- and grounds M+. When both signals are recieved, +12v is applied to M+ and
M- and nothing is grounded.


## Connections


### Motors

Spikes can be connected to a [motor](Motor "Motor" ) that does not
need to move at a variable speed. The motor cannot draw more than 20A.


### Solenoids

Spikes can be connected to one or two solenoids. To connect two solenoids
simply ground the negative ends of the [solenoid](Solenoid
"Solenoid" ) to the grounding portion of the [breaker
panel](Breaker_panel "Breaker panel" ) and the positive ends to M+
and M-.


### Air Compressor

The air compressor can also be connected to the Spike, but care should be
taken to always observe the proper polarity. The NEG output should never be
enabled. If the compressor is powered in reverse, it will appear to function,
but it will be drawing more current and producing more heat than it should for
the amount of air it moves. Also, note that FIRST recommends that you remove
the spike module's 20 amp fuse and replace it with a 20 amp circuit breaker to
avoid nuisance blowing of the fuse when the spike module is used with an air
compressor.


### Pinout of Control Input

The control input to the Spike relay is a three-pin receptacle where a three-
wire cable from the [Robot controller](Robot_controller "Robot
controller" ) is connected to. The black wire is grounded.

When the white wire is at +5V and the red wire is at 0V, M+ receives the full
input voltage. When the red wire is at +5V and the white wire is at 0V, M-
receives the full input voltage.


#  Spike Red

Occasionally you might see versions of the Spike relay floating around that
have red lettering. These are older editions of the relay and lack reverse
polarity protection on their inputs. In addition, when no control signal is
present, the M+ and M- pins are connected to +12 instead of GND (So a 0 in
software is +12, and a 1 in software is a GND)

