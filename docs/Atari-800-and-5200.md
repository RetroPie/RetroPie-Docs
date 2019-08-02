***
![atari-5200](https://cloud.githubusercontent.com/assets/10035308/12190121/2678efca-b582-11e5-954a-de6945b5f54e.png)
***
_Atari released a series of 8 bit computers (400, 800, 1200XL, 600XL, 800XL, 130XE, 65XE, 800XE, and XEGS) and a video game console known as the Atari 5200 from 1979 to 1992_
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Atari800](https://atari800.github.io/)  | atari800 **or** atari5200  | .a52 .atr .bas .bin .car .dcm .xex .xfd .atr.gz .xfd.gz | ATARIXL.ROM **and** ATARIBAS.ROM **and** ATARIOSA.ROM **and** ATARIOSB.ROM **and** 5200.rom | /opt/retropie/configs/atari800/atari800.cfg or /opt/retropie/configs/atari800.cfg on older releases|
| [lr-atari800](https://github.com/libretro/libretro-atari800)  | atari800 **or** atari5200  | .7z .a52 .atr .bas .bin .car .dcm .xex .xfd .zip .atr.gz .xfd.gz | ATARIXL.ROM **and** ATARIBAS.ROM **and** ATARIOSA.ROM **and** ATARIOSB.ROM **and** 5200.rom | /opt/retropie/configs/atari5200/retroarch.cfg |

These emulators emulate the Atari 8 bit family: 400, 800, 1200XL, 600XL, 800XL, 130XE, XEGS and the Atari 5200. This can be one of the more tricky emulators to get set up as they require a multiplicity of BIOS files and configurations depending on what systems you want to utilise but it seems to run Atari 5200 games pretty well.

Atari800 is currently a port of version 4.1.0, whereas lr-Atari800 is based on version 3.1.0. Because of this, setup is substantially similar, with some differences. The lr-Atari800 core is currently the default in Retropie.

## ROMS
Accepted File Extensions: **.a52 .bas .bin .car .xex .atr .xfd .dcm .atr.gz .xfd.gz**

Place your Atari 400,800, ROMS in
```shell
/home/pi/RetroPie/roms/atari800
```

Place your Atari 5200 ROMS in
```shell
/home/pi/RetroPie/roms/atari5200
```

## BIOS
There are 5 main BIOS needed for the Atari800 emulator:

| BIOS name | Description | MD5 | CRC32 | Notes |
| :---: | :---: | :---: | :---: |  :---: |
|**ATARIXL.ROM** | BIOS for Atari XL/XE OS | 06daac977823773a3eea3422fd26a703 | 0x1f9cd270 | Version BB01R2 OS from Atari 800XL and early Atari 65XE/130XE |
|**ATARIBAS.ROM** | BIOS for the BASIC interpreter | 0bac0c6a50104045d902df4503a4c30b | 0x7d684184 | Basic Rev. C, Atari BASIC from 800XL and all Atari XE/XEGS, also sold on cartridge |
|**ATARIOSA.ROM** | BIOS for Atari 400/800 PAL | eb1f32f5d9f382db1bbfb8d7f9cb343a| 0x72b3fed4 | OS A from PAL Atari 400/800 |
|**ATARIOSB.ROM** | BIOS for Atari 400/800 NTSC | a3e8d617c95d08031fe1b20d541434b2 | 0x3e28a1fe | PCXFormer hack ROM, based on LINBUG version; a bugfixed NTSC OS B for 400/800 |
|**5200.rom** | BIOS for the Atari 5200 | 281f20ea4320404ec820fb7ec0693b38 |0x4248d3e3 | Original (not Rev. A) BIOS from 4-port and early 2-port 5200 |

See Advanced Config below for other alternate BIOSes which may be required to run certain software.

Place these files in
```shell
/home/pi/RetroPie/BIOS
```
Once you have your ROMS and your BIOS files where they belong there is one more step of configuration needed where you tell the emulator where to look for your BIOS files. It varies based on the emulator, so look below to those sections for instructions.

## Atari 5200 setup
In both emulators, the atari.cfg file is shared between Atari computers and the 5200. In lr-atari800, the core options likewise apply to both by default. However, for either emulator, if you have a core options file in your atari5200 directory, it will let you have separate settings for just the 5200 system.

Make sure you have a file called /opt/retropie/configs/atari5200/retroarch-core-options.cfg with this in it:

```shell
atari800_artifacting = "enabled"
atari800_cassboot = "disabled"
atari800_internalbasic = "disabled"
atari800_keyboard = "poll"
atari800_ntscpal = "NTSC"
atari800_opt1 = "disabled"
atari800_opt2 = "disabled"
atari800_resolution = "336x240"
atari800_sioaccel = "enabled"
atari800_system = "5200"
```
See "Advanced Config" for solutions to problems booting 5200 games.

Please be sure to read through the docs below specific to each emulator version. 

If you are using lr-atari800 you will want to set the controller type to “Atari Joystick” and not “RetroPad” in order to get all the keys mapped to your controller.

## Emulator: [lr-atari800](https://github.com/libretro/libretro-atari800)

### BIOS setup
Make sure you have the appropriate system files in RetroArch's system directory:

```shell
~/RetroPie/BIOS
```

Then, load a content file. The Atari800 core should boot to the 'Atari Computer - Memo Pad' screen.

The Atari800 core will generate a '.atari800.cfg' config file in RetroArch's home directory and will add the required BIOS files it detects in the system directory to the config file.

Now you can manually select what Atari system you want to emulate through the 'Atari System' core option.

Finally, you can load any content files compatible with the system chosen through RetroArch's Load Content menu.

Alternatively, you can manually configure how the Atari800 will look for and handle BIOS files. While the Atari800 core is running, you can press F1 to get into the internal emulator menu. From there, You can go to the 'Emulator Configuration' section and then the System ROM Settings section to configure BIOS options. (Press Enter to confirm menu selections and press Escape to go back a menu).

Then press Escape a few times to go back to the 'Emulator Configuration' section and select Save Configuration File or alternatively change Save configuration file on exit from no to yes.

Then you can exit the emulator by pressing F9 and then try the game again or press Shift+F5 to reboot the game.

You can set per-game core option settings by creating a game-options file through RetroArch's Core Options menu.

### Options

The Atari800 core has the following options that can be tweaked from the core options menu. The default setting is bolded. Settings with (Restart) means that core has to be closed for the new setting to be applied on next launch.

| Option | Choices | Description |
| :---: | :---: | :---: |
| Atari System | **(400/800 (OS B)**/800XL (64K)/130XE (128K)/5200) | Choose what Atari System to emulate. |
| Video Standard | (**NTSC**/PAL) |  |
| Internal BASIC (hold OPTION on boot)  | (**Off**/On) | Whether to launch with BASIC enabled. Most games want this off. |
| SIO Acceleration | (**Off**/On) | Speeds up emulation during file loading. You probably want this on but a few games will fail to load with it on. |
| Boot from Cassette | (**Off**/On) | Causes a .CAS file to serve as the boot drive instead of the normal precedence (Cartridge first if present, then Disk) |
| Hi-Res Artifacting | (**Off**/On) | Enables artificial color filters in high-res mode to mimic actual hardware. See Advanced Config for more | 
| Autodetect A5200 CartType |  (**Off**/On) | There are many kinds of 5200 carts. This attempts to determine what sort a file is automatically. It often fails. See Advanced Config for more. |
| Joy hack A5200 for Robotron | (**Off**/On) | Treats the second analog stick on a modern controller as joystick 2 |
| Internal resolution | (**336x240**/320x240/384x240/384x272/384x288/400x300) | Enables alternate resolutions. Note that most software actually runs in 320x192 and the rest is overscan. |
| Retroarch Keyboard type | (**poll**/callback) | Default is poll for performance. |

### Controllers
**Device types**

The Atari800 core supports the following device type(s) in the controls menu, bolded device types are the default for the specified user(s):

**User 1 - 2 device types**

    None - Input disabled.
    RetroPad - Joypad - Don't use this, switch to ATARI Joystick for joypad usage.
    ATARI Joystick - Joypad
    ATARI Keyboard - Keyboard - For keyboard usage

**Controller tables**

_Joypad and analog device type table_

If your controller is set to “Atari Joystick” you will have the following mappings:

| User 1 Remap descriptors | RetroPad Inputs | ATARI Joystick |
| :---: | :---: | :---: |
| B | |KEY RETURN | 
| Y| | Virtual keyboard ON/OFF | 
| Select | | Select key |
| Start| | Start key |
| Up | | Up |
| Down | | Down |
| Left | | Left |
| Right | | Right |
| A |  | Joystick button and Return key in emulator menu | 
| X |  | Atari 5200 second button and ESC key in emulator menu |
| L | | Option key |
| R | | Open emulator menu |
| L2 | | Space key |
| R2 | | ESC key |

_Keyboard device type table_

See the section below for Atari800 keyboard controls, they are the same.

### Known issues with lr-atari800

* NTSC filters do not work.
* "New artifacts" do not render properly.
* Sliders for adjusting anything in the menus do not work correctly. Adjust these values by editing the config file.
* The SHIFT and CTRL keys do not work when typing, including when used from the virtual keyboard.
* Analog stick implementation for several Atari 5200 games is broken (Gorf, Missile Command, etc)

Note that any option settable in the RGUI will override the atari.cfg config file. Numerous options are only settable via the emulator menu.

## Emulator: [Atari800](https://atari800.github.io/)

### BIOS setup

Navigate to either the Atari 800 or Atari 5200 system on emulationstation and choose a game. Either a screen will open up with a bunch of different cartridge options, or the game will crash. If you are playing a 5200 game then choose a 5200 cartridge option (Option #5 seems to work). You will then get a warning telling you that it needs a real Atari OS. (You need to legally own the 5200 hardware to have the BIOS). Then press F1 to open the menu and navigate down to "Emulator Configuration" and press enter. Then navigate down to System ROM Settings and then press Enter (Quick hint: use the escape button to go back up a step in the GUI).

The easiest option is to just select "Find ROM images in a directory" then navigate into the BIOS directory and press the space bar. If you have the right files and file names it should automatically place the BIOS files where they belong. 

Alternatively you can configure them manually:

**For 400/800:**
```     
 Custom OS ROM: select ATARIOSB.ROM in /home/pi/RetroPie/BIOS/ATARIOSB.ROM
      
 ROM_OS_A_PAL=  select ATARIOSA.ROM in /home/pi/RetroPie/BIOS/ATARIOSA.ROM
```
**For XL/XE:**
```     
 BBO1 REV. 2: select ATARIXL.ROM in /home/pi/RetroPie/BIOS/ATARIXL.ROM
```
**For 5200:**
```     
 Original: Select atari5200.rom in /home/pi/RetroPie/BIOS/5200.rom
```
**For BASIC:**
```      
Rev. C:  Select ATARIBAS.ROM in /home/pi/RetroPie/BIOS/ATARIBAS.ROM 
```
Then press escape a few times to go back to the "Emulator Settings" and select Save Configuration File or alternatively change Save configuration file on exit from no to yes.

Then you can exit the emulator by pressing F9 and then try the game again or press shift+F5 to reboot the game.

If you can't seem to make it work that way, once you have tried to start a game and use F9 to exit the emulator a file called .atari800.cfg will be created in the /home/pi directory.

This is a verified working .atari800.cfg file     
```shell
Atari 800 Emulator, Version 3.1.0
ROM_OS_A_NTSC=
ROM_OS_A_PAL=/home/pi/RetroPie/BIOS/ATARIOSA.ROM
ROM_OS_B_NTSC=
ROM_OS_AA00R10=
ROM_OS_AA00R11=
ROM_OS_BB00R1=
ROM_OS_BB01R2=/home/pi/RetroPie/BIOS/ATARIXL.ROM
ROM_OS_BB02R3=
ROM_OS_BB02R3V4=
ROM_OS_CC01R4=
ROM_OS_BB01R3=
ROM_OS_BB01R4=
ROM_OS_BB01R59=
ROM_OS_BB01R59A=
ROM_5200=/home/pi/RetroPie/BIOS/5200.rom
ROM_5200_A=
ROM_BASIC_A=
ROM_BASIC_B=
ROM_BASIC_C=/home/pi/RetroPie/BIOS/ATARIBAS.ROM
ROM_XEGAME=
ROM_400/800_CUSTOM=/home/pi/RetroPie/BIOS/ATARIOSB.ROM
ROM_XL/XE_CUSTOM=
ROM_5200_CUSTOM=
ROM_BASIC_CUSTOM=
ROM_XEGAME_CUSTOM=
OS_400/800_VERSION=AUTO
OS_XL/XE_VERSION=AUTO
OS_5200_VERSION=AUTO
BASIC_VERSION=AUTO
XEGS_GAME_VERSION=AUTO
H1_DIR=
H2_DIR=
H3_DIR=
H4_DIR=
HD_READ_ONLY=1
PRINT_COMMAND=lpr %s
SCREEN_REFRESH_RATIO=1
MACHINE_TYPE=Atari XL/XE
RAM_SIZE=64
DEFAULT_TV_MODE=PAL
MOSAIC_RAM_NUM_BANKS=0
AXLON_RAM_NUM_BANKS=0
ENABLE_MAPRAM=0
DISABLE_BASIC=1
ENABLE_SIO_PATCH=1
ENABLE_H_PATCH=1
ENABLE_P_PATCH=1
ENABLE_NEW_POKEY=1
STEREO_POKEY=0
SPEAKER_SOUND=1
BUILTIN_BASIC=0
KEYBOARD_LEDS=0
F_KEYS=0
BUILTIN_GAME=0
KEYBOARD_DETACHED=0
1200XL_JUMPER=0
CFG_SAVE_ON_EXIT=1
MIO_ROM=
BLACK_BOX_ROM=
XLD_D_ROM=
XLD_V_ROM=
CARTRIDGE_FILENAME=
CARTRIDGE_TYPE=0
CARTRIDGE_PIGGYBACK_FILENAME=
CARTRIDGE_PIGGYBACK_TYPE=0
CARTRIDGE_AUTOREBOOT=1
CASSETTE_FILENAME=
CASSETTE_LOADED=0
CASSETTE_WRITE_PROTECT=0
RTIME=1
COLOURS_NTSC_SATURATION=0
COLOURS_NTSC_CONTRAST=0
COLOURS_NTSC_BRIGHTNESS=0
COLOURS_NTSC_GAMMA=0.3
COLOURS_NTSC_HUE=0
COLOURS_NTSC_GTIA_DELAY=26.8
COLOURS_NTSC_EXTERNAL_PALETTE=
COLOURS_NTSC_EXTERNAL_PALETTE_LOADED=0
COLOURS_NTSC_ADJUST_EXTERNAL_PALETTE=0
COLOURS_PAL_SATURATION=0
COLOURS_PAL_CONTRAST=0
COLOURS_PAL_BRIGHTNESS=0
COLOURS_PAL_GAMMA=0.3
COLOURS_PAL_HUE=0
COLOURS_PAL_GTIA_DELAY=23.2
COLOURS_PAL_EXTERNAL_PALETTE=
COLOURS_PAL_EXTERNAL_PALETTE_LOADED=0
COLOURS_PAL_ADJUST_EXTERNAL_PALETTE=0
ARTIFACT_NTSC=NONE
ARTIFACT_PAL=NONE
ARTIFACT_NTSC_MODE=0
SCREEN_SHOW_SPEED=0
SCREEN_SHOW_IO_ACTIVITY=1
SCREEN_SHOW_IO_COUNTER=0
SCREEN_SHOW_1200XL_LEDS=1
SOUND_ENABLED=1
SOUND_RATE=44100
SOUND_BITS=16
SOUND_FRAG_FRAMES=0
SOUND_LATENCY=20
VIDEO_FILTERING=1
VIDEO_ZOOM=1.00
SDL_JOY_0_ENABLED=1
SDL_JOY_0_LEFT=260
SDL_JOY_0_RIGHT=262
SDL_JOY_0_UP=264
SDL_JOY_0_DOWN=261
SDL_JOY_0_TRIGGER=305
SDL_JOY_1_ENABLED=0
SDL_JOY_1_LEFT=97
SDL_JOY_1_RIGHT=100
SDL_JOY_1_UP=119
SDL_JOY_1_DOWN=115
SDL_JOY_1_TRIGGER=306
```
### Controls
```shell
F1 Built in user interface
F2 Option key
F3 Select key
F4 Start key
F5 Reset key ("warm reset")
Shift+F5 Reboot ("cold reset")
F6 Help key (XL/XE only)
F7 Break key
F8 Enter monitor
F9 Exit emulator
F10 Save screenshot
Shift+F10 Save interlaced screenshot
Alt+R Run Atari program
Alt+D Disk management
Alt+C Cartridge management
Alt+Y Select system
Alt+O Sound settings
Alt+W Sound recording start/stop
Alt+S Save state file
Alt+L Load state file
Alt+A About the emulator
```
### Quick Tips for Gameplay:
```shell
Start Game: F4
Up: up or numpad 8
Down: down or numpad 2
Right: right or numpad 6
Left: left or numpad 4
Fire: RCTRL
Exit Emulator: F9
```
## Troubleshooting

* If it freezes up on you on the cartridge screen then try rebooting your pi and try again. If it keeps failing you either have the wrong BIOS, your ROM isn't compatible, or you chose the wrong cartridge option.

### Typical file formats

* **.atr**: an Atari disk image. Typically needs BASIC disabled. You load these from the gamelist, basically you boot the Atari with this in the drive.
* **.dcm** and **.xfd** are two other disk formats that lr-atari800 can read.
* **.cas** is an Atari cassette image. It's not listed on the Retropie page, but I'd be surprised if the emu couldn't load it. You can actually boot from a cassette.
* **.rom** and **.bin** are typically cartridges. Note that you can have a disk in the drive AND a cart in the cartridge slot at the same time. Carts always take precedence over disks. Also note that these formats are not the same as a .car file because they usually don't need header information.
* **.a52** and **.car** are typically Atari 5200 cartridges, but you can find .car Atari 8 bit carts as well. These usually have header information, because there are over a dozen cart formats with added banks of memory, etc. See "5200" above for how to convert a cart to a bin and back in order to put the right header info on the cart.
* **.bin** and **.xex** are executables. You may also see .com. These are just binary executables, but not entire disk images. You can load these from the gamelist, or from the Disk Operating System, which on an Atari was a menu. Boot a disk with DOS on it (and there were like a dozen different DOSes you could use, often with incompatible disk formats) and you can use the menu to launch the executable. Game compilation disk images often have collections of these.
* **.bas** is a BASIC file. You cannot run these directly from the gamelist. You have to load them from disk while in BASIC (use LOAD "D:FILENAME.EXT" and once it loads, type RUN.) Many games consist of a disk image with DOS (a directory listing of the disk contents will show DOS.SYS and DUP.SYS), a BASIC program, and a little executable named AUTORUN.SYS. This basically makes the disk bootable and runs the .BAS program directly. These end up being .atr images that require BASIC.

[See here for an exhaustive list of Atari formats.](http://www.atarimania.com/faq-atari-400-800-xl-xe-what-file-formats-for-entire-disks-tapes-cartridges-are-there_106.html)

Note that the emulators let you fully manipulate disks! You can accidentally reformat your rom, and it will look the same from the outside. Many games require you to have a blank disk to save player state on. Don't mess up and save your player file over the game! Similarly, quite a lot of "player disks" and "scenario disks" and the like out there actually have people's saved games on them.

## Advanced Config

### BASIC and games
The Atari 400 and 800 systems ran a Memo Pad when you turned the machine on without loading a program or having a cartridge inserted. The BASIC cart was packed into the box. All the XL and XE models came with BASIC built into the machine. This meant that when booting the system, you had to tell the machine "the BASIC cart isn't actually plugged in" whenever you wanted to load anything else. This was accomplished by holding down the Option key while booting. If you didn't load anything, you ended up instead in a self-test mode. Lastly, carts always disabled BASIC automatically.

    400/800 with BASIC: Blue screen with READY. This is BASIC.
    400/800 with cart: the cart.
    400/800 without BASIC: Memo Pad.
    400/800 with .atr or .bin or .xex etc: the program
    XL/XE with BASIC: Blue screen with READY.
    XL/XE without BASIC: Self-test.
    XL/XE with cart: the cart.
    XL/XE with .atr or .bin or .xex: likely a crash
    XL/XE with .atr or .bin or .xex and BASIC disabled: the program
    5200 without cart: nothing but Atari logo.
    5200 with cart: the game.

Most games you will find for the Atari are machine language, and require that BASIC be disabled. See [this thread](https://retropie.org.uk/forum/topic/22392/lr-atari800-5200-artifacting-basic-and-other-guidance)

### Booting Atari 5200 cartridges

Often when you boot an Atari 5200 game, it gets stuck at the Atari logo, or just crashes, or it asks you to specify a cart type. There's a bunch of kinds, and they all have to do with how much memory was embedded in the cart, and how many chips that memory was using, and what order the banks were in, etc. There is supposed to be a header on the cart that tells the machine how to interpret it, but lots of cart dumps don't have the header.

The emulator, though, has the facility to create carts, and this can add the missing header back in. Then you'll never see this menu again. Do this by going to the emulator menu (F1), Cartridge Management, Extract ROM from cartridge, save it, then Create Cartridge from ROM image, and select the file you just created. You will be asked which cart type to use. A handy list gathered by forum members is here: [https://retropie.org.uk/forum/topic/16556/cartridge-type-code-list-for-atari-5200-games](https://retropie.org.uk/forum/topic/16556/cartridge-type-code-list-for-atari-5200-games). Be sure to test after making your choice; if it doesn't work, just try another one. Go through the entire 5200 library (it's not that big!) and you'll never get the choose cart menu again. Be sure to have a backup of all your 5200 roms, of course.

### Missile Command and Gorf on the 5200
Don't expect Missile Command, Gorf, and other games that use analog absolute position to work correctly with your controller. Both emulators mimic this analog controls using a mouse, and this may not work well in either core.

### Artifacting
High resolution graphics mode on Atari 8-bits was a one-color, two luminance mode. You could have one color for the background, and the same color at a different brightness for the pixels drawn. However, similar to the Apple II, the Atari supported what is called _artifacting_. This is a literal "artifact," a graphical glitch, caused by the way the chroma circuits in the original hardware worked.

If artifacting is turned off, many games which ought to be in color will appear in black and white. Among them are games like Lode Runner, Drol, A.E., most pinball games, and many others.

On the other hand, because of the way artifacting is implemented in the emulators, turning it on for all games will make text harder to read and many graphics not look crisp in games that no hi-res mode.

See [this thread](https://retropie.org.uk/forum/topic/22392/lr-atari800-5200-artifacting-basic-and-other-guidance/4) for an exhaustive discussion of artifacting with many screenshot examples.

**Atari 800**

To get the best artifacting results, press F1 for the emulator menu. Go to Display Settings. Select "Full NTSC filter" for the artifacting. Under NTSC filter settings, set Burst Mode at one of -1, -0.5, 0.5, or 1 (or adjust to taste).

**lr-atari800**

NTSC filters do not work in this emulator. Retroarch will default to "Old artifacts." No other choices will render correctly, but you can use the F1 menu to switch between four different versions of artifacts which will give different colors. As a rule of thumb, you'll find that most games are either mode 1 or GTIA. 

### Automatic handling of BASIC games and artifacting
If you are using lr-atari800, there is a runcommand-onstart script that will

* Automatically launch PAL games in PAL.
* Automatically enable BASIC for games that require it.
* Let you choose from the four NTSC artifacting modes at the runcommand menu by setting an emulator for a specific rom.

See the script [in this thread.](https://retropie.org.uk/forum/topic/22392/lr-atari800-5200-artifacting-basic-and-other-guidance/9)

### Other BIOSes and BASIC versions

While the five BIOS files listed above will deal with 99% of the software you likely want to run, both versions of the emulator support many alternate versions, some of which permit loading software that would otherwise crash or run in graphically distorted form.

The following table gives the other BIOS checksums accepted by the emulators. These can be manually set in

```shell
/opt/retropie/configs/atari800/atari.cfg
```

which is also symlinked from

```shell
~/.atari.cfg
```
by adding the full path to the relevant line. Alternatively, you can use the emulator's internal menu. In lr-atari800, this can be reached via F1 or the R button; in Atari800 you can reach it via F1. Navigate to _Emulator Configuration > System ROM Settings_. Place all the BIOS files in

```shell
~/RetroPie/BIOS
```

and select _Find ROM Images in a Directory_. The emulator will find all BIOS files that match these, regardless of their filename. (Info drawn from [Peter Dell's Atari ROM Checker website](http://www.wudsn.com/productions/atari800/atariromchecker/help/AtariROMChecker.html)).

| BIOS version | MD5 | CRC | Notes |
| :---: | :---: | :---: | :---: |
| ROM_OS_A_NTSC | a3c1585b5d19719f8acfa2b093bea75f | 0x4248d3e3 | OS from early NTSC Atari 400/800 |
| ROM_OS_A_PAL | eb1f32f5d9f382db1bbfb8d7f9cb343a | 0x72b3fed4 | OS from PAL Atari 400/800 |
| ROM_OS_B_NTSC | 4177f386a3bac989a981d3fe3388cb6c | 0x0e86d61d | late NTSC Atari 400/800, LINBUG version with incorrect checksums |
| **or** | f5b246fa5237b44c41c6c831ccf18a2d | 0xf28bc97d | Corrected LINBUG version with correct checksums |
| ROM_OS_AA00R10 | e3e8c74bfe1dcd6b56af50bd9a82dc15 | 0xc5c11546 | NTSC & PAL OS from Atari 1200XL |
| ROM_OS_AA00R11 | eacb8069c45e2ec4e0a19978bf2fc334 | 0x1a1d7b1b | NTSC & PAL OS from Atari 1200XL |
| ROM_OS_BB00R1 | 9aea45e724d2588fbbeda658c7dc53ee | 0x643bcc98 | NTSC & PAL 600XL |
| ROM_OS_BB01R2 | 06daac977823773a3eea3422fd26a703 | 0x1f9cd270 | NTSC & PAL 800XL/65XE/130XE |
| ROM_OS_BB02R3 | 2dbc73da0d34994d1e2e62e22eb49224 | 0x4149fd2c | OS from Atari 1450XLD prototype, known as OSR3V2-416.BIN |
| ROM_OS_BB02R3V4 | 9f5449c881475a5cca40849c743205f8 | 0xd425a9cf | OS from Atari 1450XLD prototype, known as OS1450.128 and 1450R3VX.ROM |
| ROM_OS_CC01R4 | 65020266380e33cce50ebf8b9d91122a | 0x0e000b99 | Potential Production ROM, compiled from sources by Tomasz Krasuski on 2014-05-31 |
| ROM_OS_BB01R3 | 54e704558a6aedfc45cebf8f8ac9c312 | 0x29f133f7 | NTSC & PAL OS from late Atari 65XE/130XE | 
| ROM_OS_BB01R4 | b7a2a04677d34f069eeb643d5238bf86 | 0x1eaf4002 | NTSC/PAL XEGS |
| ROM_OS_BB01R59 | d467f55fb7643553b69b34bf7e805b7d | 0x45f47988 | Arabic Atari XEGS |
| ROM_OS_BB01R59A | 69396860e53f58d798421d06d766c3ba | 0xf0a236d3 | Arabic Atari 65XE |
| ROM_XEGAME | d7eb37aec6960cba36bc500e0e5d00bc | 0xbdca01fb | Missile Command, built-in version from Atari XEGS |

In addition, custom BIOSes can also be loaded; in fact, the default recommendation for an OS B BIOS is actually a hacked version from the PCXFormer emulator.

| BIOS version | MD5 | CRC | Notes |
| :---: | :---: | :---: | :---: |
| ROM_400/800_CUSTOM | a3e8d617c95d08031fe1b20d541434b2 | 0x3e28a1fe | NTSC PCXFormer hack ROM, based on LINBUG version |
| | 7e5e4ce9508edef684ebe2c5a0e6f0d3 | 0x0ffce3cb | NTSC Corrected PCXFormer hack ROM with correct checksums | 

There are three different versions of BASIC. Some BASIC software requires OS A and Rev. A BASIC; this is usually noted in the filename as [OSa]. The vast majority of the time, you will want Rev. C.

| BIOS version | MD5 | CRC | Notes |
| :---: | :---: | :---: | :---: |
| ROM_BASIC_A | a4dc52536d526ecc51ea857b9fa2b90f | 0x4bec4de2 | Atari BASIC sold on cartridge for the 400/800 | 
| ROM_BASIC_B | 04ea6a4e386601445ca5bfc8e37fb620 | 0xf0202fb3 | Atari BASIC from Atari 600XL/early Atari 800XL, also sold on cartridge | 
| ROM_BASIC_C | 0bac0c6a50104045d902df4503a4c30b | 0x7d684184 | Atari BASIC from 800XL and all Atari XE/XEGS, also sold on cartridge |

There are two possible BIOSes for the Atari 5200.

| BIOS version | MD5 | CRC | Notes |
| :---: | :---: | :---: | :---: |
| ROM_5200 | 281f20ea4320404ec820fb7ec0693b38 | 0x4248d3e3 | BIOS from 4-port and early 2-port 5200 |
| ROM_5200_A | ee7b85f5ca384dcb1f284946f3c12ac4 | 0xc2ba2613 | BIOS from late 2-port 5200 |

In Atari800, you can select which of these to boot into using command line switches.

```shell
-osa_rom <filename>   Use specified OS/A ROM image
-osb_rom <filename>   Use specified OS/B ROM image
-xlxe_rom <filename>  Use specified XL/XE OS ROM image
-5200_rom <filename>  Use specified 5200 OS ROM image
-basic_rom <filename> Use specified Atari BASIC ROM image

-800-rev auto|a-ntsc|a-pal|b-ntsc|custom              Select OS revision for Atari 400/800
-xl-rev auto|10|11|1|2|3a|3b|5|3|4|59|59a|custom      Select OS revision for Atari XL/XE
-5200-rev auto|orig|a|custom                          Select OS revision for Atari 5200
-basic-rev auto|a|b|c|custom                          Select BASIC revision
-xegame-rev auto|orig|custom                          Select XEGS builtin game version
``` 

In lr-atari800, Retroarch has hardcoded these choices into the Options menu. These are saved in 

```shell
/opt/retropie/configs/all/retroarch-core-options.cfg
```
where the options are

```shell
400/800 (OS B)
800XL (64K)
130XE (128K)
5200
```

and the option line is 

```shell
atari800_system = "800XL (64K)"
```

Note that since core options override the emulator's own config file, but Retroarch doesn't cover all the sub-options, you can set different versions of BASIC or different BIOSes for the supported systems via the emulator menu.