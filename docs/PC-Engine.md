***
![pce](https://cloud.githubusercontent.com/assets/10035308/12213634/206dcb84-b639-11e5-8111-e0dfe0890107.png)
![tg16](https://cloud.githubusercontent.com/assets/10035308/12213633/206e0090-b639-11e5-9c39-3fada1f9b4f4.png)
***
_This console, known as the PC Engine in Japan and as the TurboGrafx-16 Entertainment SuperSystem in the USA, is a home video game console joint-developed by Hudson Soft and NEC, released in 1987._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-beetle-pce-fast](https://github.com/libretro/beetle-pce-fast-libretro) | pcengine  | .7z .ccd .chd .cue .pce .zip | syscard3.pce | /opt/retropie/configs/pcengine/retroarch.cfg |
| [lr-beetle-supergrafx](https://github.com/libretro/beetle-supergrafx-libretro) | pcengine  | .7z .pce .zip | syscard3.pce | /opt/retropie/configs/pcengine/retroarch.cfg |

## Emulator: [lr-beetle-pce-fast](https://github.com/libretro/beetle-pce-fast-libretro), [lr-beetle-supergrafx](https://github.com/libretro/beetle-supergrafx-libretro)

## ROMS

Accepted File Extensions: **.7z .ccd .chd .cue .pce .zip**

Place your PC Engine/PC Engine CD/TurboGrafx-16/TurboGrafx-CD/SuperGrafx ROMs in
```
/home/pi/RetroPie/roms/pcengine
```

## CHD Archive Usage

lr-beetle-pce-fast has support for the CHD (V5) archive format.

This format will save space and allow you to keep your PC Engine CD/TurboGrafx-CD ROM folder tidy.

The following archive contains a MAME 0.205 version of CHDMAN and Windows batch files that can be used to quickly convert your PC Engine CD/TurboGrafx-CD games to CHD (V5): [Download](https://drive.google.com/file/d/0B-ElaPpvBHs5aUd0QUM3c05kY2c/view?usp=sharing)

## BIOS

**A BIOS file is only needed to play CD-based games.**

Several BIOS are supported, but **syscard3.pce** is the most compatible with games.

Recognized Name | No-Into Name | CRC32 | MD5 | Comment |
| :--: | :--: | :--: | :--: | :--: |
| syscard3.pce | [BIOS] Super CD-ROM System (Japan) (v3.0).pce | 6D9A73EF | 38179DF8F4AC870017DB21EBCBF53114 | This is the prefered BIOS for lr-beetle-pce-fast and should play most games. |
| syscard2.pce | [BIOS] CD-ROM System (Japan) (v2.1).pce | 283B74E0 | 3CDD6614A918616BFC41C862E889DD79 ||
| syscard2.pce | [BIOS] CD-ROM System (Japan) (v2.0).pce | 52520BC6 | 3A456F0ECCFF039EB5FF045F56EC1C3B ||
| syscard1.pce | [BIOS] CD-ROM System (Japan) (v1.0).pce | 3F9F95A4 | 2B7CCB3D86BAA18F6402C176F3065082 ||
| gexpress.pce | [BIOS] Games Express CD Card (Japan).pce | 51A12D90 | 6D2CB14FC3E1F65CEB135633D1694122 | Required to play four unlicensed games. |
| gexpress.pce | [BIOS] Games Express CD Card (Japan) (Alt).pce | 9D1E81B8 | CCF8590E2E7AC4A08BCC1D77EC168917 | Required to play four unlicensed games. |
| syscard3u.pce | [BIOS] TurboGrafx CD Super System Card (USA) (v3.0).pce | 2B5B75FE | 0754F903B52E3B3342202BDAFB13EFA5 | Most games work, but some Japan games will not. |
| syscard2u.pce | [BIOS] TurboGrafx CD System Card (USA) (v2.0).pce | FF2A5EC3 | 94279F315E8B52904F65AB3108542AFE ||

Place your BIOS in

```
/home/pi/RetroPie/BIOS
```

You can change which BIOS is used in the Quick Menu's Options.

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