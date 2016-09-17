***
![gc](https://cloud.githubusercontent.com/assets/10035308/18609175/be037df8-7cb8-11e6-918b-a57a12ebb601.png)
***
_The GameCube is a home video game console that was released by Nintendo on September 14, 2001._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [dolphin](https://github.com/dolphin-emu/dolphin.git) | gc  | .iso | none | /opt/retropie/configs/gc/Config |

> :exclamation: This is only for x86 builds- Not the Raspberry Pi!.

## Emulator: [dolphin](https://github.com/dolphin-emu/dolphin.git)

## ROMS

Accepted File Extensions: **.iso**

Place your GameCube ROMs in
```
/home/pi/RetroPie/roms/gc
```
## Controls
Dolphin controls must currently be mapped via the GUI. You will need to drop down into terminal mode press F4 on your keyboard if you are currently in emulation station, hit the unity button and search for terminal. Click to launch. Change to the Dolphin directory

cd /opt/retropie/emulators/bin/dolphin-emu 
Launch dolphin emu
./dolphin-emu 
From there there graphical client will launch and you can bind your controller in the Dolphin Interface as well as change settings.