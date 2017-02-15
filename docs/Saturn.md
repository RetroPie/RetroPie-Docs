***
![saturn_long](https://cloud.githubusercontent.com/assets/10035308/12213706/78d47d62-b63a-11e5-9128-8ba89e6f8950.png)
***
_The Sega Saturn is a 32 bit 5th generation home video game console released by Sega in 1994. It has a total of 8 processors which makes it one of the most difficult consoles to emulate._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-Yabause](https://github.com/libretro/yabause) | saturn  | .bin .iso .mdf | saturn_bios.bin | /opt/retropie/configs/saturn/retroarch.cfg |

## Emulator: [lr-Yabause](https://github.com/libretro/yabause)

Yabause stands for: Yet Another Buggy And Uncomplete Sega Emulator. It stands by its name. Currently you need to install it from the setup script under experimental builds. Any Raspberry Pi model will achieve only 1-2 frames-per-second, rendering it unplayable on those systems.

## ROMS

Accepted File Extensions: **.bin .iso .mdf**

Place your Sega Saturn ROMs in 
```
/home/pi/RetroPie/roms/saturn
```

## BIOS

The BIOS file needed is **saturn_bios.bin**

Place your BIOS in
```
/home/pi/RetroPie/BIOS
```

## Controls

lr-yabause utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/saturn/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![sega_saturn_diagram](https://cloud.githubusercontent.com/assets/10035308/16599639/7f42ac24-42c0-11e6-8978-5f3cce723393.png)

## Standalone

The standalone version runs faster but requires X, QT, etc. Even then, it manages 10FPS so probably not worth adding to the scripts. If you're curious, here's the basic instructions to get it installed:
```
sudo apt-get update
sudo apt-get install xinit qt4-dev-tools build-essential libgl1-mesa-dev
```
make some directory, and go in it

```
mkdir tempdev
cd tempdev
```

```
git clone https://github.com/Yabause/yabause.git

cd yabause/yabause/src

cmake -DYAB_WANT_OPENGL=NO $SOURCES

make
```

go into a terminal on your pi itself

navigate to /your_directory/yabause/yabausesrc/qt

```
sudo xinit ./yabause
```