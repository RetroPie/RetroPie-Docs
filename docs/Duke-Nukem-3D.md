![](http://playsmart.fr/wp-content/uploads/2015/02/Duke-Nukem-3D.png)
***
_Duke Nukem 3D is a First Person Shooter game developed by 3D Realms in 1996._

## Port: [Eduke32](http://www.eduke32.com/)

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
- | Shrink Screen
+ | Enlarge Screen
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

**Old Configs**

The grp-file-argument gets ignored.
It always loads the grp-file located at

> /usr/share/games/eduke32/duke3d.grp

If you swap this with a full version of the grp-file it works.

If you start EDuke32 and it is not recognizing your controller bring down the console and type:

`in_joystick 1`