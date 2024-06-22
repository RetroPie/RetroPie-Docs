***
_The Sega Model 3_ is an arcade platform produced by Sega. It is a successor to the Sega Model 2 platform, and was released in 1996.
The Model 3 was succeeded by the Sega NAOMI in 1998, followed by the Sega Hikaru in 1999 and Sega NAOMI 2 in 2000. 
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Supermodel](https://www.supermodel3.com/index.html) | arcade | .zip | | /opt/retropie/configs/arcade/supermodel3/Config |

## Emulator: [Supermodel](https://github.com/DirtBagXon/model3emu-code-sinden)
 
 RetroPie includes a fork of the Supermodel emulator that adds Sinden lightgun support with 2 player support in Linux/MacOS, with an additional ARM friendly branch, mainainted by [DirtBagXon](https://github.com/DirtBagXon/model3emu-code-sinden). For ARM devices, it needs at least a Pi4 (or equivalent SBC) to play the games at an acceptable speed. Some games will not be playable without overclocking (CPU/GPU).

 When starting a Sega Model 3 game from the `arcade` folder, use the [runcommand launch menu](Runcommand#runcommand-launch-menu) to choose the Supermodel3 emulator to play the game. The menu includes the following emulators:
  
 * _supermodel3_: default entry, runs the emulator with the default video resolution of the original arcade board. Recommended for low-powered devices, to be used in conjunction with a lower resolution video mode in order to fill most of the screen.
 * _supermodel3-scaled_: additional entry that scales the viewport to the display's video resolution. It will run the emulator fullscreen, but it needs additional processing power to scale the image. This entry should be used on a powerful system (i.e. PC).
 * _supermodel3-legacy_ (x86 only): additional entry for PC systems that are too weak to run the emulator with the new 3D renderer, it uses the _legacy3d_ renderer for the video output.
 
 To configure default options for all games or per-game options, the `Supermodel.ini` configuration file can be used. The parameters available are usually accompanied by the corresponding documetation in the file, the emulator's documentation can be consulted online [here](https://www.supermodel3.com/Help.html).

## ROMS
Accepted File Extensions: **.zip**

Place your arcade ROMS in:
```shell
/home/pi/RetroPie/roms/arcade
```

**Note**: the emulator accepts additional per-game parameters when run by specifying the desired parameters in a separate `<ROM>.commands` text file, which should be places next to the `ROM.zip` ROM file. For instance, to activate force feedback for [Daytona2](http://adb.arcadeitalia.net/dettaglio_mame.php?game_name=daytona2&arcade_only=0&autosearch=1), a `daytona2.commands` file should be created next to the `daytona2.zip` file, containing:

``` text
-force-feedback
```

Any parameter/option accepted by the emulator should be placed in the `.commands` file, separated by a newline or spaces.

## Controls

The controls are configured in the following configuration file:

``` sh
/opt/retropie/configs/arcade/supermodel3/Config/Supermodel.ini
```

The emulator will auto-detect the gamepads connected and assign the default values configured in the configuration file. Common controls mapping is given below and each game can have it's own set of configuration.

| Arcade input | Gamepad/Keyboard |
| :- | :- |
| P1 Start | KEY_1,JOY1_BUTTON9  |
| P2 Start | KEY_2,JOY2_BUTTON9  |
| P1 Coin  | KEY_3,JOY1_BUTTON10 |
| P2 Coin  | KEY_4,JOY2_BUTTON10 |
| Service A | KEY_5  |
| Service B | KEY_7  |
| Test A  | KEY_6 |
| Test B  | KEY_8 |
| P1 Joystick Up    | KEY_UP,JOY1_UP       |
| P1 Joystick Down  | KEY_DOWN,JOY1_DOWN   |
| P1 Joystick Left  | KEY_LEFT,JOY1_LEFT   |
| P1 Joystick Right | KEY_RIGHT,JOY1_RIGHT |
| P2 Joystick Up    | JOY2_UP    |
| P2 Joystick Down  | JOY2_DOWN  |
| P2 Joystick Left  | JOY2_LEFT  |
| P2 Joystick Right | JOY2_RIGHT |

### Lightgun support

 To activate the outline border needed by the Sinden Lightgun devices, add a `.commands` file for the game that should contain the `-borders=1` or `-borders=2` parameters. Other lightguns that emulate a mouse will not need the additional file and should work as-is.
