***
![snes](https://cloud.githubusercontent.com/assets/10035308/12213994/0dcd4e9c-b642-11e5-945d-24bf706cd642.png)
***
_The Super Nintendo Entertainment System (or SNES) was a 4th generation video game console released by Nintendo in 1991. It is one of the most popular consoles._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-snes9x2010](https://github.com/libretro/snes9x2010) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-armsnes](https://github.com/RetroPie/ARMSNES-libretro) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-snes9x2005](https://github.com/libretro/snes9x2005) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-snes9x2002](https://github.com/libretro/snes9x2002) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/retroarch.cfg |
| [snes9x-rpi](https://github.com/RetroPie/snes9x-rpi) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/snes9x.cfg |
| [PiSNES](https://github.com/RetroPie/pisnes) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/snes9x.cfg |

## Emulators: [lr-snes9x-2010](https://github.com/libretro/snes9x2010), [PiSNES](https://github.com/RetroPie/pisnes), [snes9x-rpi](https://github.com/RetroPie/snes9x-rpi), [lr-armsnes](https://github.com/RetroPie/ARMSNES-libretro), [lr-snes9x2005](https://github.com/libretro/snes9x2005), [lr-snes9x2002](https://github.com/libretro/snes9x2002)

RetroPie comes included with multiple SNES emulators. If you have a Pi 2, the preference is **lr-snes9x2010** due to better speed and sound emulation. lr-snes9x2002 is recommended for Super FX chip games.

## ROMS

Accepted File Extensions: **.zip .smc .sfc .fig .swc**

Place your SNES ROMs in
```
/home/pi/RetroPie/roms/snes
```



## Controls

### lr-armsnes, lr-snes9x2005, lr-snes9x2002, lr-snes9x2010

lr-armsnes, lr-snes9x2005, lr-snes9x2002, lr-snes9x2010 all utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/snes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

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
###3-5 Players
Some games allow more than 2 player. Currently, the only emulator which support this is [lr-snes9x2010](https://github.com/libretro/snes9x2010). In order to active this feature, you'll need to enable [Multi-tap](https://en.wikipedia.org/wiki/Multitap) by adding this line to the ``retroarch.cfg``:
```shell
input_libretro_device_p2 = "257"
```