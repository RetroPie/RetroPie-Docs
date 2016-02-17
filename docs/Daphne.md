***
![daphne_logo](https://cloud.githubusercontent.com/assets/10035308/13100363/9480ba8e-d4f9-11e5-974a-a514e3008837.png)
***
Laserdiscs were predecessors to the DVD. The first laserdisc game was released in 1982. Laserdisc games function much like interactive fiction where you choose your own story and the video adapts to the path you choose to take.

***

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
|    |    |-- dle21.command  (Optional extra command-
|    |    |                   line params!)
|    |    |-- dle21.txt      (Framefile)
|    |    |-- lair.m2v
|    |    |-- lair.ogg
|    |
|    |                (All roms go into this roms folder)
|    +-- roms
|         +-- dle21
```

## Controls

Controls are located in 

```
/opt/retropie/configs/daphne
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

### Troubleshooting

If you have issues with black screen, try deleting the .dat file as it is generated the first time you parse the video files. If you transferred the .dat file from another system it may not work, so just leave the .dat file out.