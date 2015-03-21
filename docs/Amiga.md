![Amiga Logo] (http://upload.wikimedia.org/wikipedia/en/thumb/a/a7/Amiga_Logo_1985.svg/500px-Amiga_Logo_1985.svg.png)
***

_The Amiga was a family of personal computers released by Commodore in the 1980's and 1990's._

***


## Emulator: [UAE4ALL2](https://github.com/joolswills/uae4all2)

RetroPie now has a brand new [UAE4ALL](https://github.com/joolswills/uae4all2) emulator - which works much better than the previous one and many games are playable. On a Pi 2, most OCS/ECS games run at full speed. 

## ROMS
Accepted File Extensions: **.adf**

 Place your Amiga disks images in

```shell
/home/pi/RetroPie/roms/amiga/
```

## BIOS
The emulator comes with a free AROS rom that will work for running many games and demos. 
If you want to
use a kickstart 1.3, 2.0, 3.1 rom place your **kick13.rom, kick20.rom, kick31.rom** files in 


```shell
/home/pi/RetroPie/BIOS/
```

## Controls
Current controls (this may change) - these are hardcoded currently. This initial mapping was chosen as it's somewhat similar to MAME, and should mostly work on any controllers that use that input mapping (such as the picade). Joypad/Joystick is currently untested.

in game:
```
lctrl      - joy 1/mouse 1 (button X in gui)
lalt       - joy 2/mouse 2 (button Y in gui)
lshift     - joy 1 autofire (button A in gui)
z          - mouse 1  (button B in gui)

5          - switch input between mouse/joystick

arrow keys - up / down / left / right

lctrl + esc (exit back to menu)
```

Launch it from Emulation Station, and you get the gui where you can configure disks/roms/memory and insert adfs images into the virtual drives. 

It can't currently launch games directly from the Emulation Station menu, but the GUI is easy to use.