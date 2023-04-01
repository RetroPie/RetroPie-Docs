***
![fds_header](https://cloud.githubusercontent.com/assets/10035308/23090452/7af681b8-f553-11e6-8da8-73f7815941c7.png)
***
The Family Computer Disk System a.k.a. Famicom Disk System was released in Japan in 1986. It is an add-on to the Famicom and used floppy disks.
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fceumm](https://github.com/libretro/libretro-fceumm) | fds  | .7z .fds .nes .zip | disksys.rom | /opt/retropie/configs/fds/retroarch.cfg |
| [lr-nestopia](https://github.com/libretro/nestopia) | fds  | .7z .fds .nes .zip | disksys.rom | /opt/retropie/configs/fds/retroarch.cfg |
| [lr-fbneo](https://github.com/libretro/fbneo) | fds  | .7z .zip | fdsbios.zip (containing `disksys.rom`) | /opt/retropie/configs/fds/retroarch.cfg |

## Emulators: [lr-nestopia](https://github.com/libretro/nestopia), [lr-fceumm](https://github.com/libretro/libretro-fceumm), [lr-fbneo](https://github.com/libretro/FBNeo)

## ROMS

Accepted File Extensions: **.7z .fds .nes .zip**

Place your FDS Roms in
```
/home/pi/RetroPie/roms/fds
```
**NOTE**: [lr-fbneo](lr-fbneo) expects the game roms to be in `.zip`/`.7z` archives named in a similar fashion to arcade romsets, so the filenames of the roms is important. Use a romset validation/building program like Clrmamepro or RomCenter to have the correct filenames, with the [FBNeo FDS DAT file](https://github.com/libretro/FBNeo/blob/master/dats/FinalBurn%20Neo%20(ClrMame%20Pro%20XML%2C%20FDS%20Games%20only).dat) file and a No-Intro NES ROM collection to get the correct ROMset.

## BIOS

FDS games require the **disksys.rom** bios file. Place the BIOS in:

* `/home/pi/RetroPie/BIOS` for `lr-fceumm` and `lr-nestopia`
* `/home/pi/RetroPie/BIOS` for `lr-fneo`, zipped in a file named `fdsbios.zip`

| Filename | No-Intro name | MD5 | CRC32 | 
| :--: | :--: | :--: | :--: |
| disksys.rom | [BIOS] Family Computer Disk System (Japan) (Rev 1) | ca30b50f880eb660a320674ed365ef7a | 5e607dcf |

## Controls

Both emulators utilise RetroArch configurations.

*Side Note*: In order to "switch to side B" of a ROM most controllers have this set to a default of the upper right bumper or right trigger button

*Side Note*: Games that display **Ｂメンヲセットシテクダサ** are asking for the disk to be flipped to side B in order to continue. It is common for a game to display a title screen that asks for side B before the game can start.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/fds/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nesdiagram](https://cloud.githubusercontent.com/assets/10035308/8245062/4f0c5b8e-15e6-11e5-9255-b920543518d6.png)
