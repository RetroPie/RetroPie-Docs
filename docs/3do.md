***

![3do right](https://cloud.githubusercontent.com/assets/10035308/12186059/8d7ec76a-b55c-11e5-9231-b0c561de271c.png)

***
_The Panasonic 3do Real Multiplayer was a Home Video Game Console developed by the 3do company in 1994. Its humongous price tag of $700 and oversaturation in the video game market at the time meant it was a commercial failure._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-opera](https://github.com/libretro/opera-libretro) | 3do  | .chd .cue .iso .zip | panafz10.bin | /opt/retropie/configs/3do/retroarch.cfg |

## Emulator: [lr-opera](https://github.com/libretro/opera-libretro) (formerly known as `lr-4do`).

**lr-opera** is experimental. However some games will run at playable speeds on the pi4.

With the Odroid-XU4, performance has increased and made many games playable as of July 2018 when development was taken over by a newer developer. CPU threading being added for the CPU/GPU found in the XU4 continues to increase performance as of September 2018.

## ROMS
Accepted File Extensions: **.iso** **.bin/cue** **.chd** **.zip**

Place your 3do ROMs in
```
/home/pi/RetroPie/roms/3do
```
## BIOS

One of several BIOS ROMs must be placed in `/home/pi/RetroPie/BIOS`. The _norsa_ versions have the RSA encryption check disabled which should allow unsigned software to run.

| Filename                  | Hash (MD5)                       |
| ------------------------- | -------------------------------- |
| panafz1.bin               | f47264dd47fe30f73ab3c010015c155b |
| panafz1j.bin              | a496cfdded3da562759be3561317b605 |
| panafz1j-norsa.bin        | f6c71de7470d16abe4f71b1444883dc8 |
| panafz10.bin              | 51f2f43ae2f3508a14d9f56597e2d3ce |
| panafz10-norsa.bin        | 1477bda80dc33731a65468c1f5bcbee9 |
| panafz10e-anvil.bin       | a48e6746bd7edec0f40cff078f0bb19f |
| panafz10e-anvil-norsa.bin | cf11bbb5a16d7af9875cca9de9a15e09 |
| goldstar.bin              | 8639fd5e549bd6238cfee79e3e749114 |
| sanyotry.bin              | 35fa1a1ebaaeea286dc5cd15487c13ea |
| 3do_arcade_saot.bin       | 8970fc987ab89a7f64da9f8a8c4333ff |

For certain Japanese games a second "Kanji" ROM is necessary.

| Filename                   | Hash (MD5)                       |
| -------------------------- | -------------------------------- |
| panafz1-kanji.bin          | b8dc97f778a6245c58e064b0312e8281 |
| panafz1j-kanji.bin         | c23fb5d5e6bb1c240d02cf968972be37 |
| panafz10ja-anvil-kanji.bin | 428577250f43edc902ea239c50d2240d |


## Controls

lr-opera utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/3do/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![goldstar_3do_diagram](https://cloud.githubusercontent.com/assets/10035308/16599643/7f450bd6-42c0-11e6-84d7-9cc0944e7b01.png)
