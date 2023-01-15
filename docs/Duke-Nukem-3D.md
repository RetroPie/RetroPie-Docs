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

### Installing Duke Nukem 3D Official Addons

EDuke32 port installation can automatically setup launching entries for the official addons and the NAM mod. To use this method, copy each addon files to `ports/duke32/addons/<addon_name>`. 


|Addon | Mod `.grp` file |Location |
|---|:---|:--|
| Duke It Out in DC | `dukedc.grp` | `/home/pi/RetroPie/roms/ports/duke3d/addons/dc` |
| Nuclear Winter | `nw.grp` | `/home/pi/RetroPie/roms/ports/duke3d/addons/nw` |
| Duke Caribbean: Life's a Beach | `vacation.grp` | `/home/pi/RetroPie/roms/ports/duke3d/addons/vacation` |
| NAM | `nam.grp`* | `/home/pi/RetroPie/roms/ports/duke3d/addons/nam` |

* `NAM` requires copying the `GAME.CON` file and renaming it to `NAM.CON`, in addition to the main `.grp` file.

After copying the files, install the `eduke32` package and addons launching entries will be added to the Ports system. As with all new games, EmulationStation must be restarted after the installation/re-installation for the new addon entries be picked up and displayed.

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
