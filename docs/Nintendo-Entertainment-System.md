***
![nes](https://cloud.githubusercontent.com/assets/10035308/12213379/4a0e517a-b634-11e5-98c4-91cc27549706.png)
***
_The Nintendo Entertainment System (NES) is an 8-bit home video game console that was released by Nintendo in 1985._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fceumm](https://github.com/libretro/libretro-fceumm) | nes  | .zip .nes .smc .sfc .fig .swc .mgd .fds | none | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-nestopia](https://github.com/libretro/nestopia) | nes  | .zip .nes .smc .sfc .fig .swc .mgd .fds | none | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-quicknes](https://github.com/libretro/QuickNES_Core) | nes  | .zip .nes .smc .sfc .fig .swc .mgd | none | /opt/retropie/configs/nes/retroarch.cfg |

If you want to play Famicom Disk System games see the wiki page [HERE](Famicom-Disk-System)

## Emulators: [lr-nestopia](https://github.com/libretro/nestopia), [lr-fceumm](https://github.com/libretro/libretro-fceumm), [lr-quicknes](https://github.com/libretro/QuickNES_Core)

## ROMS

Accepted File Extensions: **.zip .nes .smc .sfc .fig .swc .mgd** - Make sure your roms have headers. Roms without headers will not work. If you want to use PAL roms, make sure they contain `(E)` or `(Europe)` in the filename, or else they may be run at the wrong speed.

Place your NES Roms in
```
/home/pi/RetroPie/roms/nes
```

## Controls

Both emulators utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/nes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nesdiagram](https://cloud.githubusercontent.com/assets/10035308/8245062/4f0c5b8e-15e6-11e5-9255-b920543518d6.png)