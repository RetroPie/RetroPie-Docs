***
![pc-fx](https://retropie.org.uk/forum/assets/uploads/files/1498080299430-nec_pc-fx_logo.svg-resized.png)
***
_PC-FX is a 32-bit home video game console by NEC Home Electronics released in Japan on December 23, 1994._

***

| Emulator | Rom Folder | Extensions | BIOS | Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-beetle-pcfx](https://github.com/libretro/beetle-pcfx-libretro) | pcfx | .img .iso .ccd .cue | pcfx.rom | /opt/retropie/configs/pcfx/retroarch.cfg |

## Emulator: [lr-beetle-pcfx](https://github.com/libretro/beetle-pcfx-libretro)

**NOTE:** this emulator is experimental and suffers from slowness and sound shuttering. Probably won't be coming out of experimental any time soon. It can be installed from the experimental menu of the [RetroPie-Setup Script](Updating-RetroPie#using-the-retropie-setup-script).

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

[How do I calculate the md5sum or CRC32 of a BIOS file?](FAQ#how-do-i-calculate-the-md5sum-or-crc32-of-a-bios-file)

## Controls

lr-beetle-pcfx utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/pcfx/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

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

## Additional Documentation

[Mednafen PC-FX Documentation](https://mednafen.github.io/documentation/pcfx.html)
