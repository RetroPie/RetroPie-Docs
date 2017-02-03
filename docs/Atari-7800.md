***
![atari7800](https://cloud.githubusercontent.com/assets/10035308/12190354/dbcd3aaa-b584-11e5-9c4f-89d0d7adc783.png)
***
_The Atari 7800 was a video game console released by Atari in 1986._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-prosystem](https://github.com/libretro/prosystem-libretro) | atari7800  | .a78 .bin .zip| 7800 BIOS (U).rom | /opt/retropie/configs/atari7800/retroarch.cfg |

## Emulator: [lr-prosystem](https://github.com/libretro/prosystem-libretro)

## ROMS
Accepted File Extensions: **.a78 .bin**

Place your Atari ROMs in 
```
/home/pi/RetroPie/roms/atari7800
```

## BIOS 
This BIOS is optional if you want the Atari Logo at the beginning of games, otherwise you don't need it because the games work fine without it. The BIOS file name is **7800 BIOS (U).rom**

Place your Atari 7800 BIOS in
```
/home/pi/RetroPie/BIOS/
```
Note: if this BIOS is enabled, PAL ROMs will not work so use it accordingly.

## Controls

lr-prosystem utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/atari7800/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![atari7800diagram](https://cloud.githubusercontent.com/assets/10035308/8268732/d7b4236c-174a-11e5-8386-6fa948235267.png)