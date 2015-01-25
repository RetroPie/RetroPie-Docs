GnGeo-RPi can be installed via the RetroPie Setup Script. You can find more information in the wiki at https://github.com/ymartel06/GnGeo-Pi/wiki.

When using roms for gngeo you need 3 steps.

1 – You must put the bios file neogeo.zip in the rom folder.

2 – gngeo has a gngeo_data.zip file in the installdir/share/gngeo folder. The files inside this zip are .drv. You can only play roms that have the same name as these .drv files, e.g. mslug2.zip (rom) and mslug2.drv (data). If the names of these files dont match the game will crash.

3 – Also make sure the /home/pi/.gngeo/gngeorc file exists (this is the file you edit for configurations, joypad etc).

`# some sample joystick configuration`
`# Xbox360`
`# p1control A=J0B0,B=J0B1,C=J0B2,D=J0B3,START=J0B6,COIN=J0B10,UP=J0a1,DOWN=J0a1,LEFT=J0A0,RIGHT=J0A0,MENU=J0B7`
`# Dualshock2`
`# p1control A=J0B2,B=J0B1,C=J0B3,D=J0B0,START=J0B9,COIN=J0B8,UP=J0a1,DOWN=J0a1,LEFT=J0A0,RIGHT=J0A0`

`# Meaning of the code:`
`# Kxxx : keyboad key number xxx`
`# JxByy : Joystick number x Button `
`# JxAyy : Joystick number x Axe yy (use a lowercase 'a' if you need to invert the axis)`
`# JxHyy : Joystick number x Hat yy`
`# `
`# by the way, you can define a button multiple time, for example A=J0B0,A=K123,etc..`

https://github.com/ssilverm/PiMAME/blob/master/.gngeo/gngeorc