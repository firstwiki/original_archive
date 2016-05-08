# Talk:Programming the Robot Controller

### From FIRSTwiki

Jump to: navigation, search

About the "this focusses on PIC C" edit -- how exaxtly does the article focus
on "PIC C"? The sections all seem to be pretty basic, bare level C
programming, nothing specific to the PIC Chip. An article on programming
interrupts would have to focus on "PIC C" since that is low level hardware
business ... an article on PIC C for dummies would obviously focus on PIC C
... but this is a general overview of C, and doesn't seem to mention a single
thing unique to "PIC C". I don't mean to fuss, but we don't want to confuse
people who are earnestly trying to learn. --[Mrawls](User:Mrawls
"User:Mrawls" ) 14:04, 23 Jun 2004 (EDT)

    The name is "Programming the Robot Controller", which says nothing about whether it is for the '04 RC or previous RCs. --[Astronouth7303](User:Astronouth7303 "User:Astronouth7303" ) 14:08, 23 Jun 2004 (EDT) 

    Sure, and I imagine we can update the page yearly, reflecting the new programming reference guide and archive the older versions on yearly pages. But I don't think it will change much, -- it's all but certain we'll be using C next year. My point, though, was this article isn't specific to PIC C. In fact, PIC C, as you call it, differs from ANSI C in only a few minor instances. --[Mrawls](User:Mrawls "User:Mrawls" ) 14:30, 23 Jun 2004 (EDT) 

    I know that and you know that. But if you were to ask microchip what we program in, they'd say PIC C. --[Astronouth7303](User:Astronouth7303 "User:Astronouth7303" ) 14:36, 23 Jun 2004 (EDT) 

    If you're going to be pedantic like that, we program a Pic 18 series in C using the MPLAB C18 compiler. Otherwise, it doesn't really matter, because it's all so similar. If you were to ask Microchip what we program in, they'd say C. They'd only specify the differences if you asked them about something where the differences matter. 

* * *

According to the previous discussion, I've moved the articles dealing with
Robot Controller to proper noun form. I'm addressing the links to these
articles, and will try to get the plain text, too. Help would be appreciated,
if I've missed anything. Oh, and I assume the same thing will need to be done
to [Operator interface](Operator_interface "Operator interface"
)?--[Mrawls](User:Mrawls "User:Mrawls" ) 13:15, 23 Jun 2004 (EDT)

    Yep --[Sciencewhiz](User:Sciencewhiz "User:Sciencewhiz" ) 13:24, 23 Jun 2004 (EDT) 

* * *

Why did you move it? you also mis-capped it.
--[Astronouth7303](User:Astronouth7303 "User:Astronouth7303" )
21:39, 20 Jun 2004 (EDT)

    FRC can be confused with FIRST robotics competition and I think RC/Robot controller is more common than FRC. It's possible the caps aren't wrong, depends whether RC is proper or not. --[Max](User:Max "User:Max" ) 00:00, 21 Jun 2004 (EDT) 

    

    All titles should be capitalized, but Robot Controller is also a proper noun in this case, as far as I remember. -- [Maddie](User:Maddie "User:Maddie" )

    

    I do agree with the new title (I stuck with the old because it was there and, like a great programmer, I am lazy). However, all titles should not be capitalized, -- see [FIRSTwiki:Style guide](FIRSTwiki:Style_guide "FIRSTwiki:Style guide" ). If you like it that way, we can discuss it there, but it currently is against our style manual. And Robot Controller is not a proper noun, so far as I see it, so I think [Programming the robot controller](/index.php?title=Programming_the_robot_controller&action=edit "Programming the robot controller" ) would be best. --[Mrawls](User:Mrawls "User:Mrawls" ) 11:57, 21 Jun 2004 (EDT) 

    

    

    Robot Controller is a proper noun, used in this case. IFI capitalizes it in all of their documentation, as well. --[Sciencewhiz](User:Sciencewhiz "User:Sciencewhiz" ) 13:06, 21 Jun 2004 (EDT) 

    

    

    I stand corrected. And now quite a few articles have to be adjusted. Also, I suppose [Robot controller](Robot_controller "Robot controller" ) should redirect to [Robot Controller](Robot_Controller "Robot Controller" ) ... A clarification, though: you say "in this case". Is it always a proper noun, or only when a specific version is referred to? This doesn't refer to a specific version, so I guess I should ask, when is it not a proper noun. --[Mrawls](User:Mrawls "User:Mrawls" ) 14:38, 21 Jun 2004 (EDT) 

    

    

    

    Meaning refering to IFI's Robot Controller, not to a robot controller that, say, I designed. --[Sciencewhiz](User:Sciencewhiz "User:Sciencewhiz" ) 15:33, 21 Jun 2004 (EDT) 

    

    

    So are we all in agreement? Change all Robot controller articles to Robot Controller? --[Max](User:Max "User:Max" ) 16:20, 21 Jun 2004 (EDT) 

