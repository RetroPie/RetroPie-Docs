***
![fba](https://cloud.githubusercontent.com/assets/10035308/12213772/eb6a317c-b63b-11e5-847f-2c03ffde43f3.png)
***
_Final Burn Alpha is a Multiple Arcade Emulator most popular for emulating Neo-Geo, Capcom, Konami, and Cave games. It is developed by the final burn team and originated from FinalBurn by Dave_

See also: [[MAME]], [[Neo Geo]]

***
There are a variety of arcade emulators available in RetroPie. There are significant differences in performance, compatibility, and configuration between them. If you're getting started with arcade emulation, start by reading [Managing Arcade ROMs](https://github.com/RetroPie/RetroPie-Setup/wiki/Managing-ROMs).

This page is a resource for additional details on RetroPie's Final Burn Alpha emulators including configuration paths, controls, and the ROM sets which each emulator requires.

[**All Arcade ROMS Compatibility List**](https://docs.google.com/spreadsheets/d/1antILt7D12EWOFzyJwTfB86NceghMJKXG7CdYumuHec/edit?usp=sharing) feel free to contribute to the list.

| Emulator | Rom Folder | Required ROM Version | Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fbalpha](#lr-fbalpha) | arcade **or** fba **or** neogeo  | FB Alpha v0.2.97.39| /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/fba/retroarch.cfg, **or** /opt/retropie/configs/neogeo/retroarch.cfg |
| [lr-fbalpha2012](#lr-fbalpha2012) | arcade **or** fba **or** neogeo  | FB Alpha v0.2.97.30 | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/fba/retroarch.cfg, **or** /opt/retropie/configs/neogeo/retroarch.cfg |
| [PiFBA](#pifba) | arcade **or** fba **or** neogeo  | FB Alpha 0.2.96.71 | /opt/retropie/emulators/pifba/fba2x.cfg **or** /opt/retropie/configs/fba/fba2x.cfg |

## Arcade ROM paths

In 3.0.0 some emulators share directories, so you need to choose which FBA, NeoGeo and mame4all version you want.
So you can have 1 romset for each of these (mame4all, FBA, NeoGeo, advmame) To avoid having several EmulationStation menus for different arcade emulators, all arcade-based ROMs can be placed in the `arcade` ROM folder, but you will have to specify which emulator each will use from the [Runcommand Menu](runcommand)

## Emulators

### lr-fbalpha
[Visit the Final Burn Alpha homepage on github](https://github.com/libretro/fbalpha)

**Note: Please see [[lr-fbalpha]] for information on how to configure specific features of this emulator.**

```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/libretrocores/lr-fbalpha
Config Dir: /opt/retropie/configs/fba/retroarch.cfg
```
**ROM Version**: FB Alpha 0.2.97.39

**Total games emulated: 4375**
* BIOS: 6
* Samples: ?

**FB Alpha v0.2.97.39 DAT File**:  [FB Alpha v0.2.97.39 (Arcade Only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029739%20dats/FB%20Alpha%20v0.2.97.39%20(ClrMame%20Pro%20XML%2C%20Arcade%20Only).dat)

**FB Alpha v0.2.97.39 DAT File**: [FB Alpha v0.2.97.39 (NeoGeo Only)](https://dl.dropboxusercontent.com/u/51705339/fba%20029739%20dats/FB%20Alpha%20v0.2.97.39%20(ClrMame%20Pro%20XML)%20(NeoGeo%20Only).dat) Instructions: Rebuild using Non-merged-sets, Place the ROMs in the neogeo ROMs folder and use FB Alpha v0.2.97.39 as the default emulator."

**[lr-fbalpha Compatibility List](https://docs.google.com/spreadsheets/d/1GaqIIoiWbzKHwZ52S2xCSDQXILo81Ls1mHK6czKGAtM/edit?usp=sharing)** feel free to contribute to the list.

---

### lr-fbalpha2012
[Visit the Final Burn Alpha 2012 homepage on github](https://github.com/libretro/fbalpha2012) 
```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/libretrocores/lr-fbalpha2012
Config Dir: /opt/retropie/configs/fba/retroarch.cfg
```
**ROM Version**: FB Alpha v0.2.97.30

**Total games emulated: [3369](https://github.com/libretro/fbalpha2012/blob/master/svn-current/trunk/gamelist.txt)**
* BIOS: 5
* Samples: ?

**FB Alpha v0.2.97.30 DAT File**: [FB Alpha v0.2.97.30.dat.zip](https://drive.google.com/file/d/0B2TMeZ6iEFvHcF96YmdjaWlEdXM/view?usp=sharing)

**FB Alpha v0.2.97.30 Neo Geo Only DAT File**: [fba-lr-neogeo](https://drive.google.com/file/d/0B2TMeZ6iEFvHVk1Ud1RoSHpfcFU/view?usp=sharing)

[**lr-fbalpha2012 Compatibility List**](https://docs.google.com/spreadsheets/d/1rWO7Lm0bTGNpak6J-CPzde0GNIDP0NHDoQdJ6iWosfA/edit?usp=sharing)  feel free to contribute to the list.

**Controls**
lr-fbalpha2012 utilises RetroArch configs. Add custom retroarch controls to the retroarch.cfg file in:
```shell
/opt/retropie/configs/fba/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration) 

---

### PiFBA
[Visit the PiFBA homepage on sourceforge](http://sourceforge.net/projects/pifba/)
```shell
Roms Dir: /home/pi/RetroPie/roms/fba
Binary Dir: /opt/retropie/emulators/pifba
Config Dir: /opt/retropie/configs/fba/fba2x.cfg
```
**ROM Version**: FB Alpha 0.2.96.71

**Total games emulated: 684**
* BIOS: ?
* Samples: ?

**FB Alpha v0.2.96.71 DAT File**: [FB Alpha v0.2.96.71 (ClrMame Pro).dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHZFJOckQyRVZ5OG8/view?usp=sharing)

**FB Alpha v0.2.96.71 'Lite' DAT File**: [fba_029671_od_release_10_working_roms_filtered.zip] (https://drive.google.com/file/d/0B2TMeZ6iEFvHMTV2TnlrZWwxRXc/view?usp=sharing) (clones, non-working, mahjong, quiz, adult, casino, rythm removed)

[**PiFBA Compatibility List**](https://docs.google.com/spreadsheets/d/1OZioLrz16ptaNbjQUDP5hhVzQDTOTn9Nz46Hbj3-06k/edit?usp=sharing)  feel free to contribute to the list.

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
