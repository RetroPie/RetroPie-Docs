**Please check https://github.com/petrockblog/RetroPie-Setup/wiki/MAME for for basic information about controls and managing ROMs - this page is for specific information about the mame2003 emulator's features.**

lr-mame2003 is a popular choice for the Raspberry Pi 2 and up, as it combines a large romset (MAME 0.78) playing host to most 2D-era arcade games that people would be interested in, and a broad set of features. It also is still a relatively old MAME core, which is actually a good thing for lower-end hardware such as the Raspberry Pis, as later MAME cores feature increasingly accurate emulation which requires greater CPU power.

## MAME menu

To access the MAME internal menu, press the 'TAB' key.

Whilst lr-mame20003 is a libretro emulator and benefits from automatic controller configuration, sometimes you may still want to rebind how it internally deals with inputs. For example, the default control setup might make sense in one game, but in another they don't. In which case, you can use the 'Input (this game)' option to rebind keys for a single game, generating a .cfg file in:
```
/home/pi/RetroPie/roms/mame-libretro/mame2003/config
```
If you rebind global inputs ('Input (general)'), it will update a file in the same directory called 'default.cfg'.

These files are not human-readable, but can be safely deleted if you get into a mess and wish to return to the default configuration.

## Service menu

To access the MAME service, press the 'F2' key.

lr-mame2003 has the useful ability to access games' internal service menus to set permanent game options. This allows you to, for example, configure a game to be 'free play' (no need to insert coins). After changing options in the service mode, the games internal memory will be stored to an .nv file in:
```
/home/pi/RetroPie/roms/mame-libretro/mame2003/nvram
```

## High scores

lr-mame2003 will attempt to keep a permanent record of any high scores you set, but some games will not save these by default. There is a supplementary file that you can transfer to your Pi that will enable high score saving for more games called 'hiscore.dat'. This file can be downloaded from http://highscore.mameworld.info/, and should be placed in:
```
/home/pi/RetroPie/roms/mame-libretro/mame2003/hsdb
```
When high scores are saved, they are kept in:
```
/home/pi/RetroPie/roms/mame-libretro/mame2003/hs
```

## Samples

Some sound effects in a few older (typically pre-1986) arcade games are difficult/impossible to emulate. Instead, audio clips of these effects can be downloaded and automatically played at the appropriate times. To do this, download all the zip files available at http://www.progettosnaps.net/samples/ and place them into:
```
/home/pi/RetroPie/BIOS/mame2003/sample
```

## Nag-screen

The copyright warning should be hidden by default, but can be controlled via a setting in the retroarch-core-options.cfg file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
mame2003-skip_disclaimer = enabled
```

## Feature requests

Please use the [forum](https://retropie.org.uk/forum) for all support issues, but feature requests can be made on the [GitHub page](https://github.com/dankcushions/mame2003-libretro).