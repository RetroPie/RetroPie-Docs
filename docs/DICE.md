***
DICE is a Discrete Integrated Circuit Emulator. It emulates computer systems that lack any type of CPU, consisting only of discrete logic components.
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-dice](https://github.com/mittonk/dice-libretro) | arcade **or** dice | .zip .dmy | | |

## Emulator: [lr-dice](https://github.com/mittonk/dice-libretro)
DICE is a Discrete Integrated Circuit Emulator. It emulates computer systems
that lack any type of CPU, consisting only of discrete logic components.

**dice-libretro (lr-dice)**
 is a Libretro port of DICE, to run in RetroArch.
 
Pi4 is a reasonable minimum requirement.

Some games (like pong) will run on a
Zero2w, others (like pinpong) will run out of memory.


## ROMS
Accepted File Extensions: **.zip, .dmy**

Some games (pong, breakout, pinpong, etc) do not have any ROM on the board at
all. For these, copy the dummy launcher file from dummy_files to your ROM folder;
these have a correct name (for example, pong.dmy) that will get RetroArch to set
up lr-dice for the correct game.


Place your arcade ROMs in either:
```shell
/home/pi/RetroPie/roms/arcade
```
or
```shell
/home/pi/RetroPie/roms/dice
```
depending on whether you'd rather group them with or separately from MAME,
FBNeo, etc.


## Controls

`lr-dice` uses the [RetroArch control configuration](RetroArch-Configuration).

Analog sticks are used for paddle inputs.

A mouse can be used for paddle input, see
[lr-dice Mouse Support](https://github.com/mittonk/dice-libretro/?tab=readme-ov-file#mouse-support).
