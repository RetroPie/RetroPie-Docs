![](https://4.bp.blogspot.com/-KubMHEPz1Uk/VMJdFy57fTI/AAAAAAAAAEQ/xJFFjQsQZAY/s1600/wolf3d.png)

***

_Wolfenstein 3D is a first-person shooter video game developed by id Software and published by Apogee Software in 1992 for the PC operating system DOS._

***


## Port: [Wolf4SDL](https://github.com/mozzwald/wolf4sdl)

Wolf4SDL can be installed from the experimental menu of the RetroPie setup script. By default, shareware version 1.4 of Wolfenstein 3D will be installed.

## Playing Full Version of Wolfenstein 3D

To play the full version of Wolfenstein 3D with Wolf4SDL, you need to provide your own game data which can purchased from [Steam](http://store.steampowered.com/app/2270) or [3D Realms](https://3drealms.com/catalog/wolfenstein-3d_25/).

The game data required are the files with *.wl6 extension (see below for list). Place them in 

> /home/pi//RetroPie/roms/ports/wolf3d

The file names must be in lower case. The simplest way to do this is to run the following commands:

    cd RetroPie/roms/ports/wolf3d
    rename 'y/A-Z/a-z/' *

Wolf4SDL creates separate binaries for each version of game data. You need to select the correct binary for your game data. 

Launch Wolfenstein 3D script from the Ports section of EmulationStation. Bring up the [runcommand menu](https://github.com/RetroPie/RetroPie-Setup/wiki/runcommand) by pressing any key or js0 on your gamepad. Now select from the menu
> 2 - Select emulator for rom ().

You will be presented with the following screen:

![](https://a123516c-a-62cb3a1a-s-sites.googlegroups.com/site/dosonthepi/wolf4sdl-rom-selection.png?attachauth=ANoY7cosBgHONtrzOQX3viZ--s0TrNsppucBOMmm7TIzEKVT4cPhJnTaLy0RO_FiuUbnGnUjfdsXiLg01-LDLslLMQl-ODbePEOKALnniWFphrKcBHW_I6zxQqMoDkfxoQ3psCobXd8i6HtRscADiMm2bNAQ3qgpHnXRJCLNk4StHxLglEnFkNu4FGpZ_oHPWZwCCCMwNDZmydodoIsa-orPPmwJU2B-kFClF1DQsmCNtWcAqUAC2Kg%3D&attredirects=0)

The default is **wolf4sdl-sw-v14**, the shareware 1.4 version.

If you have the **3D Realms** version, then select the **wolf4sdl-3dr-v14** binary.

If you have the **Steam** version, the select the **wolf4sdl-gt-v14** binary.

If you would like to play **Spear of Destiny**, then select **wolf4sdl-spear-v14**.

Once you have made your selection, exit the menu and then launch rom from the runcommand menu.

## Troubleshooting

If you are getting NO WOLFENSTEIN 3-D DATA FILES to be found! or NUMCHUNKS errors or you are not sure which version of game data you have, then check your game data by finding the md5 checksums. To do this, once you have placed your game data in the rom folder and made sure the file names are lower case, run the following commands:

	cd RetroPie/roms/ports/wolf3d
	md5sum *.wl6

The md5 checksums for supported game data are as follow:

**3D Realms (Apogee 1.4)**

	a41af25a2f193e7d4afbcc4301b3d1ce  audiohed.wl6
	2385b488b18f8721633e5b2bdf054853  audiot.wl6
	aa75133df873b660d2058425ca8539b3  config.wl6
	a4e73706e100dc0cadfb02d23de46481  gamemaps.wl6
	b8d2a78bc7c50da7ec9ab1d94f7975e1  maphead.wl6
	adb10b0d6fdddba9fcc3d1a7c16937e7  vgadict.wl6
	4e96d7b4e89a5b3a4beeebf5d7d87eb7  vgagraph.wl6
	a08905e2b0d299b3fad259f90c0efb1a  vgahead.wl6
	a6d901dfb455dfac96db5e4705837cdb  vswap.wl6

**Steam (GT/ID/Activision)**

	a41af25a2f193e7d4afbcc4301b3d1ce  audiohed.wl6
	2385b488b18f8721633e5b2bdf054853  audiot.wl6
	aa75133df873b660d2058425ca8539b3  config.wl6
	a4e73706e100dc0cadfb02d23de46481  gamemaps.wl6
	b8d2a78bc7c50da7ec9ab1d94f7975e1  maphead.wl6
	dec8939cff5a4ec27ae7b43e8f52ec28  vgadict.wl6
	8b40b5b785f898e229bf1c2f2e3ee003  vgagraph.wl6
	8e75e3ffb842ed3d08abe6ffea97b231  vgahead.wl6
	b8ff4997461bafa5ef2a94c11f9de001  vswap.wl6

Check also that you have all of the files above.

If you have game data that do not match the md5sums above, then please post at the [RetroPie Forum](http://blog.petrockblock.com/forums/forum/retropie-project-forum/emulators/).