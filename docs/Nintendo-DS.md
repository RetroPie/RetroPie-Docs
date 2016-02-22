***
![nds](https://cloud.githubusercontent.com/assets/10035308/12213354/eab79344-b633-11e5-805b-7d1a93fa44dd.png)
***
The Nintendo DS is a handheld video game console that was released by Nintendo in 2004. The DS stands for Dual Screen.
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-desmume](https://github.com/libretro/desmume) | nds  | .nds .bin | none | /opt/retropie/configs/nds/retroarch.cfg |

Note that this is very experimental and lags quite a bit even with an overclocked Rpi 2. But it can be installed through the experimental menu in the [RetroPie Setup Script](Updating RetroPie).

## Emulator: [lr-desmume](https://github.com/libretro/desmume)

## ROMS
Accepted File Extensions: **.nds .bin**

Place your DS ROMs in 
```
/home/pi/RetroPie/roms/nds
```

## Controls

lr-desmume utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/nds/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![dsdiagram](https://cloud.githubusercontent.com/assets/10035308/8240819/99893d9a-15c2-11e5-9d52-c86db39493f6.png)