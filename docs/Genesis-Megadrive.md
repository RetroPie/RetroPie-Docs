![Sega Genesis](http://upload.wikimedia.org/wikipedia/en/1/12/GenesisLogo.png)![Megadrive](http://upload.wikimedia.org/wikipedia/en/a/a8/Megadrive_logo.png)
***
_This console, known as the Genesis in North America and the Mega Drive everywhere else in the world, was released by Sega in 1988_
***
## Emulators: [DGen](http://dgen.sourceforge.net/), [lr-picodrive](https://github.com/libretro/picodrive), [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX)
DGEN has the worst performance and can be tedious to configure controls, lr-picodrive seems to be the favourite for older Pi's, lr-genesis-plus-gx seems to be the favourite for the Pi 2.
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

### lr-picodrive and lr-genesis-plus-gx

lr-picodrive and lr-genesis-plus-gx utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/megadrive/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

### Configuring a 6-buttons controller

First you need to tell retroarch to use 6 buttons controllers, because the default is to use 3 buttons ones. Launch a megadrive game and go in the retroarch menu (default mapping: `select + x`). Go in `Options -> Core Options` and set the two input devices to `6 button pad`. Then go back to be root of the menu and choose to save the configuration.

Now you can edit the file `/opt/retropie/configs/megadrive/retroarch.cfg` (you will need the help of `jstest /dev/input/js0` to know which buttons to use). Example file:

    # All settings made here will override the global settings for the current emulator core

    video_shader = /opt/retropie/emulators/retroarch/shader/phosphor.glslp
    video_shader_enable = false
    video_smooth = false

    input_player1_b_btn = "1"
    input_player1_y_btn = "0"
    input_player1_a_btn = "7"
    input_player1_x_btn = "3"
    input_player1_l_btn = "2"
    input_player1_r_btn = "5"

    input_player2_b_btn = "1"
    input_player2_y_btn = "0"
    input_player2_a_btn = "7"
    input_player2_x_btn = "3"
    input_player2_l_btn = "2"
    input_player2_r_btn = "5"

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