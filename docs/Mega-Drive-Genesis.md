***
![megadrive](https://cloud.githubusercontent.com/assets/10035308/12213157/e8e39520-b630-11e5-8d3a-543bf24b1052.png)
![genesis](https://cloud.githubusercontent.com/assets/10035308/12213160/ee91d720-b630-11e5-8d66-46fc0eae4b84.png)
***
_This console, known as the Mega Drive everywhere except in the USA where it was renamed Genesis, was released by Sega in 1988_
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX) | megadrive  | .7z .bin .gen .md .sg .smd .zip | bios_MD.bin (optional)| /opt/retropie/configs/megadrive/retroarch.cfg |
| [lr-picodrive](https://github.com/libretro/picodrive) | megadrive  | .7z .bin .gen .md .smd .zip | none | /opt/retropie/configs/megadrive/retroarch.cfg |
| [DGen](http://dgen.sourceforge.net/) | megadrive | .bin .md .smd | none | /opt/retropie/configs/megadrive/dgenrc |

## Emulators: [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX), [lr-picodrive](https://github.com/libretro/picodrive), [DGen](http://dgen.sourceforge.net/)
lr-genesis-plus-gx is best for the Pi 3/Pi 2 due to its accuracy. lr-picodrive is more suited for use on the Pi 0/Pi 1 due to its speed. DGen has the worst performance and can be tedious to configure the controls for.
## ROMS
Accepted File Extensions: **.7z .bin .gen .md .sg .smd .zip**

Place your ROMS in either
```
/home/pi/RetroPie/roms/megadrive
```
or
```
/home/pi/RetroPie/roms/genesis (symlinked to megadrive folder to remove confusion)
```
## BIOS

lr-genesis-plus-gx can load MegaDrive TMSS startup ROM (bootrom): **bios_MD.bin**

Place your bios_MD.bin BIOS file in
```
/home/pi/RetroPie/BIOS
```
## Controls

### lr-genesis-plus-gx and lr-picodrive

lr-genesis-plus-gx and lr-picodrive utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/megadrive/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

### 6 button controller

The Genesis/Mega Drive had a 6 button controller released, with 3 extra buttons (X, Y, Z) placed above the normal 3 (A, B, C). A small subset of games do not function with the 6 button controller, but the vast majority do. To emulate the 6 button controller, do the following:

#### lr-genesis-plus-gx

Save a **Core Input Remap** in the same manner as [Core Input Remapping](RetroArch-Configuration#core-input-remapping), with **User 1 Device Type** and **User 2 Device Type** set to **MD Joypad 6 Button**.

#### lr-picodrive

Change the **Core Options** for **Pad 1 Type** and **Pad 2 Type** from **3 Button Pad** to **6 Button Pad**. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

This will also take effect on any other system which you may use lr-picodrive for (eg. Sega 32X, Sega CD).

### Mega Drive/Genesis Controller

![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)

### Mega Drive/Genesis Wireless Controller

![sega_megadrive_6button_diagram](https://cloud.githubusercontent.com/assets/10035308/16599642/7f43e53a-42c0-11e6-9152-c33099878ccc.png)

### Mega Drive ArcadePad Controller

![sega_megadrive_6button_arcadepad_diagram](https://cloud.githubusercontent.com/assets/10035308/16599641/7f43ae62-42c0-11e6-924a-50ca4e44f401.png)

### DGen

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

### Switching Emulation Station to the Genesis logo:

If you are from the United States it is likely that you had the Sega Genesis rather than the Sega Mega Drive. If you want EmulationStation to show the genesis graphics instead of Mega Drive then you should create a file `/opt/retropie/configs/all/platforms.cfg` with the following contents (note this requires at least v4.1.6 of the RetroPie-Setup script).

```
megadrive_theme="genesis"
megadrive_platform="genesis"
```

Once this is done, please update any of the currently installed Mega Drive emulators from RetroPie-Setup and Emulation Station will now use the Genesis logo. Scraping from within Emulation Station should also return Genesis artwork.
