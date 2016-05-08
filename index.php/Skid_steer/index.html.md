# Skid steer

## From FIRSTwiki

Jump to: navigation, search

**Skid steer**, or **Tank drive**, is the most common form of [drive train](Drive_train "Drive train") on robots. It involves two sets of wheels (or treads), one on the left and one on the right, which are individually powered. This allows turning by driving each side at unequal velocities. When the control system comes out of the box this is the default configuration of the controls.

So to stop, stop both sides:<br>
[![Image:Skid_None.png](/media/8/8f/Skid_None.png)](Image:Skid_None
.png "Image:Skid_None.png")

To go forward (or backward), set both sides equal:<br>
[![Image:Skid_Forward.png](/media/7/76/Skid_Forward.png)](Image:Ski
d_Forward.png "Image:Skid_Forward.png")

To make a turn around the left side, set Left to 0 and Right to something else:<br>
[![Image:Skid_Left1.png](/media/9/99/Skid_Left1.png)](Image:Skid_Le
ft1.png "Image:Skid_Left1.png")

To do a turn-in-place to the left, set Left to the opposite of Right:<br>
[![Image:Skid_Left2.png](/media/6/62/Skid_Left2.png)](Image:Skid_Le
ft2.png "Image:Skid_Left2.png")

To do a shallow right turn, set Right to about half of Left:<br>
[![Image:Skid_Right0p5.png](/media/5/51/Skid_Right0p5.png)](Image:S
kid_Right0p5.png "Image:Skid_Right0p5.png")
