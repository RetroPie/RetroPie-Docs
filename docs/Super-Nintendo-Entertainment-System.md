***
![snes](https://cloud.githubusercontent.com/assets/10035308/12213994/0dcd4e9c-b642-11e5-945d-24bf706cd642.png)
***
_The Super Nintendo Entertainment System (or SNES) was a 4th generation video game console released by Nintendo in 1991. It is one of the most popular consoles._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-snes9x](https://github.com/libretro/snes9x) | snes | .7z .bin .bs .fig .mgd .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-snes9x2010](https://github.com/libretro/snes9x2010) | snes  | .7z .bin .bs .fig .mgd .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-snes9x2005](https://github.com/libretro/snes9x2005) | snes | .7z .bin .bs .fig .mgd .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-snes9x2002](https://github.com/libretro/snes9x2002) | snes | .7z .bin .bs .fig .mgd .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/retroarch.cfg |
| [PiSNES](https://github.com/RetroPie/pisnes) | snes | .fig .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/snes9x.cfg |
| [snes9x-rpi](https://github.com/RetroPie/snes9x-rpi) | snes | .fig .sfc .smc .swc .zip | none | /opt/retropie/configs/snes/snes9x.cfg |

## Emulators: [lr-snes9x](https://github.com/libretro/snes9x), [lr-snes9x2010](https://github.com/libretro/snes9x2010), [lr-snes9x2005](https://github.com/libretro/snes9x2005), [lr-snes9x2002](https://github.com/libretro/snes9x2002), [PiSNES](https://github.com/RetroPie/pisnes), [snes9x-rpi](https://github.com/RetroPie/snes9x-rpi)

RetroPie includes multiple SNES emulators. 

### lr-snes9x2010

The prefered emulator on the RPi2 or RPi3B due to its balance between speed and accuracy, though an overclocked RPi3B or stock RPi3B+ are recommended for attempting full speed emulation of SA1/SFX2 games.

### lr-snes9x2005

Recommended for attempting full speed emulation of SFX/SA1/SFX2 games on the RPi2 alongside, and the same could be said when attempting full speed emulation of SA1/SFX2 games on a stock RPi3B, though accuracy will suffer in all cases.

### lr-snes9x

An optional emulator that has proper Satellaview emulation, MSU-1 hack support, and is the most accurate SNES emulator available on the Raspberry Pi, but an overclocked RPi3B or stock RPi3B+ are recommended to avoid slowdown in most regular games. This emulator is generally too demanding for SFX/SA1/SFX2 games and an overclocked RPi3B+ is recommended for attempting full speed emulation of said games.

### lr-snes9x2002

The default emulator for the RPi0 and RPi1: expect inaccurate emulation. With this emulator, full speed emulation of SFX/SA1/SFX2 games is not possible on a RPi0 or a RPi1, expect some regular games not to run full speed on a RPi0, and do not expect full speed emulation for any game on a RPi1.

This emulator may also be of use to RPi2 and RPi3B owners that need the additional speed to emulate SFX/SA1/SFX2 games at full speed consistently, though **lr-snes9x2005** should be their first choice.

Setting the Runcommand's resolution setting for this emulator to a low 4:3 resolution on the RPi0 or RPi1 is recommended for faster emulation, though 480i (CEA-6) is the lowest recommended 4:3 CEA resolution due to CEA-2 and CEA-1 causing visual issues.

### PiSNES

An optional emulator that is recommended for full speed emulation of some games that run slow on a RPi0 in lr-snes9x2002, and should be the primary emulator on a RPi1, though it has inaccurate sound emulation and SFX/SA1/SFX2 games do not work.

Setting the Runcommand's resolution setting for this emulator to a low 4:3 resolution on the RPi0 or RPi1 is recommended for faster emulation: VGA (640x480) (CEA-1) will produce a 4:3 resolution with screen tearing on a modern TV and 480i (CEA-6) will not produce a 4:3 resolution and not have screen tearing on a modern TV.

### snes9x-rpi

An optional emulator that is identical to PiSNES in that it is based on the same version of SNES9x, has the same inaccurate sound emulation, and SFX/SA1/SFX2 games do not work. Where this emulator differs is that it doesn't have the option of exiting the emulator by using Select+Start and requires a keyboard to exit without [advanced controller configuration](https://retropie.org.uk/docs/Universal-Controller-Calibration-&-Mapping-Using-xboxdrv/). How well it performs compared to PiSNES is currently unknown.

## ROMS

Accepted File Extensions: **.7z .bin .fig .mgd .sfc .smc .swc .zip**

Place your SNES ROMs in
```
/home/pi/RetroPie/roms/snes
```

## Satellaview

Satellaview games are properly emulated by **lr-snes9x**, but require a BIOS to do so. 

**English - No DRM** is the recommended version to use.

| Recognized Name | Description | CRC32 |
| :---: | :---: | :---: |
| BS-X.bin | English - No DRM | E5A91AD4 |
| BS-X.bin | English - DRM | 8ECC1963 |
| BS-X.bin | Japan - No DRM | B6BFB9B9 |
| BS-X.bin | Japan - DRM | F51F07A0 |

Place BIOS in
```
/home/pi/RetroPie/BIOS
```

For emulators like **lr-snes9x2010**, the ".bs" extension is not recognized when inside a ".zip" or ".7z" archive.

First you will need to uncompress your ROMs from ".zip" or ".7z", then either leave them uncompressed, or change all of the ROMs' extension from ".bs" to ".sfc" then recompress the ".sfc" files back to ".zip" or ".7z" archives.

A quick way to change all of your ".bs" ROMs for Windows users is to open NotePad, put the command found below in it, save the file with a ".bat" extension (name it something like "bs to sfc.bat"), then place the new batch file in the folder containing your uncompressed ".bs" ROMs.

`rename *.bs *.sfc`

Programs such as PeaZip or WinRAR can be used to batch compress all of the newly renamed ROMs back into separate ".zip" or ".7z" archives.

## Controls

### lr-snes9x, lr-snes9x2010, lr-snes9x2005, lr-snes9x2002

lr-snes9x, lr-snes9x2010, lr-snes9x2005, and lr-snes9x2002 all utilise RetroArch configurations.

Add custom RetroArch controls to the retroarch.cfg file in:
```shell
/opt/retropie/configs/snes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration).

![nintendo_snes_diagram](https://cloud.githubusercontent.com/assets/10035308/16599633/7f34d356-42c0-11e6-92c0-f8774d795bd1.png)

### PiSNES

Controller configurations are kept in a file named snes9x.cfg located in: 
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

**lr-snes9x** and **lr-snes9x2010** are the only emulators that support multitap. Multitap support is disabled by default due to it breaking two-player games that don't support it.

To enable multitap, launch the multitap supported game you wish to enable multitap support in, go to "RGUI/Main Menu/Quick Menu/Controls", change "User 2 Device Type" to "Multitap", then go back to the "Quick Menu" and select "Save Game Overrides" at the bottom of the menu.