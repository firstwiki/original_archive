

# Network rendering

### From FIRSTwiki

Jump to: navigation, search

_Note: This article is written assuming that the rendering is taking place on
a network of Windows 2000 computers with restricted user privileges, and that
the user has a network drive with a large storage capacity available._

**Network rendering** is the process of getting multiple computers to render the individual frames of an [animation](Animation "Animation" ) in order to decrease the amount of time needed before the animation is complete. The animation for the [Autodesk Visualization Competition](Autodesk_Visualization_Award "Autodesk Visualization Award" ) is limited to being thirty seconds long. 30 seconds of animation at about 30 frames per second is 900 rendered frames. In some cases, one frame rendered relatively photo realistically can take two hours to render. If one computer were to render a 900 frame animation, taking two hours to render each frame, it would take seventy-five days to render. By using a lab of twenty computers, it would take less than four days. This makes it possible to complete an animation during the period of the competition, and be able to render it at nights when the computer lab is not being used for teaching. 

In order to network render, a team must have access to a group of computers on
a network. This is the first step, find a group of relatively fast computers
on the same network (preferably in the same room, but it isn’t required) that
won't be needed overnight at any time during the competition. Each computer
must have a copy of [3D Studio Max](3D_Studio_Max "3D Studio Max" )
on it for the rendering to work. In the case of this competition, if a school
doesn't have a lab of computers with 3DS Max on it that can be used by a team,
an alternative is to install an unregistered trial version of 3DS Max onto
each computer; this will work for 30 days before 3DS Max requires
registration.

3D Studio Max comes with its own network rendering software, Backburner 2.
There are three different parts to Backburner: servers, the manager, and the
monitor. The manager runs the show, it tells the servers which frame of the
animation they are to render. The manager computer is the computer that has
3DS open with the animation on it. The servers are all of the other computers,
and even the manager computer can run a server at the same time. The monitor
is just a program that allows the user to interface with the manager.

[![Rendering Window](/media/thumb/7/75/Render_scene_net_render.jpg/180px-
Render_scene_net_render.jpg)](Image:Render_scene_net_render.jpg
"Rendering Window" )

[![Enlarge](/skins/common/images/magnify-
clip.png)](Image:Render_scene_net_render.jpg "Enlarge" )

Rendering Window

Before rendering can occur, a team must have at least one scene completed from
their animation. All of the texture images that were used in the animation
must be copied to one folder on a network drive (the servers won't be able to
find the textures on the local hard drive of another computer) In other words,
go through all of the texture files and change them from something like
"C:\myfiles\tex1.jpg" to something like
"\\\NetworkUserName\sharedtexturefolder\tex1.jpg". Activate the manager on the
computer with the animation file open. Activate a server on each computer that
will be used to render. Open the monitor on the manager computer, and check
that all of the servers have connected. In 3DS, in the rendering window, set
the output location to a folder in the network drive, and output as some type
of picture file format (AVIs will not work, tiffs are a good option). Then,
select 'network render', and hit the render button.

A new box will appear, click 'connect'. Set the alternate texture path to the
folder that was created on the network drive. Then start the rendering.

[![Network Job Assignment dialog
box](/media/thumb/4/41/Network_job_assignment.jpg/180px-
Network_job_assignment.jpg)](Image:Network_job_assignment.jpg
"Network Job Assignment dialog box" )

[![Enlarge](/skins/common/images/magnify-
clip.png)](Image:Network_job_assignment.jpg "Enlarge" )

Network Job Assignment dialog box

The monitor should show each server computer starting to render.

The manager computer will save each frame to the network drive, attaching a
number to the end. The frames will be numbered in order; in a thirty second
animation they will be numbered from 000 to 899.

The final step is combine all of the still images into a video file. This can
be done with many programs, including Adobe Premiere or tools built into 3DS
Max. Adobe Premiere is the most powerful option if your team has a copy, but
otherwise you need to use the tools in 3DS Max.

In 3DS Max, the best tool to use to composite the images is video post. The
correct process for using this is detailed in the 3DS Max User Reference under
the topic 'Useful Video Post Procedures'.

It is also possible, though it requires a single file sequence, to do this in
the RAM player. This way is not documented in the 3DS Max help files or
tutorials, and it may cause your computer to slow down or freeze if you do not
have enough RAM. Open the RAM player (Rendering->Ram Player), and open the
sequence of images by selecting the first image in the sequence, and checking
the ‘sequence’ box. After all of the images are loaded, play the file to make
sure it is correct, and output as .mov (note that file format requirements may
change year to year - please see [the FIRST webpage](http://www.usfirst.org
"http://www.usfirst.org" ) for current rules)

