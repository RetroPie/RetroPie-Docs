![Nintendo Entertainment System Logo](http://upload.wikimedia.org/wikipedia/commons/thumb/0/0d/NES_logo.svg/640px-NES_logo.svg.png)
***
_The Nintendo Entertainment System (NES) is an 8-bit home video game console that was released by Nintendo in 1985._

***
## Emulators: [lr-nestopia](https://github.com/libretro/nestopia), [lr-fceumm](https://github.com/libretro/libretro-fceumm)

Both emulators utilise RetroArch configurations for controllers. Nestopia is preferred due to better accuracy and the ability to play Famicom Disk System games.

## ROMS

Accepted File Extensions: **.zip .nes .smc .sfc .fig .swc .mgd** - Make sure your roms have headers. Roms without headers will not work.

Place your NES Roms in
```
/home/pi/RetroPie/roms/nes
```
## BIOS

Nestopia is able to play Famicom Disk System games with a **disksys.rom** bios file.

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