![](http://cdn.akamai.steamstatic.com/steam/subs/434/header_586x192.jpg?t=1343157844)
***
_Quake was a First Person Shooter series originally developed for the PC by Id Software. It is a successor to the Doom Series._

_There are 4 Quake games: Quake, Quake II, and Quake III Arena and Quake 4. RetroPie includes Quake, TyrQuake (an optimised build of the original Quake Engine), and Quake III Arena._

_The source code to the original Quake engine was released under the GPLv2 license on December 21st 1999. This has enabled a wide variety of source ports and improvements to be made and for the game to run on alternative operating systems and architectures._

***
# Quake
![](http://www.gameranx.com/images/updates/1294053269_quake_fps.jpg)

***
_The RetroPie Setup Script automatically installs the Quake 1 shareware game data._

***
## Emulator

* [libretro-tyrquake](https://github.com/libretro/tyrquake) (recommended)
* [tyrquake](https://github.com/RetroPie/tyrquake)
* [Darkplaces Quake](https://github.com/autonomous1/darkplacesrpi)

## Controls

`libretro-tyrquake` utilises Retroarch configurations and is the recommended port.

Add custom RetroArch controls to the `retroarch.cfg` file in

```shell
/opt/retropie/configs/quake/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroArch-Configuration)

`tyrquake` does not support joystick/gamepad input, so is suitable only for those with a keyboard and mouse.

## Upgrading Shareware to Registered

During installation of the port, the setup script places the shareware version of the Quake data files at:

~~~
/home/pi/RetroPie/roms/ports/quake/id1/pak0.pak
~~~

If you own the registered version, you may add the registered version data file at:

~~~
/home/pi/RetroPie/roms/ports/quake/id1/pak1.pak
~~~

The shareware version is Quake v1.06. It is recommended your registered data file be from v1.06 or v1.08 versions of the game, earlier versions may not be compatible.

There is no difference between the data files of v1.06 and v1.08, this was an update to the game engine only, not the data files.

## Quake Mission Packs

In addition to many community maps, Quake had some commercial add-ons which are considered "official".

### Mission Pack 1: Scourge of Armagon

Scourge of Armagon (aka `hipnotic`) was the first official Quake Mission Pack, sold by Hipnotic Interactive in 1997.

Place the data file at:

~~~
/home/pi/RetroPie/roms/ports/quake/hipnotic/pak0.pak
~~~

Reinstall the Quake port from the Setup Script, and a new option **Quake Mission Pack 1 (hipnotic)** will be created.

### Mission Pack 2 - Dissolution of Eternity

Dissolution of Eternity (aka `rogue`) is the second official Quake Mission Pack, sold by Rogue Entertainment in 1997.

Place the data file at:

~~~
/home/pi/RetroPie/roms/ports/quake/rogue/pak0.pak
~~~

Reinstall the Quake port from the Setup Script, and a new option **Quake Mission Pack 2 (rogue)** will be created.

### Episode 5 - Dimension of the Past

To celebrate Quake's 20th anniversary, MachineGames (developer of Wolfenstein: The New Order) created a new 10-level pack named *Episode 5 - Dimension of the Past* and released it for free at https://cdn.bethsoft.com/quake/dopa.rar

To get DOPA working in the RetroPie Quake ports, create a directory at:

~~~
/home/pi/RetroPie/roms/ports/quake/dopa/
~~~

Place the data file at:

~~~
/home/pi/RetroPie/roms/ports/quake/dopa/pak0.pak
~~~

Reinstall the Quake port from the Setup Script, and a new option **Quake Episode 5 (dopa)** will be created.

### Soundtrack Files

The CD audio from the base game and mission packs can be used if they are ripped into MP3 or OGG format files and placed into a subfolder named `music` of the relevant folder (`id1`, `dopa` or `rogue`). The ripped CD tracks must be named `trackXX.ogg` or `trackXX.mp3`, corresponding to the original track index of the CD for each song. Considering that the first track is always the data track, the first audio track will always begin with track 02, which should be reflected in the filename of the ripped audio files.

For more information refer to [this guide](https://steamcommunity.com/sharedfiles/filedetails/?id=119489135) and the directory structure below.

### Directory structure, an overview

The files `s0.sav` up to `s11.sav` represents structure of savegames. 

~~~
id1/
├── pak0.pak ## shareware data
├── pak1.pak ## registered data
├── s0.sav
├── s1.sav
├── music/
│   ├── track02.ogg ## or .mp3
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

## References

* https://retropie.org.uk/forum/topic/2431/solved-partly-issue-with-joypad-control-how-to-start-doom-doom2-heretic-and-all-episodes-of-quake-dopa-rogue-hipnotic
* https://twitter.com/machinegames/status/746363189768650752
* https://retropie.org.uk/forum/topic/11508/launching-quake-and-it-s-extras-1-year-anniversary-release
# Quake III Arena

![](http://cdn.akamai.steamstatic.com/steam/apps/2200/header.jpg?t=1343157282)

***

_Quake III Arena is the 3rd game in the Quake Series. It differs from the others in the sense that it is all multiplayer._

***
## Port: [ioQuake3](https://github.com/raspberrypi/quake3)

## Controls:
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