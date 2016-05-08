

# 2012 Webcasting &amp; Archiving

### From FIRSTwiki

Jump to: navigation, search

Links to the webcasts are located at [2012 Webcast
Links](2012_Webcast_Links "2012 Webcast Links" ).

This page is based off of [2011 Archiving](2011_Archiving "2011
Archiving" ).

## Contents

  * 1 Overview
  * 2 Required Hardware &amp; Software
  * 3 Setting up the Hardware &amp; Software
    * 3.1 Connecting the Hardware
    * 3.2 Justin.tv
    * 3.3 Video capture device
    * 3.4 Adobe Flash Media Live Encoder
    * 3.5 VH Multi Cam Studio
    * 3.6 VH Capture
  * 4 During the Event
  * 5 After the Event
    * 5.1 Splitting the Video Into Individual Matches
    * 5.2 Upload to YouTube (Recommended)
    * 5.3 Upload to The Blue Alliance/SOAP(?)/First Video Archives (Alternative)
      * 5.3.1 Naming Rules for TBA
      * 5.3.2 Event Abbreviations
  * 6 Who is Archiving What?
    * 6.1 Regional Events
    * 6.2 District Events  
---  
  

##  Overview

**This example will cover using a ~$15 device to capture video, Justin.tv to broadcast, and VH Capture software to archive.**

Part of getting _FIRST_ into the public eye is to increase accessibility to
live webcasts and archived videos of competitions. Hopefully this
documentation will make it easier for volunteers to get as many events
webcasted and archived as possible.

Webcasting and archiving can be done individually, however doing both on one
computer is most efficient. This page outlines a low-cost and easy to set up
process to webcast and archive on a single computer.

If you have any questions, please contact Greg Marra or EugeneF on
ChiefDelphi.

[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=2
"Edit section: Required Hardware & Software" )]

