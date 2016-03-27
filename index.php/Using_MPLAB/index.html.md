# Using MPLAB

### From FIRSTwiki

Jump to: navigation, search

MPLAB is the default IDE for programming PICmicros (like those found in the
RCs). It should come with either the [Kit of parts](/index.php/Kit_of_parts
"Kit of parts" ) or the [Robovation](/index.php/Robovation "Robovation" ).

## Contents

  * 1 Installation
  * 2 Getting around in MPLAB
    * 2.1 Toolbar bars
      * 2.1.1 Standard
      * 2.1.2 Project
      * 2.1.3 Debug
    * 2.2 Configuring general MPLAB options
    * 2.3 The Dialog Boxes
      * 2.3.1 File
        * 2.3.1.1 Open
        * 2.3.1.2 Open Workspace
        * 2.3.1.3 Import
        * 2.3.1.4 Save As
        * 2.3.1.5 Save Workspace As
      * 2.3.2 Project
        * 2.3.2.1 Project Wizard  
---  
  
[[edit](/index.php?title=Using_MPLAB&action=edit&section=1 "Edit section:
Installation" )]

## Installation

_The official installation guide for MPLAB is available [here](http://innovati
onfirst.com/FIRSTRobotics/pdfs/C-BOT_Install_1-29-2004.pdf
"http://innovationfirst.com/FIRSTRobotics/pdfs/C-BOT_Install_1-29-2004.pdf"
)._

[[edit](/index.php?title=Using_MPLAB&action=edit&section=2 "Edit section:
Getting around in MPLAB" )]

## Getting around in MPLAB

[[edit](/index.php?title=Using_MPLAB&action=edit&section=3 "Edit section:
Toolbar bars" )]

### Toolbar bars

[[edit](/index.php?title=Using_MPLAB&action=edit&section=4 "Edit section:
Standard" )]

#### Standard

The first part of the toolbar you are probably familiar with. This appears in
almost all Windows editing programs.

  * **New:** Creates a new, blank text document. 
  * **Open:** Opens a saved file. 
  * **Save:** Saves the currently focused file. This option is grey out if the file you have highlighted has not been changed since it was last saved. 
  * **Cut, Copy, and Paste:** Operates the standard cut, copy and paste functions of Windows. 
  * **Print:** Prints the currently focused file. 
  * **Help:** Clicking on this button opens a table of contents of help avaiable. 

[[edit](/index.php?title=Using_MPLAB&action=edit&section=5 "Edit section:
Project" )]

#### Project

MPLAB has two files which it uses to control your project. One of these is the
project file (.mcp) and the other workspace (.mcw). The project file stores
the information regerding what exactly is your project (It's in a text/INI
format). The workspace file is used by MPLAB to store window positions,
breakpoints, and other non-essential stuff.

  * **New project:** Creates a new project file. 
  * **Open project:** Opens a saved project file. 
  * **Save workspace:** Saves the currently open project file. 
  * **Build options:** Brings up a dialog box which allows you to set many options of your project and parameters passed on to the assembler, compiler, and linker. 

[[edit](/index.php?title=Using_MPLAB&action=edit&section=6 "Edit section:
Debug" )]

#### Debug

Varies depending on what debugger is selected.

[[edit](/index.php?title=Using_MPLAB&action=edit&section=7 "Edit section:
Configuring general MPLAB options" )]

### Configuring general MPLAB options

Although MPLAB is focused around single projects (by default), there are some
things which you can change which effect all projects.

  * **Editor Format:** Right click on an editor window, such as an open file, and click "Properties." 
  * **General Options:** From the menus, choose Configure > Settings... (allows you to not use the 1:1 project/workspace model) 
  * **MCC18 Location:** From the menus, choose Project > Set Language Tool Locations... This option tells MPLAB where it can find MCC18. 
  * **MCC18 Default Dirs:** From the menus, choose Project > Set Language Tool Locations... This option allows you to set the places in which MCC18 looks for various things. 

[[edit](/index.php?title=Using_MPLAB&action=edit&section=8 "Edit section: The
Dialog Boxes" )]

### The Dialog Boxes

_This section will eventually hold an entry for every dialog box in MPLAB. Or
at least most of them._  
_Dialog boxes are arranged according to nesting in menus. If there is another
way of reaching them, it will be noted at the beginning of the section._

[[edit](/index.php?title=Using_MPLAB&action=edit&section=9 "Edit section:
File" )]

#### File

[[edit](/index.php?title=Using_MPLAB&action=edit&section=10 "Edit section:
Open" )]

##### Open

_File &gt; Open..._  
**Purpose:** This option allows you to open up source, list, map, and linker files. ("All files" option is also included)  
**Use:** This window operates just like a standard Windows open box. 

[[edit](/index.php?title=Using_MPLAB&action=edit&section=11 "Edit section:
Open Workspace" )]

##### Open Workspace

_File &gt; Open Workspace..._  
**Purpose:** Allows you to open up a saved workspace.  
**Use:** This window operates just like a standard Windows open box. 

[[edit](/index.php?title=Using_MPLAB&action=edit&section=12 "Edit section:
Import" )]

##### Import

_File &gt; Import..._  
**Purpose:** Allows you to import .hex and debugger files. (all files option is also included)  
**Use:** This window operates just like a standard Windows open box. 

[[edit](/index.php?title=Using_MPLAB&action=edit&section=13 "Edit section:
Save As" )]

##### Save As

_File &gt; Save As..._  
**Purpose:** Allows you to save the currently focused document.  
**Use:** This window operates just like a standard Windows save box. 

[[edit](/index.php?title=Using_MPLAB&action=edit&section=14 "Edit section:
Save Workspace As" )]

##### Save Workspace As

_File &gt; Open Workspace..._  
**Purpose:** Allows you to save the currently open workspace.  
**Use:** This window operates just like a standard Windows save box. 

[[edit](/index.php?title=Using_MPLAB&action=edit&section=15 "Edit section:
Project" )]

#### Project

[[edit](/index.php?title=Using_MPLAB&action=edit&section=16 "Edit section:
Project Wizard" )]

##### Project Wizard

_Project &gt; Project Wizard..._  
**Purpose:** Gives an easy way to start a new project in MPLAB.  
**Use:** This is a wizard which allows you to start a new project easilly. Each option on each step of the wizard is explained below. 

  1. Select a device 
    * Device: Choose the microcontroller you are setting this project up for. If you are using the FIRST robot controller, choose "PIC18F8520." 
  2. Choose a toolsuite 
    * Active Toolsuite: Choose which ever toolsuite, which includes the compiler and linker, you need. For the FIRST robot controller, choose "Microchip C18 toolsuite." 
    * Toolsuite components: Click on any component of the suite to be able to tell MPLAB where it is located in the "Location" box. 
  3. Name your project 
    * Project name: Call it whatever you want to, such as "our_frc_code." 
    * Project directory: Use this to tell MPLAB to put the newly created project. 
  4. Add any existing files to your project 
    * The box on the left are the files stored on you computer. You can navigate this the way you would a normal Windows explorer tree. 
    * The box on the right are the files which will be added to your project. 

Retrieved from "<http://www.firstwiki.net/index.php/Using_MPLAB>"

##### Views

  * [Article](/index.php/Using_MPLAB)
  * [Discussion](/index.php/Talk:Using_MPLAB)
  * [Edit](/index.php?title=Using_MPLAB&action=edit)
  * [History](/index.php?title=Using_MPLAB&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Using_MPLAB)

[](/index.php/Main_Page "Main Page" )

##### Navigation

  * [Main Page](/index.php/Main_Page)
  * [Community portal](/index.php/FIRSTwiki:Community_portal)
  * [Current events](/index.php/Current_events)
  * [Recent changes](/index.php/Special:Recentchanges)
  * [Random page](/index.php/Special:Random)
  * [Help](/index.php/Help:Contents)
  * [Donations](/index.php/FIRSTwiki:Site_support)

##### Search



##### Toolbox

  * [What links here](/index.php/Special:Whatlinkshere/Using_MPLAB)
  * [Related changes](/index.php/Special:Recentchangeslinked/Using_MPLAB)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Using_MPLAB&printable=yes)
  * [Permanent link](/index.php?title=Using_MPLAB&oldid=37780)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 15:47, 10 June 2004.
  * This page has been accessed 2,571 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

