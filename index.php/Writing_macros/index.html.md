# Writing macros

## From FIRSTwiki

Jump to: navigation, search

Macros are simple text replacements made by the C preprocessor. They allow constants to be defined in one place where they can easily be edited and are also used to rename cryptic variable names to be more understandable. Using macros wisely in a program can increase code readability and maintainability.

## Contents

- 1 Syntax
- 2 Uses of Macros

  - 2.1 Constants
  - 2.2 Renaming

- 3 External Links

--------------------------------------------------------------------------------

## Syntax

Macros are written using the C preprocessor statement #define using the following syntax:

```
#define TEXT_TO_REPLACE   TextToBeInserted
```

Unless the text to be inserted is a complete statement, the line should not end in a semi-colon. The text to be inserted in a macro can be split into multiple lines by ending the line with a "\" (no quotes). Having multi-line statements is not recommended for beginners except for simple string replacements. Including multiple lines of code in a macro can produce errors that are very difficult to understand because syntax errors can occur after preprocessor has replaced text, making error messages hard to follow. Also, including complex macros can make the code more difficult to understand for other programmers.

There is also a function-like notation for macros with parameters inside parenthesis. Using a macro instead of a normal function benefits the speed of a program because calculations are done by the compiler, not during runtime, but this shouldn't be used for the same reasons multi-line macros are not recommended. To achieve the same effect without using macros, a function can be preceded with the keyword "inline" in any modern compiler.

## Uses of Macros

Macros can make a program more readable and maintainable by having all constants named in one place, as well as providing reasonable names for input/output variables.

### Constants

One use for macros is defining constants. For example, constant values used for PWM outputs can be defined in one place.

```
#define PWM_NEUTRAL_SPEED 127
#define PWM_MAX_FORWARD   254
#define PWM_MAX_REVERSE     0
```

Then 254 will replace every instance of PWM_MAX_SPEED by the preprocessor. This allows programmers to change the value 254 to a lower value, should they decide that 254 is too fast later on. It also removes any confusion a future programmer might have about what the value means because it is written in plain English, rather than an obscure number.

### Renaming

Macros don't just define constants, they can also be used to assign aliases for global variables, such as PWM outputs and joystick inputs. This provides the same benefits as using a macro for constants: the code is more readable and maintainable. A team's define list for a tank-like drive system could look like the following:

```
#define LEFT_MOTOR_PWM        pwm01
#define RIGHT_MOTOR_PWM       pwm02

#define LEFT_MOTOR_CONTROL    p1_y
#define RIGHT_MOTOR_CONTROL   p2_y
```

This could then be used in the user_routines.c file with the following function:

```
void Process_Data_From_Master_uP(void)
{
  Getdata(&rxdata);   /* Get fresh data from the master microprocessor. */

  LEFT_MOTOR_PWM = LEFT_MOTOR_CONTROL;
  RIGHT_MOTOR_PWM = RIGHT_MOTOR_CONTROL;

  Generate_Pwms(pwm13,pwm14,pwm15,pwm16);

  Putdata(&txdata);     /* DO NOT CHANGE! */
}
```

By using macros, any programmer reading this function can easily tell that the left motor is being assigned to the left motor controller, and the right motor is being assigned to the right motor controller.

In addition to being easier to understand and more readable, this code is also more maintainable. For example, if a team wanted to change the primary input device from two joysticks to one XBox 360 controller using a [USB chicklet](/index.php?title=USB_chicklet&action=edit "USB chicklet"), normally the programmers would need to change every instance of p2_y to p1_x in the code, but using macros, they would only need to change one line of code in the defines list:

```
#define RIGHT_MOTOR_CONTROL   p2_y
```

would change to

```
#define RIGHT_MOTOR_CONTROL   p1_x
```

## External Links

- [Wikipedia Entry](http://en.wikipedia.org/wiki/C_preprocessor "http://en.wikipedia.org/wiki/C_preprocessor")
