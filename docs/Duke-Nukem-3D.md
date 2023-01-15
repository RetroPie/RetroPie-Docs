As of 8/3/19 this guide isn't the way to install the 3 expansion packs. I had followed this guide and it used to infact work. An update of retropie script and then subsequent update of all installed packages that I had done, changed where the grp go. So now all you need to do is put _nwinter.grp_, _dukedc.grp_, and _vacation.grp_ in the duke3d folder you create and then install eduke32 as described. You may need to make the .sh files described below for each duke3d expansion pack but maybe not. Same with the emulators.cfg and eduke32.cfg files in the configs/ports/duke3d folders. 
I dont know as mine were already created using this guide before the devs changed how the duke3d install works. 

 NAM however will run and continue to run everytime you start it up but it changes the eduke32.cfg file located in .etc/eduke32 on its own and breaks duke3d and all expansion packs till you manually modify eduke32.cfg selectedgrp field back to duke3d.grp. I've tried multiple times and nam breaks duke 3d and any expansion packs every single time. To avoid this change the permissions on the eduke3d.cfg file so no one can change it. And then you can run duke 3d the expansion packs and nam without anything breaking or having to modify anything after running nam. 

I also had to modify the screen res from 1024 x 768 (iirc) in eduke32.cfg to make the screen visible if anyone else is having issues with a blurred screen smashed at the top of the monitor or tv. 


