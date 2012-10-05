## Performance

[From ToadKing:](http://www.raspberrypi.org/phpBB3/viewtopic.php?p=137827#p137827)
BTW, for most of those cores you should be able to get at or near full speed, with some exceptions:

* imame4all: Speed depends on the game. Certain Midway games are known for being really slow, like Mortal Kombat or NBA Jam.

* pocketsnes: Some games, especially SuperFX and SA-1 games, will be kinda slow on a stock speed Pi. Some graphic effects in other games can lag specific screens. I overclocked/overvolted my Pi to 950 Mhz and it runs most games at full speed, except for the SuperFX and SA-1 ones.

* vba-next: Will probably never be fullspeed on the Pi. An alternative port is being considered.

* genesis-plus-gx: Is still a bit too slow on the Pi. An alternative port is being considered.

## Settings

All settings for retroarch can be found in /etc/retroarch.cfg (if you used the original RetroPie script) or, alternatively, in your home directory at ~/.retroarch.cfg. If you suspect RetroArch isn't loading the right config file, you use the RetroArch launch argument `-c /path/to/config.cfg` (you can set launch commands in the EmulationStation config file, `~/.emulationstation/es_systems.cfg`).

This is from the [RetroArch wiki](https://wiki.archlinux.org/index.php/RetroArch):

> RetroArch provides a skeleton configuration file located at /etc/retroarch.cfg and is very well commented.

> It is capable of supporting split configuration files using the #include "foo.cfg" directive within the main retroarch.cfg file. Alternatively, extra configuration files can be appended on the command line which override the default settings in retroarch.cfg. This can be achieved by using --appendconfig /path/to/config and is beneficial if different keybinds, video configurations or audio settings are required for the various implementations. 

## Key Mapping

In what config file can we change the keyboard mapping? For RetroArch the keyboard mapping can be changed in /etc/retroarch.cfg with

    sudo nano /etc/retroarch.cfg

