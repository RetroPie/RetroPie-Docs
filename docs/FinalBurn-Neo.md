***
![fba](https://cloud.githubusercontent.com/assets/10035308/12213772/eb6a317c-b63b-11e5-847f-2c03ffde43f3.png)
***
_FinalBurn Neo is a Multiple Arcade Emulator most popular for emulating Neo-Geo, Capcom, Konami, and Cave games. It is developed by the FinalBurn team and originated from FinalBurn by Dave and old MAME versions_.

FinalBurn Neo is an active fork of the FinalBurn Alpha emulator, created by former FBA developers.

See also: [MAME](MAME), [Neo Geo](Neo-Geo).

***
There are a variety of arcade emulators available in RetroPie. There are significant differences in performance, compatibility, and configuration between them. If you're just getting started with arcade emulation, start by reading [Arcade](Arcade) page.

This page is a resource for additional details on RetroPie's FinalBurn emulators including configuration paths, controls, and the ROM sets required by each emulator.

| Emulator | Rom Folder | Extension | Required ROM Version | Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fbneo](#lr-fbneo) | arcade **or** fba **or** neogeo  | .7z .zip | FB Neo v0.2.97.44| /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/fba/retroarch.cfg, **or** /opt/retropie/configs/neogeo/retroarch.cfg |
| [lr-fbalpha2012](#lr-fbalpha2012) | arcade **or** fba **or** neogeo  | .7z .zip | FB Alpha v0.2.97.29 | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/fba/retroarch.cfg, **or** /opt/retropie/configs/neogeo/retroarch.cfg |
| [PiFBA](#pifba) | arcade **or** fba **or** neogeo  | .zip | FB Alpha 0.2.96.71 | /opt/retropie/emulators/pifba/fba2x.cfg **or** /opt/retropie/configs/fba/fba2x.cfg |

## Arcade ROM paths

Five of the available arcade ROM paths in RetroPie are shared directories which are used by more than one emulator: `arcade`, `mame-libretro`, `mame-advmame`, `fba`, and `neogeo`. In order to successfully load zipped ROM sets in these locations you must specify the arcade emulator version which matches your ROMs.

To avoid having several menus for different arcade emulators, all arcade-based ROMs can be placed in the `arcade` ROM folder, but you will have to specify which emulator each zipped ROM set will use from the [Runcommand Menu](Runcommand.md).

## Emulators

### lr-fbneo
[Visit the FinalBurn Neo homepage on github](https://github.com/libretro/fbneo)

[Important announcement about FBNeo romset constantly changing](https://retropie.org.uk/forum/topic/19741/new-fb-alpha-libretro-pre-v0-2-97-44)

**Note: Please see [lr-neo](lr-fbneo) for information on how to configure specific features of this emulator.**

Accepted File Extensions: **.7z .zip**

```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Samples Dir: /home/pi/RetroPie/BIOS/fbneo/samples/
Binary Dir: /opt/retropie/libretrocores/lr-fbneo
Config Dir: /opt/retropie/configs/fba/retroarch.cfg

Game remaps:
/opt/retropie/configs/arcade/FinalBurn Neo, **or**
/opt/retropie/configs/fba/FinalBurn Neo, **or**
/opt/retropie/configs/neogeo/FinalBurn Neo

High scores / NVRAM files:
/home/pi/RetroPie/roms/arcade/fbneo, **or**
/home/pi/RetroPie/roms/fba/fbneo, **or**
/home/pi/RetroPie/roms/neogeo/fbneo
```

NOTE: If you have updated RetroPie from an existing installation since 27th May 2019, lr-fbneo now replaces lr-fbalpha. However if you have existing game remaps, samples, or high scores, you will need to rename the directories to match the above, otherwise lr-fbneo will not be able to find these files.

**ROM Version**: Subset of latest MAME/HBMAME roms available

**Total arcade games emulated: 5500+**
* BIOS: 7
* Samples: ?

**FB Neo DAT Files**:

[FB Neo (All Arcade)](https://github.com/libretro/FBNeo/raw/master/dats/FinalBurn%20Neo%20(ClrMame%20Pro%20XML%2C%20Arcade%20only).dat)

[FB Neo (NeoGeo only)](https://github.com/libretro/FBNeo/blob/master/dats/FinalBurn%20Neo%20(ClrMame%20Pro%20XML%2C%20Neogeo%20only).dat)

[Other Dats for home console systems available here](https://github.com/libretro/fbeo/tree/master/dats)

**Controls:**
lr-fbneo utilises RetroArch configs. Add custom retroarch controls to the retroarch.cfg file in:
```shell
/opt/retropie/configs/fba/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration) 

---

### lr-fbalpha2012
[Visit the FinalBurn Alpha 2012 homepage on github](https://github.com/libretro/fbalpha2012) 

Accepted File Extensions: **.7z .zip**

```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/libretrocores/lr-fbalpha2012
Config Dir: /opt/retropie/configs/fba/retroarch.cfg
```

>lr-fbalpha2012 does not have support for Samples in any form.

**ROM Version**: FB Alpha v0.2.97.30

**Total games emulated: [3369](https://github.com/libretro/fbalpha2012/blob/master/svn-current/trunk/gamelist.txt)**
* BIOS: 5
* Samples: ?

**FB Alpha v0.2.97.30 DAT File**: [FB Alpha v0.2.97.30.dat.zip](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/lr-fbalpha2012/FB%20Alpha%20v0.2.97.30.dat)

**FB Alpha v0.2.97.30 Neo Geo Only DAT File**: [fba-lr-neogeo](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/lr-fbalpha2012/fba-lr-neogeo-only.xml)

**Controls:**
lr-fbalpha2012 utilises RetroArch configs. Add custom retroarch controls to the retroarch.cfg file in:
```shell
/opt/retropie/configs/fba/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration) 

---

### PiFBA
[Visit the PiFBA homepage on sourceforge](http://sourceforge.net/projects/pifba/)

Accepted File Extensions: **.zip**

```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/emulators/pifba
Config Dir: /opt/retropie/configs/fba/fba2x.cfg
```
**ROM Version**: FB Alpha 0.2.96.71

**Total games emulated: 684**
* BIOS: ?
* Samples: ?

**FB Alpha v0.2.96.71 DAT File**: [FB Alpha v0.2.96.71 (ClrMame Pro).dat](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/pifba/FB%20Alpha%20v0.2.96.71%20(ClrMame%20Pro).dat)

**FB Alpha v0.2.96.71 'Lite' DAT File**: [fba_029671_od_release_10_working_roms_filtered.zip] (https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/pifba/fba_029671_od_release_10_working_roms_filtered.dat) (clones, non-working, mahjong, quiz, adult, casino, rythm removed)

**Controls**

PiFBA controls are located in:
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
