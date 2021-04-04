***
![nes](https://cloud.githubusercontent.com/assets/10035308/12213379/4a0e517a-b634-11e5-98c4-91cc27549706.png)
***
_The Nintendo Entertainment System (NES) is an 8-bit home video game console that was released by Nintendo in 1985. This console officially ended the [video game crash of 1983-1984](https://en.wikipedia.org/wiki/Video_game_crash_of_1983)._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fceumm](https://github.com/libretro/libretro-fceumm) | nes  | .7z .fds .nes .zip | disksys.rom | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-nestopia](https://github.com/libretro/nestopia) | nes  | .7z .fds .nes .zip | disksys.rom | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-quicknes](https://github.com/libretro/QuickNES_Core) | nes  | .7z .nes .zip | none | /opt/retropie/configs/nes/retroarch.cfg |
| [lr-fbneo](https://github.com/libretro/FBNeo) | nes  | .7z .zip | fdsbios.zip (containing `disksys.rom`) | /opt/retropie/configs/nes/retroarch.cfg |

If you want Famicom Disk System as a separate system, see the wiki page [HERE](Famicom-Disk-System)

## Emulators: [lr-nestopia](https://github.com/libretro/nestopia), [lr-fceumm](https://github.com/libretro/libretro-fceumm), [lr-quicknes](https://github.com/libretro/QuickNES_Core), [lr-fbneo](https://github.com/libretro/FBNeo)

## ROMS

Accepted File Extensions: **.7z .fds .nes .zip** - make sure your roms have headers. Roms without headers will not work. If you want to use PAL roms, make sure they contain `(E)` or `(Europe)` in the filename, or else they may be run at the wrong speed.

Place your NES Roms in
```
/home/pi/RetroPie/roms/nes
```

**NOTE**: [lr-fbneo](lr-fbneo) expects the game roms to be in `.zip`/`.7z` archives named in a similar fashion to arcade romsets, so the filenames of the roms is important. Use a romset validation/building program like Clrmamepro or RomCenter to have the correct filenames, using the [FBNeo NES DAT file](https://github.com/libretro/FBNeo/blob/master/dats/FinalBurn%20Neo%20(ClrMame%20Pro%20XML%2C%20NES%20Games%20only).dat) file and a No-Intro NES ROM collection.

## BIOS

FDS games require the **disksys.rom** bios file. Place the BIOS in:

* `/home/pi/RetroPie/BIOS` for `lr-fceumm` and `lr-nestopia`
* `/home/pi/RetroPie/BIOS/fbneo` for `lr-fbneo`, zipped in a file named `fdsbios.zip`


| Filename | No-Intro name | MD5 | CRC32 | 
| :--: | :--: | :--: | :--: |
| disksys.rom | [BIOS] Family Computer Disk System (Japan) (Rev 1) | ca30b50f880eb660a320674ed365ef7a | 5e607dcf |

## Controls

All three emulators utilise Retroarch configurations. Add custom RetroArch controls to the retroarch.cfg file in

```shell
/opt/retropie/configs/nes/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nesdiagram](https://cloud.githubusercontent.com/assets/10035308/8245062/4f0c5b8e-15e6-11e5-9255-b920543518d6.png)

### Turbo Buttons for lr-fceumm

Change the **Core Option** for **Turbo Enable** to the player(s) you desire. You can also change the **Turbo Delay (in frames)** (default is **3**). See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

## Overscan

Overscan is the part of the game field that is typically hidden behind the margins of consumer CRTs. However, you may want to enaable it for some games if anything seems cropped.

### lr-fceumm

Change the **Core Option** for **Crop Overscan** to **disabled**. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

### lr-quicknes

Add this to your `/opt/retropie/configs/nes/retroarch.cfg` file. Make sure that this is placed **above** the `#include` line.

```
video_crop_overscan = false
```