
***
![](http://www.progettosnaps.net/mess/index_files/projectMESS.png)

***
_MESS (Multi Emulator Super System) is a system that emulates a vast quantity of obscure hardware. It was merged with MAME in version .162._
***

### Emulator: [lr-mess](https://github.com/libretro/MAME.git)

### ROMS:

Using lr-mess in the way I am telling you here will only work with MAME Software List ROMs matching the version of MAME you are compiling. Any other set of ROMs will not work. A good guideline for avoiding bad ROMs: If you are downloading them through HTTP from a public ROM site, they are not likely to work. The ROMs cannot be unzipped or renamed.

For more information on types of romsets see [HERE](https://www.reddit.com/r/MAME/comments/3wf6f0/question_what_is_the_difference_among_mame_roms/cxvt6av)

### System support 

At this point, the lr-mess script will automatically set up lr-mess for you only for systems that are known to run well on a Pi 2 with an overclock. If the system is not listed in the lr-mess script, it either has not been tested or has been tested and ran at a bad speed.

Systems that have been tested and run well with lr-mess so far:

* Colecovision (100% speed, driver: coleco)
* CreatiVision (80-100% speed, driver: crvision, not added to the script yet)
* Emerson Arcadia 2001 (100% speed, driver: arcadia)
* Nintendo Entertainment System (100% speed, driver: nes)
* Nintendo Gameboy (100% speed, driver: gameboy)
* Sega Dreamcast VMU (100% speed, driver: svmu)

Systems that have been tested and don’t run as well with lr-mess so far:

* Amstrad GX4000 (65% speed, some games still feel very playable, driver: gx4000)
* Atari 2600 (70-85% speed, driver: a2600)
* Atari 5200 (50-60% speed, driver: a5200)
* BBC Micro B (25% speed, driver: bbcb)
* Intellivision (Fails to find/load saa5050 ROM, driver: intv)
* Nintendo Gameboy Advance (50% speed, driver: gba
* Sega Game Gear (80% speed, driver: gamegear)
* Sega Genesis (46% speed, driver: megadriv)
* Sharp X68000 (14% speed, driver: x68000)
* SNK Neo Geo AES (60-65% speed, driver: aes)

All systems other than those listed above have not been tested.

### Instructions

Run the `lr-mess` script from the experimental menu. Compile should take about 3 hours on a Pi 2.

Check your BIOS folder after compilation and see if a folder named "mame" exists. Within it should be a folder named "hash" that includes a bunch of xml files. These are the software lists that lr-mess requires. If they exist, we likely compiled properly.

Go to your roms directory, wherever you have it (default: `/home/pi/RetroPie/roms/`) and create a directory named after the driver you wish to use. Place the BIOS file for that driver in the root of your roms directory.

For example, if you wanted to run the Donkey Kong Colecovision rom (dkong.zip) through lr-mess, you would place your files like this:
````
Main rom directory (/home/pi/RetroPie/roms)
|
+- Coleco Driver BIOS zip: coleco.zip (/home/pi/RetroPie/roms/coleco.zip)
|
+- coleco (/home/pi/RetroPie/roms/coleco)
|
+- dkong.zip (/home/pi/RetroPie/roms/coleco/dkong.zip)
````

If the driver you wish to use does not require a ROM, you do not need to put one into your roms directory.

Check `/opt/retropie/configs/all/retroarch-core-options.cfg` and make sure that MAME CLI launching, MAME software lists and MAME auto media type are turned on. The compilation script should set these by default at the bottom of the file, but just make sure.

You may need to add .zip and .ZIP to your extensions in `/etc/emulationstation/es_systems.cfg` and restart emulationstation for it to pick up your ROMs.

If all goes well, you should get the game running when you select it from emulationstation. If it quits back to emulationstation immediately, you likely have bad ROMs or something else unexpected happened.