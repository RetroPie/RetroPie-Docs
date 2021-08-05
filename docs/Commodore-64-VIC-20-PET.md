***
![c64](https://cloud.githubusercontent.com/assets/10035308/12191151/2f3aaf48-b58e-11e5-92e5-b39455579c63.png)
***
_The Commodore 64 is an 8 Bit personal computer introduced in 1982 by Commodore International. This model holds the world record for the highest-selling single computer model of all time._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [VICE](https://vice-emu.sourceforge.io/) | c64 | .crt .d64 .g64 .t64 .tap .x64 .zip .prg | none | /opt/retropie/configs/c64/sdl-vicerc <br> /opt/retropie/configs/c64/sdl-joymap-c64.vjm|
| [lr-vice](https://github/libretro/vice-libretro/) | c64 | .crt .d64 .d80 .d81 .g64 .t64 .tap .x64 .zip .prg .tap .t64 .crt .m3u .zip | optional | /opt/retropie/configs/c64/retroarch.cfg |

## ROMS
Accepted File Extensions: **.crt .d64 .g64 .t64 .tap .x64 .prg**

Place your ROMS in
```
/home/pi/RetroPie/roms/c64
```

## Emulator: [VICE](https://vice-emu.sourceforge.io/)


### Controls

Key       | Action
:---------|:------
Space     | Start Game
F12       | Menu
Enter     | Select
Backspace | Cancel
Esc       | Exit Menu

#### Changing Controls

Press F12 to open the VICE menu.

- Navigate to _Machine settings_, use Enter to open the menu
- Navigate to _Joystick settings_, use Enter to open the menu
- Navigate to _Joystick device in port 2_, use Enter to open the menu

  - to use a numpad to play your game, navigate to _Numpad_ use Enter to select it. The mapping will be:

    - Up: 8
    - Up/Right: 9
    - Up/Left: 7
    - Left: 4
    - Right: 8
    - Down: 2
    - Down/Left: 1
    - Down/Right: 3
    - Fire: 0

  - to use a Joystick (gamepad) instead, navigate to _Joystick_ and use Enter to select it.

Use Backspace to go back to previous menu or Escape to exit the Menu completely.

#### Saving Configuration

Configuration can be saved from _Settings management_ menu. Available options:

+ Save current settings
+ Save hotkeys
+ Save joystick map

The _Save settings on exit_ option can be toggled from the same menu, so that any changes to the VICE configuration will automatically be saved when quitting the emulator.

#### Custom Joystick Mappings

Custom mappings can be defined from the _Joystick settings_ (under the _Machine settings_ menu). The _Joystick 1 mapping_ or _Joystick 2 mapping_ menus can be used. 

The mapping can be changed by pressing Enter on each joystick input (Up/Down/Left/Righ/Fire 1,3,3), followed by pressing the corresponding button/key on the gamepad/keyboard.

### Other Commodore Systems
In addition to Commodore 64, the VICE emulator also emulates the following Commodore systems: 

- C128
- C64DTV
- almost all PET models
- PLUS4
- CBM-II (aka C610) 
- VIC20

To select the emulated system, the [Runcommand Launch Menu](Runcommand) can be used before a ROM is started.

![03062016_2322241](https://cloud.githubusercontent.com/assets/10035308/13558061/dc5eeade-e3b7-11e5-94cc-4891ccafe15a.png)

## Emulator: [lr-vice](https://github.com/libretro/vice-libretro/)

### BIOS

`lr-vice` can use external ROM files for JiffyDOS support, which should be copied to:

````
/home/pi/RetroPie/BIOS/vice
````

| Filename                     | Description                  | MD5                              |
|:-----------------------------|:-----------------------------|:---------------------------------|
| JiffyDOS_C64.bin             | JiffyDOS C64 Kernal          | be09394f0576cf81fa8bacf634daf9a2 |
| JiffyDOS_1541-II.bin         | JiffyDOS 1541 drive BIOS     | 1b1e985ea5325a1f46eb7fd9681707bf |
| JiffyDOS_1571_repl310654.bin | JiffyDOS 1571 drive BIOS     | 41c6cc528e9515ffd0ed9b180f8467c0 |
| JiffyDOS_1581.bin            | JiffyDOS 1581 drive BIOS     | 20b6885c6dc2d42c38754a365b043d71 |

### Controls

`lr-vice` uses the RetroArch configured RetroPad (see: [RetroArch Configuration](RetroArch-Configuration)).

#### Default controls

| RetroPad button | Action                  |
|-----------------|-------------------------|
| D-Pad           | Joystick                |
| Left Analog     | Mouse/paddles           |
| B               | Fire button             |
| X               | Space                   |
| L2              | Escape (RUN/STOP)       |
| R2              | Enter (RETURN)          |
| Select          | Toggle virtual keyboard |

| Keyboard key      | Action                  |
|-----------------  |-------------------------|
| F12               | Toggle statusbar        |
| Right Control     | Switch between joyports |
| End               | Reset                   |

#### Virtual keyboard controls


The VICE cores have a virtual keyboard that can be accessed by default through the Select button.   
The virtual keyboard can be controlled with:


- **RetroPad**

    | Button   | Action              |
    |----------|---------------------|
    | D-Pad    | Move                |
    | B        | Keypress            |
    | A        | Toggle transparency |
    | Y        | Toggle ShiftLock    |
    | Start    | Press Return        |

- **Keyboard**

    | Key      | Action              |
    |----------|---------------------|
    | Cursors  | Move                |
    | Enter    | Keypress            |
    | CapsLock | Toggle ShiftLock    |

Long press for sticky keys. Stickying the third key will replace the second.

#### Joystick control

Older C64 games tend to use joystick port 1 and newer ones tend to use port 2 for player 1. There are several ways to switch ports:

- Using the core options: `Quick Menu -> Options -> RetroPad Port`
- On virtual keyboard (`Select`): press the key labeled `JOY`
- Pressing the default keyboard shortcut: `Right Control`
- Assigning `Switch Joyport` to any RetroPad button, under `Quick Menu -> Options`
- Renaming the game, eg. `Bruce_Lee_j1.tap` or `Bruce_Lee_(j1).tap` for port 1, similarly `Bruce_Lee_j2.tap` or `Bruce_Lee_(j2).tap` for port 2

### M3U support and disk control

For a multi disk game, an M3U playlist file can be used to group and change disks from the RetroArch Disc Control interface.

A M3U file is a simple text file, with one disk per line (see [Wiki](https://en.wikipedia.org/wiki/M3U)).

Example:

M3U file: `Ultima VI - The False Prophet (1990)(Origin Systems).m3u`, containing:

```
Ultima VI - The False Prophet (1990)(Origin Systems)(Disk 1 of 3 Side A)(Game).d64
Ultima VI - The False Prophet (1990)(Origin Systems)(Disk 1 of 3 Side B)(Surface).d64
Ultima VI - The False Prophet (1990)(Origin Systems)(Disk 2 of 3 Side A)(Dungeon).d64
Ultima VI - The False Prophet (1990)(Origin Systems)(Disk 2 of 3 Side B)(Populace A).d64
Ultima VI - The False Prophet (1990)(Origin Systems)(Disk 3 of 3 Side A)(Populace A).d64
Ultima VI - The False Prophet (1990)(Origin Systems)(Disk 3 of 3 Side B)(Populace A).d64
```

Paths in the M3U file can be absolute or relative to the location of the M3U file.

When the game asks for it, the current disk can be change from the RetroArch _Disc Control+ menu:

- Eject the current disk with _Eject Disc_
- Select the right disk index with _Current Disc Index_ from the disk list drop-down
- Insert the new disk with _Insert Disc_

### Zip Archives Support

ZIP archives will be extracted to a temporary directory, in roms folder. The temporary directory will be removed on exit.

This allows:

- Automatic M3U playlist generation from the all files included in the archive.
- The use of zipped images in M3U files.

### Other Commodore Systems

`lr-vice` supports a large number of Commodore systems, RetroPie includes:

- C128
- C64
- C64DTV
- almost all PET models
- PLUS4
- VIC20

To select the emulated system, the [Runcommand Launch Menu](Runcommand) can be used before a ROM is started.

### Core Configuration

Configuration of the `lr-vice` core(s) is available from the RetroArch's Core _Options_ menu. A list of available parameters and configuration options is found in the [Libretro Core documentation](https://docs.libretro.com/library/vice/#core-options).

## Other configurations
Dedicated systems (e.g. VIC20/Pet/Plus4/C128) can be created in EmulationStation following these [instructions](https://retropie.org.uk/docs/Add-a-New-System-in-EmulationStation/).

SVG Logos for each Commodore system are available [here](https://retropie.org.uk/forum/topic/3226/es-custom-svg-logo-pack-includes-specific-mame-logos), courtesy of forum user [UDb32](https://github.com/UDb23/rpie-custom).
