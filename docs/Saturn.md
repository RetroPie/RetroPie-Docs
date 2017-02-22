***
![saturn_long](https://cloud.githubusercontent.com/assets/10035308/12213706/78d47d62-b63a-11e5-9128-8ba89e6f8950.png)
***
_The Sega Saturn is a 32 bit 5th generation home video game console released by Sega in 1994. It has a total of 8 processors which makes it one of the most difficult consoles to emulate._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-Yabause](https://github.com/libretro/yabause) | saturn  | .bin .cue .iso .mdf | saturn_bios.bin | /opt/retropie/configs/saturn/retroarch.cfg |
|[lr-beetle-saturn](https://github.com/libretro/beetle-saturn-libretro)| saturn | .bin .cue .iso .mdf | sega_101.bin | /opt/retropie/configs/saturn/retroarch.cfg

## Emulators: [lr-Yabause](https://github.com/libretro/yabause), [lr-beetle-saturn](https://github.com/libretro/beetle-saturn-libretro)

Yabause stands for: Yet Another Buggy And Uncomplete Sega Emulator. It stands by its name. Currently you need to install it from the setup script under experimental builds. Any Raspberry Pi model will achieve only 1-2 frames-per-second, rendering it unplayable on those systems. **Saturn is really only recommended for use on a PC and even then emulation is less than perfect.**

## ROMS

Accepted File Extensions: **.cue .bin .iso .mdf**

Place your Sega Saturn ROMs in 
```
/home/pi/RetroPie/roms/saturn
```

### Why don't my .bin or .iso files show up?

RetroPie is configured to only show .cue files in EmulationStation so that you do not have two copies showing up of all your games.  

A .cue file is basically a plain text file that tells the emulator where in the .bin file the (data and/or audio) track(s) are. This is often important in the case where multiple audio files are in the single .bin file. These are often called "mixed mode" discs. [Wikipedia .cue files](https://en.wikipedia.org/wiki/Cue_sheet_(computing))
  
If you only have a .bin file and no .cue file, you can generate it:
-  [Manually](http://www.shivaranjan.com/2007/01/03/how-to-create-cue-file-for-a-bin-file-in-5-steps/)  
-  [Individually](http://www.dslreports.com/r0/download/373724~1e45059000cfc371c157f544cc5aef07/MakeCue.zip)
-  [En masse or individually](https://github.com/thorst/CueMaker)  

a few more notes on cue sheets [HERE](https://github.com/libretro/beetle-saturn-libretro#loading-isos)

## BIOS

The BIOS file needed for lr-yabause is **saturn_bios.bin** or for lr-beetle-saturn **sega_101.bin**

Place your BIOS in

```
/home/pi/RetroPie/roms/saturn
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