***
![pce](https://cloud.githubusercontent.com/assets/10035308/12213634/206dcb84-b639-11e5-8111-e0dfe0890107.png)
![tg16](https://cloud.githubusercontent.com/assets/10035308/12213633/206e0090-b639-11e5-9c39-3fada1f9b4f4.png)
***
_The TurboGrafx-16 Entertainment SuperSystem, originally known in Japan as the PC Engine, is a home video game console joint-developed by Hudson Soft and NEC, released in 1987._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-mednafen-pce-fast](https://github.com/libretro/beetle-pce-fast-libretro) | pcengine  | .pce | syscard3.pce | /opt/retropie/configs/pcengine/retroarch.cfg |
| [lr-beetle-supergrafx](https://github.com/libretro/beetle-supergrafx-libretro) | pcengine  | .pce | syscard3.pce | /opt/retropie/configs/pcengine/retroarch.cfg |

## Emulator: [lr-mednafen-pce-fast](https://github.com/libretro/beetle-pce-fast-libretro), [lr-beetle-supergrafx](https://github.com/libretro/beetle-supergrafx-libretro)

## ROMS
Accepted File Extensions: **.pce**

Place your PC Engine/ TurboGrafx-16 ROMs in
```
/home/pi/RetroPie/roms/pcengine
```

## BIOS

The BIOS file necessary is called: **syscard3.pce** 

Place your the syscard3.pce file in 
```
/home/pi/RetroPie/BIOS
```

## Controls

lr-mednafen-pce-fast utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/pcengine/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![nec_turbografx16_diagram](https://cloud.githubusercontent.com/assets/10035308/10822284/1bde9cc4-7e1c-11e5-9683-c29b5a5a49e8.png)

### Advanced Configuration:

If you are from the United States, it is likely that you had the TurboGrafx-16 rather than the PC Engine. If you want EmulationStation to show the TurboGrafx-16 logo instead of PC Engine, then you can change the file in `/etc/emulationstation/es_systems.cfg`

from 

```
  <system>
    <name>pcengine</name>
    <fullname>TurboGrafx 16 (PC Engine)</fullname>
    <path>/home/pi/RetroPie/roms/pcengine</path>
    <extension>.pce .cue .zip .PCE .CUE .ZIP</extension>
    <command>/opt/retropie/supplementary/runcommand/runcommand.sh 0 _SYS_ pcengine %ROM%</command>
    <platform>pcengine</platform>
    <theme>pcengine</theme>
    <directlaunch/>
  </system>
```

to

```
  <system>
    <name>pcengine</name>
    <fullname>TurboGrafx 16 (PC Engine)</fullname>
    <path>/home/pi/RetroPie/roms/pcengine</path>
    <extension>.pce .cue .zip .PCE .CUE .ZIP</extension>
    <command>/opt/retropie/supplementary/runcommand/runcommand.sh 0 _SYS_ pcengine %ROM%</command>
    <platform>pcengine</platform>
    <theme>tg16</theme>
    <directlaunch/>
  </system>
```