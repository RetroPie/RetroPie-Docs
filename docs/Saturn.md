![Sega Saturn](http://fc08.deviantart.net/fs70/f/2012/230/3/e/sega_saturn_logo__vector__by_xmaster555-d5blkb5.png)
***
_The Sega Saturn is a 32 bit 5th generation home video game console released by Sega in 1994. It has a total of 8 processor which makes it one of the more difficult consoles to emulate._
***
## Emulator: [lr-Yabause](https://github.com/libretro/yabause) (NOTE: EXPERIMENTAL!)

Yabause stands for: Yet Another Buggy And Uncomplete Sega Emulator. It stands by its name. Currently you need to install it from the setup script under experimental builds. a Raspberry Pi 2 is a must. Most if not all games have incredibly choppy sound, are extremely laggy, and quite frankly aren't yet quite playable without a lot of tweaking and a few prayers.

## ROMS

Accepted File Extensions: **.bin .iso .mdf**

Place your Sega Saturn ROMs in 
```
/home/pi/RetroPie/roms/saturn
```

## BIOS

The BIOS file needed is **saturn_bios.bin**

Place your BIOS in
```
/home/pi/RetroPie/BIOS
```

## Controls

libretro-yabause utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/saturn/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![saturn](https://cloud.githubusercontent.com/assets/10035308/7449063/327bfb76-f1e9-11e4-9c58-4b38a3c1284d.png)