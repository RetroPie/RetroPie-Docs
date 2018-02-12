***
![intellivision](https://cloud.githubusercontent.com/assets/10035308/12192412/82366f36-b59b-11e5-973e-208fea792945.png)
***

_The Intellivision is a home video game console released by Mattel in 1979_

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [jzintv](#jzintv) | intellivision  | .int .bin | exec.bin grom.bin | hardcoded |
| [FreeIntv](#freeintv) | intellivision | .int .bin .rom | exec.bin grom.bin | /opt/retropie/configs/intellivision/retroarch.cfg |

## ROM and BIOS Paths
Place Intellivision ROMs in
```
/home/pi/RetroPie/roms/intellivision
```
Place your BIOS files in:
```
/home/pi/RetroPie/BIOS
```

# Emulators

## jzintv
[Visit the jzintv homepage](http://spatula-city.org/~im14u2c/intv/)

## BIOS

jzIntv requires at least the first two Intellivision BIOS files listed below to be placed in the libretro 'system' folder:

| Function | Filename* | MD5 Hash |
| --- | --- | --- | 
| **Executive ROM** | `exec.bin`  | `62e761035cb657903761800f4437b8af` |
| **Graphics ROM** - 213 predefined character images and some EXEC routines; Tutorvision variant | `grom.bin` | `0cd5946c6473e42e8e4c2137785e427f`|
| **Entertainment Computer System (ECS) ROM** - additional EXEC routines, the BASIC programming interpreter, and graphics of musical notes | `ECS.BIN` | `2e72a9a2b897d330a35c8b07a6146c52` |
| **Intellivoice RESROM** - resident ROM containing common speech words and phrases as well as program instructions | `IVOICE.BIN` | `d5530f74681ec6e0f282dab42e6b1c5f` |
| Keyboard Component EXEC ROM - BIOS for the Keyboard Component peripheral; PicSe (picture sequencer) routines for multimedia software | ? | ? |

* BIOS filenames are case-sensitive

### Controls:
By default, jzIntv maps the first (left) analog stick to the left controller's disc input. In addition, the first 9 buttons are mapped to the 3 action buttons as follows:
<pre>
Buttons 0, 3, 6:  Top action buttons, left controller
Buttons 1, 4, 7:  Lower left action button, left controller
Buttons 2, 5, 8:  Lower left action button, left controller
</pre>

jzIntv maps the first joystick's first hat's 8 directions to the numeric keypad on the right controller, making the hat usable in games such as Night Stalker and TRON Deadly Discs. [[Source](http://spatula-city.org/~im14u2c/intv/jzintv-1.0-beta3/doc/jzintv/joystick.txt)]

It is possible to remap these using a keyboard hack file. Instructions on creating these can be found [HERE](https://github.com/RetroPie/RetroPie-Setup/wiki/Mapping-a-Controller-for-Intellivision). Keys 0, Clear and Enter on the numeric keypad are not mapped by default so a keyboard hack file would be required to this.

#### Keyboard Controls

```shell
Function/Special keys, all maps:
    F1              Quit
    F4              Break into debugger
    F5              Switch to keymap 0 (default keymap)
    F6              Switch to keymap 1 (left controller only for 1 player games)

    F7              Switch to keymap 2 (ECS keyboard keymap)
    F8              Shift to keymap 3 while held (command keys)
    F9              Toggle fullscreen/windowed 
    F10             Toggle movie recording 
    F11             Take screen shot
    F12             Reset emulator
    Pause           Pause the emulator
    PgUp            Increase volume
    PgDn            Decrease volume

Numeric Keypad, maps 0 and 1
    1-9             Left controller 1 - 9
    0               Left controller Clear
    .               Left controller 0
    Enter           Left controller Enter

Main Keyboard, map 0.  (Map 1 just moves right controller mappings to left.)
    0-9             Right controller 0 - 9
    -               Right controller Clear
    =               Right controller Enter
    Left Shift      Right controller top action buttons
    Left Alt        Right controller lower left action button
    Left Control    Right controller lower right action button

    Right Shift     Left controller top action buttons
    Right Alt       Left controller lower left action button
    Right Control   Left controller lower right action button

    Up Arrow        Left controller disc up
    Down Arrow      Left controller disc down
    Left Arrow      Left controller disc left
    Right Arrow     Left controller disc right

Fine-grain directional pad inputs:

    U   I   O
      \ | /
       \|/ 
    J --+-- K      Left controller disc
       /|\
      / | \
    N   M   , 
   
    W   E   R
      \ | /
       \|/ 
    S --+-- D      Right controller disc
       /|\
      / | \
    Z   X   C
```
### Memory Map Config Files:

If a rom does not load leaving you with a black screen (and the files dump.cpu and dump.mem in your home folder upon exit), then you need a memory map config file. This is likely to be the case for titles from Atarisoft, Imagic or INTV Corp.

First determine which config file your rom requires from this [spreadsheet](https://docs.google.com/spreadsheet/ccc?key=0Ar_02usomyeqdHFyaGRnNWdLN1FzWTN3ajlacXBPWFE). 

Next download the config file from [here](https://docs.google.com/open?id=0B7_02usomyeqeWJVamRNM2FPUUk) and rename it the same as the your rom. 

For example, you are trying to get `atlantis.int` to work. From the spreadsheet, you see that it takes memory map #7 so download `7.cfg` and rename it `atlantis.cfg`. Place it in your roms folder and your rom should now work.

Full details about using memory map config files can be found [here](http://atariage.com/forums/topic/203179-config-files-to-use-with-various-intellivision-titles/#entry2605274).

![intellivision](https://cloud.githubusercontent.com/assets/10035308/8246393/3e98c8c2-15fb-11e5-9398-3f5abd60361b.png)

**********

## FreeIntv
[Visit the FreeIntv github repository](http://github.com/libretro/FreeIntv)

FreeIntv a libretro emulation core for the Mattel Intellivision designed to be compatible with joypads from the SNES era forward even if they originally required a number pad.

### BIOS
FreeIntv requires two Intellivision BIOS files to be placed in the libretro 'system' folder:

| Function | Filename* | MD5 Hash |
| --- | --- | --- | 
| Executive ROM | `exec.bin`  | `62e761035cb657903761800f4437b8af` |
| Graphics ROM | `grom.bin` | `0cd5946c6473e42e8e4c2137785e427f` |

* BIOS filenames are case-sensitive

### Entertainment Computer System and Intellivoice
FreeIntv does not currently support Entertainment Computer System (ECS) and Intellivoice funcationality. Contributions to the source are welcome!

### Controller overlays
Mattel Intellivision games were often meant to be played with game-specific cards overlaid on the numeric keypad. These overlays convey information which can be very useful in gameplay. Images of a limited selection of Intellivision titles are available at: http://www.intellivisionlives.com/bluesky/games/instructions.shtml

### Controls


* **Mini-Keypad** - Allows the user to view and select keys from a small Intellivision pad in the lower corner of the display.
* **Controller Swap** - Some Intellivision games expect the left controller to be player one, others expect the right controller. This isn't a problem if you have two controllers (and don't mind juggling them) but users with only one controller or using a portable setup would be effectively locked out of some games. Controller Swap swaps the two controller interfaces so that the player does not have to physically swap controllers.

| RetroPad | FreeIntv Function |
| --- | --- |
| D-Pad| 8-way movement |
| Left Analog Stick | 16-way disc |
| A | Left Action Button |
| Y | Top Action Button |
| X | Use the Last Selected Intellivision Keypad Button. In Astrosmash, for example, you can leave "3" selected to enable instant access to hyperspace. |
| L/R | Activate the Mini-Keypad |
| Start | Pause Game |
| Select | Controller Swap |

FreeIntv utilises Retroarch controller configurations. Add custom retroarch controls to the retroarch.cfg file in `/opt/retropie/configs/intellivision/retroarch.cfg`

For more information on RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)