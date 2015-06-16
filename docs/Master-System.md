![Master System Logo](http://selmiak.bplaced.net/games/sms/sms/sms.png)

***
_The Sega Master System was a 4th generation video game console released by Sega in 1987._
***
## Emulators: [Osmose](https://github.com/RetroPie/osmose-rpi), [libretro-Genesis-Plus-GX](https://github.com/libretro/Genesis-Plus-GX), [libretro-picodrive](https://github.com/libretro/picodrive)
Osmose has it's own configurations whereas lr-Genesis-Plus-GX and lr-picodrive utilise RetroArch configurations

## ROMS

Accepted File Extensions: **.sms**

Place your Master System ROMs in
```
/home/pi/RetroPie/roms/mastersystem
```
## Controls

### lr-picodrive and lr-Genesis-Plus-GX

lr-picodrive and lr-Genesis-Plus-GX utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/mastersystem/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![mastersystem](https://cloud.githubusercontent.com/assets/10035308/7334954/59794038-eb60-11e4-989d-6367c1fda8ef.png)

### Osmose
Once you have run Osmose at least once, a configuration file call osmose.ini will be created at
```
/home/pi/osmose_files/osmose.ini
```
It will look something like this:
```shell
# Configuration Starts Here !

#
#  General emulation keys:
#

SCREENSHOT    = SDLK_F2
SOUNDSHOT     = SDLK_F1
QUIT          = SDLK_ESCAPE
TILESHOT      = SDLK_F3
DEBUGGER      = SDLK_d
PAUSE         = SDLK_p

#
# First Player PAD:
#

PAD1_UP       = SDLK_UP
PAD1_DOWN     = SDLK_DOWN
PAD1_LEFT     = SDLK_LEFT
PAD1_RIGHT    = SDLK_RIGHT
PAD1_BUTTON_A = SDLK_LCTRL
PAD1_BUTTON_B = SDLK_LALT

#
# Second Player PAD:
#

PAD2_UP       = SDLK_KP5
PAD2_DOWN     = SDLK_KP2
PAD2_LEFT     = SDLK_KP1
PAD2_RIGHT    = SDLK_KP3
PAD2_BUTTON_A = SDLK_n
PAD2_BUTTON_B = SDLK_b
```

The above controls only apply to the keyboard. Configuring controls for a gamepad must be done by editing the es_systems.cfg file
```
/etc/emulationstation/es_systems.cfg
```
add your specific controls in this format to the gamegear section:
```
osmose -joy 1 -joy1 1 -joy2 2 -joyquit 6
```
see [This Thread](http://www.raspberrypi.org/forums/viewtopic.php?f=78&t=23550) for more details