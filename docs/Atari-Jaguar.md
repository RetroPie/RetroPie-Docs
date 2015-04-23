![](http://atariage.com/forums/uploads/monthly_09_2013/post-2754-0-29015300-1378838194.jpg)

***
_The Atari Jaguar was the first 64 bit video game console released in 1993. It was a bad enough commercial failure that it put Atari out of the home video game console business._

***


## Emulator: [virtualjaguar-libretro](https://github.com/libretro/virtualjaguar-libretro) (Experimental)

Note that this emulator is currently experimental and will need to be installed through the experimental menu in the setup script. On testing with RPi2 it is incredibly laggy and slow and experimental for a reason.

## ROMS

Accepted File Extensions: **.j64 .jag**

Place your Atari Jaguar ROMs in 
```
/home/pi/RetroPie/roms/atarijaguar
```
## Controls

Virtualjaguar-Libretro utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/atarijaguar/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)