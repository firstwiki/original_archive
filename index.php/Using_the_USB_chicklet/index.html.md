# Using the USB chicklet

## From FIRSTwiki

Jump to: navigation, search

[![The USB chicklet](/media/thumb/a/a9/USB_chicklet.gif/200px-
USB_chicklet.gif)](Image:USB_chicklet.gif "The USB chicklet")

[![Enlarge](/skins/common/images/magnify-
clip.png)](Image:USB_chicklet.gif "Enlarge")

The [USB chicklet](USB_chicklet "USB chicklet")

Starting in 2007, USB devices can be used instead of joysticks with the use of the [USB chicklet](USB_chicklet "USB chicklet"). Teams may find that drivers are more comfortable with a game pad than the joysticks given in the kit of parts. Since eight additional button inputs are available, it may be possible to have only one driver operating the robot. While the chicklet is an attractive option for drivers, it can make the programmer's job more difficult. This tutorial aims to remove the complexity that the chicklet can introduce.

IFI provides a [manual](http://www.ifirobotics.com/docs/usbchicklet-
usermanual-rev1-2.pdf "http://www.ifirobotics.com/docs/usbchicklet-usermanual-
rev1-2.pdf") on their website with programming specs, and it will be referenced a few times in this tutorial.

Further information on this product can be found at [Cross The Road Electronics](http://www.crosstheroadelectronics.com "http://www.crosstheroadelectronics.com").

## Contents

- 1 Required Hardware

  - 1.1 USB chicklet
  - 1.2 Controller

- 2 Setup
- 3 Code

  - 3.1 Tank Drive and Joystick Axises
  - 3.2 Buttons 1-4
  - 3.3 Buttons 5-8
  - 3.4 Buttons 9-12

- 4 External Links

--------------------------------------------------------------------------------

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=1 "Edit
section: Required Hardware")]

## Required Hardware

Two pieces of hard ware are required for this tutorial:

- The USB chicklet
- A compatible game controller

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=2 "Edit
section: USB chicklet")]

### USB chicklet

The chicklet can be purchased from IFI Robotics. It plugs into the joystick slot on the Operator Interface and is powered by a 7.2-volt or 9-volt power source. This power source can be an external power supply during practice, but the 2007 rulebook requires that a 7.2 volt battery be used during competition.

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=3 "Edit
section: Controller")]

### Controller

The controller used must _exactly_ match the make and model in the USB- Chicklet manual. Any controller on the supported devices list will work, but for the purposes of this tutorial, we will use the **official** Microsoft Xbox 360 controller. The chicklet is not able to configure a generic brand XBox controller (such as MadCatz), so be sure to purchase the official, Microsoft branded, wired (wireless will not work) Xbox 360 controller.

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=4 "Edit
section: Setup")]

## Setup

The setup instructions are relatively straight forward in the [user manual](http://www.ifirobotics.com/docs/usbchicklet-usermanual-rev1-2.pdf "http://www.ifirobotics.com/docs/usbchicklet-usermanual-rev1-2.pdf"). Since the configuration directions are described in adequate detail in the user manual, I will only give a general overview, noting anything specific to this tutorial.

1. Plug the chicklet into joystick port 1
2. Plug in a 7.2 or 9 volt power source
3. Set the calibration jumper
4. Press any button once and wait to choose the first analog mode
5. Press the 12 buttons that you will want available. Be sure to write down the order in which you pressed the button. You'll be referencing the order in your code.
6. Move both joysticks on the XBox controller in full rotation to configure the x-axis and y-axis
7. Press any button to finish the configuration
8. Remove calibration jumper
9. Begin coding

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=5 "Edit
section: Code")]

## Code

For the most part, the chicklet acts as a normal joystick. Hopefully, you've been [using macros](Writing_macros "Writing macros") to define all your inputs, so that switching from two joysticks in tank drive to just one will require minimal effort. If your code does not use macros, then I would recommend using them. I will give examples in this tutorial with and without macros, and you'll notice that the macros example is considerably more "friendly."

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=6 "Edit
section: Tank Drive and Joystick Axises")]

### Tank Drive and Joystick Axises

Since we chose analog mode 1, the x-axises are ignored in both the left and right joysticks. Instead, the left y-axis will be registered as the y-axis on joystick one (or whichever port the chicklet happens to be plugged into) and the right y-axis will be registered as the x-axis on joystick one.

If you use macros, then just change the defines for the right input from p2_y to p1_x.

```
#define LEFT_MOTOR_CONTROL   p1_y
#define RIGHT_MOTOR_CONTROL  p1_x
```

If you don't happen to use macros, then be absolutely sure to change every value of p2_y to p1_x. Your tank drive code should look something like

```
pwm01 = p1_y;
pwm02 = p1_x;
```

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=7 "Edit
section: Buttons 1-4")]

### Buttons 1-4

Buttons one through four are extremely simple. Actually, there probably won't be any changes needed in the code to get these buttons working. The buttons just map to the trigger, top, and auxiliary buttons, so they act just like the normal buttons on the joysticks included in the kit. A simple define file may contain code like

```
#define BUTTON_1  p1_sw_trig
#define BUTTON_2  p1_sw_top
#define BUTTON_3  p1_sw_aux1
#define BUTTON_4  p1_sw_aux2
```

Actually, I would recommend that your define file include some description of function, more like

```
#define ARM_DOWN_BUTTON  p1_sw_trig
```

This will give a better description in your code to remind you what is supposed to be happing. It is much easier to know what is happening in

```
if(ARM_DOWN_BUTTON)
```

than in

```
if(BUTTON_1)
```

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=8 "Edit
section: Buttons 5-8")]

### Buttons 5-8

Buttons five through twelve are what makes the chicklet a bit tricky. You'll need a good understanding of [bitwise operators](Bitwise_operators "Bitwise operators") to follow this section fully. I'll give the code first, and then explain what's happening later on.

```
#define BUTTON_5 ((~p1_wheel & 0x80) != 0)
#define BUTTON_6 ((~p1_wheel & 0x40) != 0)
#define BUTTON_7 ((~p1_wheel & 0x20) != 0)
#define BUTTON_8 ((~p1_wheel & 0x10) != 0)
```

You can use this in your defines section just like the other buttons. If the button is pressed, then BUTTON_x will be true, if it's not pressed, then BUTTON_x will be false.

Since there are only four button variables available, the engineers that made the [USB chicklet](USB_chicklet "USB chicklet") had to be a bit creative to allow for more than four digital inputs. Their solution: use the top four bits of the two remaining analog inputs to add eight more digital buttons. The wheel axis contains buttons 5-8, and the auxiliary axis contains buttons 9-12.

When no buttons are pressed the top four bits are filled with ones. The bottom four bits are not used; they may contain any value. This means the binary representation of p1_wheel with no buttons pressed will be

```
1111 XXXX
```

If a button is pressed, then its bit is replaced with 0 instead of 1\. When the fifth button is pressed, the topmost bit will be 0; when the sixth button is pressed, the second bit will be 0, and so on. The binary representations for each of the four buttons will look like

```
Button 5   0111 XXXX
Button 6   1011 XXXX
Button 7   1101 XXXX
Button 8   1110 XXXX
```

Also note that more one button can be pressed at the same time. For example, if the fifth and seventh buttons are pressed, the binary representation would be

```
0101 XXXX
```

To take this data and separate it into different variables, we'll need to do some binary math. Since we want each button to evaluate as true when pressed, we need to use the binary NOT operator to change any 1s to 0s and vice versa. The code to do a binary NOT is

```
~p1_wheel
```

If the fifth button and the seventh button are pressed, it's new binary representation will look like

```
1010 XXXX
```

While this is closer to what we want, the buttons are still not separated into parts. To find if just one individual button is pressed, we need to use the binary AND operator. To find what just one bit is we need to do an AND with every bit being 0 except for the one in which we are testing. To test for just button five, we want something like

```
  1010 XXXX
& 1000 0000
= 1000 0000
```

When the fifth button is not pressed the AND statement will result in all zeros, but when the fifth button is pressed (like in the example) it will result in all zeros except for the topmost bit. To test each button we'll do a binary AND against a number with 0s in every bit except for the bit associated with that particular button. Since this number will be hexadecimal in the code, I'll give examples of the binary and hexadecimal.

```
Button 5   1000 0000   0x80
Button 6   0100 0000   0x40
Button 7   0010 0000   0x20
Button 8   0001 0000   0x10
```

Right now the code to test for button five looks like

```
#define BUTTON_5  (~p1_wheel & 0x80)
```

This is actually "good enough" for most purposes. BUTTON_5 will be 0 when the button is not pressed and will be something other than 0 (in this case 128) when the button is pressed. This will be enough for

```
if(BUTTON_5) { ...do something... }
```

to run properly, because an if statement runs for every value except 0\. For the sake of consistency and cases where a boolean number (one or zero) is required (such as relay outputs), we need to do one more step. To make "anything except zero" become a one, we need to use a comparison operator. The "not equals" comparison against zero will give us exactly what we want. This will make our final code be

```
#define BUTTON_5 ((~p1_wheel & 0x80) != 0)
#define BUTTON_6 ((~p1_wheel & 0x40) != 0)
#define BUTTON_7 ((~p1_wheel & 0x20) != 0)
#define BUTTON_8 ((~p1_wheel & 0x10) != 0)
```

Now, when a button is pressed, it will equal 1, and when it is not pressed, it will be 0.

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=9 "Edit
section: Buttons 9-12")]

### Buttons 9-12

Buttons nine through twelve use exactly the same logic as buttons five through eight. The only difference between the two sets of buttons is that buttons nine through twelve are on the top four bits of the auxiliary input rather than on the wheel input. The final code for buttons nine through twelve will be

```
#define BUTTON_9  ((~p1_aux & 0x80) != 0)
#define BUTTON_10 ((~p1_aux & 0x40) != 0)
#define BUTTON_11 ((~p1_aux & 0x20) != 0)
#define BUTTON_12 ((~p1_aux & 0x10) != 0)
```

[[edit](/index.php?title=Using_the_USB_chicklet&action=edit&section=10 "Edit
section: External Links")]

## External Links

- [IFI manual](http://www.ifirobotics.com/docs/usbchicklet-usermanual-rev1-2.pdf "http://www.ifirobotics.com/docs/usbchicklet-usermanual-rev1-2.pdf")
- [Cross The Road Electronics](http://www.crosstheroadelectronics.com "http://www.crosstheroadelectronics.com")

[![Image:LinkFA-star.png](/media/6/60/LinkFA-star.png)](Image
:LinkFA-star.png "Image:LinkFA-star.png")
