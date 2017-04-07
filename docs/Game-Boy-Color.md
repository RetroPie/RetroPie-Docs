***
![gbc](https://cloud.githubusercontent.com/assets/10035308/12191836/672b3014-b596-11e5-9bbe-bcafd30bb402.png)
***
_The Game Boy Color was an 8 bit handheld gaming console released by Nintendo in 1998. Pokemon Yellow anyone?_

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-gambatte](https://github.com/libretro/gambatte-libretro) | gbc  | .gbc .zip | none | /opt/retropie/configs/gbc/retroarch.cfg |
| [lr-tgbdual](https://github.com/libretro/tgbdual-libretro) | gbc  | .gbc .zip | none | /opt/retropie/configs/gb/retroarch.cfg |

## Emulator: [lr-gambatte](https://github.com/libretro/gambatte-libretro)

lr-gambatte is a libretro port of Gambatte that utilises RetroArch configurations for your controller
## ROMS

Accepted File Extensions: **.gbc**

Place your Game Boy Color ROMs in
```
/home/pi/RetroPie/roms/gbc
```
## Controls

lr-gambatte utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/gbc/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![gameboycolor](https://cloud.githubusercontent.com/assets/10035308/7334404/bd65e496-eb4e-11e4-82e6-78494534d305.png)

## Com Link

Com link support is currently only available in lr-tgbdual. Once a ROM is launched with lr-tgbdual, two synced game screens will be displayed side-by-side. Player one is then able to control the left screen, while player two controls the right.