***
![gba](https://cloud.githubusercontent.com/assets/10035308/12191989/d423d454-b597-11e5-866f-8aaeec0b88b9.png)
***
_The Game Boy Advance is a 32 bit handheld video game console released by Nintendo in 2001._

***
## Emulators: [gpSP](https://github.com/DPRCZ/gpsp), [lr-gpSP](https://github.com/libretro/gpsp), [lr-vba-next](https://github.com/libretro/vba-next), [lr-mgba](https://github.com/libretro/mgba)

GPSP has separate controls than lr-gpSP, lr-vba-next, and lr-mgba. lr-gpSP, lr-vba-next, and lr-mgba all utilise RetroArch configurations (see below under controls)

## ROMS
Accepted File Extensions: **.gba**

Place your Game Boy Advance ROMS in 
```
/home/pi/RetroPie/roms/gba
```

## BIOS
The Game Boy Advance requires a BIOS called **gba_bios.bin**

Place the BIOS in
```
/home/pi/RetroPie/BIOS
```

## Controls

There are two ways to configure your Game Boy Advance controls depending on the emulator.

### lr-gpSP, lr-vba-next, and lr-mgba

lr-gpSP, lr-vba-next, and lr-mgba utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/gba/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![gameboyadvance](https://cloud.githubusercontent.com/assets/10035308/7334407/bd688f52-eb4e-11e4-8899-246bad0ad139.png)

### gpSP

To configure your controls for gpSP, once you are in a game you can press F10 to access the menu

**if you want your settings to be saved you need to select quit from the F10 menu instead of pressing esc on the keyboard**

For Gamepad: Navigate to configure gamepad input and modify the controls to fit your preferences.

**Example Gamepad Controls**
```shell
D-pad up: asix Y-
D-pad down: asix Y+
D-pad left: asix X-
D-pad right: asix X+
A: Button 1
B: Button 2
Left Trigger: Button 5
Right Trigger: Button 6
Start: Button 3
Select: Button 4

Menu Hotkey: yes  (this means if you hold select+right trigger it will open the menu- but it is mapped to whichever buttons you configure for select and right trigger above)
```
For Keyboard: Navigate to configure keyboard input and modify the controls to fit your preferences.

**Example Keyboard Controls**
```shell
D-pad up: Up
D-pad down: Down
D-pad left: Left
D-pad right: Right
A: Z
B: X
Left Trigger: A
Right Trigger: S
Start: Return
Select: Backspace
```
## Video Tutorial:

<a href="https://www.youtube.com/watch?v=eM9BB9v9288" target="_blank"><img src="https://i.ytimg.com/vi_webp/eM9BB9v9288/mqdefault.webp" 
alt="GBA Configuration Video" width="300" height="180" border="10" /></a>