![](https://static.3drealms.com/media/game_logos/7ac8171e68e941dd9147d57d9803575d.png)
***
_Duke Nukem 3D is a First Person Shooter game developed by 3D Realms in 1996._

## Port: [Eduke32](http://www.eduke32.com/)

## Basic Installation

The shareware port can be installed under RetroPie setup. Go to **Manage packages** > **Manage optional packages** and select **eduke32**. You can install from binary or from source.

## ROMs

Shareware versions of **duke3d.grp** and **duke.rts** are provided via symlinks in
```
/home/pi/RetroPie/roms/ports/duke3d
```
The shareware files are physically located in a different directory, but if you just replace the links in the folder above with your full version game data, it should work.

### Installing Duke Nukem 3D Official Addons "Nuclear Winter", "Duke It Out in DC" and "Duke Caribbean: Life's a Beach"

#### Automated installation

Since September 2019, the EDuke32 port installation can automatically setup launching entries for the official addons and the NAM mod. To use this method, copy each addon files to `ports/duke32/addons/<addon_name>`. 


|Addon | Mod `.grp` file |Location |
|---|:---|:--|
| Duke It Out in DC | `dukedc.grp` | `/home/pi/RetroPie/roms/ports/duke3d/addons/dc` |
| Nuclear Winter | `nw.grp` | `/home/pi/RetroPie/roms/ports/duke3d/addons/nw` |
| Duke Caribbean: Life's a Beach | `vacation.grp` | `/home/pi/RetroPie/roms/ports/duke3d/addons/vacation` |
| NAM | `nam.grp`* | `/home/pi/RetroPie/roms/ports/duke3d/addons/nam` |

* `NAM` requires copying the `GAME.CON` file and renaming it to `NAM.CON`, in addition to the main `.grp` file.

After copying the files, install the `eduke32` package and addons launching entries will be added to the Ports system. As with all new games, EmulationStation must be restarted after the installation/re-installation for the new addon entries be picked up and displayed.

#### Manual installation
The files tested for this method came from the Megaton Edition on Steam on Windows and these instructions assume that you'll be modifying files on your RetroPie instance via the Samba network share from your Windows PC. If you have a different version of the game or a different method of modifying files on your RetroPie instance then you should be able to interpret these instructions for the game version and method you have.

1. Install full Duke Nukem 3D Megaton Edition as already documented on this page.

2. Copy the three folders in `C:\Program Files (x86)\Steam\steamapps\common\Duke Nukem 3D\gameroot\addons` from your PC to your `\\RETROPIE\roms\ports\duke3d` folder. This means you will have `nw`, `dc` and `vacation` subfolders.

3. In `\\RETROPIE\configs\ports\`, make three copies of the `\\RETROPIE\configs\ports\duke3d` folder, renaming them to, `duke3d-nw`, `duke3d-dc` and `duke3d-vacation`.

4. In each of the three folders, edit `eduke32.cfg` so that `SelectedGRP = "nwinter.grp"`, `"dukedc.grp"` and `"vacation.grp"` respectively, instead of plain `"duke3d.grp"` Change any other settings you want for these addons, like maybe some Christmas-themed taunts for Nuclear Winter or some political taunts for Duke It Out in DC.

5. `\\RETROPIE\configs\ports\duke3d\emulators.cfg` in the duke3d config folder normally looks like this:
```
eduke32 = "/opt/retropie/ports/eduke32/eduke32 -j/home/pi/RetroPie/roms/ports/duke3d"
default = "eduke32"
```

Change`\\RETROPIE\configs\ports\duke3d-nw\emulators.cfg` to look like this:
```
eduke32 = "/opt/retropie/ports/eduke32/eduke32 -g nw/nwinter.grp -x nw/nwinter.con -j/home/pi/RetroPie/roms/ports/duke3d"
default = "eduke32"
```

(Note the `-x nw/nwinter.con`. You need that.)

Change `\\RETROPIE\configs\ports\duke3d-dc\emulators.cfg` to look like this:
```
eduke32 = "/opt/retropie/ports/eduke32/eduke32 -g dc/dukedc.grp -j/home/pi/RetroPie/roms/ports/duke3d"`
default = "eduke32"
```

Change `\\RETROPIE\configs\ports\duke3d-vacation\emulators.cfg` to look like this:
```
eduke32 = "/opt/retropie/ports/eduke32/eduke32 -g vacation/vacation.grp -j/home/pi/RetroPie/roms/ports/duke3d"
default = "eduke32"
```

6. In `\\RETROPIE\roms\ports` make three copies of `Duke Nukem 3D.sh`.

Name the first one `Duke Nukem 3D - Nuclear Winter.sh` and it should say:
```
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "duke3d-nw" ""
```

Name the second one `Duke Nukem 3D - Duke It Out In DC.sh` and it should say:
```
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "duke3d-dc" ""
```

Name the third one `Duke Nukem 3D - Lifes a Beach.sh` and it should say:
```
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "duke3d-vacation" ""
```

### Installing NAM

The files tested for this method came from NAM on Steam on Windows and these instructions assume that you'll be modifying files on your RetroPie instance via the Samba network share from your Windows PC. If you have a different version of the game or a different method of modifying files on your RetroPie instance then you should be able to interpret these instructions for the game version and method you have.

1.  Copy `GAME.CON`, `NAM.GRP` and `NAM.RTS` to a new folder you make called `\\RETROPIE\roms\ports\duke3d\nam`. The Windows Steam version of NAM has these files located in `C:\Program Files (x86)\Steam\steamapps\common\Nam\NAM`.

2. Rename `GAME.CON` to `NAM.CON`.

3. In `\\RETROPIE\configs\ports\`, make a copy of the `\\RETROPIE\configs\ports\duke3d` folder, renaming it `nam`.

4. Edit `\\RETROPIE\configs\ports\nam\eduke32.cfg` so that `SelectedGRP = "NAM.GRP"` and choose some taunts about giving free helicopter rides to Commies.

5. Edit `\\RETROPIE\configs\ports\nam\emulators.cfg` to look like this:
```
eduke32 = "/opt/retropie/ports/eduke32/eduke32 -nam -g NAM.GRP -x NAM.CON -j/home/pi/RetroPie/roms/ports/duke3d/nam"
default = "eduke32"
```

6. Add a file `\\RETROPIE\roms\ports\NAM.sh`, which should contain:

```
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "nam" ""
```

## Controls:

Key | Action
 --- | ---
W or NUMPAD 8 | Move Forward
S or NUMPAD 2 | Move Backward
Left or NUMPAD 4 | Turn Left
Right or NUMPAD 6 | Turn Right
ALT | Strafe
Right CTRL or Left Click | Fire
E | Open/Use
Shift | Run
Caps Lock | Autorun
Space or / | Jump
Left CTRL | Crouch
PGUP or NUMPAD 9 | Look Up
PGDN or NUMPAD 3 | Look Down
INS or NUMPAD 0 | Look Left
DEL or NUMPAD . | Look Right
A | Strafe Left
D | Strafe Right
HOME or NUMPAD 7 | Aim Up
END or NUMPAD 1 | Aim Down
0-9 | Weapons
Enter | Inventory
[ | Inventory Left
] | Inventory Right
H | Holo Duke
J | Jetpack
N | Nightvision
M | Medkit
Backspace | Turnaround
T | Send Message
Tab | Map
\- | Shrink Screen
\+ | Enlarge Screen
5 | Center View
Scroll Lock | Holster Weapon
Y | Show Opponents Weapon
F | Map Follow Mode
K | See Co-op View
U | Mouse Aiming
I | Toggle Crosshair
R | Steroids
Q | Quick Kick
" | Next Weapon
: | Previous Weapon
` | Show Console
F1 | Help
F2 | Save
F3 | Load 
F4 | Sound/Music
F5 | Change Music
F6 | Quicksave
F7 | Chase View 
F8 | Messages
F9 | Quickload
F10 | Quit
F11 | Brightness 
F12 | Save PCX
ESC | Menu


If you start EDuke32 and it is not recognizing your controller bring down the console and type:

`in_joystick 1`

For information on how to configure an XBox360 controller to work in eduke32, check out [this forum post](https://retropie.org.uk/forum/post/130059).