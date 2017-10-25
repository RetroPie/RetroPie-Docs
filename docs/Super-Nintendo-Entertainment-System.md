***
![snes](https://cloud.githubusercontent.com/assets/10035308/12213994/0dcd4e9c-b642-11e5-945d-24bf706cd642.png)
***
_The Super Nintendo Entertainment System (or SNES) was a 4th generation video game console released by Nintendo in 1991. It is one of the most popular consoles._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-snes9x2010](https://github.com/libretro/snes9x2010) | snes  | .7z .bin .fig .mgd .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/retroarch.cfg |
| lr-snes9x | snes | .7z .bin .fig .mgd .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-snes9x2002](https://github.com/libretro/snes9x2002) | snes | .7z .bin .fig .mgd .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/retroarch.cfg |
| [PiSNES](https://github.com/RetroPie/pisnes) | snes | .fig .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/snes9x.cfg |
| [lr-snes9x2005](https://github.com/libretro/snes9x2005) | snes | .7z .bin .fig .mgd .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-armsnes](https://github.com/RetroPie/ARMSNES-libretro) | snes | .7z .bin .fig .mgd .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/retroarch.cfg |
| [snes9x-rpi](https://github.com/RetroPie/snes9x-rpi) | snes | .fig .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/snes9x.cfg |

## Emulators: [lr-snes9x-2010](https://github.com/libretro/snes9x2010), lr-snes9x, [lr-snes9x2002](https://github.com/libretro/snes9x2002), [PiSNES](https://github.com/RetroPie/pisnes), [lr-snes9x2005](https://github.com/libretro/snes9x2005), [lr-armsnes](https://github.com/RetroPie/ARMSNES-libretro), [snes9x-rpi](https://github.com/RetroPie/snes9x-rpi)

RetroPie comes included with multiple SNES emulators. If you have a Pi 2, the preference is **lr-snes9x2010** due to better speed and sound emulation. lr-snes9x2002 is recommended for Super FX chip games on the Pi 2. lr-snes9x is an optional emulator that has MSU-1 support and more accurate emulation, but requires a sufficiently overclocked Pi 3 for guaranteed constant full speed emulation, and is sometimes too demanding for enhancement chip games.

## ROMS

Accepted File Extensions: **.7z .bin .fig .mgd .sfc .smc .swc .zip**

Place your SNES ROMs in
```
/home/pi/RetroPie/roms/snes
```

## Satellaview

Satellaview games are supported, but most you will find on the internet have the ".bs" extension, which is an issue if the ROM is compressed with the extension since ".bs" is not included in any of the emulators' compression support.

First you will need to uncompress your ROMs from ".zip" or ".7z" (if you have them compressed that is), then either leave them uncompressed, or change all of the ROMs' extension from ".bs" to ".sfc" then recompress the ".sfc" files back to ".zip" or ".7z" archive formats.

A quick way to change all of your ".bs" ROMs for Windows users is to open NotePad, put the command found below in it, save the file with a ".bat" extension (name it something like "bs to sfc.bat"), then place the new batch file in the folder containing your uncompressed ".bs" ROMs.

`rename *.bs *.sfc`

Programs such as PeaZip or WinRAR can be used to batch compress all of the newly renamed ROMs back into separate ".zip" or ".7z" archives.

## Controls

### lr-snes9x2010, lr-snes9x, lr-snes9x2002, lr-snes9x2005, lr-armsnes

lr-snes9x2010, lr-snes9x, lr-snes9x2002, lr-snes9x2005, lr-armsnes all utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/snes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nintendo_snes_diagram](https://cloud.githubusercontent.com/assets/10035308/16599633/7f34d356-42c0-11e6-92c0-f8774d795bd1.png)

### PiSNES

Controller configurations are kept in a file named snes9x.cfg located in 
```
/opt/retropie/emulators/pisnes
```
**Example Configurations**
```shell
[Keyboard]
# Get codes from /usr/include/SDL/SDL_keysym.h
A_1=100
B_1=99
X_1=115
Y_1=120
L_1=97
R_1=102
START_1=13
SELECT_1=9
LEFT_1=276
RIGHT_1=275
UP_1=273
DOWN_1=274
QUIT=27
ACCEL=8

[Joystick]
# Get codes from "jstest /dev/input/js0"
# from package "joystick"
A_1=3
B_1=2
X_1=1
Y_1=0
L_1=4
R_1=6
START_1=9
SELECT_1=8
QUIT=99
ACCEL=7
QLOAD=10
QSAVE=11
#Joystick axis
JA_LR=0
JA_UD=1
```

### 3-5 Players

Some games allow more than 2 players. Currently, the only emulator which supports this is [lr-snes9x2010](https://github.com/libretro/snes9x2010). In order to active this feature, you'll need to enable [Multi-tap](https://en.wikipedia.org/wiki/Multitap) by adding this line to the ``retroarch.cfg``:
```shell
input_libretro_device_p2 = "257"
```