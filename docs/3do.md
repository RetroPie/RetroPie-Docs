***

![3do right](https://cloud.githubusercontent.com/assets/10035308/12186059/8d7ec76a-b55c-11e5-9231-b0c561de271c.png)

***
_The Panasonic 3do Real Multiplayer was a Home Video Game Console developed by the 3do company in 1994. Its humongous price tag of $700 and oversaturation in the video game market at the time meant it was a commercial failure._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-4do](https://github.com/libretro/4do-libretro) | 3do  | .iso .cue | panafz10.bin | /opt/retropie/configs/3do/retroarch.cfg |

## Emulator: [lr-4do](https://github.com/libretro/4do-libretro)

**lr-4do** is experimental, and even with an overclocked RPi3B+ it is slow so it isn't recommended for Raspberry Pi users at this time.

With the Odroid-XU4, performance has increased and made many games playable as of July 2018 when development was taken over by a newer developer. CPU threading being added for the CPU/GPU found in the XU4 continues to increase performance as of September 2018.

## ROMS
Accepted File Extensions: **.iso** **.bin/cue**

Place your 3do ROMs in
```
/home/pi/RetroPie/roms/3do
```
## BIOS

The file needed is **panafz10.bin**

Place your panafz10.bin BIOS file in
```
/home/pi/RetroPie/BIOS
```
## Controls

lr-4do utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/3do/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![goldstar_3do_diagram](https://cloud.githubusercontent.com/assets/10035308/16599643/7f450bd6-42c0-11e6-84d7-9cc0944e7b01.png)