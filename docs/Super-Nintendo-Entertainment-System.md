***
![snes](https://cloud.githubusercontent.com/assets/10035308/12213994/0dcd4e9c-b642-11e5-945d-24bf706cd642.png)
***
_The Super Nintendo Entertainment System (or SNES) was a 4th generation video game console released by Nintendo in 1991. It is one of the most popular consoles._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-snes9x-next](https://github.com/libretro/snes9x-next) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-armsnes](https://github.com/rmaz/ARMSNES-libretro) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-catsfc](https://github.com/libretro/CATSFC-libretro) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/retroarch.cfg |
| [lr-pocketsnes](https://github.com/libretro/pocketsnes-libretro) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/retroarch.cfg |
| [snes9x-rpi](https://github.com/RetroPie/snes9x-rpi) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/snes9x.cfg |
| [PiSNES](https://github.com/RetroPie/pisnes) | snes  | .zip .smc .sfc .fig .swc | none | /opt/retropie/configs/snes/snes9x.cfg |

## Emulators: [lr-snes9x-next](https://github.com/libretro/snes9x-next), [PiSNES](https://github.com/RetroPie/pisnes), [snes9x-rpi](https://github.com/RetroPie/snes9x-rpi), [lr-armsnes](https://github.com/rmaz/ARMSNES-libretro), [lr-catsfc](https://github.com/libretro/CATSFC-libretro), [lr-pocketsnes](https://github.com/libretro/pocketsnes-libretro)

RetroPie comes included with multiple SNES emulators. If you have a Pi 2, the preference is **lr-SNES9x-Next** due to better speed and sound emulation. PocketSnes is recommended for Super FX chip games.

## ROMS

Accepted File Extensions: **.zip .smc .sfc .fig .swc**

Place your SNES ROMs in
```
/home/pi/RetroPie/roms/snes
```



## Controls

### lr-armsnes, lr-catsfc, lr-pocketsnes, lr-snes9x-next

lr-armsnes, lr-catsfc, lr-pocketsnes, lr-snes9x-next all utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/snes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![snes](https://cloud.githubusercontent.com/assets/10035308/7334403/bd655d6e-eb4e-11e4-8fd7-a4424aad1034.png)

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