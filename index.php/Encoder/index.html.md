# Encoder

## From FIRSTwiki

Jump to: navigation, search

The [Control System](Control_system "Control system")

**[Logic of a Control System](Logic_of_a_control_system "Logic of a control system")**

- [Closed loop](Closed_loop "Closed loop")

  - [PID controller](PID_controller "PID controller")

- [Open loop](Open_loop "Open loop")

**[Parts of a Control System](Parts_of_a_control_system "Parts of a control system")**

- [Computer](Computer "Computer")

  - [Robot Controller](robot-controller)

    - [2010 RC](Robot_Controller_%282010%29 "Robot Controller \(2010\)")
    - [2009 RC](Robot_Controller_%282009%29 "Robot Controller \(2009\)")
    - [2006 RC](Robot_Controller_%282006%29 "Robot Controller \(2006\)")
    - [2004 RC](Robot_Controller_%282004%29 "Robot Controller \(2004\)")
    - [2003 RC](Robot_Controller_%282003%29 "Robot Controller \(2003\)")
    - [2000 RC](Robot_Controller_%282000%29 "Robot Controller \(2000\)")
    - [1996 RC](/index.php?title=Robot_Controller_%281996%29&action=edit "Robot Controller \(1996\)")
    - [1993 RC](/index.php?title=Robot_Controller_%281993%29&action=edit "Robot Controller \(1993\)")

  - [Robovation](robovation)

- [Input](Input "Input")

  - [Operator Interface](operator-interface)
  - [Joystick](joystick)

- [Output](Output "Output")

  - [Victor 884](victor-884)
  - [Spike](spike-relay)

- [Sensors](sensor)

  - **Encoder**
  - [Accelerometer](Accelerometer "Accelerometer")
  - [Light sensor](/index.php?title=Light_sensor&action=edit "Light sensor")
  - [IR sensor](IR_sensor "IR sensor")
  - [Gyro](gyro)
  - [CMUcam2](CMUcam2 "CMUcam2")

--------------------------------------------------------------------------------

An incremental encoder (aka a "wheel encoder") is a device that when rotated sends out a series of digital signals that signify intervals in rotation of the shaft with which the encoder is connected.

Strictly speaking, a device that records speed, but not velocity (which has a direction component) is more accurately referred to as a tachometer. Other encoding methods include using reflective optical detection, mechanical wipers (unreliable), and hall effect sensors (used in car ABS systems).

## Contents

- 1 Calculations

  - 1.1 Immediate Velocity

- 2 Types of Encoders

  - 2.1 VEX Encoders
  - 2.2 Quadrature Encoders

- 3 Interfacing Considerations

--------------------------------------------------------------------------------

## Calculations

By counting up these digital "clicks" that a encoder sends can yield the total [angular displacement](http://www.wikipedia.org/wiki/angular_displacement "wikipedia:angular_displacement") of a shaft. With wheels of known size, the linear [displacement](http://www.wikipedia.org/wiki/displacement "wikipedia:displacement") and [velocity](http://www.wikipedia.org/wiki/velocity "wikipedia:velocity") are easy to calculate.

### Immediate Velocity

To calculate a more immediate look at the velocity on the encoder, an ordinary input port can look at the width of one rotation pulse. This requires the use of interrupts and timers to keep track of how many fractions of a second have gone by since the last pulse.

Note that at high speed, this method can be very noisy, so a running average of the last few pulse durations can be useful.

## Types of Encoders

### VEX Encoders

The VEX encoder uses a single LED/photodetector set with a radially slit disc passing between them.

### Quadrature Encoders

Quadrature encoders use two sensors offset 90 degrees out of phase with each other to recover direction information as well.

These two sensors, usually referred to as phase A and phase B, will indicate direction by polling one line on the transition of the other. For example, on a rising interrupt of phase A, if phase B is high, then the robot knows it is traveling in one direction. If phase B is low, then the robot is going to opposite way.

By capturing interrupts on the rising and falling edge of phase A, the encoder enters what is known as "X2" mode, as two counts are made for every slit in the photo interrupter disk. Alternatively, interrupts can be enabled on both edges of phase B as well (and the interrupt handlers will poll phase A now, instead) to generate four times the counts per slit ("X4" mode). These techniques allow a low resolution encoder to effectively double or quadruple its CPR (counts per revolution), which can be valuable in some applications.

## Interfacing Considerations

The biggest problem with using incremental encoders in [FIRST](first) is generally on the interfacing side of things. The [robot controller](robot-controller) only has a limited number of digital inputs and thus, affects how many encoders that can be mounted on the robot.

Additionally, whenever a rising/falling edge is detected, a small piece of code (called the interrupt service routine) must run. If the ticks are coming too fast, the [RC](robot-controller) will spend too much time handling the interrupts and not enough doing other things. In the worst case, this can mean communication dropout, erratic data, or the red- light-of-death.

Some teams choose to use supplemental electronics (such as a second microprocessor, FPGAs, or up/down counter ICs) to "decode" the quadrature signal. In this manner, the [RC](Robot_controller "Robot
controller") can request the count information via a serial or parallel link whenever it is ready.

Other interfacing issues that can arise have to do with the low current sourcing abilities of many commercial encoders, meaning that buffer circuitry may be needed to drive the signal across longer wires. Lastly, the time it takes the [robot controller](robot-controller) between starting to service the interrupt and reading the other phase (for direction information) can be long enough that by the time the RC is ready, the other line has already changed state. A pulse-stretch circuit can alleviate this issue. Banebots offers a simple quadrature decoder circuit that addresses both the current sourcing and read lag issues.