##  Required Hardware &amp; Software

  * Internet connectivity at the event 
    * Work with event coordinators 
    * Preferably wired (better speed and reliability, won't interfere with FMS) 
  * Video/audio feed connectivity at the event 
    * Work with event coordinators 
    * Typically a composite video signal (yellow) with stereo audio (red/white) 
  * Adobe Flash Media Live Encoder v3.2 (Free): <http://www.adobe.com/products/flashmediaserver/flashmediaencoder/>
  * VH Capture &amp; VH Multi Cam Studio (both are included in the download) (Free): <http://download.cnet.com/VH-Screen-Capture-Driver/3000-2169_4-10436367.html>
  * Video capture device 
    * These can get expensive 
    * Affordable solution for composite video to USB input that has been tested (~$15): [http://www.monoprice.com/products/product.asp?c_id=108&amp;cp_id=10810&amp;cs_id=1081003&amp;p_id=5616&amp;seq=1&amp;format=2](http://www.monoprice.com/products/product.asp?c_id=108&cp_id=10810&cs_id=1081003&p_id=5616&seq=1&format=2 "http://www.monoprice.com/products/product.asp?c_id=108&cp_id=10810&cs_id=1081003&p_id=5616&seq=1&format=2" )
    * Make sure the video capture device can handle the inputs available at the event 
  * Computer 
    * Needs internet connectivity 
    * Must be able to interface with the video capture device (typically USB) 
    * ~5 GB hard drive space (depends on video quality &amp; number of matches) 
    * Dual core or more processor preferred 
    * Line In/Microphone input 
    * 3.5mm Stereo to RCA audio adapter 
      * For example (~$1): ([http://www.monoprice.com/products/product.asp?c_id=102&amp;cp_id=10218&amp;cs_id=1021804&amp;p_id=666&amp;seq=1&amp;format=2](http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10218&cs_id=1021804&p_id=666&seq=1&format=2 "http://www.monoprice.com/products/product.asp?c_id=102&cp_id=10218&cs_id=1021804&p_id=666&seq=1&format=2" )) 
  * Justin.tv Account (Free): <http://www.justin.tv>


##  Setting up the Hardware &amp; Software

[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=4
"Edit section: Connecting the Hardware" )]

###  Connecting the Hardware

    

  1. Plug in the video capture device into the proper port on your computer 
  2. Connect the composite video feed (yellow) to the video in port on the video capture device 
  3. Connect the audio feed (red/white) to the 3.5mm Stereo to RCA audio adapter 
  4. Plug the 3.5mm Stereo to RCA audio adapter into the Line in/Microphone port on your computer 

[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=5
"Edit section: Justin.tv" )]

###  Justin.tv

    

  1. Create an account at <http://justin.tv>
  2. While logged in, visit <http://www.justin.tv/broadcast/adv_other> and click "Show" next to "Stream Key:' 
  3. Copy and save the stream key 


###  Video capture device

    

  1. Install the necessary drivers and/or any software that comes with the device 
  2. If software is included with the video capture device, hook up the video capture device to a video source, such as a DVD player, and confirm that video can be displayed on your computer through the included software 


###  Adobe Flash Media Live Encoder

This software broadcasts the video to Justin.tv.

    

  1. Open Adobe Flash Media Live Encoder. 
  2. Adjust the video and audio settings. Suggested settings are below. 
  3. Set "FMS URL" to: rtmp://live.justin.tv/app 
  4. Set "Stream" to the stream key you saved when you set up your Justin.tv account. 

  * Suggested video settings: 
    * Device: VHMultiCam 
    * Format: H.264 
      * Wrench icon: Profile: Main, Level: 5.1, Keyframe Frequency: 3 seconds 
    * Frame Rate: 30 fps 
    * Input Size 720x480 if you're using a composite video source 
      * The resolution can be higher if you're using a higher quality video capture device. 
    * Bit Rate: Check only the first box, ideally ~3000-4000 Kbps 
      * Bitrate will depend on your internet connection. You can check your upload speed at <http://www.speedtest.net>. Set the bitrate to around 500 Kbps (0.5 Mbps) less than your upload speed. There shouldn't be a need to set it to more than 4000 Kbps. 
    * Output Size: Same as "Input Size" 
    * Crop: Unchecked 
    * Deinterlace: Unchecked 
    * Timecode: Unchecked 
  * Suggested audio settings: 
    * Device: Line in/Microphone 
    * Formate: MP3 
    * Channels: Stereo 
    * Sample Rate: 44100 Hz 
    * Bit Rate: 96 Kbps 
    * Volume: Adjust so that the volume preview does not max out 

[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=8
"Edit section: VH Multi Cam Studio" )]

###  VH Multi Cam Studio

This software enables both recording and broadcasting from one piece of
hardware.

    

  1. Open VH Multi Cam Studio 
  2. Under "View," set "Resolution" to "720x480" if you're using a composite video source. The resolution can be higher if you're using a higher quality video capture device 
  3. Under "View," set "Frame rate" to "30 fps." 
  4. Under "File," select "Add Camera," and select the video capture device. 
  5. Resize the video by hovering over it and dragging the white border until it fills the frame. 

[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=9
"Edit section: VH Capture" )]

###  VH Capture

