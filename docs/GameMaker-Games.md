***
![GameMakerGames](https://www.raspberrypi.org/wp-content/uploads/2016/02/GameMaker-in-post-500x328.png)
***
YoYo Games has teamed up with Vlambeer, Jesse Venbrux and Locomalito, to give you a taste of what we hope will soon follow. With the help of these amazing developers, YoYo Games is proud to present to you 3 astounding, full games. Absolutely FREE.

***
# They Need To Be Fed
![TNTBF](https://img.yoyogames.com/pages/pi/TNTBF.png)

***
_Run and jump through 11 crazy worlds to feed the monsters in this 360° gravity platformer. It doesn't matter which way you go; up or down, left or right, you can't fall off because of the 360° gravity! Jump from rotating planes to moving platforms, avoiding dangers and collecting diamonds._

***
## Emulator: [GameMaker: Studio](http://www.yoyogames.com/gamemaker)

## Controls:
Key  |  Action
 --- | ---
Left Mouse Click | Navigate HUD
Space | Jump
Arrow Keys | Move
ESC | Return to Menu/Quit

***
# Super Crate Box
![SuperCrateBox](https://img.yoyogames.com/pages/pi/scb.png)

***
_Grab your baseball cap and loosen your pants, it's time to fight endless hordes of enemies and collect every weapon crate you can. Prepare for an arcade delight with tight controls, refreshing game mechanics, cracking retro art and a terribly hip chiptune soundtrack._

***
## Emulator: [GameMaker: Studio](http://www.yoyogames.com/gamemaker)

## Controls:
Key  |  Action
 --- | ---
Arrow Keys | Navigate HUD/Move
Z/Up Arrow | Jump
X | Fire
ESC | Return to Menu/Quit

***
# Maldita Castilla
![MalditaCastilla](https://img.yoyogames.com/pages/pi/Maldita%20Castilla.png)

***
_Maldita Castilla (Cursed/damn Castile) is an action arcade game full of myths from Spain and the rest of Europe. The graphic style is raw, made pixel by pixel with a limited color palette, like in the old days, and displayed through a dirty old monitor effect._

***
## Emulator: [GameMaker: Studio](http://www.yoyogames.com/gamemaker)

## Controls:
Key  |  Action
 --- | ---
Arrow Keys | Navigate HUD/Move/Aim
Z | Attack
X | Jump
ESC | Return to Menu
ALT+ENTER | Toggle Fullscreen
ALT+F4 | Quit

***
## Installation
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