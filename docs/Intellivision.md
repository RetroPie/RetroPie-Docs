***
![intellivision](https://cloud.githubusercontent.com/assets/10035308/12192412/82366f36-b59b-11e5-973e-208fea792945.png)
***

_The Intellivision is a home video game console released by Mattel in 1979_

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [jzintv](#jzintv) | intellivision  | .int .bin | exec.bin grom.bin | hardcoded |
| [FreeIntv](#freeintv) | intellivision | .int .bin .rom | exec.bin grom.bin | /opt/retropie/configs/intellivision/retroarch.cfg |

## ROMS
Place Intellivision ROMs in
```
/home/pi/RetroPie/roms/intellivision
```
## BIOS
The first two files listed below are the most important:
* Executive ROM: **exec.bin** MD5: `62e761035cb657903761800f4437b8af`
* Graphics ROM: **grom.bin** MD5: `0cd5946c6473e42e8e4c2137785e427f`
* Entertainment Computer System ROM: ECS.BIN. Required to play ECS games. 
* Intellivoice ROM: IVOICE.BIN. Required to play Intellivoice games. 

Place your BIOS files in:
```
/home/pi/RetroPie/BIOS
```

# Emulators

## jzintv
[Visit the jzintv homepage](http://spatula-city.org/~im14u2c/intv/)

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
[Visit the FreeIntv homepage](http://neocomputer.org/projects/freeintv/)

FreeIntv a libretro emulation core for the Mattel Intellivision designed to be compatible with joypads from the SNES era forward even if they originally required a number pad.

### Controls:

* The d-pad will give you 8-way movement. If available, the left analog stick will function like the 16-way disc. 
* The FreeIntv "mini keypad" allows you to view and press keys on a small keypad that appears in the lower-corner of the display while L or R is being held.
* The "X" button is also mapped to the last selected keypad button, giving quick access. In Astrosmash, for example, you can leave "3" selected to enable instant access to hyperspace.
* The select button lets you switch the left and right controllers. Some games expect the left controller to be player one, others expect the right controller. This isn't a problem if you have two controllers (and don't mind juggling them) but users with only one controller or using a portable setup would be effectively locked out of some games. Pressing select from either controller with swap the left controller for the right and vice-versa.

FreeIntv utilises Retroarch controller configurations. Add custom retroarch controls to the retroarch.cfg file in `/opt/retropie/configs/intellivision/retroarch.cfg`

For more information on RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)
