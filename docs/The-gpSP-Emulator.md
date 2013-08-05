## BIOS file

The gpSP emulator needs a GBA BIOS file `gba_bios.bin` in the directory of the gpsp binary. The RetroPie SD-card image, e.g., has the gpsp binary located in `/home/pi/RetroPie/emulators/gpsp/raspberry/`. Copy your GBA BIOS file into this directory.

## Controller Setup

From [here](https://github.com/petrockblog/RetroPie-Setup/issues/193#issuecomment-19900909):

It appears that gpsp is not run via libretro thus its not configured like the rest of RetroArch. My solution was to run gpsp from command line with no arguments (sudo ./~/RetroPie/emulators/gpsp/raspberrypi/gpsp ) and configure my buttons through the onscreen menu there. This generated a gpsp.cfg file (binary).

## Games are not working/White Screen

GPSP uses a File called game_config.txt.

> What is this file??? game_config.txt is a database of settings on a
per-game basis. A couple of the settings are required to make games
work at all, but most of them are there to improve the performance of
a game. If a game doesn't work then look through the settings here,
but keep in mind that this file can not be used to fix a majority of
games, the ones that don't work because of emulator bugs. For those
you'll have to wait for a new release and hope it someday gets fixed.

This file is in the wrong folder on RetroPie. It is in `./~/RetroPie/emulators/gpsp/game_config.txt` but it needs to be in `./~/RetroPie/emulators/gpsp/raspberry/game_config.txt`. You need to fix this, otherwise you will get problems with some games/roms.