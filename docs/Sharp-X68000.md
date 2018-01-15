***
![x68000](https://user-images.githubusercontent.com/22881403/29473948-549047ec-841f-11e7-9828-4160b39733be.png)
***
_The Sharp X68000 was a Japan-only home computer released in 1987._
***

| Emulator | Rom Folder | Extension | BIOS Files | Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-px68k](https://github.com/libretro/px68k-libretro/) | x68000 | .dim, .m3u | iplrom30.dat, iplromco.dat, iplrom.dat,  iplromxv.dat, cgrom.dat | /opt/retropie/configs/x68000/retroarch.cfg |

## Emulator: [lr-px68k](https://github.com/libretro/px68k-libretro/)
This emulator must be installed from the experimental section in RetroPie Setup.

Currently, MIDI/sound module capabilities are not supported in the emulator.

## ROMS

Accepted File Extensions: **.dim** 

Place your X68000 ROMs in:
```
/home/pi/RetroPie/roms/x68000
```

## BIOS

lr-px68k only requires a single BIOS file (out of a selection of four) and a font file.  Below is a list of all the BIOS files to choose from, plus the required font file:

| BIOS File | CRC-32 | File type |
| :---: | :---: | :---: |
| iplrom.dat | 72BDF532 | BIOS file |
| iplrom30.dat | E8F8FDAD | BIOS file |
| iplromco.dat | 6C7EF608 | BIOS file |
| iplromxv.dat | 00EEB408 | BIOS file |
| cgrom.dat | 9F3195F1 | Font file |

Place your BIOS files in:
```
/home/pi/RetroPie/BIOS/keropi
```

## Controls

lr-px68k utilises Retroarch configurations.

Add custom retroarch controls to the retroarch.cfg file in:

```
/opt/retropie/configs/x68000/retroarch.cfg
```

For more information on custom RetroArch controls, see: [RetroArch Configuration](RetroArch-Configuration)

## Swapping Disks
By default, when loaded through a .m3u file, lr-px68k places the first disk listed in Drive 0, and the second disk listed in Drive 1.

To swap either drive, press F12 to access the PX68k menu, then select your drive.  You'll then need to navigate to /home/pi/RetroPie/roms/x68000 and select the disk you want to use.