* * *

"Robot controller (2003)" ah, yes, even better name for it, time to change
some links --[Max](User:Max "User:Max" ) 22:25, 28 May 2004 (EDT)

    New style suggestion for all: Make a general page first, then make pages with titles like "[General title here] ([specific year])" --[SilverStar](User:SilverStar "User:SilverStar" ) 22:27, 28 May 2004 (EDT) 
    I'm going to change the Team pages like that also. --[SilverStar](User:SilverStar "User:SilverStar" ) 22:27, 28 May 2004 (EDT) 
    Are you going to use "Full RC" or "Robot Controller"? I set all my pages up as 200# Full RC or EDU bot --[Astronouth7303](User:Astronouth7303 "User:Astronouth7303" ) 22:32, 28 May 2004 (EDT) 

Under the comments section, the second bullet in the list at the bottom says
something about being able to have multi-line comments without adding '/*' at
the beginning of each line. Shouldn't that be moved up with the C-style
comments and make it '//' instead? Confusing. :) Good work on this though
--[Texan](User:Texan "User:Texan" ) 15:49, 8 Jun 2004 (EDT)

Your right. Let me clarify here.

If you were to use only C style comments, some code might look llike this:

    
    
    DoSomething(); /* Does something */
    DoSomethingElse(); /* Does something else */
    DoSomethingNovel(); /* Does something novel */
    

But if you wanted to comment it out, it would now look like:

    
    
    /* DoSomething(); /* Does something */
    /* DoSomethingElse(); /* Does something else */
    /* DoSomethingNovel(); /* Does something novel */
    

If you were to use C++ comments, it would be:

    
    
    DoSomething(); // Does something
    DoSomethingElse(); // Does something else
    DoSomethingNovel(); // Does something novel
    

Now commenting the block out would be:

    
    
    /* DoSomething(); // Does something
     DoSomethingElse(); // Does something else
     DoSomethingNovel(); // Does something novel */
    

Get it? --[Astronouth7303](User:Astronouth7303
"User:Astronouth7303" ) 16:27, 8 Jun 2004 (EDT)

    That was a clarification?!? :P Are you saying that C++ style comments are useful because they allow you to comment out blocks of code which include line comments (since C style comments cannot be nested)? We really need some sort of ` tags that cause some sort of table/box to separate code and preserve line breaks, etc., to make this easier to read.` Well look at that, we do have code tags. I inadvertnatly stumbled upon them ... --[Mrawls](User:Mrawls "User:Mrawls" ) 16:43, 8 Jun 2004 (EDT) 

    

    Sorry, there was a slight error with the second block. 
    Yes, that's what the second bullet in the article is saying. Also, You can't forget to end a comment. --[Astronouth7303](User:Astronouth7303 "User:Astronouth7303" ) 17:15, 8 Jun 2004 (EDT) 

Retrieved from
"<http://www.firstwiki.netTalk:Programming_the_Robot_Controller>"

##### Views

  * [Article](Programming_the_Robot_Controller)
  * [Discussion](Talk:Programming_the_Robot_Controller)
  * [Edit](/index.php?title=Talk:Programming_the_Robot_Controller&action=edit)
  * [+](/index.php?title=Talk:Programming_the_Robot_Controller&action=edit&section=new)
  * [History](/index.php?title=Talk:Programming_the_Robot_Controller&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Talk:Programming_the_Robot_Controller)

[](Main_Page "Main Page" )

##### Navigation

  * [Main Page](Main_Page)
  * [Community portal](FIRSTwiki:Community_portal)
  * [Current events](Current_events)
  * [Recent changes](Special:Recentchanges)
  * [Random page](Special:Random)
  * [Help](Help:Contents)
  * [Donations](FIRSTwiki:Site_support)

##### Search



##### Toolbox

  * [What links here](Special:Whatlinkshere/Talk:Programming_the_Robot_Controller)
  * [Related changes](Special:Recentchangeslinked/Talk:Programming_the_Robot_Controller)
  * [Upload file](Special:Upload)
  * [Special pages](Special:Specialpages)
  * [Printable version](/index.php?title=Talk:Programming_the_Robot_Controller&printable=yes)
  * [Permanent link](/index.php?title=Talk:Programming_the_Robot_Controller&oldid=37810)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 20:56, 23 June 2004.
  * This page has been accessed 2,267 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

