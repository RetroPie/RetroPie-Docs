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

* [libretro-tyrquake](https://github.com/libretro/tyrquake) - recommended
* [tyrquake](https://github.com/RetroPie/tyrquake)

## Controls

`libretro-tyrquake` utilises Retroarch configurations and is the recommended port.

Add custom RetroArch controls to the `retroarch.cfg` file in

```shell
/opt/retropie/configs/quake/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/RetroPie/RetroPie-Setup/wiki/RetroArch-Configuration)

## Registered Version

The RetroPie Setup Script places the shareware Quake data files at:

~~~
/home/pi/RetroPie/roms/ports/quake/id1/pak0.pak
~~~

Add the registered version data file at:

~~~
/home/pi/RetroPie/roms/ports/quake/id1/pak1.pak
~~~

## Quake Mission Packs

In future, these level packs may be accessible via a "map launcher" which would also work with game engines like Doom.

For now, we can create scripts to launch them manually.

### Mission Pack 1: Scourge of Armagon

Scourge of Armagon (aka `hipnotic`) was the first official Quake Mission Pack, sold by Hipnotic Interactive in 1997.

Place the data file at:

~~~
/home/pi/RetroPie/roms/ports/quake/id1/hipnotic/pak0.pak
~~~

To launch it in `lr-tyrquake`, create a launcher script at:

~~~
/home/pi/RetroPie/roms/ports/Quake Mission Pack 1 (hipnotic).sh
~~~

With the contents:

~~~
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-tyrquake/tyrquake_libretro.so --config /opt/retropie/configs/ports/quake/retroarch.cfg /home/pi/RetroPie/roms/ports/quake/id1/hipnotic/pak0.pak" "lr-tyrquake"
~~~

### Mission Pack 2 - Dissolution of Eternity

Dissolution of Eternity (aka `rogue`) is the second official Quake Mission Pack, sold by Rogue Entertainment in 1997.

Place the data file at:

~~~
/home/pi/RetroPie/roms/ports/quake/id1/rogue/pak0.pak
~~~

To launch it in `lr-tyrquake`, create a launcher script at:

~~~
/home/pi/RetroPie/roms/ports/Quake Mission Pack 2 (rogue).sh
~~~

With the contents:

~~~
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-tyrquake/tyrquake_libretro.so --config /opt/retropie/configs/ports/quake/retroarch.cfg /home/pi/RetroPie/roms/ports/quake/id1/rogue/pak0.pak" "lr-tyrquake"
~~~

## References

* https://retropie.org.uk/forum/topic/2431/solved-partly-issue-with-joypad-control-how-to-start-doom-doom2-heretic-and-all-episodes-of-quake-dopa-rogue-hipnotic

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