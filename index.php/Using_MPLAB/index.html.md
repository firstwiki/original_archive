# Using MPLAB

## From FIRSTwiki

Jump to: navigation, search

MPLAB is the default IDE for programming PICmicros (like those found in the RCs). It should come with either the [Kit of parts](Kit_of_parts "Kit of parts") or the [Robovation](robovation).

## Contents

- 1 Installation
- 2 Getting around in MPLAB

  - 2.1 Toolbar bars

    - 2.1.1 Standard
    - 2.1.2 Project
    - 2.1.3 Debug

  - 2.2 Configuring general MPLAB options
  - 2.3 The Dialog Boxes

    - 2.3.1 File

      - 2.3.1.1 Open
      - 2.3.1.2 Open Workspace
      - 2.3.1.3 Import
      - 2.3.1.4 Save As
      - 2.3.1.5 Save Workspace As

    - 2.3.2 Project

      - 2.3.2.1 Project Wizard

--------------------------------------------------------------------------------

## Installation

_The official installation guide for MPLAB is available [here](http://innovati
onfirst.com/FIRSTRobotics/pdfs/C-BOT_Install_1-29-2004.pdf "http://innovationfirst.com/FIRSTRobotics/pdfs/C-BOT_Install_1-29-2004.pdf")._

## Getting around in MPLAB

### Toolbar bars

#### Standard

The first part of the toolbar you are probably familiar with. This appears in almost all Windows editing programs.

- **New:** Creates a new, blank text document.
- **Open:** Opens a saved file.
- **Save:** Saves the currently focused file. This option is grey out if the file you have highlighted has not been changed since it was last saved.
- **Cut, Copy, and Paste:** Operates the standard cut, copy and paste functions of Windows.
- **Print:** Prints the currently focused file.
- **Help:** Clicking on this button opens a table of contents of help avaiable.

#### Project

MPLAB has two files which it uses to control your project. One of these is the project file (.mcp) and the other workspace (.mcw). The project file stores the information regerding what exactly is your project (It's in a text/INI format). The workspace file is used by MPLAB to store window positions, breakpoints, and other non-essential stuff.

- **New project:** Creates a new project file.
- **Open project:** Opens a saved project file.
- **Save workspace:** Saves the currently open project file.
- **Build options:** Brings up a dialog box which allows you to set many options of your project and parameters passed on to the assembler, compiler, and linker.

#### Debug

Varies depending on what debugger is selected.

### Configuring general MPLAB options

Although MPLAB is focused around single projects (by default), there are some things which you can change which effect all projects.

- **Editor Format:** Right click on an editor window, such as an open file, and click "Properties."
- **General Options:** From the menus, choose Configure > Settings... (allows you to not use the 1:1 project/workspace model)
- **MCC18 Location:** From the menus, choose Project > Set Language Tool Locations... This option tells MPLAB where it can find MCC18\.
- **MCC18 Default Dirs:** From the menus, choose Project > Set Language Tool Locations... This option allows you to set the places in which MCC18 looks for various things.

### The Dialog Boxes

_This section will eventually hold an entry for every dialog box in MPLAB. Or at least most of them._<br>
_Dialog boxes are arranged according to nesting in menus. If there is another way of reaching them, it will be noted at the beginning of the section._

#### File

##### Open

_File > Open..._<br>
**Purpose:** This option allows you to open up source, list, map, and linker files. ("All files" option is also included)<br>
**Use:** This window operates just like a standard Windows open box.

##### Open Workspace

_File > Open Workspace..._<br>
**Purpose:** Allows you to open up a saved workspace.<br>
**Use:** This window operates just like a standard Windows open box.

##### Import

_File > Import..._<br>
**Purpose:** Allows you to import .hex and debugger files. (all files option is also included)<br>
**Use:** This window operates just like a standard Windows open box.

##### Save As

_File > Save As..._<br>
**Purpose:** Allows you to save the currently focused document.<br>
**Use:** This window operates just like a standard Windows save box.

##### Save Workspace As

_File > Open Workspace..._<br>
**Purpose:** Allows you to save the currently open workspace.<br>
**Use:** This window operates just like a standard Windows save box.

#### Project

##### Project Wizard

_Project > Project Wizard..._<br>
**Purpose:** Gives an easy way to start a new project in MPLAB.<br>
**Use:** This is a wizard which allows you to start a new project easilly. Each option on each step of the wizard is explained below.

1. Select a device 

  - Device: Choose the microcontroller you are setting this project up for. If you are using the FIRST robot controller, choose "PIC18F8520."

2. Choose a toolsuite 

  - Active Toolsuite: Choose which ever toolsuite, which includes the compiler and linker, you need. For the FIRST robot controller, choose "Microchip C18 toolsuite."
  - Toolsuite components: Click on any component of the suite to be able to tell MPLAB where it is located in the "Location" box.

3. Name your project 

  - Project name: Call it whatever you want to, such as "our_frc_code."
  - Project directory: Use this to tell MPLAB to put the newly created project.

4. Add any existing files to your project 

  - The box on the left are the files stored on you computer. You can navigate this the way you would a normal Windows explorer tree.
  - The box on the right are the files which will be added to your project.
