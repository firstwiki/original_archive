# Template talk:Teamtable

## From FIRSTwiki

Jump to: navigation, search

[[edit](/index.php?title=Template_talk:Teamtable&action=edit&section=1 "Edit
section: Comments")]

## Comments

Since it seems like this part of the [Team page format](FIRSTwiki:Team_page_format "FIRSTwiki:Team page format") keeps changing, maybe it should be a template. It is the one part of the page that is template-able. --[Astronouth7303](User:Astronouth7303 "User:Astronouth7303") 14:27, 21 Aug 2004 (EDT)

[[edit](/index.php?title=Template_talk:Teamtable&action=edit&section=2 "Edit
section: Problems with more than one of something")]

## Problems with more than one of something

I have noticed on several occations now that this template seems to have problems whenever someone tries to add more than one thing in a catagory by adding another line for the second thing. For example, what would happen for more than one school:

```
{{teamtable|
|name=Team Name
|color=Some Color
|image=An image
|year=A year
|school=School 1
School 2
|location=Random place
|website=The website
|size=People
}}
```

You could also try doing the school option twice with the same result:

```
{{teamtable|
|name=Team Name
|color=Some Color
|image=An image
|year=A year
|school=School 1
|school=School 2
|location=Random place
|website=The website
|size=People
}}
```

The result of either of these will generate something like what happened on this page: [1382](1382 "1382") (note the bits of code at the top of the page that isn't supposed to be there).

Would it be possible to add a feature that would allow more than one thing to be added in the same catagory using this template? I don't know enough about wiki code to do it myself. [Cbale2000](User:Cbale2000 "User:Cbale2000") 12:28, 15 January 2008 (EST)

```
 To my knowledge, no. Having more than 1 value for the same parameter is simply impossible. Just put in all the values separated by `<br>`. --[Astronouth7303](User:Astronouth7303 "User:Astronouth7303" ) 10:42, 3 March 2008 (EST) 
```

[[edit](/index.php?title=Template_talk:Teamtable&action=edit&section=3 "Edit
section: More links")]

## More links

The current template links to the TIMS information page. Could we expand this to include things like TBA? --[Astronouth7303](User:Astronouth7303 "User:Astronouth7303") 10:46, 3 March 2008 (EST)

Does TBA have predictible non-changing page names for every team, something like the TIMS pages? If they do, it probably wouldn't be that hard to set up. [Cbale2000](User:Cbale2000 "User:Cbale2000") 14:13, 3 March 2008 (EST)

- Yep. Format is "[http://www.thebluealliance.net/tbatv/team.php?team=<teamNumber>](http://www.thebluealliance.net/tbatv/team.php?team=<teamNumber&gt);", where <teamNumber> is formatted without leading zeros. For example, pages for teams [612](http://www.thebluealliance.net/tbatv/team.php?team=612 "http://www.thebluealliance.net/tbatv/team.php?team=612") and [47](http://www.thebluealliance.net/tbatv/team.php?team=47 "http://www.thebluealliance.net/tbatv/team.php?team=47"). [Nlaverdure](User:Nlaverdure "User:Nlaverdure") 12:34, 4 March 2008 (EST)

- That should be easy then, all you'd have to do is create a link where the page name comes after the "team=" part of the url. Not sure what the code for that is right off hand but I'll do some looking around. [Cbale2000](User:Cbale2000 "User:Cbale2000") 13:01, 4 March 2008 (EST)

```
Well it seems to work, what do you think? [Cbale2000](User:Cbale2000 "User:Cbale2000" ) 13:08, 4 March 2008 (EST) 
```

- Very nice. How about adding a link to team photos on CD? The format is "[http://www.chiefdelphi.com/media/photos/tags/frc<teamNumber>](http://www.chiefdelphi.com/media/photos/tags/frc<teamNumber&gt);," so I guess the format of the addition to the teamtable would be:

```
|-
!align="left" valign="top"|Photos on ChiefDelphi:
|valign="top"|{{{teaminfo|[http://www.chiefdelphi.com/media/photos/tags/frc{{PAGENAME}} www.chiefdelphi.com/media]}}}






 \--[Nlaverdure](User:Nlaverdure "User:Nlaverdure" ) 19:22, 4 March 2008 (EST) 







 Good idea, though I think I'm going to try to compress the info links a bit, don't want to get the template too cluttered. [Cbale2000](User:Cbale2000 "User:Cbale2000" ) 12:19, 5 March 2008 (EST) 
 You know, since we seem to have the space issue solved with the new side by side arrangement of links, perhaps we should go ahead and add the ChiefDelphi Photos links? [Cbale2000](User:Cbale2000 "User:Cbale2000" ) 17:34, 18 June 2008 (EDT) 
```
