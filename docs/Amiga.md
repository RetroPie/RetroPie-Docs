***
![amiga](https://cloud.githubusercontent.com/assets/10035308/12189019/a46a4d44-b577-11e5-8378-d8196412103c.png)
***

_The Amiga was a family of personal computers released by Commodore in the 1980's and 1990's._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [UAE4ALL2](https://github.com/RetroPie/uae4all2), [UAE4ARM](https://github.com/Chips-fr/uae4arm-rpi/) | amiga  | .adf | kick13.rom, kick20.rom, kick31.rom | Hardcoded |

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

## Video Tutorial

<a href="https://www.youtube.com/watch?v=dleumwWZp6Q
" target="_blank"><img src="https://i.ytimg.com/vi_webp/dleumwWZp6Q/mqdefault.webp" 
alt="Testing joypad in RetroPie" width="300" height="190" border="10" /></a> 

## Tips and troubleshooting

- Some games work better with the '512Kb Chip' + '512Kb Slow' memory configuration rather than the default A500 '1MB Chip'. If your game crashes or fails to load, change the memory settings in the 'CPU RAM' tab of the UAE4ALL2 GUI.

- Some games do not work properly if more than one floppy drive is in use. If your game crashes or fails to load try to use just DF0 (change disc image during game if required) and not use DF1, DF2 and DF3.

- For Raspberry Pi 1 users - make sure you overclock your device. Amiga emulation works much faster when overclocked to maximum. Without overclocking some games do not run at full speed.

## Launching games directly from EmulationStation

Here you will find an application (with GUI):

http://s000.tinyupload.com/index.php?file_id=22898544572562431631

http://www.filehosting.org/file/details/572532/AMIGA%20Game%20Config%20Creator%20GUI.zip

It uses the "config.uae" in order to create games configuration. The file is included in the main folder of the app and you can edit it. For default behavior "config.uae" is searching for kickstart 2.04 in

``/home/pi/RetroPie/roms/amiga/``

renamed in "kick20.rom", so you have to rename your kickstart or edit configuration file. In that folder you have to put the config files created.

Also follow these steps:

``sudo nano /etc/emulationstation/es_systems.cfg``

and add ".uae" (without quote) on tag <extension> for "amiga" emulator:

``<extension>.sh .SH .uae</extension>``

``sudo nano /opt/retropie/configs/amiga/emulators.cfg``

and edit the line in this way:

``uae4arm="pushd /opt/retropie/emulators/uae4arm/; ./uae4arm -f %ROM%"``

Point attention to the floppy image extension: ".adf" or ".adz".

For game with multiple disks rename them in this way: 

Game bla bla bla (Disk 1 of N).adf  
Game bla bla bla (Disk 2 of N).adf  
...  
Game bla bla bla (Disk N of N).adf

in other words change ONLY the floppy identifier.  

Note: The old script from Mark Dunning has a problem with games with more than 9 floppies (creates others wrong config files) and creates a config file with name like "Game bla bla bla (Disk 1 of N).uae".  
  
This new app create only 1 file for a multiple disk game with the exact name of the game