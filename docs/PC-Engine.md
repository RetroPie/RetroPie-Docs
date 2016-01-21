***
![pce](https://cloud.githubusercontent.com/assets/10035308/12213634/206dcb84-b639-11e5-8111-e0dfe0890107.png)
![tg16](https://cloud.githubusercontent.com/assets/10035308/12213633/206e0090-b639-11e5-9c39-3fada1f9b4f4.png)
***
_The TurboGrafx-16 Entertainment SuperSystem, originally known in Japan as the PC Engine, is a home video game console joint-developed by Hudson Soft and NEC, released in 1987._
***
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
Note: The 'SYSCARD3.PCE' needs to be placed in with the ROM files to play Turbo CD games.

## Editing instructions for PCE CD games before adding to rom folder

The bin/cue or iso/cue is case sensitive and only needs the name of the game without the country of origin info, no underscores or dashes etc. Just the name. Example: Vasteel.iso and Vasteel.cue or Motoroader MC.bin and Motoroader MC.cue. Extensions must be all lower case (.bin,.cue, .iso)

Edit the .cue file with a text editor. Match the name to the iso or bin. It's in the first line. Case sensitive and again, the extension needs to be all lower case.

Place bios file in both roms and bios folder. Make sure the name of the bios file is all lower case. syscard3.pce

Place edited bin/cue or iso/cue files in the rom folder

## Controls

lr-mednafen-pce-fast utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/pcengine/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![nec_turbografx16_diagram](https://cloud.githubusercontent.com/assets/10035308/10822284/1bde9cc4-7e1c-11e5-9683-c29b5a5a49e8.png)