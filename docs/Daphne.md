***
![daphne_logo](https://cloud.githubusercontent.com/assets/10035308/13100363/9480ba8e-d4f9-11e5-974a-a514e3008837.png)
***
_Laserdiscs were predecessors to the DVD. The first laserdisc game was released in 1982. Laserdisc games function much like interactive fiction where you choose your own story and the video adapts to the path you choose to take._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Daphne](http://www.daphne-emu.com/site3/index_hi.php) | daphne  | .daphne | none | /opt/retropie/configs/daphne/dapinput.ini |

## Emulator: [Daphne](http://www.daphne-emu.com/site3/index_hi.php)

Matt Ownby is the developer of Daphne. For the best replication of Laserdisc games check out his Dexter project [HERE](http://www.daphne-emu.com/mediawiki/index.php/DexterFAQ)

## ROMS

Accepted extensions: **.daphne**

Place your Laserdisc roms in 

```
/home/pi/RetroPie/roms/daphne
```

The file structure is like so:

```
roms
|-- daphne
|    |   (The folder below holds a laserdisc...".daphne"
|    |   tells emulationstation to add this to the menu,
|    |   and "dle21" tells daphne to use that game engine)
|    |
|    |-- dle21.daphne     
|    |    |-- dle21.commands  (Optional extra command-
|    |    |                   line params!)
|    |    |-- dle21.txt      (Framefile)
|    |    |-- lair.m2v
|    |    |-- lair.ogg
|    |
|    |                (All roms go into this roms folder)
|    +-- roms
|         +-- dle21.zip
```

## Controls

Controls are located in 

```
/opt/retropie/configs/daphne/dapinput.ini
```

**Default Keyboard Controls:**

|Key|Action|
|:---:|---|
|ESC|Quit the game|
|5 and 6|Insert Coin (coin chutes)|
|1|Player 1 Start (and "FEET" in Cliffhanger)|
|2|Player 2 Start (and "FEET" in Cliffhanger)|
|Arrow Keys|Directional Movement|
|CTRL or Space Bar|Button #1 (Primary fire and/or Sword)|
|Left ALT|Button #2 (Alternate fire, used in Bega's Battle, Cobra Command, etc)|
|Left Shift|Button #3 (used in a few games like Road Blaster, if memory serves)|
|/ (keypad)|Cadet skill level (Space Ace)|
|* (keypad)|Captain skill level (Space Ace)|
|-(keypad)|Space Ace skill level (Space Ace)|
|P|Pause game (laserdisc player must be playing)|
|T|Tilt game (just a gimmick, only works in a few games)|
|9|Go into service mode (used in Dragon's Lair 2)|
|F2|Go into test mode (similar to service mode, used in Cliff Hanger)|
|F3|Reset/reboot game|
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

### Command Parametres

Example Dragon's Lair Commands file in

`/home/pi/RetroPie/roms/daphne/lair.daphne/lair.commands`

```
-nocrc -noissues -nolog -noserversend -latency 950 -x 640 -y 480 -bank 1 00110111 -bank 0 10011000
```

See [here](http://www.daphne-emu.com/mediawiki/index.php/CmdLine) for more cmdline parameters.

### Troubleshooting

If you have issues with black screen, try deleting the .dat file as it is generated the first time you parse the video files. If you transferred the .dat file from another system it may not work, so just leave the .dat file out.

It is also case sensitive so if it's not working try making the extensions in the .daphne file lowercase.