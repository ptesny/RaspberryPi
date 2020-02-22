startlxde-pi
============================


The problem [statement](https://www.raspberrypi.org/forums/viewtopic.php?t=210425)

if one assumes that **startx** will launch a graphical Desktop, like the one one would have with an attached monitor?

That's not straightforward if you are accessing an RPi headlessly via SSH.

A simpler alternative is to use VNC as documented by the Raspberry Pi Foundation here:
https://www.raspberrypi.org/documentati ... /README.md

But if you want to persist with your ssh connection, you need the following 3 components for the special sauce needed:
  * Run an X-windows server on your host OS
  * Make the ssh connection with X-windows forwarding enabled
  * From the Raspbian shell prompt, start the GUI with startlxde-pi.
