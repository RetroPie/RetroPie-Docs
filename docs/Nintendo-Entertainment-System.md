***
![nes](https://cloud.githubusercontent.com/assets/10035308/12213379/4a0e517a-b634-11e5-98c4-91cc27549706.png)
***
_The Nintendo Entertainment System (NES) is an 8-bit home video game console that was released by Nintendo in 1985._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fceumm](https://github.com/libretro/libretro-fceumm) | nes  | .zip .nes .smc .sfc .fig .swc .mgd | none | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-nestopia](https://github.com/libretro/nestopia) | nes  | .zip .nes .smc .sfc .fig .swc .mgd | disksys.rom | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-quicknes](https://github.com/libretro/QuickNES_Core) | nes  | .zip .nes .smc .sfc .fig .swc .mgd | none | /opt/retropie/configs/nes/retroarch.cfg |

## Emulators: [lr-nestopia](https://github.com/libretro/nestopia), [lr-fceumm](https://github.com/libretro/libretro-fceumm), [lr-quicknes](https://github.com/libretro/QuickNES_Core)

Both emulators utilise RetroArch configurations for controllers. lr-nestopia is preferred due to better accuracy and the ability to play Famicom Disk System games, plus [better input latency](http://libretro.com/forums/showthread.php?t=5428&p=41746&viewfull=1#post41746). lr-fceumm is slightly faster, which may give a benefit to Raspberry Pi 1/0 users.

## ROMS

Accepted File Extensions: **.zip .nes .smc .sfc .fig .swc .mgd** - Make sure your roms have headers. Roms without headers will not work.

Place your NES Roms in
```
/home/pi/RetroPie/roms/nes
```
## BIOS

Both lr-nestopia and lr-fceumm are able to play Famicom Disk System games with a **disksys.rom** bios file.

Place the BIOS in
```
/home/pi/RetroPie/BIOS
```
## Controls

Both emulators utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/nes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![nesdiagram](https://cloud.githubusercontent.com/assets/10035308/8245062/4f0c5b8e-15e6-11e5-9255-b920543518d6.png)