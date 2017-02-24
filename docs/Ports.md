***
![ports](https://cloud.githubusercontent.com/assets/10035308/12213893/ee2ca4a0-b63e-11e5-8d01-03c9dce2ab11.png)
***


Current software ported to RetroPie:

* [Baldur's Gate](GemRB) [(GemRB)](https://github.com/gemrb/gemrb) (EXPERIMENTAL)
* [Cave Story](Cave-Story) [(nxengine-libretro)](https://github.com/libretro/nxengine-libretro)
* [Descent](Descent) [(DXX-Rebirth)](http://www.dxx-rebirth.com/) 
* [DOOM](Doom) [(lr-prboom)](https://github.com/libretro/libretro-prboom), [(ZDOOM)](https://github.com/rheit/zdoom)
* [Duke Nukem 3D](Duke-Nukem-3D) [(Eduke32)](http://www.eduke32.com/)
* [Löve](Love) [(Löve)](https://bitbucket.org/rude/love/src)
* [KODI](KODI)
* [Minecraft Pi Edition](Minecraft) (EXPERIMENTAL)
* [OpenBOR](OpenBOR) [(OpenBOR)](https://github.com/rofl0r/openbor.git) (EXPERIMENTAL)
* [OpenTTD](OpenTTD) (EXPERIMENTAL)
* [OpenTyrian](OpenTyrian) [(OpenTyrian)](https://bitbucket.org/opentyrian/opentyrian/wiki/Home)
* [OutRun Engine](Cannonball) [(Cannonball)](https://github.com/djyt/cannonball/wiki/Cannonball-Manual)
* [Quake Series](Quake) [(lr-tyrquake)](https://github.com/libretro/tyrquake), [(Tyrquake)](https://github.com/RetroPie/tyrquake), [(Darkplaces Quake)](https://github.com/autonomous1/darkplacesrpi), [(ioQuake3)](https://github.com/raspberrypi/quake3)
* [ResidualVM](ResidualVM) [ResidualVM](https://github.com/residualvm/residualvm) (EXPERIMENTAL)
* [Rick Dangerous](Xrick) [(Xrick)](http://www.bigorno.net/xrick/)
* [Prince of Persia](SDLPoP) [(SDLPoP)](https://github.com/NagyD/SDLPoP)
* [Super Mario War](Super-Mario-War) [(Super Mario War)](https://github.com/HerbFargus/Super-Mario-War)
* [SuperTux](SuperTux)
* [The-Ur-Quan-Masters](The-Ur-Quan-Masters) [(UQM)](http://wiki.uqm.stack.nl/Main_Page)
* [Warcraft/Starcraft](Stratagus) [(Stratagus)](https://github.com/Wargus/stratagus.git)
* [Wolfenstein 3D](Wolfenstein-3D) [(Wolf4SDL)](https://github.com/mozzwald/wolf4sdl)
* [Zelda Engine](Solarus) [(Solarus)](http://www.solarus-games.org/)

## Overview

This page describes the process of adding software to the ports menu of EmulationStation. This is not to be taken lightly by Linux new-comers as this requires installing the software from the command-line and then making a shell script that EmulationStation will call to start it all up.

Please don't get scared off, this is a great introduction to some basic things in Linux, and for the most part it is a simple when you have the parts explained.

## Installing Ports from apt-get

Any game in the raspbian [repos](http://archive.raspbian.org/raspbian/dists/wheezy/main/binary-armhf/) can be installed from a script based on the following (This is provided that they do not need x server to run. a good portion will not run and those that do will likely require a keyboard.) Just do a find and replace on `supertux` and save the file as a shell script with the same name as the game (i.e. supertux.sh) in `/home/pi/RetroPie-Setup/scriptmodules/ports` and then you should be able to install it from the experimental menu of the setup script:

```
#!/usr/bin/env bash
 
# This file is part of The RetroPie Project
#
# The RetroPie Project is the legal property of its developers, whose names are
# too numerous to list here. Please refer to the COPYRIGHT.md file distributed with this source.
#
# See the LICENSE.md file at the top-level directory of this distribution and
# at https://raw.githubusercontent.com/RetroPie/RetroPie-Setup/master/LICENSE.md
#
 
rp_module_id="supertux"
rp_module_desc="SuperTux 2d scrolling platform"
rp_module_menus="4+"
rp_module_flags="nobin"
 
function install_supertux() {
    aptInstall supertux
}
 
function configure_supertux() {
    mkRomDir "ports"

    addPort "$md_id" "supertux" "SuperTux" "supertux"
}
```

##Installing the software

To install the software, typically find the website that hosts the project that works on the software. They may mention how to install it. It may be in the repositories already which makes installing super simple. We are going to use quake as an example on this page. The package is acctually called darkplaces. Exit to the commandline to begin.

```
# update the pi before installing
sudo rpi-update
sudo reboot

# make a folder to install the game to
sudo mkdir /opt/retropie/emulators/darkplaces
```

We are now ready to download the game. The file is located here[https://github.com/autonomous1/darkplacesrpi/archive/dprpi_v1.1.zip]. You can just download the file directly to your Pi with the first command below if it is conected to the internet. For copying it off a flashdrive, you will have to google mounting for linux. You may just want to download the file and place it directly on the storage section of the SD card as it is the simplest option. 

```
# download the file
sudo wget https://github.com/autonomous1/darkplacesrpi/archive/dprpi_v1.1.zip
# unzip the file so that we can use the things inside of it
sudo unzip darkplacesrpi-dprpi_v1.1.zip -d /opt/retropie/emulators/darkplaces

#move the files from the zip to the proper location
sudo mv /opt/retropie/emulators/darkplaces/darkplacesrpi*/* /opt/retropie/emulators/darkplaces
sudo rmdir /opt/retropie/emulators/darkplaces/darkplacesrpi*

#install the acctual game
sudo dpkg -i /opt/retropie/emulators/darkplaces/darkplaces-rpi.deb
```

Now time to find another file. Google for quake106.zip and put that in the folder `/opt/retropie/emulators/darkplaces`

```
#unzip the file
sudo unzip quake106.zip -d /opt/retropie/emulators/darkplaces
#install some other dependencies
sudo apt-get install lhasa
sudo lhasa e resource.1

#make the files accesable to all people so that we can load this later
sudo chmod a+rwx /opt/retropie/emulators/darkplaces/ -R
```

##Linking the Game

Now that we have installed quake, it is time to link the game to EmulationStation. Go to the home directory with `cd ~` and then cd into the `roms/ports` folder. We are now going to make a shell script that will tell EmulationStation how to start the game.

```
touch quake.sh
chmod a+rwx quake.sh
nano quake.sh
```

Information to put in the file:

```
#!/bin/bash
sudo darkplaces-sdl -quake -basedir /opt/retropie/emulators/darkplaces/
```

##How to adapt to other games/software

There are only 2 parts to having software appear in the ports menu and have it work. The first is that you must have installed the software, however it gets done. You need to make sure it runs from the command-line before the next part. The second part is simply making a shell script that does the command line arguments to start the game/software. EmulationStation will launch it and then wait for it to exit. 

##GameMaker Games

Here's a module for the GameMaker Games. Just create a file called `gamemaker.sh` in `/home/pi/RetroPie-Setup/scriptmodules/ports`

With the following contents:

```shell
#!/usr/bin/env bash

# This file is part of The RetroPie Project
# 
# The RetroPie Project is the legal property of its developers, whose names are
# too numerous to list here. Please refer to the COPYRIGHT.md file distributed with this source.
# 
# See the LICENSE.md file at the top-level directory of this distribution and 
# at https://raw.githubusercontent.com/RetroPie/RetroPie-Setup/master/LICENSE.md
#

rp_module_id="gamemaker"
rp_module_desc="GameMaker - Games for the Raspberry Pi"
rp_module_section="exp"
rp_module_flags="!mali !x86"

function install_bin_gamemaker() {
# Install They Need To Be Fed Game
wget -O- -q https://www.yoyogames.com/download/pi/tntbf | tar -xvz -C "$md_inst"
# Install Super Crate Box Game
wget -O- -q https://www.yoyogames.com/download/pi/crate | tar -xvz -C "$md_inst"
# Install Maldita Castilla Game
wget -O- -q https://www.yoyogames.com/download/pi/castilla | tar -xvz -C "$md_inst"
}

function configure_gamemaker() {
    mkRomDir "ports"

    addPort "$md_id" "TheyNeedToBeFed" "TheyNeedToBeFed" "$md_inst/TheyNeedToBeFed/TheyNeedToBeFed"
    addPort "$md_id" "SuperCrateBox" "SuperCrateBox" "$md_inst/SuperCrateBox/SuperCrateBox"
    addPort "$md_id" "MalditaCastilla" "MalditaCastilla" "$md_inst/MalditaCastilla/MalditaCastilla"
}
```

