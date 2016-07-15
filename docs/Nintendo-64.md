***
![n64](https://cloud.githubusercontent.com/assets/10035308/12213210/ca04f1fc-b631-11e5-8ae7-d402371c9124.png)
***
_The Nintendo 64 is a 5th generation gaming console released by Nintendo in 1996_

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Mupen64plus](https://code.google.com/p/mupen64plus/) | n64  | .z64 .n64 .v64 | none | /opt/retropie/configs/n64/InputAutoCfg.ini **and** /opt/retropie/configs/n64/mupen64plus.cfg|
| [lr-Mupen64plus](https://github.com/libretro/mupen64plus-libretro) | n64 | .z64 .n64 .v64 | none | /opt/retropie/configs/n64/retroarch.cfg |

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

Secondary Rom Compatibility list with testing on Raspberry Pi 3 need to merge 2 lists. 
https://docs.google.com/spreadsheets/d/1Sn3Ks3Xv8cIx3-LGCozVFF7wGLagpVG0csWybnwFHXk/edit

Don't want to step on any toes and Credit to the author of the original list, but here is another. I just took the original sheet and did some formatting. Use the first tab for Comments and Suggestions. Just trying to help get this to one sheet.
https://docs.google.com/spreadsheets/d/1e9o3sNLKxlUBDDG6Sr0n6VBwAgwlFGPYr8Al46MdAqE/edit?usp=sharing

## Performance

Low screen resolution are recommended to get best performance. Performance suffers if HD resolutions are used.

RetroPie 4.0 forces a resolution of 320x240 for best performance. 

## Tweaks

RetroPie 3.x:
```
/opt/retropie/configs/all/autoconf.cfg
```
*mupen64plus_audio                  enable auto configuration of audio output path (0/1)
*mupen64plus_hotkeys                enable hotkey auto configuration (0/1)
*mupen64plus_compatibility_check    enable compatibility check which alters game related settings (0/1)

RetroPie 4.0:
```
/opt/retropie/emulators/mupen64plus/bin/mupen64plus.sh line 282
```
SDL_VIDEO_RPI_SCALE_MODE=x
*"0"       - Window resolution is desktop resolution. This is the behaviour of SDL <= 2.0.4. (default)
*"1"       - Requested video resolution will be scaled to desktop resolution. Aspect ratio of requested video resolution will be respected.
*"2"       - Requested video resolution will be scaled to desktop resolution.
*"3"       - Requested video resolution will be scaled to desktop resolution. Aspect ratio of requested video resolution will be respected. If possible output resolution will be integral multiple of video resolution.

## Controls

### lr-Mupen64plus

lr-Mupen64plus utilises RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/n64/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![nintendo_n64_diagram](https://cloud.githubusercontent.com/assets/10035308/16599636/7f3630fc-42c0-11e6-952f-60d97a511f38.png)

### Mupen64plus

Starting with RetroPie 3.3 Mupen64Plus configurations are automatically generated when you configure your controller for the first time in emulationstation. Mupen64plus configurations differ from the RetroArch configs listed above and more closely match the original physical N64 controller.

![nintendo_n64_mupen64plus_diagram](https://cloud.githubusercontent.com/assets/10035308/16599635/7f35579a-42c0-11e6-9615-9a3670932332.png)
There are two main configuration files that can be modified located at:
```
/opt/retropie/configs/n64/mupen64plus.cfg
and
/opt/retropie/configs/n64/InputAutoCfg.ini
```

Note that, by default, the memory expansion pack is configured as installed.

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



# Note for configuring Arcade Joystick or non analogue controller to use N64 correctly.
Changing the below inside /opt/retropie/configs/n64/InputAutoCfg.ini

From
X Axis = "hat(0 Left, 0 Right)"
Y Axis = "hat(0 Up, 0 Down)"

To 
X Axis = "hat(0 Left Right)"
Y Axis = "hat(0 Up Down)"

Gets joystick correctly configured
Tested with Akishop PS360+ 

If your config will differ, go to input configuration, and configure your joystick to use the joystick for Left Analogue UP Down Left and right.  Then browse to /opt/retropie/configs/n64/InputAutoCfg.ini  and cat that file
cat /opt/retropie/configs/n64/InputAutoCfg.ini
Copy that into a text file.   Then go back to input configuration and map your controller correctly again using joystick inputs to dpad up down left and right.  After this completes go back to edit the /opt/retropie/configs/n64/InputAutoCfg.ini   and only change the portion that relates to X and Y axis from your previous state where your joystick was mapped to the analogue inputs. 

From there you will be able to use your joystick as analogue inputs in 64 games. 



##Configuring N64 USB Controller for use with Retropie accurately
What I do is I will configure via Retropie the config how I like it for all the general emulators and then i will edit the /opt/retropie/configs/n64/InputAutoCfg.ini file with the below which as long as your using the USB N64 pad should get your 64 controller mapped correctly.

I sacrifice Ltrigger to Select and don't define it so It can be used to xit the emulator with start
```
; Generic USB Joystick _START
[Generic USB Joystick ]
plugged = True
plugin = 2
mouse = False
AnalogDeadzone = 4096,4096
AnalogPeak = 32768,32768
Mempak switch =
Rumblepak switch =
R Trig = button(5)
Start = button(9)
Y Axis = axis(1-,1+)
Z Trig = button(7)
DPad U = hat(0 Up)
A Button = button(6)
DPad D = hat(0 Down)
X Axis = axis(0-,0+)
DPad R = hat(0 Right)
B Button = button(8)
DPad L = hat(0 Left)
C Button R = button(1)
C Button L = button(3)
C Button D = button(2)
C Button U = button(0)
; Generic USB Joystick _END

```
