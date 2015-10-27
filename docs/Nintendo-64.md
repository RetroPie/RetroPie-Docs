![Nintendo 64 Logo](http://images2.wikia.nocookie.net/__cb20130424181606/theamazingworldofgumball/images/3/38/Nintendo_64_Logo.png)
***
_The Nintendo 64 is a 5th generation gaming console released by Nintendo in 1996_

***

## Emulators: [Mupen64plus](https://code.google.com/p/mupen64plus/), [lr-Mupen64plus](https://github.com/libretro/mupen64plus-libretro)

While the mupen64plus-libretro core has the convenience of RetroArch configurations, the actual Mupen64plus does better with performance. 

You can choose between the RICE, glesN64 and GLideN64 video plugin from the [runcommand](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand) menu- you may have to test out each one to see which works best- but you can also check the compatibility list below.

Note that you need a Raspberry Pi 2 if you want any decent N64 performance and even then it is hit and miss.

## ROMS
Accepted File Extensions: **.z64 .n64 .v64**

Place your Nintendo 64 ROMs in 
```
/home/pi/RetroPie/roms/n64
```

## [Rom Compatibility List](https://docs.google.com/spreadsheets/d/1Wjzbu90l6eCEW1w6ar9NtfyDBQrSPILQL5MbRSpYSzw/edit?usp=sharing) feel free to contribute!


## Controls

### lr-Mupen64plus

lr-Mupen64plus utilises RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/n64/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![nintendo_n64_diagram](https://cloud.githubusercontent.com/assets/10035308/7334793/6b406d8c-eb5b-11e4-8474-56a340521e71.png)

### Mupen64plus

There are two main configuration files that can be modified located at:
```
/opt/retropie/configs/n64/mupen64plus.cfg
and
/opt/retropie/configs/n64/InputAutoCfg.ini
```

#### Example mupen64plus.cfg
```
[CoreEvents]

# Mupen64Plus CoreEvents config parameter set version number.  Please don't change this version number.
Version = 1
# SDL keysym for stopping the emulator
Kbd Mapping Stop = 27
# SDL keysym for switching between fullscreen/windowed modes
Kbd Mapping Fullscreen = 0
# SDL keysym for saving the emulator state
Kbd Mapping Save State = 286
# SDL keysym for loading the emulator state
Kbd Mapping Load State = 288
# SDL keysym for advancing the save state slot
Kbd Mapping Increment Slot = 0
# SDL keysym for resetting the emulator
Kbd Mapping Reset = 290
# SDL keysym for slowing down the emulator
Kbd Mapping Speed Down = 291
# SDL keysym for speeding up the emulator
Kbd Mapping Speed Up = 292
# SDL keysym for taking a screenshot
Kbd Mapping Screenshot = 293
# SDL keysym for pausing the emulator
Kbd Mapping Pause = 112
# SDL keysym for muting/unmuting the sound
Kbd Mapping Mute = 109
# SDL keysym for increasing the volume
Kbd Mapping Increase Volume = 93
# SDL keysym for decreasing the volume
Kbd Mapping Decrease Volume = 91
# SDL keysym for temporarily going really fast
Kbd Mapping Fast Forward = 102
# SDL keysym for advancing by one frame when paused
Kbd Mapping Frame Advance = 47
# SDL keysym for pressing the game shark button
Kbd Mapping Gameshark = 103
# Joystick event string for stopping the emulator
Joy Mapping Stop = "J0B7/B6,J1B7/B6"
# Joystick event string for switching between fullscreen/windowed modes
Joy Mapping Fullscreen = ""
# Joystick event string for saving the emulator state
Joy Mapping Save State = "J0B5/B6,J1B5/B6"
# Joystick event string for loading the emulator state
Joy Mapping Load State = "J0B4/B6,J1B4/B6"
# Joystick event string for advancing the save state slot
Joy Mapping Increment Slot = ""
# Joystick event string for taking a screenshot
Joy Mapping Screenshot = ""
# Joystick event string for pausing the emulator
Joy Mapping Pause = ""
# Joystick event string for muting/unmuting the sound
Joy Mapping Mute = ""
# Joystick event string for increasing the volume
Joy Mapping Increase Volume = ""
# Joystick event string for decreasing the volume
Joy Mapping Decrease Volume = ""
# Joystick event string for fast-forward
Joy Mapping Fast Forward = ""
# Joystick event string for pressing the game shark button
Joy Mapping Gameshark = ""


[Input-SDL-Control1]

# Mupen64Plus SDL Input Plugin config parameter version number.  Please don't change this version number.
version = 2
# Controller configuration mode: 0=Fully Manual, 1=Auto with named SDL Device, 2=Fully automatic
mode = 2
# Specifies which joystick is bound to this controller: -1=No joystick, 0 or more= SDL Joystick number
device = 0
# SDL joystick name (or Keyboard)
name = "Logitech Gamepad F310"
# Specifies whether this controller is 'plugged in' to the simulated N64
plugged = True
# Specifies which type of expansion pak is in the controller: 1=None, 2=Mem pak, 5=Rumble pak
plugin = 2
# If True, then mouse buttons may be used with this controller
mouse = False
# Scaling factor for mouse movements.  For X, Y axes.
MouseSensitivity = "2.00,2.00"
# The minimum absolute value of the SDL analog joystick axis to move the N64 controller axis value from 0.  For X, Y axes.
AnalogDeadzone = "4096,4096"
# An absolute value of the SDL joystick axis >= AnalogPeak will saturate the N64 controller axis value (at 80).  For X, Y axes. For each axis, this must be greater than the corresponding AnalogDeadzone value
AnalogPeak = "32768,32768"
# Digital button configuration mappings
DPad R = "hat(0 Right)"
DPad L = "hat(0 Left)"
DPad D = "hat(0 Down)"
DPad U = "hat(0 Up)"
Start = "button(7)"
Z Trig = "button(5)"
B Button = "button(2)"
A Button = "button(0)"
C Button R = "axis(3+)"
C Button L = "axis(3-)"
C Button D = "axis(4+)"
C Button U = "axis(4-)"
R Trig = "axis(5-)"
L Trig = "axis(2-)"
Mempak switch = "button(1)"
Rumblepak switch = "button(3)"
# Analog axis configuration mappings
X Axis = "axis(0-,0+)"
Y Axis = "axis(1-,1+)"


[Input-SDL-Control2]

# Mupen64Plus SDL Input Plugin config parameter version number.  Please don't change this version number.
version = 2
# Controller configuration mode: 0=Fully Manual, 1=Auto with named SDL Device, 2=Fully automatic
mode = 2
# Specifies which joystick is bound to this controller: -1=No joystick, 0 or more= SDL Joystick number
device = 1
# SDL joystick name (or Keyboard)
name = "Logitech Gamepad F310"
# Specifies whether this controller is 'plugged in' to the simulated N64
plugged = True
# Specifies which type of expansion pak is in the controller: 1=None, 2=Mem pak, 5=Rumble pak
plugin = 2
# If True, then mouse buttons may be used with this controller
mouse = False
# Scaling factor for mouse movements.  For X, Y axes.
MouseSensitivity = "2.00,2.00"
# The minimum absolute value of the SDL analog joystick axis to move the N64 controller axis value from 0.  For X, Y axes.
AnalogDeadzone = "4096,4096"
# An absolute value of the SDL joystick axis >= AnalogPeak will saturate the N64 controller axis value (at 80).  For X, Y axes. For each axis, this must be greater than the corresponding AnalogDeadzone value
AnalogPeak = "32768,32768"
# Digital button configuration mappings
DPad R = "hat(0 Right)"
DPad L = "hat(0 Left)"
DPad D = "hat(0 Down)"
DPad U = "hat(0 Up)"
Start = "button(7)"
Z Trig = "button(5)"
B Button = "button(2)"
A Button = "button(0)"
C Button R = "axis(3+)"
C Button L = "axis(3-)"
C Button D = "axis(4+)"
C Button U = "axis(4-)"
R Trig = "axis(5-)"
L Trig = "axis(2-)"
Mempak switch = "button(1)"
Rumblepak switch = "button(3)"
# Analog axis configuration mappings
X Axis = "axis(0-,0+)"
Y Axis = "axis(1-,1+)"
```

#### Example InputAutoCfg.ini
```
[Logitech Gamepad F310]
plugged = True
plugin = 2
mouse = False
AnalogDeadzone = 4096,4096
AnalogPeak = 32768,32768
DPad R = hat(0 Right)
DPad L = hat(0 Left)
DPad D = hat(0 Down)
DPad U = hat(0 Up)
Start = button(7)
Z Trig = button(5)
B Button = button(2)
A Button = button(0)
C Button R = axis(3+)
C Button L = axis(3-)
C Button D = axis(4+)
C Button U = axis(4-)
R Trig = axis(5-)
L Trig = axis(2-)
Mempak switch = button(1)
Rumblepak switch = button(3)
X Axis = axis(0-,0+)
Y Axis = axis(1-,1+)
``` 
## Video Tutorials

<a href="http://www.youtube.com/watch?feature=player_embedded&v=4WX7RrzUtII
" target="_blank"><img src="https://i.ytimg.com/vi_webp/4WX7RrzUtII/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a> |
<a href="https://www.youtube.com/watch?v=lh0n5PWN2lI
" target="_blank"><img src="https://i.ytimg.com/vi_webp/lh0n5PWN2lI/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a> 