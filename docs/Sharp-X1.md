***
![x1](https://user-images.githubusercontent.com/22881403/46316267-544e0b80-c595-11e8-8824-bf4042eaf6fd.png)
***
_The X1, sometimes called the Sharp X1, is a series of home computers released by Sharp Corporation from 1982 to 1988. It was based on a Z80 CPU._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-x1](https://github.com/r-type/xmil-libretro) | x1 | .dx1 .zip .2d .2hd .tfd .d88 .88d .hdm .xdf .dup .cmd | IPLROM.X1, IPLROM.X1T |  /opt/retropie/configs/x1/retroarch.cfg |

## Emulator: [lr-x1](https://github.com/r-type/xmil-libretro)
This emulator is a work in progress.  It can be installed from the experimental menu of the [RetroPie-Setup script.](https://github.com/RetroPie/RetroPie-Setup/wiki/Updating-RetroPie#using-the-retropie-setup-script)

Note that the emulator freezes if you attempt to load a ROM through the emulator's built-in GUI.

## ROMS

Accepted File Extensions: **.dx1 .zip .2d .2hd .tfd .d88 .88d .hdm .xdf .dup .cmd**

Place your Sharp X1 ROMs in:
```
/home/pi/RetroPie/roms/x1
```


## BIOS

Place your BIOS files in:
```
/home/pi/RetroPie/BIOS/xmil
```

## BIOS files

| File | CRC32 |
| :--: | :--: |
| IPLROM.X1 | 7B28D9DE |
| IPLROM.X1T | 2E8B767C |

## Controls

lr-x1 utilises Retroarch configurations.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/x1/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)