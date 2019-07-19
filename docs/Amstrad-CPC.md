
***

![amstradcpc](https://cloud.githubusercontent.com/assets/10035308/12186502/90cc75ee-b560-11e5-8293-5ea82fa8b2d7.png)
***
_The Amstrad CPC (short for Colour Personal Computer) is a series of 8-bit home computers produced by Amstrad between 1984 and 1990._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-caprice32](https://github.com/libretro/libretro-cap32.git), [CapriceRPI](https://github.com/KaosOverride/CapriceRPI.git) | amstradcpc  | .dsk .cpc | none | /opt/retropie/configs/armstradcpc/retroarch.cfg |

## Emulators: [CapriceRPI](https://github.com/KaosOverride/CapriceRPI.git), [lr-caprice32](https://github.com/libretro/libretro-cap32.git)

## ROMS

Accepted File Extensions: **.dsk .cpc**

Place your Amstrad CPC ROMs in
```
/home/pi/RetroPie/roms/amstradcpc
```
## Joystick Controls Setup
As usual for a "classic" computer, a keyboard is needed for optimum input control. Flight simulators or complex building simulations require a variety of key combinations. For further input we need a connected (real) keyboard or a **Virtual Keyboard**. This can be called with the **START+Y-Button** of your PAD in lr-caprice32 (older versions < 4.5 make use of Y-Button only)

When we talk about joysticks, these are directly interpreted as cursor inputs by the CPC. The fire button is displayed as `X`. So if you press right HAT button a right arrow will be printed. So you see the CPC interprets the joysticks input as ASCII code, very unsimilar to the Atari 2600 or C64. But the devices use all a D-SUB-9 connector and theoretically even a Megadrive/Genesis PAD could be connected to this mashines (afaik Start or Select button bridges 5V and Ground -- risk of a short circuit with possible damage to original hardware). 

### JoyPad setup for lr-caprice32
By default the `RetroPad` is selected as controller input we have to select `Amstrad Joystick` to make the Virtual Keyboard work. Enter the retroarch core by using `SELECT + Y` on your pad, now use *Retroarch -> Quickmenu -> Controls -> User [1-4] Select Device Type Amstrad Joystick* and save the overlay.

Now you can launch the **Virtual Keyboard** to configurate any game. If the overlay window seems to stuck then press Select-Button on your pad to activate it and move its white cursor with the HATs. A-Button selects the character.

A more elegant way is to directly edit the configuration file with `nano /opt/retropie/configs/amstradcpc/retroarch.cfg` and add `input_libretro_device_p1 = "513"`. So the file could look like this

```
# Settings made here will only override settings in the global retroarch.cfg if placed above the #include line

input_remapping_directory = "/opt/retropie/configs/amstradcpc/"
input_libretro_device_p1 = "513"
input_libretro_device_p2 = "513"

#include "/opt/retropie/configs/all/retroarch.cfg"
```

### JoyPad setup for CapriceRPI
Default keys:
* Analog1 / HATs is cursor control
* Y-Button brings up the Virtual Keyboard
* X-Button brings up configuration menu (with possibitly for save state)
* B-Button is FIRE (lr-caprice uses A-Button)
* A-Button is charcter `Z`

## CapriceRPI

If you are open into a ROM from EmulationStation and it opens to a blue screen you can type
```
CAT
```
and it will list the file names of your game. The you will type RUN"FILENAME (match the lettercase exactly)

e.g. CAT results:
```
CABAL     .BI1
CABAL     .BI2
CABAL     .BIN
CABAL     .LV1
```
Then I type:
```
RUN"CABAL
```
If your keyboard types `@` when you try to type `"`, then the Pi may be configured for the English (UK) keyboard layout, in which case you can type `"` by trying to type `@`.

**QUICK START CONTROLS**
```
F5: reset
F6: exit

Keyboard Controls will vary by game
```

## lr-caprice32

lr-caprice32 utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/amstradcpc/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

## Links of interest / References
[[Solved] Amstrad CPC - Virtual Keyboard? lr-caprice32](https://retropie.org.uk/forum/topic/21885)\
[How to remap Keyboard chars to specific Joypad buttons](https://retropie.org.uk/forum/topic/20708)