

# PWM signal

### From FIRSTwiki

Jump to: navigation, search

[![](/media/thumb/1/10/FIRST_logo.gif/50px-
FIRST_logo.gif)](Image:FIRST_logo.gif "" )

|  _This article is currently a stub (a short article without much content).  
_

[Please add more
content](http://www.firstwiki.net/index.php?title=PWM_signal&action=edit
"http://www.firstwiki.net/index.php?title=PWM_signal&action=edit" ) to make a
significant article. _See more [stubs](Special:Shortpages
"Special:Shortpages" )._  
  
---|---  
  
  
A PWM signal, pulse-width-modulated signal, is an [analog
output](/index.php?title=Analog_output&action=edit "Analog output" ) value
used to control motors through [Victors](Victor "Victor" ) or
[Jaguars](Jaguar "Jaguar" ).


## Programming

On the [robot controller](Robot_Controller "Robot Controller" ), a
PWM signal has a range from -127 to 127 in where -127 corresponds to full
power "backwards" on the motor and 127 to full power "forwards" on the motor.
Some controllers may use a range from -1 to 1 with the same actions occurring
at the minimums and maximums of the range. Zero is neutral in both cases and
does not move send any current to the motor (though the
[Victor](Victor "Victor" ) or [Jaguar](Jaguar "Jaguar" )
can change what exactly happens at this signal).


## External Links

  * [Explanation of PWM Signals](http://www.powerdesignersusa.com/InfoWeb/design_center/articles/PWM/pwm.shtm "http://www.powerdesignersusa.com/InfoWeb/design_center/articles/PWM/pwm.shtm" )

