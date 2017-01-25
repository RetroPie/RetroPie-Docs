***

***
_PC-FX is a 32-bit home video game console by NEC Home Electronics released in Japan on December 23, 1994._

***

| Emulator | Rom Folder | Extensions | BIOS | Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-beetle-pcfx](https://github.com/libretro/beetle-pcfx-libretro) | pcfx | .img .iso .ccd .cue | pcfx.rom | /opt/retropie/configs/pcfx/retroarch.cfg |

## Emulator: [lr-beetle-pcfx](https://github.com/libretro/beetle-pcfx-libretro)

## ROMS

Place your PC-FX ROMs in
```
/home/pi/RetroPie/roms/pcfx
```

## BIOS

The BIOS file is named **pcfx.rom** (all in lower-case)

Place pcfx.rom in
```
/home/pi/RetroPie/BIOS
```

| md5sum          |        CRC32 |
|--------------|--------------------|
| 08e36edbea28a017f79f8d4f7ff9b6d7 | 76ffb97a |

## Controls

utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/pcfx/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

## PC-FX BIN/CUE Files

It is important that the image file (usually `.bin`) and the CUE file (`.cue`) match.

CUE files are just text files containing a description of the CD. If you have files named like:

~~~
Chip Chan Kick.bin
Chip Chan Kick.cue
~~~

then ensure the first line of the CUE file contains:

~~~
FILE "Chip Chan Kick.bin" BINARY
~~~
