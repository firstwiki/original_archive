# Talk:Multiple autonomous modes

### From FIRSTwiki

Jump to: navigation, search

Any reason to use a macro? It's kinda bad practice to utilize the preproccesor
too much. It creates room for problems that a debugger can't find. The fact
that the default code already contains such a huge number of #define's doesnt
help. If they are read in the wrong order, trouble can easily arise. (I think
the variables in your macro would actually be #defined 3 times from the
original PIC registers.) --[Max](/index.php/User:Max "User:Max" ) 12:38, 5 Jun
2004 (EDT)

**Concerning my recent edit ...** I agree with [Max](/index.php/User:Max "User:Max" ) about the macro thing. Personally, we used a simple switch that was either on or off, so the choice was easier ... but we also implemented a pot select, where we called a "step" function that would return a certain value for a given range. I think something like that would be best ... but of course, it all depends, as there's a wide variety of selecting mechanisms out there. To the point, though, I kept your way of doing it, namely 
    
    
       #define SELECT_AUTO_MODE (char)((p4_sw_trig<<3) | (p4_sw_top<<2) |  \
         (p4_sw_aux1<<1) | p4_sw_aux2)
    

But I believe you should explain what this does. It is by no means the
simplest (and IMO would only confuse new people looking at it), but if you
want to keep it, at least explain in words what it does.

I did change the macro name, however. I felt OI_AutoChoice was a bad name,
because it doesn't insulate the user from the implementation. If you should
change the selector from the OI to the RC, so long as it returns a number in
the right range, why should the user care where it came from? Also, by most
sensible styles, macro names are all capped. I did a few other minor edits ...
hopefully nothing controversial. Though, I'll try to add my code for selecting
multiple autons, since we put a switch on the RC it should offer a nice
contrast and cover the issue more fully (I don't have the code with me ...
recently cleaned up my computer). --[Mrawls](/index.php/User:Mrawls
"User:Mrawls" ) 12:53, 5 Jun 2004 (EDT)

Thank you for your comments, and I will try to implement them when I have
time. :rolleyes: Also, It makes the macro far more readable if i use
p4_sw_trig then if I had used rxdata.oi_swB_byte.bitselect.bit4. (And in the
actual code, I had one more #define: OI_Auto_Bit1)
--[Astronouth7303](/index.php/User:Astronouth7303 "User:Astronouth7303" )
13:36, 5 Jun 2004 (EDT)

    I wasn't saying that you shouldn't use the aliased names, I was saying that you shouldn't use a macro, rather, use a function. As I said before, macro's don't get debugged, only the final code that gets compiled can be debugged. Macros also introduce new kinds of problems because the order in which they are included matters while regular code doesn't matter (as long as function declarations come before their first usage.) --[Max](/index.php/User:Max "User:Max" ) 15:19, 5 Jun 2004 (EDT) 

Nothing wrong with too many #defines, so far as I know, so long as they do
their job -- i.e., aid in abstraction and only have to change something once,
instead of many times, etc. I just felt that a function might be more
appropriate as a general solution to offer teams. (Maybe Max could explain why
this constitutes excessive use of the preprocessor.) But as far as your
description,

    
    
     What this example does is it takes each bit, bit-shifts it up the appropriate amount, and ORs it with the other bits, generating a number (in this case, 0 to 15 (2^4 - 1).
    

Yes, this explains what the code does, and that is a good thing (I imagine we
should have some bit-wise operator pages) ... but it doesn't explain how the
user would actually use the code. I.e., what would the operator press to get
mode 13 activated, for instance. I assume it's a joystick you are connecting
to the port, ... so I'd explain the sequence of button pushes, or at least a
few examples of them. (Oh, and this seems like a good article to put on
[FIRSTwiki:Featured article
candidates](/index.php/FIRSTwiki:Featured_article_candidates
"FIRSTwiki:Featured article candidates" ). Putting there now ...)
--[Mrawls](/index.php/User:Mrawls "User:Mrawls" ) 14:32, 5 Jun 2004 (EDT)

Retrieved from
"<http://www.firstwiki.net/index.php/Talk:Multiple_autonomous_modes>"

##### Views

  * [Article](/index.php/Multiple_autonomous_modes)
  * [Discussion](/index.php/Talk:Multiple_autonomous_modes)
  * [Edit](/index.php?title=Talk:Multiple_autonomous_modes&action=edit)
  * [+](/index.php?title=Talk:Multiple_autonomous_modes&action=edit&section=new)
  * [History](/index.php?title=Talk:Multiple_autonomous_modes&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Talk:Multiple_autonomous_modes)

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

  * [What links here](/index.php/Special:Whatlinkshere/Talk:Multiple_autonomous_modes)
  * [Related changes](/index.php/Special:Recentchangeslinked/Talk:Multiple_autonomous_modes)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Talk:Multiple_autonomous_modes&printable=yes)
  * [Permanent link](/index.php?title=Talk:Multiple_autonomous_modes&oldid=39103)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 19:19, 5 June 2004.
  * This page has been accessed 410 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

