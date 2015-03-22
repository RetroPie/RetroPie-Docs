![Nintendo 64 Logo](http://images2.wikia.nocookie.net/__cb20130424181606/theamazingworldofgumball/images/3/38/Nintendo_64_Logo.png)
***
_The Nintendo 64 is a 5th generation gaming console released by Nintendo in 1996_

***

## Emulators: [Mupen64plus](https://code.google.com/p/mupen64plus/) [Mupen64plus-libretro](https://github.com/libretro/mupen64plus-libretro)

While the mupen64plus-libretro core has the convenience of RetroArch configurations, the actual Mupen64plus does better with performance. Note that you should be using a Raspberry Pi 2 if you want any decent N64 performance.

## ROMS
Accepted File Extensions: **.z64 .n64 .v64**

Place your Nintendo 64 ROMs in 
```
/home/pi/RetroPie/roms/n64
```
## Controls

### Mupen64plus-libretro

Mupen64plus-libretro utilises RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/N64/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

### Mupen64plus-libretro

There are two main configuration files that can be modified located at:
```
/opt/retropie/configs/N64/mupen64plus.cfg
and
/opt/retropie/configs/N64/InputAutoCfg.ini
```
See this video to get an idea of how to customise them for your needs

<a href="http://www.youtube.com/watch?feature=player_embedded&v=4WX7RrzUtII
" target="_blank"><img src="https://i.ytimg.com/vi_webp/4WX7RrzUtII/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a>