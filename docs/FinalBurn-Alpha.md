***
![fba](https://cloud.githubusercontent.com/assets/10035308/12213772/eb6a317c-b63b-11e5-847f-2c03ffde43f3.png)
***
_Final Burn Alpha is a Multiple Arcade Emulator most popular for emulating Neo-Geo, Capcom, Konami, and Cave games. It is developed by the final burn team and originated from FinalBurn by Dave_
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fbalpha](https://github.com/libretro/fbalpha) | arcade **or** fba **or** neogeo  | .zip | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/fba/retroarch.cfg, **or** /opt/retropie/configs/neogeo/retroarch.cfg |
| [lr-fba](https://github.com/libretro/fba-libretro) | arcade **or** fba **or** neogeo  | .zip | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/fba/retroarch.cfg, **or** /opt/retropie/configs/neogeo/retroarch.cfg |
| [PiFBA](https://github.com/RetroPie/pifba) | arcade **or** fba **or** neogeo  | .zip | neogeo.zip | /opt/retropie/emulators/pifba/fba2x.cfg **or** /opt/retropie/configs/fba/fba2x.cfg |

## Emulators: [PiFBA](https://github.com/RetroPie/pifba), [lr-fba](https://github.com/libretro/fba-libretro), [lr-fbalpha](https://github.com/libretro/fbalpha)

lr-fbalpha is favoured as it is mature, runs the current FBA romset, and enjoys all the usual libretro/RetroArch advantages of automatic controller configuration, shaders, etc. PiFBA is an earlier romset, not libretro/RetroArch, but still can be useful for Raspberry Pi 1/0 users as it is heavily optimised.

## ROMS

Accepted File Extensions: **.zip**

**For information on how to rebuild newer romsets to be compatible with these emulators see this post:**
**[Managing ROMs](https://github.com/petrockblog/RetroPie-Setup/wiki/Managing-ROMs)**

### lr-fbalpha

**Please see [[lr-fbalpha]] for information on how to configure specific features of this emulator.**

Romset Used: FBA **0.2.97.39** which is based on MAME 0.175

Total Games Emulated: [8982](https://raw.githubusercontent.com/libretro/fbalpha/master/gamelist.txt) (includes clones etc..)
 
Place your lr-fbalpha ROMs in
```shell
/home/pi/RetroPie/roms/fba
```
you can also place your ROMs in

```shell
/home/pi/RetroPie/roms/neogeo
```

### [**lr-fbalpha COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing)  feel free to contribute to the list.

### PiFBA 

Romset Used: FBA **0.2.96.71 romset** which is based on MAME 0.114 (April 2007) (see list below) 

Total Games Emulated: 684 (no clones)

### [**PiFBA COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing)  feel free to contribute to the list.

Place your PiFBA ROMS in

```shell
/home/pi/RetroPie/roms/fba
```

you can also place your ROMs in

```shell
/home/pi/RetroPie/roms/neogeo
```

### lr-fba

Romset Used: FBA **0.2.97.30** which is based on MAME 0.154 (Jul 2014)

Total Games Emulated: [3369](https://raw.githubusercontent.com/libretro/fba-libretro/master/svn-current/trunk/gamelist.txt) (includes clones etc..)

### [**lr-fba COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1rWO7Lm0bTGNpak6J-CPzde0GNIDP0NHDoQdJ6iWosfA/edit?usp=sharing)  feel free to contribute to the list.
 
Place your lr-fba ROMs in
```shell
/home/pi/RetroPie/roms/fba
```
you can also place your ROMs in

```shell
/home/pi/RetroPie/roms/neogeo
```

## BIOS

Neo-Geo ROMs require a `neogeo.zip` BIOS file. Place this with your ROMs in
```
/home/pi/RetroPie/roms/fba
```
or
```
/home/pi/RetroPie/roms/neogeo
```

For more information relating to the BIOS contents, MVS/AES modes, and Universe BIOS (UNIBIOS) mode, refer to the [Neo-Geo](https://github.com/RetroPie/RetroPie-Setup/wiki/Neo-Geo) wiki page.

## Controls
As there are 2 emulators there are two sets of controls.
### lr-fba and lr-fbalpha Controls
lr-fba and lr-fbalpha utilise RetroArch configs.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/fba/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration) 

![neogeodiagram](https://cloud.githubusercontent.com/assets/10035308/8245309/a575cc8c-15e9-11e5-8735-0a4ab2a4e137.png)

### PiFBA Controls
PiFBA controls are located in
```shell
/opt/retropie/emulators/pifba/fba2x.cfg
```
As there is no menu to configure controllers with PiFBA like there is with Mame4all, you'll have to edit the aforementioned file manually. 

**NOTE** PiFBA currently only supports 2 players.

**Example of fba2x.cfg**

```shell
[Keyboard]
# Get codes from /usr/include/SDL/SDL_keysym.h
A_1=306 #LCTRL (button1)
B_1=32 #SPACE (button3)
X_1=308 #LALT (button2
Y_1=304 #LSHIFT
L_1=122 #z
R_1=120 #x
START_1=49 #1
SELECT_1=53 #5
LEFT_1=276 #left
RIGHT_1=275 #right
UP_1=273 #up
DOWN_1=274 #down
QUIT=27 #escape
#player 2 keyboard controls, disabled by default
A_2=97 #a (button1)
B_2=113 #q (button3)
X_2=115 #s (button2)
Y_2=119 #w
L_2=105 #i
R_2=107 #k
START_2=50 #2
SELECT_2=54 #6
LEFT_2=100 #d
RIGHT_2=103 #g
UP_2=114 #r
DOWN_2=102 #f

[Joystick]
# Get codes from "jstest /dev/input/js0"
# from package "joystick"
A_1=3
B_1=1
X_1=2
Y_1=0
L_1=4
R_1=5
START_1=9
SELECT_1=8
#Joystick axis
JA_LR=0
JA_UD=1
#player 2 button configuration
A_2=3
B_2=1
X_2=2
Y_2=0
L_2=4
R_2=5
START_2=9
SELECT_2=8
#Joystick axis
JA_LR=0
JA_UD=1


[Graphics]
DisplaySmoothStretch=1
# Display Effect: 0 none, 1 scanlines
DisplayEffect=0
DisplayBorder=0
MaintainAspectRatio=1

[Sound]
```
## Video Tutorial:

<a href="https://www.youtube.com/watch?v=C7ETQUBNVRo" target="_blank"><img src="https://i.ytimg.com/vi_webp/C7ETQUBNVRo/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a>

## List of Hardware Supported
* Capcom CPS-1
* Capcom CPS-2
* Capcom CPS-3
* Cave
* Data East DEC-0, DEC-8 and DECO IC16 based games
* Galaxian based hardware
* Irem M62, M63, M72, M90, M92 and M107 hardware
* Kaneko 16
* Konami
* Neo-Geo
* NMK16
* Pacman based hardware
* PGM
* Psikyo 68EC020 and SH-2 based hardware
* Sega System 1, System 16 (and similar), System 18, X-Board and Y-Board
* Super Kaneko Nova System
* Toaplan 1
* Toaplan 2
* Taito F2, X, Z and others
* Miscellaneous drivers for lots of other hardware