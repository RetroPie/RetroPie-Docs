![](http://www.hardcoregaming101.net/princeofpersia/old/LOGO.png)
***
_SDLPoP is an open source port of the game Prince of Persia._

***


### Emulator: [SDLPoP](https://github.com/NagyD/SDLPoP)

### Controls:

```
Controlling the kid:
* left: turn or run left
* right: turn or run right
* up: jump or climb up
* down: crouch or climb down
* shift: pick up things
* shift+left/right: careful step
* home or up+left: jump left
* page up or up+right: jump right
You can also use the numeric keypad.

Gamepad equivalents:
* left/right = left/right
* A = down
* B = quit
* X = shift
* Y = up

Controlling the game:
* Esc: pause game
* Space: show time left
* Ctrl-A: restart level
* Ctrl-G: save game (on levels 3..13)
* Ctrl-J: joystick mode (implemented by segrax) / gamepad mode (implemented by Norbert)
* Ctrl-K: keyboard mode
* Ctrl-R: return to intro
* Ctrl-S: sound on/off
* Ctrl-V: show version
* Ctrl-Q: quit game
* Ctrl-L: load game (when in the intro)
* Alt-Enter: toggle fullscreen
* F6: quicksave
* F9: quickload

Viewing or recording replays:
* Ctrl+Tab (in game): start or stop recording
* Tab (on title screen): view/cycle through the saved replays in the SDLPoP directory

Cheats: (Note: Cheats only work if you start the game with the command line option: "megahit")

* Shift-L: go to next level
* c: show numbers of current and adjacent rooms
* Shift-C: show numbers of diagonally adjacent rooms
* -: less remaining time
* +: more remaining time
* r: resurrect kid
* k: kill guard
* Shift-I: flip screen upside-down
* Shift-W: slow falling
* h: look at room to the left
* j: look at room to the right
* u: look at room above
* n: look at room below
* Shift-B: toggle hiding of non-animated objects
* Shift-S: Restore lost hit-point. (Like a small red potion.)
* Shift-T: Give more hit-points. (Like a big red potion.)

Troubleshooting / Tweaking / Saving the game:

You can change the in-game behavior of this game in the following way:

Go to the folder: /opt/retropie/ports/sdlpop

There should be an file called "SDLPoP.ini". If not, copy the file SDLPoP.ini.def 
over it. When you open this file you can edit some of the configurations of the game, 
like from which level onward you are allowed to save the game (default = 3). 
There are many other tweaks possible, the file will explain itself.
```