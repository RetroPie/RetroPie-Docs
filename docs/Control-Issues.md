Control Issues
==============

Setting Up an USB joystick/gamepad 
----------------------------------
(according to this [post](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=207824#p207824))

To configure USB joystick / gamepad for RetroArch run...

retroarch-joyconfig

And to configure DGEN joystick / gamepad...

1.  go to .dgen folder - cd .dgen

2.  sudo nano dgenrc

and uncomment the joystick lines. Putting your own button numbers corresponding to your joystick / gamepad.

Setting Up a Bluetooth Controller
---------------------------------

You can find a nice tutorial about setting up a bluetooth controller at http://mypiandi.blogspot.de/2012/12/retropie-sixaxis-over-bluetooth.html.

GameGear and MasterSystem Keyboard Input
----------------------------------------

If you want to use the keyboard as input for these systems you need to remove the parameter "-joy" from the call of Osmose in the file ~/.emulationstation/es_systems.cfg.
