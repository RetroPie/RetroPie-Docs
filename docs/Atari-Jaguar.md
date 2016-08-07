***
![atarijaguar](https://cloud.githubusercontent.com/assets/10035308/12190454/f776b6a4-b585-11e5-9b8b-1f7ed69480b3.png)
***
_The Atari Jaguar was the first 64 bit video game console released in 1993. It was a bad enough commercial failure that it put Atari out of the home video game console business._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-virtualjaguar](https://github.com/libretro/virtualjaguar-libretro) | atarijaguar  | .j64 .jag | none | /opt/retropie/configs/atarijaguar/retroarch.cfg |

## Emulator: [lr-virtualjaguar](https://github.com/libretro/virtualjaguar-libretro) :small_red_triangle: 

Note that this emulator is currently experimental and will need to be installed through the experimental menu in the setup script. On testing with RPi2 it is incredibly laggy and slow and experimental for a reason. As of 8/6/16, testing on RPi3 (overclocked and normal speed) where choppy as well. For example, Doom took 48 seconds stock speed to load the first level, 41 seconds overclocked to 1ghz.

## ROMS

Accepted File Extensions: **.j64 .jag**

Place your Atari Jaguar ROMs in 
```
/home/pi/RetroPie/roms/atarijaguar
```
## Controls

lr-virtualjaguar utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/atarijaguar/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![atarijaguardiagram](https://cloud.githubusercontent.com/assets/10035308/8268598/4a5d1868-1748-11e5-994d-e0d508d8877b.png)