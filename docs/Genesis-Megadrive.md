***
![megadrive](https://cloud.githubusercontent.com/assets/10035308/12213157/e8e39520-b630-11e5-8d3a-543bf24b1052.png)
![genesis](https://cloud.githubusercontent.com/assets/10035308/12213160/ee91d720-b630-11e5-8d66-46fc0eae4b84.png)
***
_This console, known as the Genesis in North America and the Mega Drive everywhere else in the world, was released by Sega in 1988_
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-picodrive](https://github.com/libretro/picodrive) | megadrive  | .smd .bin .md .iso | none | /opt/retropie/configs/megadrive/retroarch.cfg |
| [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX) | megadrive  | .smd .bin .md .iso | none | /opt/retropie/configs/megadrive/retroarch.cfg |
| [DGen](http://dgen.sourceforge.net/) | megadrive | .smd .bin .md .iso | none | /opt/retropie/configs/megadrive/dgenrc |

## Emulators: [DGen](http://dgen.sourceforge.net/), [lr-picodrive](https://github.com/libretro/picodrive), [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX)
DGEN has the worst performance and can be tedious to configure controls, lr-picodrive seems to be the favourite for older Pi's, lr-genesis-plus-gx seems to be the favourite for the Pi 2.
## ROMS
Accepted File Extensions: **.smd .bin .gen .md .sg .zip**

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
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

### Configuring a 6 button controller

First you need to tell retroarch to use 6 buttons, because the default is to use 3.

#### lr-picodrive

Launch a Megadrive game and go to the Retroarch menu (default mapping: `select + x`). Go to `Quick Menu -> Core Options` and set the two input devices to `6 button pad`. Then exit the Retroarch menu. Once you quit the game, the configuration will be saved within the `retroarch-core-options.cfg` file under `/opt/retropie/configs/all`. You do not need to edit this file. These core options will also take affect on any other system which you may use lr-picodrive for (eg. Sega 32X, Sega CD).

#### lr-genesis-plus-gx

There are two ways to achieve this:

##### Option 1
You can edit the file `/opt/retropie/configs/megadrive/retroarch.cfg` and add in the following:

    input_libretro_device_p1 = "513"
    input_libretro_device_p2 = "513"

This will set the controller type to a 6 button pad, and will reload this configuration every time the emulator is launched.

##### Option 2
You can save a Core Remap File which reloads every time the emulator is launched:

Go to the Retroarch menu (default mapping: `select + x`). Go to `Quick Menu -> Core Input Options` and set the User 1 and User 2 Device Type to be MD Joypad 6 Button.

Scroll down on the same page and select Save Core Remap File. This will save a core remap file (.rmp) to a folder called "Genesis Plus GX" in the `/opt/retropie/configs/megadrive` folder. By default this remap file will load every time the emulator is launched.

### 3 Button Genesis/MegaDrive Controller

![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)

### 6 Button Genesis/MegaDrive Wireless Controller

![genesis6btn](https://cloud.githubusercontent.com/assets/10035308/7336429/7e524110-ebbb-11e4-8777-05a824384d34.png)

### 6 Button Genesis/MegaDrive ArcadePad Controller

![megadrive6btnarcadepaddiagram](https://cloud.githubusercontent.com/assets/10035308/8268483/8b1b6dae-1744-11e5-9407-df58e2a81aad.png)

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

### Advanced Configuration:

If you are from the United States it is likely that you had the Sega Genesis rather than the Sega Megadrive. If you want EmulationStation to show the genesis menu and boxart instead of megadrive then you can change the file in `/etc/emulationstation/es_systems.cfg`

from 

```
  <system>
    <name>megadrive</name>
    <fullname>Sega Mega Drive / Genesis</fullname>
    <path>~/RetroPie/roms/megadrive</path>
    <extension>.smd .bin .gen .md .sg .zip .SMD .BIN .GEN .MD .SG .ZIP</extension>
    <command>/opt/retropie/supplementary/runcommand/runcommand.sh 0 _SYS_ megadrive %ROM%</command>
    <platform>megadrive</platform>
    <theme>megadrive</theme>
  </system>
```

to

```
    <name>genesis</name>
    <fullname>Sega Genesis</fullname>
    <path>~/RetroPie/roms/megadrive</path>
    <extension>.smd .bin .gen .md .sg .zip .SMD .BIN .GEN .MD .SG .ZIP</extension>
    <command>/opt/retropie/supplementary/runcommand/runcommand.sh 0 _SYS_ megadrive %ROM%</command>
    <platform>genesis</platform>
    <theme>genesis</theme>
  </system>
```