G910 is a quite common bluetooth controler used with android/iPhone devices to play a mobile games.

How to pair with RetroPie
* G910 shall je switched off
** To switch it off press Home button for 5 secs
* Pairing mode shall be entered by pressing A + Home buttons together
** all four red lights shall start flashing quickly, if not pairing mode was not initiated, repeat previous steps again
** Warning, there are 4 pairing modes but only one work with with retropie
*** A + Home: keyboard pairing mode (use this one)
*** X + Home: gamepad pairing mode
*** B + Home: app pairing mode
*** Y + Home: icade pairing mode (ios compatible)
* start bluetoothctl from command line and type following commands
** pairable on
** scan on
*** wait until gamepad address appears
** trust [gamepad address]
** pair [gamepad address]
** connect [gamepad address]
*** successful connection is indicated by second led on, the others are off
* reboot your retropie, after rebooting gamepad shall connect automatically, if it is switched off just switched it on by short press by Home button
* long press of aby button shall start kdy mapping wizzard