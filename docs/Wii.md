***
![wii](https://cloud.githubusercontent.com/assets/10035308/18609217/13ac9b3a-7cba-11e6-990b-bf983afafbbc.png)
***
_The Wii is a home video game console that was released by Nintendo on November 19, 2006. It was the first console to successfully market motion controllers. After 7 years of production, the orginal console was discontinued in 2013. A scaled down version known as the Wii Mini remained in production until 2017._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [dolphin](https://github.com/dolphin-emu/dolphin.git) | wii  | .iso | none | /opt/retropie/configs/wii/Config |

> **Note This is only for x86 builds- Not the Raspberry Pi!.**

## Emulator: [dolphin](https://github.com/dolphin-emu/dolphin.git)

## ROMS

Accepted File Extensions: **.iso**

Place your Wii ROMs in
```
/home/pi/RetroPie/roms/wii
```
## Controls

Dolphin controls must currently be mapped via the GUI, accessed by launching **dolphin-gui** via [Runcommand](Runcommand).

From there there graphical client will launch and you can bind your controller in the Dolphin Interface as well as change settings.

### Exiting

To exit Dolphin via a keyboard use **Alt+F4** or additionally **Escape** available in **dolphin** (not **dolphin-gui**).

To map a button on your controller to exit Dolphin you will need to launch via the gui method above. 
Once in the menu navigate to Hotkey Behavior.  
Switch the device indicator to your controller
select the exit function and map a button like select to this function.
You will also need to configure in the graphics window to always force window on top and to hide mouse/cursor

Now enter back into emulationstation mode and launch a dolphin game from the gamecube menu
press x when the game is starting
Select **dolphin-gui** instead of dolphin as the runcommand default emulator.
Launch game
You will now be able to exit back to emulationstation with that button you mapped. 
