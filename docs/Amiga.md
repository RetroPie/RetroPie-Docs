***
![amiga](https://cloud.githubusercontent.com/assets/10035308/12189019/a46a4d44-b577-11e5-8378-d8196412103c.png)
***

_The Amiga was a family of personal computers released by Commodore in the 1980's and 1990's._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Amiberry](https://github.com/midwan/amiberry) | amiga  | .lha | kick33180.A500, kick34005.A500, kick40068.A1200 | Hardcoded |
| [UAE4ALL2](https://github.com/RetroPie/uae4all2) | amiga  | .adf | kick12.rom, kick13.rom, kick20.rom, kick31.rom | Hardcoded |
| [UAE4ARM](https://github.com/Chips-fr/uae4arm-rpi/) | amiga  | .zip .adf .dms .exe .adz .rp9 | kick13.rom, kick20.rom, kick31.rom | Hardcoded |
| [lr-puae](https://github.com/libretro/libretro-uae) | amiga | .zip .uae | kick34005.A500, kick40063.A600, kick40068.A1200 | /opt/retropie/configs/amiga/retroarch.cfg |

## Emulators: [Amiberry](https://github.com/midwan/amiberry)

Amiberry is a fork of UAE4ARM with support for WHDLoad, which offers a better console-like experience.

Please refer to the official Amiberry wiki for [**a detailed step-by-step installation and config guide**](https://github.com/midwan/amiberry/wiki/Using-Amiberry-WHDBooter-with-RetroPie).

## ROMS

For the optimal Amiberry experience, it is recommended that pre-installed WHDLoad packages are used. Amiberry has been designed to have compatibility with the 'Retroplay' WHDLoad packs. For more information on WHDLoad packages, see [here](https://github.com/midwan/amiberry/wiki/WHDLoad-Booter-(WHDBooter)-F.A.Q.#what-is-whdload-anyway).

Accepted File Extensions: **.lha**

 Place your WHDLoad packages in

```shell
/home/pi/RetroPie/roms/amiga/
```
More information on adding game data can be found [here](https://github.com/midwan/amiberry/wiki/Using-Amiberry-WHDBooter-with-RetroPie-(Step-3)).

## BIOS

Full documentation on the Kickstart roms required by Amiberry can be found [here](https://github.com/midwan/amiberry/wiki/Using-Amiberry-WHDBooter-with-RetroPie-(Step-2)).

Place your Kickstart roms in 

```shell
/home/pi/RetroPie/BIOS/
```
## Controls

Amiberry makes use the RetroArch configs created on [first controller configuration](https://retropie.org.uk/docs/Controller-Configuration/) in EmulationStation. Consequently, hotkey+X will bring up the UI and hotkey+Start can be used to exit Amiberry. For full documentation, please refer [here](https://github.com/midwan/amiberry/wiki/RetroArch-Commands).

Default controller choice can be edited in `/opt/retropie/configs/amiga/amiberry/whdboot/hostprefs.conf`. It is also possible to set the default controller choice as well as other Amiberry settings for individual games. For full documentation, please refer [here](https://github.com/midwan/amiberry/wiki/WHDLoad-Auto-booting#game-specific-settings-improving-game-compatibility).

It is possible to customise controls for individual games using the Amiberry UI. For full documentation, please refer [here](https://github.com/midwan/amiberry/wiki/Customised-Controls).


## Emulators: [UAE4ALL2](https://github.com/RetroPie/uae4all2), [UAE4ARM](https://github.com/Chips-fr/uae4arm-rpi/)

UAE4ALL2 is no longer developed and we recommend using UAE4ARM on the Raspberry Pi.

## ROMS
Accepted File Extensions: **.adf**

UAE4Arm also supports: **.dms .exe .rp9** and compressed formats **.zip .adz**

 Place your Amiga disks images in

```shell
/home/pi/RetroPie/roms/amiga/
```

## BIOS
The emulator comes with a free AROS rom that will work for running many games and demos. 

If you want to use a kickstart 1.3, 2.0, 3.1 rom place your **kick13.rom, kick20.rom, kick31.rom** files in 


```shell
/home/pi/RetroPie/BIOS/
```

|Name |Description |md5          |CRC32       |Comment |
| :--- | :--- | :--- | :--- | :--- |
|kick13.rom|KS ROM v1.3 (A500,A1000,A2000) rev 34.5 (256k)|82a21c1890cae844b3df741f2762d48d|c4f0f55f||
|kick20.rom|KS ROM v2.04 (A500+) rev 37.175 (512k)|dc10d7bdd1b6f450773dfb558477c230|c3bdb240||
|kick31.rom|KS ROM v1.3 (A1200) rev 40.68 (512k)|646773759326fbac3b2311fd8c8793ee|1483a091||


## Controls
These are hardcoded currently. This initial mapping was chosen as it's somewhat similar to MAME, and should mostly work on any controllers that use that input mapping (such as the picade). Joypad/Joystick is currently untested.

in game:
```
lctrl      - joy 1/mouse 1 (button X in gui)
lalt       - joy 2/mouse 2 (button Y in gui)
lshift     - joy 1 autofire (button A in gui)
z          - mouse 1  (button B in gui)

5          - switch input between mouse/joystick

arrow keys - up / down / left / right

F12 (UAE4ARM) and/or [CTRL]+[ESC] (UAE4ALL) - Open emulator menu
```

Launch it from Emulation Station, and you get the GUI where you can configure disks/roms/memory and insert adf images into the virtual floppy disk drives.

## Video Tutorial

[![Testing joypad in RetroPie](http://img.youtube.com/vi/dleumwWZp6Q/0.jpg)](http://www.youtube.com/watch?v=dleumwWZp6Q)

## Tips and troubleshooting

- Stuttering? Amiga systems/games are PAL (50Hz), but modern TVs typically default to a 60Hz mode when connected to a Raspberry Pi. Enter the RunCommand menu for your Amiga emulator, and select a valid mode that uses a 50Hz refresh rate in order to match the original PAL rate, and thus, eliminate stuttering.

- Some games work better with the '512Kb Chip' + '512Kb Slow' memory configuration rather than the default A500 '1MB Chip'. If your game crashes or fails to load, change the memory settings in the 'CPU RAM' tab of the UAE4ALL2 GUI.

- Some games do not work properly if more than one floppy drive is in use. If your game crashes or fails to load try to use just DF0 (change disc image during game if required) and not use DF1, DF2 and DF3.

- For Raspberry Pi 1 users - make sure you overclock your device. Amiga emulation works much faster when overclocked to maximum. Without overclocking some games do not run at full speed.

## Launching games directly from EmulationStation

### Script for creating configuration files 

Here you will find a script, and the necessary configuration files according to different version of UAE4arm, for creating game configuration file:

http://www.retropie-italia.it/viewtopic.php?f=10&t=16 

On EmulationStation, AMIGA, open "+Start UAE4Arm" and save a profile with random name then open the file and check the number in the parameter "config_version". Download the correct configuration file from previous link then rename it in "config.uae" and copy it, together with "AGCC.sh" (also download this from previous link), on Raspberry Pi. AGCC.sh uses the "config.uae" file in order to create games configuration and (if you want) you can edit it. For default behavior emulator is searching for kickstart 2.04 in

``/home/pi/RetroPie/roms/amiga/``

renamed in "kick20.rom", so you have to rename your kickstart or edit "config.uae".

Also follow these steps:

``sudo nano /etc/emulationstation/es_systems.cfg``

and edit the tag <extension> for "amiga" emulator in this way:

``<extension>.sh .uae .SH .UAE</extension>``

Then
``sudo nano /opt/retropie/configs/amiga/emulators.cfg``

and edit the line in this way:

``uae4arm = "pushd /opt/retropie/emulators/uae4arm/; ./uae4arm -f %ROM%"``

Point attention to the floppy image extension (case-insensitive):  .adf, .adz, .dms, .ipf, .zip

For game with multiple disks rename them in this way: 

Game bla bla bla (Disk 1 of N).adf  
Game bla bla bla (Disk 2 of N).adf  
...  
Game bla bla bla (Disk N of N).adf

in other words change ONLY the floppy identifier.  

Note: The old script from Mark Dunning has a problem with games with more than 9 floppies (creates others wrong config files) and creates a config file with name like "Game bla bla bla (Disk 1 of N).uae". This new app create only 1 file for a multiple disk game with the exact name of the game, "Game bla bla bla.uae"

### Other solution

Alternatively, a native BASH script to perform the same steps directly on the RetroPie machine can be found here:
https://github.com/Douggernaut/RetroPieAssistant/tree/master/Amiga

## Emulator: [lr-puae](https://github.com/libretro/libretro-uae)

lr-puae is an experimental emulator.  It can be installed from the experimental section of the [RetroPie-Setup Script.](https://github.com/RetroPie/RetroPie-Setup/wiki/Updating-RetroPie#using-the-retropie-setup-script)

## ROMS

Accepted File Extensions: **.zip .uae**

Place your Amiga ROMs and configuration files in 
```
/home/pi/RetroPie/roms/amiga
```

lr-puae requires the user to create .uae files manually, pointing to the ADF and Kickstart ROM like this:
```shell
kickstart_rom_file=/home/pi/RetroPie/BIOS/[insert kickstart ROM filename here]
floppy0=/home/pi/RetroPie/roms/amiga/[insert ADF filename here]
```

Below is a sample to use as a template for creating your own .uae file:
```ini
kickstart_rom_file=/home/pi/RetroPie/BIOS/kick31.rom
chipmem_size=1
bogomem_size=2
use_gui=no
nr_floppies=2
cpu_type=68000
cpu_speed=real
cpu_compatible=true
ntsc=false
chipset=ocs
immediate_blits=false
gfx_linemode=double
gfx_framerate=1
sound_output=normal
sound_frequency=44100
sound_channels=mixed
sound_interpol=none
show_leds=true
floppy_speed=100
gfx_center_vertical=smart
gfx_center_horizontal=smart
gfx_color_mode=16
floppy0=/home/pi/RetroPie/roms/amiga/Rick Dangerous.adf
```
## BIOS

Place your desired Kickstart ROM in:
```shell
/home/pi/RetroPie/BIOS/
```

## Controls

lr-puae utilizes Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/amiga/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)