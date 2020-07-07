***
![atarilynx](https://cloud.githubusercontent.com/assets/10035308/12190664/6ef7c284-b588-11e5-9dc2-875676e9ea78.png)
***
_The Atari Lynx is the world's first handheld gaming console with a color screen. It was released by Atari in 1989_
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-handy](https://github.com/libretro/libretro-handy) | atarilynx  | .7z .lnx .zip | lynxboot.img (optional)| /opt/retropie/configs/atarilynx/retroarch.cfg |
| [lr-beetle-lynx](https://github.com/libretro/beetle-lynx-libretro) | atarilynx  | .7z .lnx .zip | lynxboot.img | /opt/retropie/configs/atarilynx/retroarch.cfg |

## Emulator: [lr-handy](https://github.com/libretro/libretro-handy), [lr-beetle-lynx](https://github.com/libretro/beetle-lynx-libretro)

## ROMS
Accepted File Extensions: **.7z .lnx .zip**

Place your Lynx ROMS in:
```shell
/home/pi/RetroPie/roms/atarilynx/
```
## BIOS

The file needed is **lynxboot.img** (only for lr-beetle-lynx)

Place your lynxboot.img BIOS file in
```
/home/pi/RetroPie/BIOS
```

| File | md5sum | CRC32 |
| :--: | :--: | :--: |
| lynxboot.img | fcd403db69f54290b51035d82f835e7b | 0d973c9d |

## Controls

lr-handy utilises Retroarch configurations

Add custom RetroArch controls to the retroarch.cfg file in:
```shell
/opt/retropie/configs/atarilynx/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![atari_lynx_diagram](https://cloud.githubusercontent.com/assets/10035308/16599640/7f435408-42c0-11e6-8034-d04fec9310ce.png)