***
![pce](https://cloud.githubusercontent.com/assets/10035308/12213634/206dcb84-b639-11e5-8111-e0dfe0890107.png)
![tg16](https://cloud.githubusercontent.com/assets/10035308/12213633/206e0090-b639-11e5-9c39-3fada1f9b4f4.png)
***
_The TurboGrafx-16 Entertainment SuperSystem, originally known in Japan as the PC Engine, is a home video game console joint-developed by Hudson Soft and NEC, released in 1987._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-beetle-pce-fast](https://github.com/libretro/beetle-pce-fast-libretro) | pcengine  | .7z .ccd .chd .cue .pce .zip | syscard3.pce | /opt/retropie/configs/pcengine/retroarch.cfg |
| [lr-beetle-supergrafx](https://github.com/libretro/beetle-supergrafx-libretro) | pcengine  | .7z .pce .zip | syscard3.pce | /opt/retropie/configs/pcengine/retroarch.cfg |

## Emulator: [lr-beetle-pce-fast](https://github.com/libretro/beetle-pce-fast-libretro), [lr-beetle-supergrafx](https://github.com/libretro/beetle-supergrafx-libretro)

## ROMS

Accepted File Extensions: **.7z .ccd .chd .cue .pce .zip**

Place your PC Engine/ TurboGrafx-16 ROMs in
```
/home/pi/RetroPie/roms/pcengine
```

## BIOS

**The BIOS file is only needed to play CD-based games.**

The BIOS file must be named: **syscard3.pce** 

Place your syscard3.pce file in

```
/home/pi/RetroPie/BIOS
```

Working BIOS files:

| Filename | md5sum | CRC32 | Comment |
| :--: | :--: | :--: | :--: |
| Super CD-ROM System (Japan) (v3.0).pce | 38179df8f4ac870017db21ebcbf53114 | 6d9a73ef | This is the prefered BIOS for lr-beetle-pce-fast and should play all games. |
| TurboGrafx CD Super System Card (USA) (v3.0).pce | 0754f903b52e3b3342202bdafb13efa5 | 2b5b75fe | Most games work, but some Japan games will not. |

## Controls

lr-beetle-pce-fast and lr-beetle-supergrafx utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/pcengine/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nec_turbografx16_diagram](https://cloud.githubusercontent.com/assets/10035308/10822284/1bde9cc4-7e1c-11e5-9683-c29b5a5a49e8.png)

## PC Engine CD

It is important that the image file (usually `.bin`) and the CUE file (`.cue`) match.

CUE files are just text files containing a description of the CD. If you have files named like:

~~~
Akumajou Dracula X.bin
Akumajou Dracula X.cue
~~~

then ensure the first line of the CUE file contains:

~~~
FILE "Akumajou Dracula X.bin" BINARY
~~~

Any of the following are wrong and will not work:

~~~
### extension has incorrect case
FILE "Akumajou Dracula X.BIN" BINARY

### file name has incorrect case
FILE "AKUMAJOU DRACULA X.bin" BINARY

### does not match the actual file name
FILE "Akumajou_Dracula_X_-_Chi_no_Rinne_(NTSC-J)_[KMCD3005].bin" BINARY
~~~

## Advanced Configuration

### Switching Emulation Station to the TurboGrafx-16 logo:

If you are from the United States it is likely that you had the TurboGrafx-16 rather than the PC Engine. If you want EmulationStation to show the TurboGrafx-16 graphics instead of PC Engine then you should create a file /opt/retropie/configs/all/platforms.cfg with the following contents (note this requires at least v4.1.6 of the RetroPie-Setup script).

```
pcengine_theme="tg16"
```

Once this is done, please update any of the currently installed PC Engine emulators from RetroPie-Setup and Emulation Station will now use the TurboGrafx-16 logo.