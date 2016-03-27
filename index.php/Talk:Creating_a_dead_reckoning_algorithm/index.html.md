# Talk:Creating a dead reckoning algorithm

### From FIRSTwiki

Jump to: navigation, search

Do most teams have luck testing with a full battery? We found that if we do
all our testing with a full battery, we need to make sure that we have a full
battery or else it doesn't work. If we tweaked for a slightly discharged
battery, we could run several matches without bad results. I did this 2 years
ago with 73 (we were the first team at the buckeye regional with working
autonomous, and easily the most consistant until early saturday when other
people got theirs working) and last year with 1405. For example, this last
year, we got up on the platform in autonomous. With a full battery we failed
to get up. After running 1 match, we got up. After 2 and 3 matches, we got our
first wheel on the second platform, and after 4 and 5 matches, we got up on
the first platform. It was only after that we failed again. So, how do other
people tweake theirs? --[Sciencewhiz](/index.php/User:Sciencewhiz
"User:Sciencewhiz" ) 11:25, 12 Jul 2004 (EDT)

* * *

Is the name correct? We need some how-to naming standards. I don't like
calling every how-to "creating a....". Well maybe I do, I'm not sure. Just
trying to start a discussion. --[Max](/index.php/User:Max "User:Max" ) 13:48,
11 Jul 2004 (EDT)

* * *

when you are discussing step and time, where are they declared? and how is
time supposed to work? Can you please clarify that section? (especialy since I
think you have it wrong). --[Astronouth7303](/index.php/User:Astronouth7303
"User:Astronouth7303" ) 20:10, 10 Jul 2004 (EDT)

In this code the timer variable is really counting processor cycles through
the slow(26.2ms) loop. I tried to make tha tmore clear in a code comment. The
article also discusses two potential placements for the variable
assignments... Do you feel that this is unclear, or perhaps should be
emphasized more? [Noah](/index.php/User:Noah "User:Noah" )

[[edit](/index.php?title=Talk:Creating_a_dead_reckoning_algorithm&action=edit&
section=1 "Edit section: Formatting C Code" )]

##  Formatting C Code

Is there a guideline in this wiki regarding formatting C code? I have been
indenting all code by 1 space, leading to code that looks like the following:

    
    
    if (some_var)
    {
        some_function();
    }
    

The problem comes with code that involves blank lines inserted to increase
readability. A blank line leads to two different blocks, which in turn looks
like they are different code blocks. My solution was to insert a line
consisting of the space indent followed by a &amp;nbsp; (a nonbreaking space.)
This is invisible to most users, while keeping the block intact. Is there a
preferable way to do this? [Noah](/index.php/User:Noah "User:Noah" )

    wikipedia has the answer, as usual: [wikipedia:preprocessor](http://www.wikipedia.org/wiki/preprocessor "wikipedia:preprocessor" ). They use &lt;pre&gt;code goes here&lt;/pre&gt; around the code block. like so: 
    
    
    code with 
    
    all 
    
    
    the damn
    
    
    blank lines i can
    
    
    
    
    
    
    
    ask for
    

\--[Max](/index.php/User:Max "User:Max" ) 00:42, 12 Jul 2004 (EDT)

Retrieved from "<http://www.firstwiki.net/index.php/Talk:Creating_a_dead_recko
ning_algorithm>"

##### Views

  * [Article](/index.php/Creating_a_dead_reckoning_algorithm)
  * [Discussion](/index.php/Talk:Creating_a_dead_reckoning_algorithm)
  * [Edit](/index.php?title=Talk:Creating_a_dead_reckoning_algorithm&action=edit)
  * [+](/index.php?title=Talk:Creating_a_dead_reckoning_algorithm&action=edit&section=new)
  * [History](/index.php?title=Talk:Creating_a_dead_reckoning_algorithm&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=Talk:Creating_a_dead_reckoning_algorithm)

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

  * [What links here](/index.php/Special:Whatlinkshere/Talk:Creating_a_dead_reckoning_algorithm)
  * [Related changes](/index.php/Special:Recentchangeslinked/Talk:Creating_a_dead_reckoning_algorithm)
  * [Upload file](/index.php/Special:Upload)
  * [Special pages](/index.php/Special:Specialpages)
  * [Printable version](/index.php?title=Talk:Creating_a_dead_reckoning_algorithm&printable=yes)
  * [Permanent link](/index.php?title=Talk:Creating_a_dead_reckoning_algorithm&oldid=39749)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 15:25, 12 July 2004.
  * This page has been accessed 692 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](/index.php/FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](/index.php/FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](/index.php/FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

