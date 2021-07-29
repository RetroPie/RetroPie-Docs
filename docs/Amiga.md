***
![amiga](https://cloud.githubusercontent.com/assets/10035308/12189019/a46a4d44-b577-11e5-8378-d8196412103c.png)
***

_The Amiga was a family of personal computers released by Commodore in the 1980's and 1990's._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Amiberry](https://github.com/midwan/amiberry) | amiga  | .lha .zip .uae .adf .dms .fdi .ipf .hdf .hdz | kick33180.A500, kick34005.A500, kick40068.A1200 | /opt/retropie/configs/amiga/retroarch.cfg |
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

Amiberry makes use the RetroArch configs created during [Controller Configuration](Controller-Configuration). Consequently, **Hotkey+X** will bring up the UI and **Hotkey+Start** can be used to exit Amiberry. For full documentation, please refer [here](https://github.com/midwan/amiberry/wiki/RetroArch-Commands).

Default controller choice can be edited in `/opt/retropie/configs/amiga/amiberry/whdboot/hostprefs.conf`. It is also possible to set the default controller choice as well as other Amiberry settings for individual games. For full documentation, please refer [here](https://github.com/midwan/amiberry/wiki/WHDLoad-Auto-booting#game-specific-settings-improving-game-compatibility).

It is possible to customise controls for individual games using the Amiberry UI. For full documentation, please refer [here](https://github.com/midwan/amiberry/wiki/Customised-Controls).

## Emulator: [lr-puae](https://github.com/libretro/libretro-uae)

lr-puae is an experimental emulator.  It can be installed from the experimental section of the [RetroPie-Setup Script.](Updating-RetroPie#using-the-retropie-setup-script)

### BIOS

Place your desired Kickstart ROMs in:
```shell
/home/pi/RetroPie/BIOS/
```
To use disk and WHDLoad games with this core you'll need the following Kickstart ROMs. Rename them to the given name and copy the file in the BIOS folder.

It is critical to use Kickstarts with the right MD5, otherwise the core might not start.

Filename  |Description  |Amiga Forever name |System  |MD5 checksum
:---------|:------------|:------------------|:-------|:------------
kick33180.A500 | Kickstart v1.2 rev 33.180 (!)     | amiga-os-120.rom       | Amiga 500  |85ad74194e87c08904327de1a9443b7a
kick34005.A500 | Kickstart v1.3 rev 34.005         | amiga-os-130.rom       | Amiga 500  | 82a21c1890cae844b3df741f2762d48d
kick37175.A500 | Kickstart v2.04 rev 37.175        | amiga-os-204.rom       | Amiga 500+ | dc10d7bdd1b6f450773dfb558477c230
kick40063.A600 | Kickstart v3.1 rev 40.063         | amiga-os-310-a600.rom  | Amiga 600  | e40a5dfb3d017ba8779faba30cbd1c8e
kick40068.A1200| Kickstart v3.1 rev 40.068         | amiga-os-310-a1200.rom | Amiga 1200 | 646773759326fbac3b2311fd8c8793ee
kick40068.A4000| Kickstart v3.1 rev 40.068         | amiga-os-310-a4000.rom | Amiga 4000 | 9bdedde6a4f33555b4a270c8ca53297d
kick34005.CDTV | CDTV extended ROM v1.00           | amiga-os-130-cdtv-ext.rom | Amiga CDTV | 89da1838a24460e4b93f4f0c5d92d48d
kick40060.CD32 | CD32 Kickstart v3.1 rev 40.060    | N/A | Amiga CD32       | 5f8924d013dd57a89cf349f4cdedc6b1
kick40060.CD32.ext| CD32 extended ROM rev 40.060   | amiga-os-310-cd32.rom  | Amiga CD32 | bb72565701b1b6faece07d68ea5da639
kick40060.CD32 | CD32 KS + extended v3.1 rev 40.060| amiga-os-310-cd32.rom  | Amiga CD32 | f2f241bf094168cfb9e7805dc2856433

Note:
- The core has a built-in AROS fallback Kickstart, which is used when the real Kickstart is not found. It can be compatible enough for some A500 games.
- Kickstart v1.2 (1) is only needed for WHDLoad Arcadia games
- For CD32 emulation, either **kick40060.CD32**(CD32 KS + extended v3.1 rev 40.060) or both **kick40060.CD32**(CD32 Kickstart v3.1 rev 40.060) and **kick40060.CD32.ext**(CD32 extended ROM rev 40.060)
### Controls

lr-puae uses Retroarch input configurations.

Add custom RetroArch controls to the `retroarch.cfg` file in
```shell
/opt/retropie/configs/amiga/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration).

#### Default Controls

| RetroPad Button| Action  |
| :------------- | :------- |
| D-Pad          | Joystick |
| Left Analog    | Mouse    |
| Righ Analog    | Mouse    |
| A  | Fire button 2 / Blue |
| B  | Fire button 1 / Red  |
| L2  | Left mouse button   |
| R2  | Right mouse button  |
| Select | Toggle virtual keyboard |

| Keyboard key.  | Action   |
| :------------- | :------- |
| F12            | Toggle statusbar |
| Right Control  | Switch between joystick/mouse  |

#### Virtual keyboard

The PUAE core has a virtual keyboard that can be accessed by default through RetroPad Select.    
The virtual keyboard can be controlled with:

* **RetroPad**

    | Button   | Action              |
    |----------|---------------------|
    | D-Pad    | Move                |
    | B        | Keypress            |
    | A        | Toggle transparency |
    | Y        | Toggle CapsLock     |
    | X        | Toggle position     |
    | Start    | Press Return        |

* **Keyboard**

    | Key      | Action              |
    |----------|---------------------|
    | Cursors  | Move                |
    | Enter    | Keypress            |
    | CapsLock | Toggle CapsLock     |

- **Mouse**
- **Touch screen**

The virtual keyboard has these additional actions:

- `J/M` = Switch between joystick/mouse
- `TRBF` = Toggle turbo fire
- `ASPR` = Toggle aspect ratio
- `STBR` = Toggle statusbar
- Reset (Red key with undo icon, soft reset = Ctrl-Amiga-Amiga)
- Mouse controls (Left+right button, up, down, left, right)
- Numpad key (Toggles numbers, arrows, Return etc. to numpad variants)

Long press for sticky keys. Stickying the third key will replace the second.

#### Joyport control

Some games use mouse instead of joystick. D-Pad can be switched between joystick and mouse control in several ways:

- Use the core option: `Quick Menu -> Options -> RetroPad Joystick/Mouse`
- Bring up the virtual keyboard with `Select` button, then press the key labeled `J/M`
- Press the default keyboard shortcut - `Right Control`
- Assign `Switch Joystick/Mouse` to any RetroPad button under `Quick Menu -> Options`

### Core configuration

The P-UAE core has a comprehesive set of configuration options which control the emulation experience. A comprehensive list can be found [here](https://docs.libretro.com/library/puae/#core-options).

### Model selection

You can force a specific model if a game needs one (AGA games for instance) either by the "Model" core option or by file path tags.

The "Model" core option at "**Automatic**" will default to A500 when booting floppy disks, A600 when booting hard drives, and CD32 when booting CD images.

The whole path (filename and directory) will be searched for the following tags if the model is "**Automatic**":

| Floppy | HD/LHA | CD    | String/Tag                                  | Result                                       |
|--------|--------|-------|---------------------------------------------|----------------------------------------------|
| **x**  | **x**  |       | **(A500OG)**, **(512K)**                    | Amiga 500 (0.5MB Chip RAM)                   |
| **x**  | **x**  |       | **(A500)**, **OCS**                         | Amiga 500 (0.5MB Chip RAM + 0.5MB Slow RAM)  |
| **x**  | **x**  |       | **(A500+)**, **(A500PLUS)**                 | Amiga 500+ (1MB Chip RAM)                    |
| **x**  | **x**  |       | **(A600)**, **ECS**                         | Amiga 600 (2MB Chip RAM + 8MB Fast RAM)      |
| **x**  | **x**  |       | **(A1200OG)**, **(A1200NF)**                | Amiga 1200 (2MB Chip RAM)                    |
| **x**  | **x**  |       | **(A1200)**, **AGA**, **CD32**, **AmigaCD** | Amiga 1200 (2MB Chip RAM + 8MB Fast RAM)     |
| **x**  | **x**  |       | **(A4030)**, **(030)**                      | Amiga 4000/030 (2MB Chip RAM + 8MB Fast RAM) |
| **x**  | **x**  |       | **(A4040)**, **(040)**                      | Amiga 4000/040 (2MB Chip RAM + 8MB Fast RAM) |
|        |        | **x** | **CDTV**                                    | Amiga CDTV (1MB Chip RAM)                    |
|        |        | **x** | **(CD32)**, **(CD32NF)**                    | Amiga CD32 (2MB Chip RAM)                    |
|        |        | **x** | **(CD32FR)**, **FastRAM**                   | Amiga CD32 (2MB Chip RAM + 8MB Fast RAM)     |
| **x**  | **x**  | **x** | **NTSC**, **(USA)**                         | NTSC 60Hz                                    |
| **x**  | **x**  | **x** | **PAL**, **(Europe)** (!)                   | PAL 50Hz                                     |
| **x**  |        |       | **(MD)** (!!)                               | Insert each disk in different drives         |
| **x**  | **x**  | **x** | **(CE)**                                    | Force CPU Cycle-exact                        |

- (!) Additional tags: **(Denmark)**, **(Finland)**, **(France)**, **(Germany)**, **(Italy)**, **(Spain)**, **(Sweden)**
- (!!) **Maximum 4 disks**

Example: When launching "Alien Breed 2 AGA.hdf" or "AGA/Alien Breed 2.hdf" the model will be Amiga 1200.


### ROMS

Place your Amiga ROMs and configuration files in 
```
/home/pi/RetroPie/roms/amiga
```

Content that can be loaded by `lr-puae` has the following file extensions:

**Floppy images**

- .adf
- .adz
- .dms
- .fdi
- .ipf

**Hard drives**

- .hdf
- .hdz
- directory

**WHDLoad**

- .lha
- .slave
- .info

**Compact discs**

- .cue
- .ccd
- .nrg
- .mds
- .iso

**Other**

- .uae
- .m3u
- .zip

One thing that Amiga enthusiasts seem to point out repeatedly is that although you may be able to expand an `.lha` file on Windows, you often shouldn't; the Amiga operating system and Windows don't always agree on paths and special characters, with the result that you can corrupt the file when unzipping it.

#### Disk images
You can pass a disk or hdd image (WHDLoad) as a rom.

Supported formats are :

- `.adf`, `.adz`, `.dms`, `.fdi`, `.ipf` for disk images.
- `.hdf`, `.hdz`, `.lha` for hdd images.
- `.cue`, `.iso`, `.ccd`, `.nrg`, `.mds` for compact disc images

When passing a disk image, a hdd image or a M3U file as parameter, the core will generate a temporary `puae_libretro.uae` configuration file in RetroArch `saves` directory (the `amiga` rom folder) and use it to automatically launch the game.

#### M3U Support
When you have a multi disk game, you can use an `.m3u` file to specify each disk of the game and change them from the RetroArch Disc Control interface.

An M3U file is a simple text file with one disk per line (see [Wiki](https://en.wikipedia.org/wiki/M3U)).

An example M3U file: 

_Simpsons, The - Bart vs. The Space Mutants.m3u_

containing

```
Simpsons, The - Bart vs. The Space Mutants_Disk1.adf
Simpsons, The - Bart vs. The Space Mutants_Disk2.adf
```

Path in the M3U file can be absolute or relative to the location of the M3U file.

When a game asks for it, you can change the current disk in the RetroArch **Disc Control** menu:

 * Eject the current disk with _Eject Disc_
 * Select the right disk index with _Current Disc Index_
 * Insert the new disk with _Insert Disc_

For games that support multiple disk drives, append "**(MD)**" (as in "MultiDrive") to the M3U filename to insert each disk in different drives, up to a maximum of 4 disks.

For games that require a dedicated save disk, one may be generated automatically by entering the following line in an M3U file: `#SAVEDISK:VolumeName`. `VolumeName` is optional and may be omitted. For example, this will create a blank, unlabelled disk image at disk index 5:

`Secret of Monkey Island.m3u`

```
Secret of Monkey Island_Disk 1.adf
Secret of Monkey Island_Disk 2.adf
Secret of Monkey Island_Disk 3.adf
Secret of Monkey Island_Disk 4.adf
#SAVEDISK:
```

By default, RetroArch will display the filename (without extension) of each M3U entry when selecting a disk via the Current Disc Index drop-down menu. Custom display labels may be set for each disk using the following syntax in the `.m3u` playlist file: `DISK_FILE|DISK_LABEL`. 

For example:

M3U Playlist | Retroarch Disc control drop-down
------------ | ---------------------------------
`Valhalla & the Fortress of Eve_Disk1.adf|Game Disk` | `1: Game Disk`
`Valhalla & the Fortress of Eve_Disk2.adf|Data Disk` | `2: Data Disk`
`Valhalla & the Fortress of Eve_Disk3.adf|Level 1 Disk` | `3:Level 1 Disk`
`Valhalla & the Fortress of Eve_Disk4.adf|Level 2 Disk` | `4:Level 2 Diskisk`
`Valhalla & the Fortress of Eve_Disk5.adf|Level 3 Disk` | `5:Level 3 Diskisk`
`Valhalla & the Fortress of Eve_Disk6.adf|Level 4 Disk` | `6:Level 4 Diskisk`

#### WHDLoad Disc Images
Pre-installed WHDLoad LHA archives can be launched directly, there is no need for any kind of manual preparing and downloading.

* WHDLoad helper files (Directory or HDF) will be generated to the save folder (ROM folder), `WHDLoad.prefs` will be generated to the `BIOS` folder.
* `WHDLoad.prefs` & `WHDLoad.key` will be copied from the `BIOS` (system) folder to the helper image
* Kickstarts will be copied automatically to the helper image
* To update `WHDLoad:` simply delete the directory or the HDF file

#### Zip Archives Support

ZIP archives will be extracted to a temporary directory in saves, bypassing the default frontend extraction.The temporary directory will be removed on exit.

This allows:

* Automatic M3U playlist generation of all floppy disks
* The use of zipped images in M3Us
* Hard drive and CD images will be treated one by one and only the first file found is selected for launch
* If no disk/drive images are found, the ZIP will be treated as a directory

#### IPF Support

IPF support is done through the CAPSIMG library. To enable it, you have to put the dynamic library called `capsimg.so` (Linux) in RetroArch system directory (`/home/pi/RetroPie/BIOS`).

Compatible CAPSIMG libraries for Windows, macOS and Linux can be found at http://www.softpres.org/download and https://fs-uae.net/download#plugins.

If you cannot find CAPSIMG library for your CPU architecture, you can always build `capsimg.so` from the source which is available at https://github.com/FrodeSolheim/capsimg.

```bash
git clone https://github.com/FrodeSolheim/capsimg
cd capsimg
./bootstrap
./configure
make
cp capsimg.so ~/RetroPie/BIOS
```

### Floppy drive sounds

The core has embedded internal floppy drive samples. External sound samples have to be copied from https://github.com/libretro/libretro-uae/tree/master/sources/uae_data into a directory named `uae_data` or `uae` in RetroArch system directory (`/home/pi/RetroPie/BIOS`).

### Resolution and rendering
The following core options control the output resolution of the core (defaults are **bolded**):

| Name                 | Values                                  |
|----------------------|-----------------------------------------|
| Video Standard       | **PAL 50Hz**, NTSC 60Hz                 |
| Video Resolution     | **Automatic**, Low, High, Super-High    |
| Video Line Mode      | **Automatic**, Single Line, Double Line |
| Aspect Ratio         | **Automatic**, PAL, NTSC                |

With these settings all the standard resolutions are available:

| PAL 50Hz Resolution  | Description            |
|----------------------|------------------------|
| 360x288              | Lores                  |
| 720x288              | Hires Single Line      |
| 720x576              | Hires Double Line      |
| 1440x288             | SuperHires Single Line |
| 1440x576             | SuperHires Double Line |

| NTSC 60Hz Resolution | Description            |
|----------------------|------------------------|
| 360x240              | Lores                  |
| 720x240              | Hires Single Line      |
| 720x480              | Hires Double Line      |
| 1440x240             | SuperHires Single Line |
| 1440x480             | SuperHires Double Line |

When using low resolution mode, rendering will be halved horizontally and forced into "**Single Line**" mode. 
Scaling shaders looks great, but high resolution games and Workbench are badly rendered.

When using high resolution "**Double Line**" mode, rendering will be doubled vertically. 
It is compatible with high resolution games and Workbench, but scaling shaders will look ugly. 
"**Double Line**" shows interlaced fields separately (weave) and is suited for de-interlacing shaders.

When using high resolution "**Single Line**" mode, rendering is presented as is. 
It delivers the best of both worlds, and looks great with high resolution games, Workbench and shaders. 
"**Single Line**" combines interlaced fields into one field (bob), which will make high resolution images blocky and jittery.

- Automatic "Resolution" defaults to "**Hires**" and selects "**SuperHires**" when needed (practically only in Workbench and Super Skidmarks)
- Automatic "Line Mode" defaults to "**Single Line**" and selects "**Double Line**" on interlaced screens


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




