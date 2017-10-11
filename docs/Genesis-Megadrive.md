***
![megadrive](https://cloud.githubusercontent.com/assets/10035308/12213157/e8e39520-b630-11e5-8d3a-543bf24b1052.png)
![genesis](https://cloud.githubusercontent.com/assets/10035308/12213160/ee91d720-b630-11e5-8d66-46fc0eae4b84.png)
***
_This console, known as the Genesis in North America and the Mega Drive everywhere else in the world, was released by Sega in 1988_
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-picodrive](https://github.com/libretro/picodrive) | megadrive  | .7z .bin .gen .md .smd .zip | none | /opt/retropie/configs/megadrive/retroarch.cfg |
| [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX) | megadrive  | .7z .bin .gen .md .sg .smd .zip | none | /opt/retropie/configs/megadrive/retroarch.cfg |
| [DGen](http://dgen.sourceforge.net/) | megadrive | .bin .md .smd | none | /opt/retropie/configs/megadrive/dgenrc |

## Emulators: [DGen](http://dgen.sourceforge.net/), [lr-picodrive](https://github.com/libretro/picodrive), [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX)
DGEN has the worst performance and can be tedious to configure controls, lr-picodrive seems to be the favourite for older Pi's, lr-genesis-plus-gx seems to be the favourite for the Pi 2.
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

## Controls

There are two methods for configuring controls- one for DGen and the other for lr-picodrive and lr-Genesis-Plus-GX.

### lr-picodrive and lr-genesis-plus-gx

lr-picodrive and lr-genesis-plus-gx utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/megadrive/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

### Configuring a 6 button controller

First you need to tell retroarch to use 6 buttons, because the default is to use 3.

#### lr-picodrive

There are two ways to achieve this, most people will want to use Option 1:

##### Option 1 - RetroArch Menu

Launch a Megadrive game and go to the Retroarch menu (default mapping: **Select + X**).

Go to **Quick Menu -> Options** and set the two input devices to **6 button pad**.

Exit the Retroarch menu.

Once you quit the game, the configuration will be saved within the `/opt/retropie/configs/all/retroarch-core-options.cfg` file. You do not need to edit this file.

These core options will also take affect on any other system which you may use lr-picodrive for (eg. Sega 32X, Sega CD).

##### Option 2 - Config file edit

If you don't have access to the Quick Menu (due to misconfigured controls or some other reason), then edit the `/opt/retropie/configs/all/retroarch-core-options.cfg` file and add:

~~~
picodrive_input1 = "6 button pad"
picodrive_input2 = "6 button pad"
~~~

#### lr-genesis-plus-gx

There are two ways to achieve this, most people will want to use Option 1:

##### Option 1 - RetroArch Menu

You can save a Core Remap File which reloads every time the emulator is launched.

Launch a Megadrive game and go into the RetroArch menu (default mapping: **Select + X**).

Go to **Quick Menu -> Input Options** and set the User 1 Device Type and User 2 Device Type to **MD Joypad 6 Button**.

Scroll down on the same page and select **Save Core Remap File*.

This will save a core remap file (`.rmp`) to a folder called "Genesis Plus GX" in the `/opt/retropie/configs/megadrive` folder. By default this remap file will load every time the emulator is launched.

##### Option 2 - Config file edit

Edit the file `/opt/retropie/configs/megadrive/retroarch.cfg` and add:

~~~
input_libretro_device_p1 = "513"
input_libretro_device_p2 = "513"
~~~

This will set the controller type to a 6 button pad, and will reload this configuration every time the emulator is launched.

### 3 Button Genesis/MegaDrive Controller

![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)

### 6 Button Genesis/MegaDrive Wireless Controller

![sega_megadrive_6button_diagram](https://cloud.githubusercontent.com/assets/10035308/16599642/7f43e53a-42c0-11e6-9152-c33099878ccc.png)

### 6 Button Genesis/MegaDrive ArcadePad Controller

![sega_megadrive_6button_arcadepad_diagram](https://cloud.githubusercontent.com/assets/10035308/16599641/7f43ae62-42c0-11e6-924a-50ca4e44f401.png)

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

### Switching Emulation Station to the Genesis logo:

If you are from the United States it is likely that you had the Sega Genesis rather than the Sega Megadrive. If you want EmulationStation to show the genesis graphics instead of megadrive then you should create a file `/opt/retropie/configs/all/platforms.cfg` with the following contents (note this requires at least v4.1.6 of the RetroPie-Setup script).

```
megadrive_theme="genesis"
megadrive_platform="genesis"
```

Once this is done, please update any of the currently installed megadrive emulators from RetroPie-Setup and Emulation Station will now use the Genesis logo. Scraping from within Emulation Station should also return Genesis artwork.