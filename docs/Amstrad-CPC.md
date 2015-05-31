![Amstrad CPC Logo](http://www.iamretro.gr/wp-content/uploads/2013/01/logo_amstrad2.png)
***
_The Amstrad CPC (short for Colour Personal Computer) is a series of 8-bit home computers produced by Amstrad between 1984 and 1990._
***
## Emulators: [CPC4Rpi](http://gaming.capsule-sa.co.za/?gamepress_reviews=cpc4rpi-cpc-6128-emulator-for-raspberry-pi), [libretro-caprice32](https://github.com/libretro/libretro-cap32.git)

## ROMS

Accepted File Extensions: **.dsk .cpc**

Place your Amstrad CPC ROMs in
```
/home/pi/RetroPie/roms/amstradcpc
```
## Controls

## CPC4Rpi

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
if your keyboard can't seem to make the " then try holding shift and pressing the number 2 and it should type a quotation mark

**QUICK START CONTROLS**
```
F5: reset
F6: exit

Keyboard Controls will vary by game
```

## libretro-cap32 

libretro-cap32 utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/armstradcpc/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)