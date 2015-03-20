![Atari 2600](http://upload.wikimedia.org/wikipedia/commons/0/09/Atari_2600_Logo.png)
***
_The Atari 2600 was a home video game console released by Atari in 1977_
***
## Emulators: [Stella](http://stella.sourceforge.net/), [stella-libretro](https://github.com/libretro/stella-libretro)

Both work fine. Stella-libretro is a port of Stella that utilises RetroArch configurations- see "Controls" below.

## ROMS
Accepted File Extensions: **.bin .a26 .rom .zip .gz** (stella-libretro has a hard time extracting .zip files)

Place your Atari 2600 ROMS in
```shell
/home/pi/RetroPie/roms/atari2600/
```
## Controls
You will configure controls differently depending on which emulator you use:

### Stella

Default Controls:
```shell
P0 Joystick Up: Up, J0/A1/-
P0 Joystick Down: Down, J0/A1/+
P0 Joystick Left: Left, J0/A0/-
P0 Joystick Right: Right, J0/A0/+
P0 Joystick Fire: Space, Lctrl, J0/B0
P0 Booster Top Trigger: 4
P0 Booster Handle Grip: 5

Configuration Menu: TAB

Press Tab to access configuration menu- choose input settings and under the tab Emul. Events you can create custom controller mappings to work for your individual controllers
```
### Stella-Libretro

Stella-Libretro utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/atari2600/retroarch.cfg
```
For more information on custom retroarch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)