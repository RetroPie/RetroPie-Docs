
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
## Controls

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