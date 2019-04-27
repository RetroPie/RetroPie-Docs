***
![gba](https://cloud.githubusercontent.com/assets/10035308/12191989/d423d454-b597-11e5-866f-8aaeec0b88b9.png)
***
_The Game Boy Advance is a 32 bit handheld video game console released by Nintendo in 2001._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-mgba](https://github.com/libretro/mgba) | gba  | .7z .gba .zip | gba_bios.bin | /opt/retropie/configs/gba/retroarch.cfg |
| [lr-vba-next](https://github.com/libretro/vba-next) | gba  | .7z .gba .zip | gba_bios.bin (optional) | /opt/retropie/configs/gba/retroarch.cfg |
| [lr-gpSP](https://github.com/libretro/gpsp) | gba  | .7z .gba .zip | gba_bios.bin | /opt/retropie/configs/gba/retroarch.cfg |
| [gpSP](https://github.com/DPRCZ/gpsp) | gba  | .gba .zip | gba_bios.bin | /opt/retropie/emulators/gpsp/gpsp.cfg |

## Emulators: [lr-mgba](https://github.com/libretro/mgba), [lr-vba-next](https://github.com/libretro/vba-next), [lr-gpSP](https://github.com/libretro/gpsp), [gpSP](https://github.com/DPRCZ/gpsp)

**lr-mgba** is a modern emulator that aims to be fast and accurate, supports local cable games, external BIOS, Super Game Boy palette and border, and many other features. It also emulates [Game Boy](Game-Boy) and [Game Boy Color](Game-Boy-Color). This is the advised emulator for the RPi3B/RPi3B+.

**lr-vba-next** is a faster yet less accurate emulator possibly useful for those on a RPi2B: it is not available on the RPi0 or RPi1.

**lr-gpSP** is the default emulator for the RPi0 and RPi1: expect inaccurate emulation. It runs full speed on the RPi0, but doesn't run full speed on a RPi1.

**gpSP** is advised for full speed emulation on the RPi1. It may require manual controller reconfiguration, but outside of that has a user-friendly Select+Start exit hotkey and a Select+R hotkey to access the built-in menu enabled by default.

## ROMS
Accepted File Extensions: **.7z .gba .zip**

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

To verify your BIOS file:

```
$ md5sum /home/pi/RetroPie/BIOS/gba_bios.bin 
a860e8c0b6d573d191e4ec7db1b1e4f6  /home/pi/RetroPie/BIOS/gba_bios.bin
```

If you get something else besides that `a860...` string, that's not the correct file.

| Filename | No-intro | CRC32 | MD5 | SHA-1 |
|--------------|--------------|--------------|--------------|--------------|
| gba_bios.bin | [BIOS] Game Boy Advance (World).gba | 81977335 | a860e8c0b6d573d191e4ec7db1b1e4f6 | 300c20df6731a33952ded8c436f7f186d25d3492 |

## Controls

There are two ways to configure your Game Boy Advance controls depending on the emulator.

### lr-mgba, lr-vba-next, lr-gpSP

lr-mgba, lr-vba-next, lr-gpSP utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/gba/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nintendo_gameboyadvance_diagram](https://cloud.githubusercontent.com/assets/10035308/16599631/7f238b14-42c0-11e6-90e0-eac12cb4db3d.png)

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