# Downloading a program

## From FIRSTwiki

Jump to: navigation, search

This article explains how to **download a program** from a computer to either the [Full-size Robot Controller](Robot_Controller "Robot
Controller") or the [Robovation](robovation) kit. Note that it is necessary to have a _hex_ file to download, but the actual source code is not needed.

1. Using [MPLAB](MPLAB "MPLAB"), **build** the project to produce a _hex_ file (see [Using MPLAB](Using_MPLAB "Using MPLAB") for more information on how to do this)
2. **Connect** one end of a DB9 M-F cable to the serial port on the computer
3. **Connect** the other end of the cable to the program port on the [Robot Controller](robot-controller)
4. Press and hold the program button on the RC until the first LED is green and some other LED is orange.
5. Open [IFI Loader](IFI_Loader "IFI Loader"), click browse and locate the _hex_ file produced in step 1, then **download**

See the [documentation from IFI](http://innovationfirst.com/FIRSTRobotics/documentation.htm "http://innovationfirst.com/FIRSTRobotics/documentation.htm") for more information.
