***
![fds_header](https://cloud.githubusercontent.com/assets/10035308/23090452/7af681b8-f553-11e6-8da8-73f7815941c7.png)
***
The Family Computer Disk System a.k.a. Famicom Disk System was released in Japan in 1986. It is an addon to the Famicom and used floppy disks.
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fceumm](https://github.com/libretro/libretro-fceumm) | fds  | .7z .fds .nes .zip | disksys.rom | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-nestopia](https://github.com/libretro/nestopia) | fds  | .7z .fds .nes .zip | disksys.rom | /opt/retropie/configs/nes/retroarch.cfg |

## Emulators: [lr-nestopia](https://github.com/libretro/nestopia), [lr-fceumm](https://github.com/libretro/libretro-fceumm)

## ROMS

Accepted File Extensions: **.7z .fds .nes .zip**

Place your FDS Roms in
```
/home/pi/RetroPie/roms/fds
```
## BIOS

FDS games require the **disksys.rom** bios file.

Place the BIOS in
```
/home/pi/RetroPie/BIOS
```

| Name | md5sum | CRC32 |
| :--: | :--: | :--: |
| Family Computer Disk System (Japan) (Rev 1) | ca30b50f880eb660a320674ed365ef7a | 5e607dcf |

## Controls

Both emulators utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/nes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nesdiagram](https://cloud.githubusercontent.com/assets/10035308/8245062/4f0c5b8e-15e6-11e5-9255-b920543518d6.png)