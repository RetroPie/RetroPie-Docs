![Atari 7800 Logo](http://atarihq.com/danb/images/Atari_7800_logo.png)
***
_The Atari 7800 was a video game console released by Atari in 1986._
***
## Emulator: [Prosystem-libretro](https://github.com/libretro/prosystem-libretro)

## ROMS
Accepted File Extensions: **.a78 .bin**

Place your Atari ROMs in 
```
/home/pi/RetroPie/roms/atari7800
```

## BIOS 
This BIOS is optional if you want the Atari Logo at the beginning of games, otherwise you don't need it because the games work fine without it. The BIOS file name is **7800 BIOS (U).rom**

Place your Atari 7800 BIOS in
```
/home/pi/RetroPie/BIOS/7800 BIOS (U).rom
```
Note: if this BIOS is enabled, PAL ROMs will not work so use it accordingly.

## Controls

Prosystem-Libretro utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/atari7800/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)