This software records the video.

    

  1. Open VH Capture 
  2. Browse (near the bottom) for a location to store saved videos 
  3. Set the video capture source to VHMultiCam 
  4. Click on the ">" next to browse and make sure it's set on "avi" 
  5. For "Video compression," use a MPEG-4 codec 
  6. Click on the down arrow in the video compression section to get to compressor settings, and set the data rate to 6000 Kbps (6 Mbps) if the option is available. 
  7. Set the frame rate to 30 
  8. Set the audio capture source to Line In/Microphone 
  9. Leave "Audio compression" on "None." 
  10. Record a short clip, paying attention to the CPU usage (shouldn't be maxing out your CPU), Data rate (~10 MB/minute), and Avg. fps (~30). 
  11. Verify that the output file plays, is of reasonable quality, and that sound levels are appropriate. 


##  During the Event

Let everyone know about the webcast! MadStream
(<http://madstream.team1323.com>) (currently undergoing upgrades) will be
providing webcast and score aggregation during the events, so contact them
with the link to your webcast.

If you want to be listed on NASA's website, email drew.r.price[at]nasa.gov
with the url and info about your team/organization.

  * The stream should be started before the opening ceremony and stopped after the awards ceremony. 
  * The recording should be started and stopped before and after each match. DO NOT include the announcers introduction, we are just looking for the robot action. 
    * If no volunteer is able to start and stop the video for each match, a continuous recording can be made, but will require more work and trouble later to parse. See Splitting the Video Into Individual Matches for more details. 
  * To start streaming, press "Start" in Adobe Flash Media Encoder. 
  * To stop streaming, press "Stop" in Adobe Flash Media Encoder. 
  * To start recording, press the record button in VH Capture. 
  * To stop recording, press the stop button in VH Capture. 

[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=11
"Edit section: After the Event" )]

##  After the Event


###  Splitting the Video Into Individual Matches

If someone manually started and stopped the video for each match, you may
ignore this section.

Splitting the video into individual matches can be done with whatever video
editing program you would like, every Windows machine comes with Windows Movie
Maker and every Mac comes with iMovie. As for the output video and naming
standards please see below!

  * DO NOT include the announcers introduction, we are just looking for the robot action. 
  * End the video once the play has stopped, if you like you can cut in the final score (this is a bit of a pain, and TBA already has it listed on their site anyway). 


###  Upload to YouTube (Recommended)

The Blue Alliance (<http://www.thebluealliance.com>) is currently working on
using YouTube to host the videos. This method will be easier than the
traditional method of uploading files to TBA (less work renaming files,
converting them to proper formats, etc.). Also, it allows the quality of the
videos to be much better, as TBA won't have to worry about server space.

This spreadsheet tracks videos on YouTube so we can add them to TBA. <https://
docs.google.com/spreadsheet/ccc?key=0ApRO2Yzh2z01dExFZEdieV9WdTJsZ25HSWI3VUxsW
Gc>

[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=14
"Edit section: Upload to The Blue Alliance/SOAP\(?\)/First Video Archives
\(Alternative\)" )]

###  Upload to The Blue Alliance/SOAP(?)/First Video Archives (Alternative)

This is the traditional method to upload videos to TBA. Contact Greg Marra or
Jonathan Norris or Mike Aalderink on the Chief Delphi forums for more
information about how to send video to the TBA and SOAP and Firstvideo
Archives via FTP.

**Video Format Standards:**

  * Format: MPEG4 or H264 (.mp4, .mpv, or .mov are all acceptable containers). WMV is acceptable, but for reasons explained below not favored 
  * File Size: 15-25 Mb per file, this roughly a bitrate of: 1000-1250 kb/s, with an audio bitrate of: 128 kb/s. 
    * Video Resolution: recommended 640X480, acceptable 320X240 
    * HTTP Streaming: when encoding the video to its final format of MPEG4 or h264 enable HTTP streaming (for most encoders it will be an option). This will allow anyone with a smart phone, iPhone, or iPod touch to stream the matches and watch them directly on their handset. 

[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=15
"Edit section: Naming Rules for TBA" )]

####  Naming Rules for TBA

**Example File Names:**

  * ct_001.mp4 
  * fl_qf2m1.wmv 
  * ca_fm1.wmv 

**Naming Rules:**

  * Two or three character event abbreviation in lowercase, e.g. "fl" 
  * Underscore, "_" 
  * XOR: 
    * Qualification: Use THREE digits, "001", "047", "108". 
    * Elimination: Use "qf4m2", "sf2m1", "fm3" 
    * Awards: Use "award_" + AwardDescription. 
    * Opening: Use "openingremarks_" + "friday" or "saturday". 
    * Closing: Use "closingremarks_" + "friday" or "saturday". 
    * Else: any string that does not begin with "qf", "sf", "fm", or a digit. 
  * ".wmv" , ".mov", ".divx" , ".whatever" 

**Notes:**

  1. Always use lowercase, please. 
  2. No spaces in a filename, please. 
  3. Sometimes a match gets replayed- name the one that counts in the standings as "fl_001.wmv". The one(s) that do NOT count, "fl_001bad1.wmv", "fl_001bad2.wmv", etc... 

[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=16
"Edit section: Event Abbreviations" )]

####  Event Abbreviations

stx | Alamo |   | swm | Niles FiM  
---|---|---|---|---  
az | Arizona |   | nc | North Carolina  
or | Autodesk Oregon |   | ct | Northeast Utilities Connecticut  
nh | BAE Granite State |   | wca | Northville FiM  
la | Bayou |   | ok | Oklahoma  
in | Boilermaker |   | fl | Orlando  
ma | Boston |   | sc | Palmetto  
oh | Buckeye |   | ga | Peachtree  
caf | Central Valley |   | pit | Pittsburgh  
md | Chesapeake |   | ohc | Queen City  
phl | Chestnut Hill MAR |   | nj | Rutgers University MAR  
co | Colorado |   | sac | Sacramento  
da | Dallas East |   | sdc | San Diego  
da2 | Dallas West |   | li | SBPLI Long Island  
dt | Detroit FiM |   | wa2 | Seattle Cascade  
qc | Festival de Robotique FRC a Montreal |   | wa | Seattle Olympic  
roc | Finger Lakes |   | sj | Silicon Valley  
kc | Greater Kansas City |   | tn | Smoky Mountain  
on | Greater Toronto East |   | sfl | South Florida  
on2 | Greater Toronto West |   | was | Spokane  
pah | Hatboro-Horsham MAR |   | mo | St. Louis  
hi | Hawaii |   | gt | Traverse City FiM  
gg | Kettering University FiM |   | ut | Utah  
is | Israel |   | oc | Troy FiM  
dmn | Lake Superior |   | va | Virginia  
nv | Las Vegas |   | dc | Washington DC  
njt | Lenape MAR |   | oc1 | Waterford FiM  
ww | Livonia FiM |   | wat | Waterloo  
tx | Lone Star |   | mi | West Michigan FiM  
ca | Los Angeles |   | wi | Wisconsin  
gl | Michigan State Championship |   | wor | WPI  
pa | Mid-Atlantic Region Championship |   | cmp | FIRST Championship  
il | Midwest |   | arc | FIRST Championship - Archimedes Division  
mn | Minnesota 10000 Lakes |   | cur | FIRST Championship - Curie Division  
mn2 | Minnesota North Star |   | gal | FIRST Championship - Galileo Division  
njf | Mount Olive MAR |   | new | FIRST Championship - Newton Division  
ny | New York City |   | ein | FIRST Championship - Einstein Field  
  
[[edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit&section=17
"Edit section: Who is Archiving What?" )]

##  Who is Archiving What?


### Regional Events

**Dates** | **Regional Name** | **Webcast Provided By (Name/Team #)** | **Archiving Provided By (Name/Team #)**  
---|---|---|---  
Mar. 1-3| Greater Kansas City| |  
Mar. 1-3| BAE Systems Granite State| |  
Mar. 1-3| Smoky Mountains| FRC1466/FRC2200|  
Mar. 1-3| Alamo| |  
Mar. 2-4| San Diego| |  
Mar. 5-7| Israel| |  
Mar. 8-10| Greater Toronto East| FRC2200| FRC2200  
Mar. 8-10| Orlando| |  
Mar. 8-10| WPI| |  
Mar. 8-10| Chesapeake| |  
Mar. 8-10| Lake Superior| |  
Mar. 8-10| Finger Lakes| |  
Mar. 8-10| Oregon| |  
Mar. 8-10| Pittsburgh| |  
Mar. 15-17| Montreal| |  
Mar. 15-17| Sacramento| FRC604| FRC604  
Mar. 15-17| Los Angeles| |  
Mar. 15-17| Peachtree| |  
Mar. 15-17| Boilermaker| |  
Mar. 15-17| Bayou| |  
Mar. 15-17| Utah| |  
Mar. 15-17| Virginia| |  
Mar. 16-18| New York City| |  
Mar. 22-24| Waterloo| FRC2200| FRC2200  
Mar. 22-24| Arizona| |  
Mar. 22-24| Colorado| |  
Mar. 22-24| Hawaii| |  
Mar. 22-24| Midwest| |  
Mar. 22-24| Boston| Daniel Bathgate| Daniel Bathgate  
Mar. 22-24| St. Louis| |  
Mar. 22-24| Buckeye| |  
Mar. 22-24| Palmetto| |  
Mar. 22-24| Seattle Olympic| |  
Mar. 22-24| Seattle Cascade| |  
Mar. 22-24| Wisconsins| |  
Mar. 29-31| Greater Toronto West| FRC2200| FRC2200  
Mar. 29-31| Silicon Valley| FRC604| FRC604  
Mar. 29-31| Northeast Utilities FIRST Connecticut| |  
Mar. 29-31| Washington DC| |  
Mar. 29-31| South Florida| |  
Mar. 29-31| Minnesota 10000 Lakes| |  
Mar. 29-31| Minnesota North Star| |  
Mar. 29-31| SBPLI Long Island| |  
Mar. 29-31| Oklahoma| Steven Bell| Steven Bell  
Mar. 29-31| Dallas East| |  
Mar. 29-31| Dallas West| |  
Apr. 5-7| Central Valley| FRC1323| FRC1323  
Apr. 5-7| North Carolina| FRC2059| FRC2059  
Apr. 5-7| Las Vegas| |  
Apr. 5-7| Queen City| |  
Apr. 5-7| Lone Star| |  
Apr. 5-7| Spokane| |  
  

### District Events

**Dates** | **Regional Name** | **Webcast Provided By (Name/Team #)** | **Archiving Provided By (Name/Team #)**  
---|---|---|---  
Mar. 2-3| Kettering University| |  
Mar. 2-3| Gull Lake| |  
Mar. 2-3| Hatboro-Horsham| |  
Mar. 9-10| Traverse City| |  
Mar. 9-10| Waterford| |  
Mar. 9-10| Chestnut Hill| |  
Mar. 10-11| Rutgers University| |  
Mar. 16-17| West Michigan| | FRC 3458 Mike Aalderink  
Mar. 16-17| Detroit| |  
Mar. 23-24| Niles| | FRC 3458 Mike Aalderink  
Mar. 23-24| Northville| |  
Mar. 24-25| Lenape| |  
Mar. 30-31| Livonia| |  
Mar. 30-31| Troy| |  
Mar. 31-Apr. 1| Mount Olive| |  
Apr. 12-14| Michigan FRC State Championship| |  
Apr. 12-14| Mid-Atlantic Robotics FRC Region Championship| |  
  
  

Retrieved from
"<http://firstwiki.net2012_Webcasting_%26_Archiving>"

##### Views

  * [Article](2012_Webcasting_%26_Archiving)
  * [Discussion](Talk:2012_Webcasting_%26_Archiving)
  * [Edit](/index.php?title=2012_Webcasting_%26_Archiving&action=edit)
  * [History](/index.php?title=2012_Webcasting_%26_Archiving&action=history)

##### Personal tools

  * [Log in / create account](/index.php?title=Special:Userlogin&returnto=2012_Webcasting_%26_Archiving)

[](Main_Page "Main Page" )

##### Navigation

  * [Main Page](Main_Page)
  * [Community portal](FIRSTwiki:Community_portal)
  * [Current events](Current_events)
  * [Recent changes](Special:Recentchanges)
  * [Random page](Special:Random)
  * [Help](FIRSTwiki:Help)
  * [Donations](FIRSTwiki:Site_support)

##### Search



##### Toolbox

  * [What links here](Special:Whatlinkshere/2012_Webcasting_%26_Archiving)
  * [Related changes](Special:Recentchangeslinked/2012_Webcasting_%26_Archiving)
  * [Upload file](Special:Upload)
  * [Special pages](Special:Specialpages)
  * [Printable version](/index.php?title=2012_Webcasting_%26_Archiving&printable=yes)
  * [Permanent link](/index.php?title=2012_Webcasting_%26_Archiving&oldid=93270)

[![MediaWiki](/skins/common/images/poweredby_mediawiki_88x31.png)](http://www.
mediawiki.org/)

[![GNU Free Documentation License 1.2](/stylesheets/images/gnu-
fdl.png)](http://www.gnu.org/copyleft/fdl.html)

  * This page was last modified 05:19, 9 March 2012.
  * This page has been accessed 2,781 times.
  * Content is available under [GNU Free Documentation License 1.2](http://www.gnu.org/copyleft/fdl.html "http://www.gnu.org/copyleft/fdl.html" ).
  * [Privacy policy](FIRSTwiki:Privacy_policy "FIRSTwiki:Privacy policy" )
  * [About FIRSTwiki](FIRSTwiki:About "FIRSTwiki:About" )
  * [Terms and Conditions](FIRSTwiki:Terms_and_conditions "FIRSTwiki:Terms and conditions" )

