![](http://upload.wikimedia.org/wikipedia/commons/4/43/Nintendo_DS_logo.png)

***
The Nintendo DS is a handheld video game console that was released by Nintendo in 2004. The DS stands for Dual Screen.

***
Note that this is very experimental and lags quite a bit even with an overclocked Rpi 2. But it can be installed through the experimental menu in the RetroPie Setup Script.

## Emulator: [libretro-desmume](https://github.com/libretro/desmume)

## ROMS
Accepted File Extensions: **.nds .bin**

Place your DS ROMs in 
```
/home/pi/RetroPie/roms/nds
```

## Controls

Libretro-Desmume utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/nds/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![dsdiagram](https://cloud.githubusercontent.com/assets/10035308/8240819/99893d9a-15c2-11e5-9d52-c86db39493f6.png)