![Commodore 64 Logo](http://img2.wikia.nocookie.net/__cb20140907072807/logopedia/images/2/2c/Commodore_64_logo.png)

***
_The Commodore 64 is an 8 Bit personal computer introduced in 1982 by Commodore International. This model holds the world record for the highest-selling single computer model of all time._
***
## Emulator: [VICE](http://vice-emu.sourceforge.net/)

## ROMS
Accepted File Extensions: **.crt .d64 .g64 .t64 .tap .x64 .zip**

Place your ROMS in
```shell
/home/pi/RetroPie/roms/c64
```
## Controls
```shell
Start Game: Spacebar
Menu: F12
Select: Enter
Cancel: Backspace
Exit GUI: Escape

Changing Controls:
-Press F12 to enter menu
-Navigate to machine settings and press enter
-Navigate to Joystick settings and press enter
-Navigate to Joystick device in port 2 and press enter
-to use a numpad to play your game navigate to Numpad and press enter
     -Up: 8
     -Up/Right: 9
     -Up/Left: 7
     -Left: 4
     -Right: 8
     -Down: 2
     -Down/Left: 1
     -Down/Right: 3
     -Fire: 0
-to use a Joystick (gamepad) instead, navigate to Joystick and press enter

CUSTOM MAPPING
- Go back to Joystick settings by pressing backspace and navigate to Joystick 1 Mapping and press enter
- Press enter on each key followed by pressing the key on your gamepad you wish to be mapped.
- Press escape to exit the menu and return to your game
```
### Advanced Configuration
Once you've started and exited the VICE emulator at least once it will create a configuration file in /home/pi/.vice which is a symbolic link to 
```shell
/opt/retropie/configs/c64/sdl-vicerc 
```
open the file "sdl-vicerc" and to double the screen size change
 
VICIIDoubleSize=0
 
to VICIIDoubleSize=1 

## Troubleshooting
* There have been some reports of the emulator crashing when it exits requiring a hard reboot