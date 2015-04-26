![Sega Genesis](http://upload.wikimedia.org/wikipedia/en/1/12/GenesisLogo.png)![Megadrive](http://upload.wikimedia.org/wikipedia/en/a/a8/Megadrive_logo.png)
***
_This console, known as the Genesis in North America and the Mega Drive everywhere else in the world, was released by Sega in 1998_
***
## Emulators: [DGen](http://dgen.sourceforge.net/), [libretro-picodrive](https://github.com/libretro/picodrive), [libretro-Genesis-Plus-GX](https://github.com/libretro/Genesis-Plus-GX)
DGEN has the worst performance and can be tedious to configure controls, libretro-picodrive seems to be the favourite for older Pi's, libretro-Genesis-Plus-GX seems to be the favourite for the Pi 2.
## ROMS
Accepted File Extensions: **.smd .bin .md .iso**

Place your ROMS in either
```
/home/pi/RetroPie/roms/megadrive
```
or
```
/home/pi/RetroPie/roms/genesis (symlinked to megadrive folder to remove confusion)
```

## Controls

There are two methods for configuring controls- one for DGen and the other for lr-picodrive and lr-Genesis-Plus-GX.

### lr-picodrive and lr-Genesis-Plus-GX

lr-picodrive and lr-Genesis-Plus-GX utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/megadrive/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)

![genesis6btn](https://cloud.githubusercontent.com/assets/10035308/7336429/7e524110-ebbb-11e4-8777-05a824384d34.png)

### Dgen

DGen uses a configuration file called dgenrc located in
```
/opt/retropie/configs/megadrive/dgenrc
```

To set up an exit button:
modify this line to match your controller button
```shell
# Quit DGen or switch to the next ROM on the command-line.
key_quit = escape
joy_quit = joystick0-button12
```