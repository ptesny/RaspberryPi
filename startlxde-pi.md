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


## X11 connection rejected because of wrong authentication.

```
$ startlxde-pi &
[1] 2583
pi@phoscon:~ $ ** Message: 18:10:11.832: main.vala:101: Session is LXDE-pi
** Message: 18:10:11.832: main.vala:102: DE is LXDE
** Message: 18:10:11.992: main.vala:133: log directory: /home/pi/.cache/lxsession/LXDE-pi
** Message: 18:10:11.992: main.vala:134: log path: /home/pi/.cache/lxsession/LXDE-pi/run.log
X11 connection rejected because of wrong authentication.
```

```
$ xauth list $DISPLAY
phoscon/unix:10  MIT-MAGIC-COOKIE-1  32b3f20f1adc511445b76e7573f090e1

$ sudo su
root@phoscon:/home/pi# 
root@phoscon:/home/pi# xauth merge /home/pi/.Xauthority
xauth:  file /root/.Xauthority does not exist
root@phoscon:/home/pi# cp /home/pi/.Xauthority /root
root@phoscon:/home/pi# 
root@phoscon:/home/pi# exit
exit

```

### running startlxde-pi as root user (not recommended)

```
pi@phoscon:~ $ xauth list $DISPLAY
phoscon/unix:10  MIT-MAGIC-COOKIE-1  84b79b42b73c0b4b9df5ce036bf380d0
pi@phoscon:~ $ sudo su
root@phoscon:/home/pi# xauth add phoscon/unix:10  MIT-MAGIC-COOKIE-1  84b79b42b73c0b4b9df5ce036bf380d0
root@phoscon:/home/pi# startlxde-pi
** Message: 18:34:09.287: main.vala:101: Session is LXDE-pi
** Message: 18:34:09.287: main.vala:102: DE is LXDE
** Message: 18:34:09.492: main.vala:133: log directory: /root/.cache/lxsession/LXDE-pi
** Message: 18:34:09.492: main.vala:134: log path: /root/.cache/lxsession/LXDE-pi/run.log

```

https://raspberrypi.stackexchange.com/questions/1719/x11-connection-rejected-because-of-wrong-authentication/4618
