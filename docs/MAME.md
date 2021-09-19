***
![mame](https://cloud.githubusercontent.com/assets/10035308/12213821/0acf7328-b63d-11e5-8127-48c8c5d31fe3.png)
***
_MAME stands for Multiple Arcade Machine Emulator. MAME can emulate thousands of games that otherwise would have been lost in the ash-heaps of history._

See Also: [FinalBurn-Neo](FinalBurn-Neo), [Neo Geo](Neo-Geo)

***

There are a variety of arcade emulator versions available in RetroPie. There are significant differences in performance, compatibility, and configuration between them. If you're getting started with an arcade emulation project, begin by reading the [Arcade](Arcade) page.

This page is a resource for additional details on RetroPie's MAME emulators including configuration paths, controls, and the ROM sets which each emulator requires.

| Emulator | ROM Folder(s) | Extension | Required ROM Set Version
| :---: | :---: | :---: | :--- |
| [mame4all-pi](#mame4all-pi) | arcade **or** mame-mame4all | .zip | MAME 0.37b5 
| [lr-mame2000](#lr-mame2000-mame-2000) | arcade **or** mame-libretro | .zip | MAME 0.37b5
| [lr-mame2003](#lr-mame2003-mame-2003) | arcade **or** mame-libretro | .zip | MAME 0.78
| [lr-mame2003-plus](#lr-mame2003-plus-mame-2003-plus) | arcade **or** mame-libretro | .zip | MAME 0.78-MAME 0.188
| [lr-mame2010](#lr-mame2010-mame-2010) | arcade **or** mame-libretro | .zip | MAME 0.139
| [lr-mame2015](#lr-mame2015-mame-2015) | arcade **or** mame-libretro | .zip .7z | MAME 0.160
| [lr-mame2016](#lr-mame2016-mame-2016) | arcade **or** mame-libretro | .zip .7z | MAME 0.174
| [AdvanceMAME 0.94](#advancemame-094) | arcade **or** mame-advmame | .zip | MAME 0.94
| [AdvanceMAME 1.4](#advancemame-14) | arcade **or** mame-advmame | .zip | MAME 0.106
| [AdvanceMAME 3](#advancemame-3) | arcade **or** mame-advmame | .zip | MAME 0.106
| [MAME](#mame) | arcade **or** mame | .zip .7z | same as MAME version
| [lr-mame](#lr-mame) | arcade **or** mame-libretro | .zip .7z | same as MAME version

## MAME ROM paths

Three of the available MAME ROM paths in RetroPie are shared directories which are used by more than one emulator: `arcade`, `mame-libretro`, `mame-advmame`. In order to successfully load zipped ROM sets in these locations you must specify the arcade emulator version which matches your ROMs.

To avoid having several menus for different arcade emulators, all arcade-based ROMs can be placed in the `arcade` ROM folder, but you will have to specify which emulator each zipped ROM set will use from the [Runcommand Menu](Runcommand).

## Emulators

---
### [mame4all-pi](http://sourceforge.net/projects/mame4allpi/ "MAME4ALL-Pi website")

| Folder | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-mame4all`
| Binary | `/opt/retropie/emulators/mame4all`
| Configuration | `/opt/retropie/configs/mame-mame4all`
| Samples | `/home/pi/RetroPie/mame4-all/samples/`


**MAME Version**: 0.37b5 (July 2000)

**Active Sets: 2241**

* BIOS: 1
* CHDs: 0
* Samples: 35

* 1126 Parent Roms
* 1025 Clones Roms
* 129 NeoGeo Roms (Parent+Clone)

**MAME 0.37b5 DAT File**: [mame4all-037b5-RetroPie-260.dat](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/mame4all/mame4all-037b5-RetroPie-260.dat)

**MAME 0.37b5 XML File**: [mame4all-no-clones-no-neogeo](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/mame4all/mame4all-no-clones-no-neogeo.xml) Does not include clones or NeoGeo romsets.

#### Controls

While in a game press <kbd>Tab</kbd> to open the menu to set up controls. The **MAME4ALL** configuration is saved in:
```shell
/opt/retropie/configs/mame-mame4all/cfg/default.cfg
```

Other files in the `cfg` directory are ROM specific configs.

_**Note**_: If configuration or other aspect of the configuration need resetting to defaults, remove the `default.cfg` or ROM specific `.cfg` file, and it will be re-created with default values next time MAME4ALL is started or the ROM configuration modified.

---
### [lr-mame2000 (MAME 2000)](https://github.com/libretro/mame2000-libretro "MAME 2000 website")

| Folder | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-mame4all` <br> `/home/pi/RetroPie/roms/mame-libretro` <br> `/home/pi/RetroPie/roms/arcade`
| Binary | `/opt/retropie/libretrocores/lr-mame2000`
| Configuration | `/opt/retropie/configs/mame-mame4all/retroarch.cfg`
| Samples | `/home/pi/RetroPie/BIOS/mame2000/samples/`

**MAME Version**: 0.37b5 (July 2000)

**Active Sets: 2241**

* BIOS: 1
* CHDs: 0
* Samples: 35

**MAME 0.37b5 DAT File**: [mame4all-037b5-RetroPie-260.zip](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/mame4all/mame4all-037b5-RetroPie-260.dat)

**MAME 0.37b5 'Lite' DAT File**: [mame4all-no-clones-no-neogeo](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/mame4all/mame4all-no-clones-no-neogeo.xml) - Does not include clones or NeoGeo romsets.

#### Controls

MAME 2000 uses [RetroArch control configuration](RetroArch-Configuration). Custom Retroarch controls can be added to the `retroarch.cfg` file in

 * `/opt/retropie/configs/mame-libretro/retroarch.cfg`
 * `/opt/retropie/configs/arcade/retroarch.cfg`

---
### [lr-mame2003 (MAME 2003)](https://github.com/libretro/mame2003-libretro "MAME 2003 website")

Please see **[MAME 2003 on RetroPie](lr-mame2003)** for information on how to configure specific features of this emulator.

| Folder | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-libretro` <br> `/home/pi/RetroPie/roms/arcade`
| Binary | `/opt/retropie/libretrocores/lr-mame2003`
| Configuration | `/opt/retropie/configs/mame-libretro/retroarch.cfg`
| Samples | `/home/pi/RetroPie/BIOS/mame2003/samples/`


**MAME Version**: 0.78 (December 2003)

**Active Sets: 4705**

* BIOS: 15
* CHDs: 30
* Samples: 56

**MAME 0.78 XML DAT File**: [MAME 0.78.dat](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/lr-mame2003/MAME%200.78.dat)

**MAME 0.78u5 DAT File**: [mame2003-lr-working-no-clones](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/lr-mame2003/mame2003-lr-no-clones-no-neogeo.xml) - Working romsets only. Does not include clones.

**MAME 0.78u5 'Lite' DAT File**: [mame2003-lr-lite](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/lr-mame2003/mame2003-lr-lite.xml) - Working romsets only. Does not include: clones, NeoGeo, PlayChoice NES/multiplay, romsets with rotary/dial/trackball/light gun controls, or romsets classified as casino/quiz/mahjong/fruit_machines/rhythm/mature.

**[Mame 2003 catver.ini](https://raw.githubusercontent.com/libretro/mame2003-libretro/master/metadata/catver.ini)** also contains data on games definitively known not to work, as well as sorting data for mature games and other, less desirable, romsets.

#### Controls


MAME 2003-Plus uses both [RetroArch control configuration](RetroArch-Configuration) and the MAME input configuration menu (accessible by pressing <kbd>Tab</kbd>). Custom Retroarch controls can be added to the `retroarch.cfg` file in

 * `/opt/retropie/configs/mame-libretro/retroarch.cfg`
 * `/opt/retropie/configs/arcade/retroarch.cfg`

---
### [lr-mame2003-plus (MAME 2003-Plus)](https://github.com/libretro/mame2003-plus-libretro "MAME 2003-Plus website")


MAME 2003-Plus (also referred to as MAME 2003+ and mame2003-plus) is a libretro arcade system emulator core with an emphasis on high performance and broad compatibility with mobile devices, single board computers, embedded systems, and similar platforms.

In order to take advantage of the performance and lower hardware requirements of an earlier MAME architecture, MAME 2003-Plus began with the MAME 2003 codebase, which is itself derived from xmame 0.78. Upon that base, MAME 2003-Plus contributors have back-ported support for several hundred additional games as well as other functionality not originally present in MAME 0.78.

**Please see [the libretro MAME 2003-Plus core documentation](https://docs.libretro.com/library/mame2003_plus/) for information on how to configure specific features of this emulator.**

| Folder/File | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-libretro` <br> `/home/pi/RetroPie/roms/arcade`
| Binary | `/opt/retropie/libretrocores/lr-mame2003-plus`
| Configuration | `/opt/retropie/configs/mame-libretro/retroarch.cfg` <br> `/opt/retropie/configs/arcade/retroarch.cfg`
| Samples | `/home/pi/RetroPie/BIOS/mame2003-plus/samples/`

**MAME Version**: 0.78-0.188 (MAME 0.78 as a baseline with other ROMs back-ported from later MAME romsets)

**Active Sets: 4850**

* BIOS: 15
* CHDs: 30
* Samples: 66 + 6 Optional "Soundtrack Samples"

**MAME 2003-Plus DAT File**: [Github project page](https://raw.githubusercontent.com/libretro/mame2003-plus-libretro/master/metadata/mame2003-plus.xml). An XML "DAT" file can be generated from the emulator, directly from the MAME menu.

**[The MAME 2003-Plus catver.ini](https://raw.githubusercontent.com/libretro/mame2003-plus-libretro/master/metadata/catver.ini)** also contains data on games definitively known not to work, as well as sorting data for mature games or other, less desirable, romsets.

#### Controls

MAME 2003-Plus uses both [RetroArch control configuration](RetroArch-Configuration) and the MAME input configuration menu (accessible by pressing <kbd>Tab</kbd>). Custom Retroarch controls can be added to the `retroarch.cfg` file in

 * `/opt/retropie/configs/mame-libretro/retroarch.cfg`
 * `/opt/retropie/configs/arcade/retroarch.cfg`
 
**Some notes** about extra controls options and configuration available in MAME 2003-Plus:

* MAME 2003-Plus can use different [RetroPad layouts](https://docs.libretro.com/library/mame2003_plus/#default-retropad-layouts), chosen with the _Device Type_ configuration option in the _Controls_ menu in RetroArch:
   * _Classic Gamepad_, based on mainline MAME's default Xbox 360 controller layout, likely to suit DualShock or SNES-style gamepads.
   * _Modern Fightstick_, a fight stick and pad layout popularised by Street Fighter IV and assumes an 8+ button controller.
   * _6-Button_, a layout intended for SNES-type RetroPad controls as well as 6-button arcade panels arcade panels.
   * _8-Button_, a layout intended for an arcade panel (8 buttons)

* MAME 2003-Plus maps the analog controls to joystick control by default, instead of the D-Pad. This can be changed from the [Core Options](RetroArch-Core-Options), switching the _Control mapping_ option to digital.

* MAME 2003-Plus disables the MAME menu by default (usually mapped to <kbd>Tab</kbd>). It can be enabled by changing the _Input interface_ [Core Option](RetroArch-Core-Options) to `simultaneous`.
 
 
---
### [lr-mame2010 (MAME 2010)](https://github.com/libretro/mame2010-libretro "MAME 2010 website")

| Folder | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-libretro` <br> `/home/pi/RetroPie/roms/arcade`
| Binary | `/opt/retropie/libretrocores/lr-mame2010`
| Configuration | `/opt/retropie/configs/mame-libretro/retroarch.cfg`
| Samples | `/home/pi/RetroPie/BIOS/mame2010/samples`

**MAME Version**: 0.139 (August 2010)

**Active Sets: 8782**

* BIOS: 67
* CHDs: 406
* Samples: 70 (4 more samples are not in circulation)

**MAME 0.139 DAT File**: [MAME 0.139.dat](https://raw.githubusercontent.com/libretro/mame2010-libretro/master/metadata/mame2010.xml) 

#### Controls

MAME 2010 uses [RetroArch control configuration](RetroArch-Configuration). Custom Retroarch controls can be added to the `retroarch.cfg` file in

 * `/opt/retropie/configs/mame-libretro/retroarch.cfg`
 * `/opt/retropie/configs/arcade/retroarch.cfg`

##### Default Player 1 and 2 Controls

	RETRO_DEVICE_ID_JOYPAD_START        MAME: KEY_START
	RETRO_DEVICE_ID_JOYPAD_SELECT       MAME: KEY_COIN
	RETRO_DEVICE_ID_JOYPAD_A            MAME: KEY_BUTTON_1
	RETRO_DEVICE_ID_JOYPAD_B            MAME: KEY_BUTTON_2
	RETRO_DEVICE_ID_JOYPAD_X            MAME: KEY_BUTTON_3
	RETRO_DEVICE_ID_JOYPAD_Y            MAME: KEY_BUTTON_4
	RETRO_DEVICE_ID_JOYPAD_L            MAME: KEY_BUTTON_5
	RETRO_DEVICE_ID_JOYPAD_R            MAME: KEY_BUTTON_6
	RETRO_DEVICE_ID_JOYPAD_L2           MAME: KEY_BUTTON_7
	RETRO_DEVICE_ID_JOYPAD_UP           MAME: KEY_JOYSTICK_U
	RETRO_DEVICE_ID_JOYPAD_DOWN         MAME: KEY_JOYSTICK_D
	RETRO_DEVICE_ID_JOYPAD_LEFT         MAME: KEY_JOYSTICK_L
	RETRO_DEVICE_ID_JOYPAD_RIGHT        MAME: KEY_JOYSTICK_R
	RETRO_DEVICE_ID_JOYPAD_R2           Turbo Button

##### Default Player 3 and 4 Controls

	RETRO_DEVICE_ID_JOYPAD_START        MAME: KEY_START
	RETRO_DEVICE_ID_JOYPAD_SELECT       MAME: KEY_COIN
	RETRO_DEVICE_ID_JOYPAD_A            MAME: KEY_BUTTON_1
	RETRO_DEVICE_ID_JOYPAD_B            MAME: KEY_BUTTON_2
	RETRO_DEVICE_ID_JOYPAD_X            MAME: KEY_BUTTON_3
	RETRO_DEVICE_ID_JOYPAD_UP           MAME: KEY_JOYSTICK_U
	RETRO_DEVICE_ID_JOYPAD_DOWN         MAME: KEY_JOYSTICK_D
	RETRO_DEVICE_ID_JOYPAD_LEFT         MAME: KEY_JOYSTICK_L
	RETRO_DEVICE_ID_JOYPAD_RIGHT        MAME: KEY_JOYSTICK_R
	RETRO_DEVICE_ID_JOYPAD_R2           Turbo Button
    
##### Native MAME UI Controls

_Note: these controls are only operational for Player 1_

	RETRO_DEVICE_ID_JOYPAD_L3           Test/Service Mode
	RETRO_DEVICE_ID_JOYPAD_R3           Enter MAME UI
	RETRO_DEVICE_ID_JOYPAD_A            MAME: IPT_UI_SELECT (Make selections in the MAME GUI)
      
---
### [lr-mame2015 (MAME 2015)](https://github.com/libretro/mame2015-libretro "MAME 2015 website")

**Note**: This emulator is considered 'experimental' in RetroPie and has limited functionality. It requires more processing power than earlier MAME versions and will not run as many games at full speed on Raspberry Pi hardware.

| Folder | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-libretro` <br> `/home/pi/RetroPie/roms/arcade`
| Binary | `/opt/retropie/libretrocores/lr-mame2015`
| Configuration | `/opt/retropie/configs/mame-libretro/retroarch.cfg`
| Samples | `/home/pi/RetroPie/BIOS/mame2010/samples`

**MAME Version**: 0.160

**Active Sets: ??**

* BIOS: ??
* CHDs: ??
* Samples: ?? (4 more samples are not in circulation)

**MAME 0.160 DAT File**: [ProgettoSnaps MAME .dat page](http://www.progettosnaps.net/dats/MAME/)

#### Controls

MAME 2015 uses [RetroArch control configuration](RetroArch-Configuration). Custom Retroarch controls can be added to the `retroarch.cfg` file in

 * `/opt/retropie/configs/mame-libretro/retroarch.cfg`
 * `/opt/retropie/configs/arcade/retroarch.cfg`

---
### [lr-mame2016 (MAME 2016)](https://github.com/libretro/mame2016-libretro "MAME 2015 website")

**Note**: This emulator is considered 'experimental' in RetroPie and has limited functionality. It requires more processing power than earlier MAME versions and will not run as many games at full speed on Raspberry Pi hardware.

| Folder | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-libretro` <br> `/home/pi/RetroPie/roms/arcade`
| Binary | `/opt/retropie/libretrocores/lr-mame2016`
| Configuration | `/opt/retropie/configs/mame-libretro/retroarch.cfg`

**MAME Version**: 0.174

**Active Sets: ??**

* BIOS: ??
* CHDs: ??
* Samples: ?? (4 more samples are not in circulation)

**MAME 0.174 DAT File**: [ProgettoSnaps MAME .dat page](http://www.progettosnaps.net/dats/MAME/)

#### Controls

MAME 2016 uses [RetroArch control configuration](RetroArch-Configuration). Custom Retroarch controls can be added to the `retroarch.cfg` file in

 * `/opt/retropie/configs/mame-libretro/retroarch.cfg`
 * `/opt/retropie/configs/arcade/retroarch.cfg`

---
### [AdvanceMAME 0.94](https://sourceforge.net/projects/advancemame/ "AdvanceMAME website")

| Folder | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-advmame` <br> `/home/pi/RetroPie/roms/arcade`
| Binary | `/opt/retropie/emulators/advmame/bin`
| Configuration | `/opt/retropie/configs/mame-advmame`
| Samples | `/home/pi/RetroPie/roms/mame-advmame/samples`

**MAME Version**: MAME 0.94 (March 2005)

**Active Sets: 5563**

* BIOS: 25
* CHDs: ?
* Samples: ?

**AdvanceMAME 0.94 DAT File**: [advmame-0.94-RetroPie-260.7z](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/advmame.94/advmame-0.94-RetroPie-260.dat)

#### Controls

While in a game, press <kbd>Tab</kbd> to open the menu and set up controls. AdvanceMAME configuration for controls is stored in `/opt/retropie/configs/mame-advmame/advmame-0.94.0.rc`. Changes to specific games result in `.rc` file entries with a prefix for the ROM (i.e. `bwidow/input_map[p1_doubleleft_up] keyboard[0,up]` for the `bwidow` game).

_**Note**_: The `.rc` file can also be edited manually, with a text editor. Any config can be made ROM-specific using a `romname/` prefix which is handy for overriding a setting for a specific ROM or class of ROMs, such as `vertical/`. However, a single mistake in the .rc file will stop AdvanceMAME from launching. It is always best to make a backup of the configuration file before manual edits.

---

### [AdvanceMAME 1.4](https://sourceforge.net/projects/advancemame/ "AdvanceMAME website")

| Folder | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-advmame` <br> `/home/pi/RetroPie/roms/arcade`
| Binary | `/opt/retropie/emulators/advmame/bin`
| Configuration | `/opt/retropie/configs/mame-advmame`
| Samples | `/home/pi/RetroPie/roms/mame-advmame/samples`

**MAME Version**: MAME 0.106 (May 2006)

**Active Sets: 6166**

* BIOS: 26
* CHDs: 86
* Samples: 64 (3 more samples are not in circulation)

**AdvanceMAME 1.4 DAT File**: [advmame12-106.7z](https://raw.githubusercontent.com/HerbFargus/retropie-dat/master/advmame1.2/advmame12-106.dat)

#### Controls

While in a game press <kbd>Tab</kbd> to open the menu to set up controls. AdvanceMAME configuration for controls is stored in `/opt/retropie/configs/mame-advmame/advmame-1.4.rc`. Changes to specific games result in `.rc` file entries with a prefix for the ROM (i.e. `bwidow/input_map[p1_doubleleft_up] keyboard[0,up]`)

Note: The `.rc` file can also be edited manually. Any config can be made ROM-specific using a `romname/` prefix which is handy for overriding a setting for a specific ROM or class of ROMs, such as `vertical/`. However, a single mistake in the `.rc` file will stop AdvanceMAME from launching. It is always best to make a backup of the configuration file before manual edits.

---
### [AdvanceMAME 3](https://sourceforge.net/projects/advancemame/ "AdvanceMAME website")

| Folder | Location |
|:------ |:------ |
| Roms | `/home/pi/RetroPie/roms/mame-advmame` <br> `/home/pi/RetroPie/roms/arcade`
| Binary | `/opt/retropie/emulators/advmame/bin`
| Configuration | `/opt/retropie/configs/mame-advmame`
| Samples | `/home/pi/RetroPie/roms/mame-advmame/samples`

**MAME Version**: MAME 0.106 (May 2006)

**Active Sets: 6166**

* BIOS: 26
* CHDs: 86
* Samples: 64 (3 more samples are not in circulation)

**AdvanceMAME 3 DAT File**: same as AdvanceMAME 1.4, see above.

#### Controls

While in a game, press <kbd>Tab</kbd> to open the menu and set up the controls. AdvanceMAME configuration for controls is stored in `/opt/retropie/configs/mame-advmame/advmame.rc`. Changes to specific games result in `.rc` file entries with a prefix for the ROM (i.e. `bwidow/input_map[p1_doubleleft_up] keyboard[0,up]`)

_**Note**_: The .rc file can be edited manually. Any config can be made ROM-specific using a `romname/` prefix, which is handy for overriding a setting for a specific ROM or class of ROMs, such as `vertical/`. However, a single mistake in the `.rc` file will stop AdvanceMAME from launching. It is always best to make a backup of the `advmame.rc` file before manual edits.

---
### [MAME](https://mamedev.org "MAME project website")
**Note**: This emulator is considered 'experimental' in RetroPie. It requires more processing power than earlier MAME versions and will not run as many games at full speed on Raspberry Pi hardware.

| Folder | Location |
|:------ |:------ |
|Roms | `/home/pi/RetroPie/roms/mame` <br> `/home/pi/RetroPie/roms/arcade` |
|Binary | `/opt/retropie/emulators/mame/bin` |
|Configuration | `/opt/retropie/configs/mame` |
|BIOS | `/home/pi/RetroPie/BIOS/mame` |
|Samples | `/home/pi/RetroPie/roms/mame/samples` |

**MAME Version**: MAME has monthly versioned releases, there is no single version. Version `0.221` was released for May 2020, `0.222` for June 2020, etc.   
Installing from binary will probably get a version that's a little behind the current MAME, installing from source will always get the latest monthly release.

**_NOTE_**: installing from source requires a lot of RAM and CPU power, on Pi3 and lower end systems could take more than one day - use the binary release when available, instead of installing from source.

**MAME Dat Files**: [ProgettoSnaps MAME .dat page](http://www.progettosnaps.net/dats/MAME/) has versions for each MAME release.

**Active Sets:** ???

#### Controls

While in a game, press <kbd>Tab</kbd> to open the MAME menu, then choose the Input configuration. MAME controls configuration is saved in `/home/pi/RetroPie/roms/mame/cfg` :

* default/general input configuration file is `default.cfg`
* per-game configurations are saved in `<romname>.cfg`

---
### [lr-mame](https://github.com/libretro/mame "lr-mame project website")
**Note**: This emulator is considered 'experimental' in RetroPie. It requires more processing power than earlier MAME versions and will not run as many games at full speed on Raspberry Pi hardware.

| Folder | Location |
|:------ |:------ |
|Roms | `/home/pi/RetroPie/roms/mame` <br> `/home/pi/RetroPie/roms/mame-libretro` |
|Binary | `/opt/retropie/libretrocores/lr-mame` |
|Configuration | `/opt/retropie/configs/arcade` |
|BIOS | `/home/pi/RetroPie/BIOS/mame` |
|Samples | `/home/pi/RetroPie/roms/mame/samples` |

**MAME Version**: Similar to [MAME](#mame), `lr-mame` follows the monthtly MAME releases, so there is no single version. Installing from binary will probably get a version that's a little behind the current MAME, but the upstream Libretro repository tries to keep up with MAME's monthly releases, so installing from source 

**_NOTE_**: installing from source requires a lot of RAM and CPU power, on Pi3 and lower end systems could take more than a day. Use the binary release when available.

**MAME Dat Files**: [ProgettoSnaps MAME .dat page](http://www.progettosnaps.net/dats/MAME/) has versions for each MAME release.

**Active Sets:** ???

#### Controls

`lr-mame` uses the [RetroArch control configuration](RetroArch-Configuration).

 * `/opt/retropie/configs/mame-libretro/retroarch.cfg`
 * `/opt/retropie/configs/arcade/retroarch.cfg`
