***
![daphne_logo](https://cloud.githubusercontent.com/assets/10035308/13100363/9480ba8e-d4f9-11e5-974a-a514e3008837.png)
***
_Laserdiscs were predecessors to the DVD. The first laserdisc game was released in 1982. Laserdisc games function much like interactive fiction where you choose your own story and the video adapts to the path you choose to take._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Daphne](http://www.daphne-emu.com/site3/index_hi.php) | daphne  | .daphne | none | /opt/retropie/configs/daphne/dapinput.ini |
| [Hypseus](https://github.com/DirtBagXon/hypseus-singe) | daphne  | .daphne | none | /opt/retropie/configs/daphne/hypinput.ini |
| [lr-dirksimple](https://github.com/icculus/DirkSimple) | daphne | .ogv | none | /opt/retropie/configs/daphne/retroarch.cfg |

## Emulator: [daphne](http://www.daphne-emu.com/site3/index_hi.php), [hypseus](https://github.com/DirtBagXon/hypseus-singe), [dirksimple](https://github.com/icculus/DirkSimple) 

**daphne** was developed by Matt Ownby. For the best replication of Laserdisc games check out his Dexter project [HERE](https://www.daphne-emu.com:9443/mediawiki/index.php/DexterFAQ)  
**hypseus** is a SDL2 fork of the Daphne codebase. This version includes **Singe** game support.
**DirkSimple** is a FMV/laserdisc game player. It uses the original footage from the supported games but not their ROMs. The game logic has been implemented from scratch in Lua. It currently supports 2 games: _Dragon's Lair_ and _Cliff Hanger_. RetroPie includes the Libretro core version, not the standalone emulator.

## ROMS
Accepted extensions: **.daphne** and **ogv**

Place your Laserdisc roms in 

```
/home/pi/RetroPie/roms/daphne
```

The file structure is like so:

### Daphne

```
roms
|-- daphne
|    |   (The folder below holds a laserdisc...".daphne"
|    |   tells emulationstation to add this to the menu,
|    |   and "dle21" tells daphne to use that game engine)
|    |
|    |-- dle21.daphne     
|    |    |-- dle21.commands  (Optional extra command-line params!)
|    |    |-- dle21.txt       (Framefile)
|    |    |-- lair.m2v
|    |    |-- lair.ogg
|    |
|    +-- roms                 (All roms go into this roms folder)
|         +-- dle21.zip
```
### Singe 
Only supported in **hypseus**. Ensure the main *.singe* file matches the game directory name.
```
roms
|-- daphne
|    |
|    |-- timegal.daphne
|    |    |
|    |    |-- timegal.commands  (Optional)
|    |    |-- timegal.txt       (Framefile)
|    |    |-- timegal.m2v
|    |    |-- timegal.ogg
|    |    |-- timegal.singe     (Main LUA Singe file)
|    |    |-- *.*               (Other peripheral files)
|    |
|    +-- roms                   (No Singe data but required)
|
```
### DirkSimple
The Libretro core supports playing from an **.ogv** file, which is an Ogg-Theora video created from the original Daphne DVD MPEG files. To create the **.ogv** file from a standard Daphne/Hypseus `.daphne` game folder (see above), the `ffmpeg` is needed utility is needed, installable by running `sudo apt install -y ffpmeg`).

Run the commands:

``` sh
cd $HOME/RetroPie/roms/daphne

# for Dragon's Lair
ffmpeg -i dlair.daphne/lair.m2v -i dlair.daphne/lair.ogg -codec:v libtheora -qscale:v 7 -codec:a libvorbis -qscale:a 5 -pix_fmt yuv420p lair.ogv

# for Cliff Hanger
ffmpeg -i cliff.daphne/cliff.m2v -i cliff.daphne/cliff.ogg -codec:v libtheora -qscale:v 7 -codec:a libvorbis -qscale:a 5 -pix_fmt yuv420p cliff.ogv
```
Check that the **ogv** files are correctly placed in the `$HOME/RetroPie/roms/daphne` after the conversion with `ffmpeg`, then restart EmulationStation for the new game entries to appear. Choose the `lr-dirksimple` libretro core as the emulator for the new files using the [runcommand launch menu](https://retropie.org.uk/docs/Runcommand/#runcommand-launch-menu.

More info about the **ogv** format understood by DirkSimple can be found at <https://github.com/icculus/DirkSimple#how-do-i-use-this>.

## Controls
### daphne
```
/opt/retropie/configs/daphne/dapinput.ini
```
### hypseus
```
/opt/retropie/configs/daphne/hypinput.ini
```

**Default Keyboard Controls:**

|Key|Action|
|:---:|---|
|ESC|Quit the game|
|5 and 6|Insert Coin (Coin chutes)|
|1|Player 1 Start|
|2|Player 2 Start|
|Arrow Keys|Directional Movement|
|Left CTRL|Button #1 (Primary trigger)|
|Left ALT|Button #2 (Alternate trigger)|
|Space|Button #3 (Secondary trigger)|
|W|Cadet skill level (Space Ace)|
|I|Captain skill level (Space Ace)|
|K|Space Ace skill level (Space Ace)|
|P|Pause game (laserdisc player must be playing)|
|T|Tilt game (just a gimmick, only works in a few games)|
|9|Go into service mode (used in Dragon's Lair 2)|
|F2|Go into test mode (similar to service mode)|
|0|Reset/reboot game|
|F12|Take screenshot (VLDP only)|


Default **dapinput.ini**
```
# Daphne cutom keyboard and joystick mapping
#
# Each input is mapped to 2 keyboard keys and one joystick button.
# A joystick's first analog stick is also automatically mapped.
#
# The first two numbers are SDL keyboard codes (or 0 for "none")
# Find keyboard codes here:
# http://www.daphne-emu.com/mediawiki/index.php/KeyList
#
# The third number is the joystick button code (or 0 for "none")
# Since 0 is reserved for special meaning, joystick button 0 is identified
# as 1 here.  Button 1 is identified as 2, and so on.
# 
# Find the button you want to map by running:
# jstest /dev/input/js0

[KEYBOARD]
KEY_UP = 273 114 5
KEY_DOWN = 274 102 7
KEY_LEFT = 276 100 8
KEY_RIGHT = 275 103 6
KEY_BUTTON1 = 306 97 14
KEY_BUTTON2 = 308 115 15
KEY_BUTTON3 = 32 113 16
KEY_START1 = 49 0 4
KEY_START2 = 50 0 0
KEY_COIN1 = 53 0 1
KEY_COIN2 = 54 0 0
KEY_SKILL1 = 304 119 0
KEY_SKILL2 = 122 105 0
KEY_SKILL3 = 120 107 0
KEY_SERVICE = 57 0 0
KEY_TEST = 283 0 0
KEY_RESET = 284 0 0
KEY_SCREENSHOT = 293 0 0
KEY_QUIT = 27 113 17
END
```

Default **hypinput.ini**

As of version **v2.10.1** of Hypseus Singe you are able to use the **SDL_GameController** API for configuration.  
This is enabled via the `-gamepad` argument.

```
# To use: Rename this file to hypinput.ini and use -gamepad
#
# Hypseus uses SDL2 Keycodes and SDL_GameController
# SWITCH = Key1 Key2 Joy (Axis)

# Available AXIS MACROS
#
# AXIS_LEFT_UP
# AXIS_LEFT_DOWN
# AXIS_LEFT_LEFT
# AXIS_LEFT_RIGHT
# AXIS_RIGHT_UP
# AXIS_RIGHT_DOWN
# AXIS_RIGHT_LEFT
# AXIS_RIGHT_RIGHT
#
# Available BUTTON MACROS
#
# BUTTON_A
# BUTTON_B
# BUTTON_X
# BUTTON_Y
# BUTTON_BACK
# BUTTON_GUIDE
# BUTTON_START
# BUTTON_LEFTSTICK
# BUTTON_RIGHTSTICK
# BUTTON_LEFTSHOULDER
# BUTTON_RIGHTSHOULDER
# BUTTON_DPAD_UP
# BUTTON_DPAD_DOWN
# BUTTON_DPAD_LEFT
# BUTTON_DPAD_RIGHT
# AXIS_TRIGGER_LEFT
# AXIS_TRIGGER_RIGHT

[KEYBOARD]
KEY_UP = SDLK_UP 0 0 AXIS_LEFT_UP
KEY_DOWN = SDLK_DOWN 0 0 AXIS_LEFT_DOWN
KEY_LEFT = SDLK_LEFT 0 0 AXIS_LEFT_LEFT
KEY_RIGHT = SDLK_RIGHT 0 0 AXIS_LEFT_RIGHT
KEY_COIN1 = SDLK_5 0 BUTTON_BACK
KEY_COIN2 = SDLK_6 0 0
KEY_START1 = SDLK_1 0 BUTTON_START
KEY_START2 = SDLK_2 0 0
KEY_BUTTON1 = SDLK_LCTRL 0 BUTTON_A
KEY_BUTTON2 = SDLK_LALT 0 BUTTON_B
KEY_BUTTON3 = SDLK_SPACE 0 AXIS_TRIGGER_RIGHT
KEY_SKILL1 = SDLK_LSHIFT 0 0
KEY_SKILL2 = SDLK_z 0 0
KEY_SKILL3 = SDLK_x 0 0
KEY_SERVICE = SDLK_9 0 0
KEY_TEST = SDLK_F2 0 0
KEY_RESET = SDLK_0 0 0
KEY_SCREENSHOT = SDLK_F12 0 0
KEY_QUIT = SDLK_ESCAPE 0 0
KEY_PAUSE = SDLK_p 0 0
KEY_CONSOLE = SDLK_BACKSLASH 0 0
KEY_TILT = SDLK_t 0 0
END
```

Traditional Joystick API configuration is still *default*:

```
# The first two entries are SDL2 keyboard codes or names (0 for "none")
#
# Find SDL2 keyboard code information here:
# https://github.com/DirtBagXon/hypseus-singe/blob/master/doc/keylist.txt
#
# Hypseus Singe supports configuration on multiple joysticks
# First joystick is defined as 0, second joystick as 1 etc.
#
# IMPORTANT: Find the joystick button and axis by running:
#
# Use the 'hypjsch' tool to help configure this file
# https://github.com/DirtBagXon/hypjsch
# With this tool, you do not need to perform the +1 detailed in this file.
#
# Alternatively:
# jstest /dev/input/js0 || jstest /dev/input/js1
#
# The third number in config is a joystick button code (or 0 for "none")
# Since 0 is reserved for special meaning, joystick button 0 is
# identified as 1. Button 1 is identified as 2, and so on.
#
# Defining 001 (or 1) identifies first joystick(0) button 0
# Defining 111 identifies second joystick(1) button 10
#
# The fourth number in config (if specified) is the joystick axis
# configuration (or 0 for "none"). Since 0 is reserved for
# special meaning, joystick axis 0 is identified as 1.
# Axis 1 is identified as 2, and so on.
#
# Only the first four switches are defined (SWITCH_UP->SWITCH_RIGHT) for axis
#
# Defining -001 (or -1) identifies first joystick(0) axis 0 in negative direction
# Defining +102 identifies second joystick(1) axis 1 in positive direction

# KEY_BUTTON3 Turns scoreboard on/off in lair/ace

[KEYBOARD]
KEY_UP = SDLK_UP SDLK_r 5 -002
KEY_DOWN = SDLK_DOWN SDLK_f 7 +002
KEY_LEFT = SDLK_LEFT SDLK_d 8 -001
KEY_RIGHT = SDLK_RIGHT SDLK_g 6 +001
KEY_COIN1 = SDLK_5 0 1
KEY_COIN2 = SDLK_6 0 0
KEY_START1 = SDLK_1 0 4
KEY_START2 = SDLK_2 0 0
KEY_BUTTON1 = SDLK_LCTRL SDLK_a 14
KEY_BUTTON2 = SDLK_LALT SDLK_s 15
KEY_BUTTON3 = SDLK_SPACE SDLK_d 16
KEY_SKILL1 = SDLK_LSHIFT SDLK_w 0
KEY_SKILL2 = SDLK_z SDLK_i 0
KEY_SKILL3 = SDLK_x SDLK_k 0
KEY_SERVICE = SDLK_9 0 0
KEY_TEST = SDLK_F2 0 0
KEY_RESET = SDLK_0 0 0
KEY_SCREENSHOT = SDLK_F12 0 0
KEY_QUIT = SDLK_ESCAPE SDLK_q 17
KEY_PAUSE = SDLK_p 0 0
KEY_CONSOLE = SDLK_BACKSLASH 0 0
KEY_TILT = SDLK_t 0 0
END
```
### Command Parametres

Example Dragon's Lair Commands file in

`/home/pi/RetroPie/roms/daphne/lair.daphne/lair.commands`

```
-nocrc -noissues -nolog -noserversend -latency 950 -x 640 -y 480 -bank 1 00110111 -bank 0 10011000
```

See [here](https://www.daphne-emu.com:9443/mediawiki/index.php/CmdLine) for more **daphne** cmdline parameters. **hypseus** has extended parameters defined [here](https://github.com/DirtBagXon/hypseus-singe#extended-arguments-and-keys).

### Troubleshooting

If you have issues with black screen, try deleting the .dat file as it is generated the first time you parse the video files. If you transferred the .dat file from another system it may not work, so just leave the .dat file out.

It is also case sensitive so if it's not working try making the extensions in the .daphne file lowercase.
