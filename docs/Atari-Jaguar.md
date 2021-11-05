***
![atarijaguar](https://cloud.githubusercontent.com/assets/10035308/12190454/f776b6a4-b585-11e5-9b8b-1f7ed69480b3.png)
***
_The Atari Jaguar was the first 64 bit video game console released in 1993. It was a bad enough commercial failure that it put Atari out of the home video game console business._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-virtualjaguar](https://github.com/libretro/virtualjaguar-libretro) | atarijaguar  | .j64 .jag | none | /opt/retropie/configs/atarijaguar/retroarch.cfg |

## Emulator: [lr-virtualjaguar](https://github.com/libretro/virtualjaguar-libretro) 

**lr-virtualjaguar** is experimental and too slow for most Raspberry Pi systems, but with an overclocked Pi4 it's possible to run some games at full speed. See [this forum topic](https://retropie.org.uk/forum/topic/27999/) for an overview of the tested games and the overclock settings used.

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
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![atarijaguardiagram](https://cloud.githubusercontent.com/assets/10035308/8268598/4a5d1868-1748-11e5-994d-e0d508d8877b.png)
