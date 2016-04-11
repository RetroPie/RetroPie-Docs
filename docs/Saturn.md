***
![saturn_long](https://cloud.githubusercontent.com/assets/10035308/12213706/78d47d62-b63a-11e5-9128-8ba89e6f8950.png)
***
_The Sega Saturn is a 32 bit 5th generation home video game console released by Sega in 1994. It has a total of 8 processors which makes it one of the more difficult consoles to emulate._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-Yabause](https://github.com/libretro/yabause) | saturn  | .bin .iso .mdf | saturn_bios.bin | /opt/retropie/configs/saturn/retroarch.cfg |

## Emulator: [lr-Yabause](https://github.com/libretro/yabause) (NOTE: EXPERIMENTAL!)

Yabause stands for: Yet Another Buggy And Uncomplete Sega Emulator. It stands by its name. Currently you need to install it from the setup script under experimental builds. a Raspberry Pi 2 is a must. Most if not all games have incredibly choppy sound, are extremely laggy, and quite frankly aren't yet quite playable without a lot of tweaking and a few prayers.

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
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![saturn](https://cloud.githubusercontent.com/assets/10035308/7449063/327bfb76-f1e9-11e4-9c58-4b38a3c1284d.png)

## Standalone

The standalone version runs faster but requires X, QT, etc. Even then, it manages 10FPS so probably not worth adding to the scripts. If you're curious, here's the basic instructions to get it installed:

sudo apt-get install xinit

sudo apt-get install qt4-dev-tools

sudo apt-get install build-essential libgl1-mesa-dev

make some directory, and go in it

git clone https://github.com/Yabause/yabause.git

cd yabause/yabause/src

cmake -DYAB_WANT_OPENGL=NO $SOURCES

make

go into a terminal on your pi itself

navigate to /your_directory/yabause/yabausesrc/qt

sudo xinit ./yabause