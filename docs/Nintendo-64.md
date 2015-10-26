![Nintendo 64 Logo](http://images2.wikia.nocookie.net/__cb20130424181606/theamazingworldofgumball/images/3/38/Nintendo_64_Logo.png)
***
_The Nintendo 64 is a 5th generation gaming console released by Nintendo in 1996_

***

## Emulators: [Mupen64plus](https://code.google.com/p/mupen64plus/), [lr-Mupen64plus](https://github.com/libretro/mupen64plus-libretro)

While the mupen64plus-libretro core has the convenience of RetroArch configurations, the actual Mupen64plus does better with performance. 

You can choose between the RICE, glesN64 and GLideN64 video plugin from the [runcommand](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand) menu- you may have to test out each one to see which works best- but you can also check the compatibility list below.

Note that you need a Raspberry Pi 2 if you want any decent N64 performance and even then it is hit and miss.

## ROMS
Accepted File Extensions: **.z64 .n64 .v64**

Place your Nintendo 64 ROMs in 
```
/home/pi/RetroPie/roms/n64
```

## [Rom Compatibility List](https://docs.google.com/spreadsheets/d/1Wjzbu90l6eCEW1w6ar9NtfyDBQrSPILQL5MbRSpYSzw/edit?usp=sharing) feel free to contribute!


## Controls

### lr-Mupen64plus

lr-Mupen64plus utilises RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/n64/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![nintendo_n64_diagram](https://cloud.githubusercontent.com/assets/10035308/7334793/6b406d8c-eb5b-11e4-8474-56a340521e71.png)

### Mupen64plus

There are two main configuration files that can be modified located at:
```
/opt/retropie/configs/n64/mupen64plus.cfg
and
/opt/retropie/configs/n64/InputAutoCfg.ini
```
## Video Tutorials

<a href="http://www.youtube.com/watch?feature=player_embedded&v=4WX7RrzUtII
" target="_blank"><img src="https://i.ytimg.com/vi_webp/4WX7RrzUtII/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a> |
<a href="https://www.youtube.com/watch?v=lh0n5PWN2lI
" target="_blank"><img src="https://i.ytimg.com/vi_webp/lh0n5PWN2lI/mqdefault.webp" 
alt="N64 Configuration Video" width="300" height="180" border="10" /></a> 