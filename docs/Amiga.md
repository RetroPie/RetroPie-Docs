![Amiga Logo] (http://upload.wikimedia.org/wikipedia/en/thumb/a/a7/Amiga_Logo_1985.svg/500px-Amiga_Logo_1985.svg.png)
***

_The Amiga was a family of personal computers released by Commodore in the 1980's and 1990's._

***


## Emulators: [UAE4ALL2](https://github.com/RetroPie/uae4all2), [UAE4ARM](https://github.com/Chips-fr/uae4arm-rpi/)

RetroPie now has a brand new [UAE4ALL2](https://github.com/RetroPie/uae4all2) emulator - which works much better than the previous one and many games are playable. On a Pi 2, most OCS/ECS games run at full speed. 

## ROMS
Accepted File Extensions: **.adf**

 Place your Amiga disks images in

```shell
/home/pi/RetroPie/roms/amiga/
```

## BIOS
The emulator comes with a free AROS rom that will work for running many games and demos. 

If you want to use a kickstart 1.3, 2.0, 3.1 rom place your **kick13.rom, kick20.rom, kick31.rom** files in 


```shell
/home/pi/RetroPie/BIOS/
```

## Controls
These are hardcoded currently. This initial mapping was chosen as it's somewhat similar to MAME, and should mostly work on any controllers that use that input mapping (such as the picade). Joypad/Joystick is currently untested.

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

Launch it from Emulation Station, and you get the GUI where you can configure disks/roms/memory and insert adf images into the virtual floppy disk drives. 

It can't currently launch games directly from the Emulation Station menu, but the GUI is easy to use.

## Video Tutorial

<a href="https://www.youtube.com/watch?v=dleumwWZp6Q
" target="_blank"><img src="https://i.ytimg.com/vi_webp/dleumwWZp6Q/mqdefault.webp" 
alt="Testing joypad in RetroPie" width="300" height="190" border="10" /></a> 

## Tips and troubleshooting

- Some games work better with the '512Kb Chip' + '512Kb Slow' memory configuration rather than the default A500 '1MB Chip'. If your game crashes or fails to load, change the memory settings in the 'CPU RAM' tab of the UAE4ALL2 GUI.

- Some games do not work properly if more than one floppy drive is in use. If your game crashes or fails to load try to use just DF0 (change disc image during game if required) and not use DF1, DF2 and DF3.

- For Raspberry Pi 1 users - make sure you overclock your device. Amiga emulation works much faster when overclocked to maximum. Without overclocking some games do not run at full speed.