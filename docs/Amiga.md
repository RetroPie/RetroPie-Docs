***
![amiga](https://cloud.githubusercontent.com/assets/10035308/12189019/a46a4d44-b577-11e5-8378-d8196412103c.png)
***

_The Amiga was a family of personal computers released by Commodore in the 1980's and 1990's._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Amiberry](https://github.com/midwan/amiberry) | amiga  | .lha | kick33180.A500, kick34005.A500, kick40068.A1200 | Hardcoded |
| [lr-puae](https://github.com/libretro/libretro-uae) | amiga | .zip .uae .adf .dms .fdi .ipf .hdf .hdz .m3u | kick34005.A500, kick40063.A600, kick40068.A1200 | /opt/retropie/configs/amiga/retroarch.cfg |
| [UAE4ALL2](https://github.com/RetroPie/uae4all2) | amiga  | .adf | kick12.rom, kick13.rom, kick20.rom, kick31.rom | Hardcoded |
| [UAE4ARM](https://github.com/Chips-fr/uae4arm-rpi/) | amiga  | .zip .adf .dms .exe .adz .rp9 | kick13.rom, kick20.rom, kick31.rom | Hardcoded |


## Emulators: [Amiberry](https://github.com/midwan/amiberry)

Amiberry is a fork of UAE4ARM with support for WHDLoad, which offers a better console-like experience.

Please refer to the official Amiberry wiki for [**a detailed step-by-step installation and config guide**](https://github.com/midwan/amiberry/wiki/Using-Amiberry-with-RetroPie---Installation-and-Setup).

### ROMS

For the optimal Amiberry experience, it is recommended that pre-installed WHDLoad packages are used. Amiberry has been designed to have compatibility with the 'Retroplay' WHDLoad packs. For more information on WHDLoad packages, see [here](https://github.com/midwan/amiberry/wiki/WHDLoad-Booter-(WHDBooter)-F.A.Q.#what-is-whdload-anyway).

Accepted File Extensions: **.lha**

 Place your WHDLoad packages in

```shell
/home/pi/RetroPie/roms/amiga/
```
More information on adding game data can be found [here](https://github.com/midwan/amiberry/wiki/Using-Amiberry-WHDBooter-with-RetroPie-(Step-3)).

### BIOS

Full documentation on the Kickstart roms required by Amiberry can be found [here](https://github.com/midwan/amiberry/wiki/Using-Amiberry-WHDBooter-with-RetroPie-(Step-2)).

Place your Kickstart roms in 

```shell
/home/pi/RetroPie/BIOS/
```
### Controls

Amiberry makes use the RetroArch configs created on [first controller configuration](https://retropie.org.uk/docs/Controller-Configuration/) in EmulationStation. Consequently, hotkey+X will bring up the UI and hotkey+Start can be used to exit Amiberry. For full documentation, please refer [here](https://github.com/midwan/amiberry/wiki/RetroArch-Commands).

Default controller choice can be edited in `/opt/retropie/configs/amiga/amiberry/whdboot/hostprefs.conf`. It is also possible to set the default controller choice as well as other Amiberry settings for individual games. For full documentation, please refer [here](https://github.com/midwan/amiberry/wiki/WHDLoad-Auto-booting#game-specific-settings-improving-game-compatibility).

It is possible to customise controls for individual games using the Amiberry UI. For full documentation, please refer [here](https://github.com/midwan/amiberry/wiki/Customised-Controls).

## Emulator: [lr-puae](https://github.com/libretro/libretro-uae)

lr-puae is an experimental emulator.  It can be installed from the experimental section of the [RetroPie-Setup Script.](https://github.com/RetroPie/RetroPie-Setup/wiki/Updating-RetroPie#using-the-retropie-setup-script)

### BIOS

Place your desired Kickstart ROMs in:
```shell
/home/pi/RetroPie/BIOS/
```
To use disk and WHDLoad games with this core you'll need the following Kickstart ROMs. Rename them to the given name and copy the file to RetroArch system directory.

It is critical to use Kickstarts with the right MD5, otherwise the core might not start.

|Name|Description|System|MD5|
|---|---|---|---|
|kick34005.A500|Kickstart v1.3 (Rev. 34.005)|Amiga 500|82a21c1890cae844b3df741f2762d48d|
|kick40063.A600|Kickstart v3.1 (Rev. 40.063)|Amiga 600|e40a5dfb3d017ba8779faba30cbd1c8e|
|kick40068.A1200|Kickstart v3.1 (Rev. 40.068)|Amiga 1200|646773759326fbac3b2311fd8c8793ee|

### Controls

lr-puae utilizes Retroarch configurations.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/amiga/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

| Button | Control |
| :---: | :---: |
| L2 | Show/Hide status|
| R2 | Sound on/off|
| L  | Toggle Num Joy |
| R  | Change Mouse speed 1 to 6 (for gui and emu)|
| Select | Toggle Mouse/Joy mode |
| Start | Show/Hide vkbd |
| A  | Fire/Mouse btn A / Valid key in virtual keyboard|
| B  | Mouse btn B|
| X  |  |
| Y  | Emulator GUI|

### ROMS

Place your Amiga ROMs and configuration files in 
```
/home/pi/RetroPie/roms/amiga
```

| extension | file description | requirements |
| :---: | :---: | :---: |
| .uae | text config file pointing to .hdf, .adf, or .ipf | needs to be created per ROM |
| .adf | disk image | loads directly |
| .adz | zipped disk image | loads directly |
| .dms | disk image, seems rare | loads directly |
| .fdi | disk image, seems rare | loads directly |
| .ipf | disk image | requires capsimg.so in retroarch directory |
| .hdf | hard disk image | requires WHDLoad set up |
| .hdz | zipped hard disk image | requires WHDLoad set up |
| .m3u | text config file | needs to be created for multidisk games |
| .zip | must contain an .adf, .hdf, or .ipf | unzip is handled by Retroarch |
| .lha | zipped hard disk image in an *Amiga-specific* compression format, not handled by lr-puae | unzip is handled within the emulator |

One thing that Amiga enthusiasts seem to point out repeatedly is that although you may be able to expand an `.lha` file on Windows, you often shouldn't; the Amiga operating system and Windows don't always agree on paths and special characters, with the result that you can corrupt the file when unzipping it.

#### Disk images, WHDLoad and M3U support
You can pass a disk or hdd image (WHDLoad) as a rom.

Supported format are :
- `.adf`, `.dms`, `.fdi`, `.ipf`, `.zip` files for disk images. Note that `.ipf` files require additional files, see below.
- `.hdf`, `.hdz` for hdd images. Note that hdd images require WHDLoad to be set up, see below.
- `.m3u` for multiple disk images. Note that these have special requirements, see below.

_Note that `.lha` files are not supported._

When passing a disk image, a hdd image or a m3u file as parameter the core will generate a temporary `puae_libretro.uae` configuration file in RetroArch saves directory and use it to automatically launch the game.

#### Configuration
To generate the temporary `.uae` configuration file the core will use the core options configured in RetroArch.

The most important option is the model.

Three models are provided (hardcoded configuration) :

|Model|Description|
|---|---|
|A500|Simulate an Amiga 500 with OCS chipset, 1MB of RAM and 1.8MB of slow memory expansion (bogomem).|
|A600|Simulate an Amiga 600 with ECS chipset, 1MB of RAM and 4MB of fast memory expansion.|
|A1200|Simulate an Amiga 1200 with AGA chipset, 2MB of RAM and 8MB of fast memory expansion.|

As the configuration file is only generated when launching a game you must restart RetroArch for the changes to take effects.

#### IPF Support
Most full-price commercial Amiga games had some form of custom disk format and/or copy protection on them. For this reason, most commercial Amiga games cannot be stored in ADF files unaltered, but there is an alternative called Interchangeable Preservation Format (IPF) which was specifically designed for this purpose.

IPF support is done through the CAPSIMG library. To enable it you have to put a dynamic library called capsimg.dll (Windows) or capsimg.so (Linux, macOS) in your retroarch root directory (where the retroarch executable is located; in a default install, this is `/opt/retropie/emulators/retroarch/bin/`).

Compatible CAPSIMG libraries for Windows, macOS and Linux can be found at https://fs-uae.net/download#plugins

Please be aware that there are 32-bit and 64-bit versions of the library. Choose the one corresponding to your RetroArch executable.

_As of July 1 2019, .ipf support may not work on Raspberry Pi, though it is apparently working on Windows_.

#### M3U Support
When you have a multi disk game, you can use an `.m3u` file to specify each disk of the game and change them from the RetroArch Disk control interface.

An M3U file is a simple text file with one disk per line (see https://en.wikipedia.org/wiki/M3U).

Example :

Simpsons, The - Bart vs. The Space Mutants.m3u
```
Simpsons, The - Bart vs. The Space Mutants_Disk1.adf
Simpsons, The - Bart vs. The Space Mutants_Disk2.adf
```
Path can be absolute or relative to the location of the M3U file.

When a game asks for it, you can change the current disk in the RetroArch 'Disk Control' menu :
- Eject the current disk with 'Disk Cycle Tray Status'.
- Select the right disk index.
- Insert the new disk with 'Disk Cycle Tray Status'.

Note : zip support is provided by RetroArch and is done before passing the game to the core. So, when using a m3u file, the specified disk image must be uncompressed (`.adf`, `.dms`, `.fdi`, `.ipf` file formats).

#### WHDLoad
To use WHDLoad games you'll need to have a prepared WHDLoad image named 'WHDLoad.hdf' in RetroArch system directory (`~/RetroPie/BIOS`).

In this WHDLoad image you must have the three kickstart roms (kick34005.A500, kick40063.A600, kick40068.A1200) in the 'Dev/Kickstart' directory.

To do this, you can consult the excellent tutorial made by Allan Lindqvist (http://lindqvist.synology.me/wordpress/?page_id=182) just jump to the 'Create WHDLoad.hdf' section.

The core only supports HDD image files format (hdf and hdz) and slave file must be named 'game.slave'. 

#### Create a hdf file for a game 
If you have a WHDLoad game in a zip or a directory, you will have to create an image file.

To do this you can use ADFOpus (http://adfopus.sourceforge.net/) or amitools (https://github.com/cnvogelg/amitools).

Example, to create a hdf file from a zipped WHDLoad game :
- Extract files from the zip to a directory.
- Go to the directory where files were extracted.
- Rename the main slave file (ending with '.Slave') to 'game.Slave' (certain games have many slave files, guess which is the right one).
- Pack the directory in a hdf file :
	- Using ADFOpus (see [Allan Lindqvist's tutorial](http://lindqvist.synology.me/wordpress/?page_id=182)).
	- Using amitools.
	
The amitools command to use is :
```
xdftool -f <NAME_OF_HDF> pack <GAME_DIRECTORY> size=<SIZE_OF_HDF>
```

Note the size of the HDF specified by SIZE_OF_HDF must be greater than size of the directory to store the additional filesystem informations (I use a 1.25 ratio).

Many files out there have a directory structure that looks like this:

```
Agony (1992)(Psygnosis).hdf
  Agony.info
  Agony (folder)
    Agony.info
    Disk.1
    Disk.2
    Disk.3
    Agony.slave
    Manual
    Manual.info
    ReadMe
    ReadMe.info
    scores.sav
```

This will not work in lr-puae. You can use ADF Opus to create an HDF file that looks like this:

```
Agony (1992)(Psygnosis).hdf
    Agony.info
    Disk.1
    Disk.2
    Disk.3
    game.slave
    Manual
    Manual.info
    ReadMe
    ReadMe.info
    scores.sav
```

The two big changes:
1. there isn't a folder at the top level. _If your .slave file isn't at the top level of the .hdf,_ you will get a DOS window popup stating "DOS Error #205 (object not found) on reading '.slave'".
2. Instead of <gamename>.slave, that file must be named `game.slave`. It doesn't matter (despite what you may see on the net) whether it's `.Slave` or `.slave`, based on my testing.

#### Game that needs a specific Amiga model (AGA games for instance)
If a game needs a specific Amiga model (AGA games for instance), you can specify which amiga model to use.

To do this just add these strings to your adf, hdf or m3u filename :

* "(A500)" or "(OCS)" to use an Amiga 500 model.

* "(A600)" or "(ECS)" to use an Amiga 600 model.

* "(A1200)" or "(AGA)" to use an Amiga 1200 model.

Example : When launching "Alien Breed 2 (AGA).hdf" file the core will use an Amiga 1200 model.

If no special string is found the core will use the model configured in core options.

#### .uae: Using a configuration file for your games
You can pass an '.uae' configuration file as a rom and the core will load the settings and start emulation without first showing the gui. 

Look at the sample configuration file "RickDangerous.uae" for help  (see below). You can use that sample as a starting point for making your own configuration files for each of your games.

You can find the whole documentation in [configuration.txt](https://github.com/libretro/libretro-uae/blob/master/configuration.txt).

lr-puae auto-generates a .uae file called `/roms/amiga/puae_libretro.uae` based on your Retroarch settings, but you can create them manually, pointing to the ADF and Kickstart ROM like this:
```shell
kickstart_rom_file=/home/pi/RetroPie/BIOS/[insert kickstart ROM filename here]
floppy0=/home/pi/RetroPie/roms/amiga/[insert ADF filename here]
```

Files may be `.hdf` or `.adf`. Note that `.m3u` files are not supported.

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

### Resolution and rendering

A said in P-UAE configuration.txt:

```
	To emulate a high-resolution, fully overscanned PAL screen - either
	non-interlaced with line-doubling, or interlaced - you need to use a
	display of at least 720 by 568 pixels. If you specify a smaller size,
	E-UAE's display will be clipped to fit (and you can use the gfx_center_*
	options - see below - to centre the clipped region of the display).
	Similarly, to fully display an over-scanned lo-res PAL screen, you need a
	display of 360 by 284 pixels.
```

Three parameters control the output resolution of the core :

|Name|Values|Default|
|---|---|---|
|Video standard|PAL, NTSC|PAL|
|High resolution|false, true|false|
|Crop overscan|false, true|false|

With this settings all the standards resolutions of the amiga are available :
* **360x284**: PAL Low resolution with overscan
* **320x256**: PAL Low resolution cropped/clipped (without the "borders")
* **360x240**: NTSC Low resolution with overscan
* **320×200**: NTSC Low resolution cropped/clipped (without the "borders")
* **720x568**: PAL High resolution with overscan
* **640×512**: PAL High resolution cropped/clipped (without the "borders")
* **720x480**: NTSC High resolution with overscan
* **640×400**: NTSC High resolution cropped/clipped (without the "borders")

When using a high resolution mode, rendering will be doubled horizontally and vertically for low res games. It's compatible with High res games and the Workbench but scaling shaders (ex: scalefx) will look ugly.

When using a low resolution, scaling shaders (scalefx) look great but high res games and and the workbench are badly rendered (but still usable).

### Known Bugs
- When load savestate, exiting GUI without reset. You have to re-enter GUI and do the reset.
- It's a debug release, so expect bugs.

## Emulators: [UAE4ALL2](https://github.com/RetroPie/uae4all2), [UAE4ARM](https://github.com/Chips-fr/uae4arm-rpi/)

UAE4ALL2 is no longer developed and we recommend using UAE4ARM on the Raspberry Pi.

### ROMS
Accepted File Extensions: **.adf**

UAE4Arm also supports: **.dms .exe .rp9** and compressed formats **.zip .adz**

 Place your Amiga disks images in

```shell
/home/pi/RetroPie/roms/amiga/
```

### BIOS
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


### Controls
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

### Video Tutorial

[![Testing joypad in RetroPie](http://img.youtube.com/vi/dleumwWZp6Q/0.jpg)](http://www.youtube.com/watch?v=dleumwWZp6Q)

### Launching games directly from EmulationStation

#### Script for creating configuration files 

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

#### Other solution

Alternatively, a native BASH script to perform the same steps directly on the RetroPie machine can be found here:
https://github.com/Douggernaut/RetroPieAssistant/tree/master/Amiga

## Tips and troubleshooting

- Stuttering? Amiga systems/games are PAL (50Hz), but modern TVs typically default to a 60Hz mode when connected to a Raspberry Pi. Enter the RunCommand menu for your Amiga emulator, and select a valid mode that uses a 50Hz refresh rate in order to match the original PAL rate, and thus, eliminate stuttering.

- Some games work better with the '512Kb Chip' + '512Kb Slow' memory configuration rather than the default A500 '1MB Chip'. If your game crashes or fails to load, change the memory settings in the 'CPU RAM' tab of the UAE4ALL2 GUI.

- Some games do not work properly if more than one floppy drive is in use. If your game crashes or fails to load try to use just DF0 (change disc image during game if required) and not use DF1, DF2 and DF3.

- For Raspberry Pi 1 users - make sure you overclock your device. Amiga emulation works much faster when overclocked to maximum. Without overclocking some games do not run at full speed.




