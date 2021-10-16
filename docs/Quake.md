![](http://cdn.akamai.steamstatic.com/steam/subs/434/header_586x192.jpg?t=1343157844)
***
_Quake was a First Person Shooter series originally developed for the PC by Id Software. It is a successor to the Doom Series._

_There are 4 Quake games: Quake, Quake II, and Quake III Arena and Quake 4. RetroPie includes ports for Quake, Quake II and Quake III Arena._

_The source code to the original Quake engine was released under the GPLv2 license on December 21st 1999. This has enabled a wide variety of source ports and improvements to be made and for the game to run on alternative operating systems and architectures._

***
## Quake
![](https://cdn.cloudflare.steamstatic.com/steam/apps/2310/header.jpg)

***
_The RetroPie Setup Script automatically installs the Quake 1 shareware game data._

### Ports

* [libretro-tyrquake](https://github.com/libretro/tyrquake) (recommended)
* [tyrquake](https://github.com/RetroPie/tyrquake)
* [Darkplaces Quake](https://github.com/autonomous1/darkplacesrpi)

### Controls

`libretro-tyrquake` utilises Retroarch configurations and is the recommended port, since it supports a joystick/gamepad to play. See [here](https://docs.libretro.com/library/tyrquake/#joypad) for how the inputs are mapped to the Quake's keyboard.    
You can also switch to a mouse/keyboard combination by changing the the _Device Type_ of the Player 1 connected controller to _Keyboard + Mouse_.

The other ports use the keyboard and mouse for controls.

### Upgrading Shareware version to Registered

During installation of the port, the setup script places the shareware version of the Quake data files at:

~~~
/home/pi/RetroPie/roms/ports/quake/id1/pak0.pak
~~~

If you own the registered version, you may add the `id1` folder files from the installation of the registered version to:

~~~
/home/pi/RetroPie/roms/ports/quake/id1/
~~~

The shareware version is Quake v1.06. It is recommended your registered data file be from v1.06 or v1.08 versions of the game, earlier versions may not be compatible.

There is no difference between the data files of v1.06 and v1.08, this was an update to the game engine only, not the data files.

### Quake Mission Packs

In addition to many community maps, Quake had some commercial add-ons which are considered "official".

#### Scourge of Armagon

Scourge of Armagon (aka `hipnotic`) was the first official Quake Mission Pack, developed by Hipnotic Interactive and released in 1997.

Place the `hipnotic/pak0.pak` file from your registered installation at:

~~~
/home/pi/RetroPie/roms/ports/quake/hipnotic/pak0.pak
~~~

Reinstall the Quake port from the Setup Script and a **Quake Mission Pack 1 (hipnotic)** launcher will be added in _Ports_.

#### Dissolution of Eternity

Dissolution of Eternity (aka `rogue`) is the second official Quake Mission Pack, developed by Rogue Entertainment and released in 1997.

Place he `rogue/pak0.pak` file from your registered installation at:

~~~
/home/pi/RetroPie/roms/ports/quake/rogue/pak0.pak
~~~

Reinstall the Quake port from the Setup Script, and a new entry - **Quake Mission Pack 2 (rogue)** - will be created in _Ports_.

#### Episode 5 - Dimension of the Past

To celebrate Quake's 20th anniversary, MachineGames (developer of Wolfenstein: The New Order) created a new 10-level pack named *Episode 5 - Dimension of the Past* and released it for free at <https://cdn.bethsoft.com/quake/dopa.rar>.

To get DOPA working in the RetroPie Quake ports, create a directory at:

~~~
/home/pi/RetroPie/roms/ports/quake/dopa/
~~~

Place the `pak0.pak` file from the DOPA archive file at:

~~~
/home/pi/RetroPie/roms/ports/quake/dopa/pak0.pak
~~~

Reinstall the Quake port from the Setup Script, and a new entry - **Quake Episode 5 (dopa)** - will be created in _Ports_.


### Soundtrack Files 

The `libretro-tyrquake` and `Darkplaces` clients support playback of the original soundtrack from the base game and official mission packs' CDs.

CD audio should be ripped into OGG format files, and placed into a subfolder named `music` of the appropriate folder (`id1`, `hipnotic` or `rogue`). The ripped CD tracks must be named `trackXX.ogg`, corresponding to the original CD track index for each audio track. Considering that the first CD track in all cases is the data track, the first audio track will always begin with track 02, which should be reflected in the filename of the ripped audio files.

For more information refer to [this guide](https://steamcommunity.com/sharedfiles/filedetails/?id=119489135) and the directory structure below.

### Directory structure - overview

The files `s0.sav` up to `s11.sav` represents structure of savegames. 

~~~
id1/
├── pak0.pak ## shareware data
├── pak1.pak ## registered data
├── s0.sav
├── s1.sav
├── music/
│   ├── track02.ogg
│   ├── ...
│   └── track11.ogg
│
hipnotic/
├── pak0.pak
├── s0.sav
├── s1.sav
├── music/
│   ├── track02.ogg
│   ├── ...
│   └── track09.ogg
│
rogue/
├── pak0.pak
├── s0.sav
├── s1.sav
├── music/
│   ├── track02.ogg
│   ├── ...
│   └── track09.ogg
│
dopa/
├── pak0.pak
├── s0.sav
└── s1.sav
~~~

### References

* <https://retropie.org.uk/forum/topic/2431/solved-partly-issue-with-joypad-control-how-to-start-doom-doom2-heretic-and-all-episodes-of-quake-dopa-rogue-hipnotic>
* <https://twitter.com/machinegames/status/746363189768650752>
* <https://retropie.org.uk/forum/topic/11508/launching-quake-and-it-s-extras-1-year-anniversary-release>


## Quake II

![](https://cdn.cloudflare.steamstatic.com/steam/apps/2320/header.jpg)

***

_Quake II is the 2nd game in the Quake Series, though not a sequel to the first installment._

***
_The RetroPie installation script downloads and configured the Q2 Shareware/Demo (v3.14)._

The Quake II port installed is [Yamagi Quake II](https://github.com/yquake2/yquake2).

### Controls

Yamagi Quake II supports gamepad controls, they can be customized from the in-game menu.

### Upgrading Shareware version to Registered

During installation of the port, the setup script places the shareware version of the Quake II data files at:

```
/home/pi/RetroPie/roms/ports/quake2/baseq2/pak0.pak
```

If you own the registered version, you may add the `baseq2` folder files from the installation of the registered version to:

```
/home/pi/RetroPie/roms/ports/quake2/baseq2
```

### Mission Packs

#### The Reckoning

Quake II Mission Pack: The Reckoning (aka `xatrix`) is the first official Quake II Mission Pack, developed by Xatrix Entertainment and released in 1998.

Copy the `xatrix` folder contents from your mission pack installation at:

~~~
/home/pi/RetroPie/roms/ports/quake2/xatrix
~~~

Reinstall the Quake II port from the Setup Script, and a new entry - **Quake II - The Reckoning** - will be created in _Ports_.

#### Ground Zero

Quake II Mission Pack: Ground Zero (aka `rogue`) is the second official Quake II Mission Pack, developed by Rogue Entertainment and released in 1998.

Copy the `rogue` folder contents from your mission pack installation at:

~~~
/home/pi/RetroPie/roms/ports/quake2/rogue
~~~

Reinstall the Quake II port from the Setup Script, and a new entry - **Quake II - Ground Zero** - will be created in _Ports_.


## Quake III Arena

![](http://cdn.akamai.steamstatic.com/steam/apps/2200/header.jpg?t=1343157282)

***

_Quake III Arena is the 3rd game in the Quake Series. It differs from the others in the sense that it is all multiplayer._

***
### Ports
* an [ioQuake3](https://github.com/raspberrypi/quake3) Raspberry PI optimized build, useful for Pi3/Pi2.
* the official [ioQuake3][https://github.com/ioquake/ioq3] engine, for PC and more powerful SBC (Pi4/Odroid) systems.

### Controls

Key  |  Action
 --- | ---
Ctrl or Left Mouse Click | Attack
/ | Next Weapon
1-9 | Weapons
Space | Jump
Up Arrow or W | Walk Forward
Down Arrow or S | Backpedal
Left Arrow | Turn Left 
Right Arrow  | Turn Right
ALT | Sidestep
PGDN | Look Up
DEL | Look Down
END | Center View
 Mouse Movement | Mouse Look
D | Strafe Right
A | Strafe Left
Mouse Scroll Wheel Click | Zoom
C | Crouch
TAB | Stats
T | Chat 
F11 | Take Screenshot
ESC | Menu
