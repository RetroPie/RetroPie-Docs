***
![zx_spectrum](https://cloud.githubusercontent.com/assets/10035308/12212920/3dc40236-b62d-11e5-8ee4-c224358c1424.png)
***
_The ZX Spectrum was an 8 bit series of home computers released by Sinclair Research in 1982._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-fuse](https://github.com/libretro/fuse-libretro) | zxspectrum  | sna .szx .z80 .tap .tzx .gz .udi .mgt .img .trd .scl .dsk | none | /opt/retropie/configs/zxspectrum/retroarch.cfg |
| [FBZX](http://www.rastersoft.com/programas/fbzx.html) | zxspectrum  | sna .szx .z80 .tap .tzx .gz .udi .mgt .img .trd .scl .dsk | none | hardcoded |
| [Fuse](http://fuse-emulator.sourceforge.net/) | zxspectrum  | sna .szx .z80 .tap .tzx .gz .udi .mgt .img .trd .scl .dsk | none | hardcoded |

## Emulators: [lr-fuse](https://github.com/libretro/fuse-libretro), [FBZX](http://www.rastersoft.com/programas/fbzx.html), [Fuse](http://fuse-emulator.sourceforge.net/)

## ROMS

Accepted File Extensions: **sna .szx .z80 .tap .tzx .gz .udi .mgt .img .trd .scl .dsk**

Place your ZX Spectrum ROMs in
```
/home/pi/RetroPie/roms/zxspectrum
```

## Video Overview:
[![ZX Spectrum Video](http://img.youtube.com/vi/_Rs20bAy-sY/0.jpg)](http://www.youtube.com/watch?v=_Rs20bAy-sY)

## Controls

### lr-fuse

lr-fuse utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/zxspectrum/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

By default, 

* Buttons A, X and Y are mapped to the joystick's fire button, and button B is mapped to the UP directional button. 
* Buttons L1 and R1 are mapped to RETURN and SPACE, respectively. 
* The SELECT button brings up the embedded, on-screen keyboard.

If you are using more than one joystick, then it is worth reading the [official documentation](https://github.com/libretro/fuse-libretro#input-devices) at lr-fuse Github page.

The default joystick emulated by lr-fuse is the Cursor joystick. If you wish to set Kempston as your default, then add the following line to the file `/opt/retropie/configs/all/zxspectrum/retroarch.cfg`:

    input_libretro_device_p1 = "513"

### Running a 48K Machine

Some ZX Spectrum games require a 16K machine (e.g. Deathchase) or will run only on a 48K machine, for example, titles from Ultimate Play The Game such as Atic Atac and Jetpac.

By default, lr-fuse runs the 128K machine but it is possible to load the 48K machine on launch in the RetroArch Core options.

1. Launch the game for which you wish to run on a 48K machine. 
2. The game will not load but launch the RGUI by pressing hotkey+X and navigate to `Quick menu` -> `Options`. 
3. Set `Model (needs content load)` to `48K` and then select `Game-options file`. This will save the setting to a game specific options file. 
4. Exit lr-fuse and when you re-launch, the game should run.

### Joypad to Keyboard Mapping
Thanks to forum member @pjft's [contribution](https://retropie.org.uk/forum/topic/16753/lr-fuse-joypad-to-keyboard-mapping) to lr-fuse, it is possible to play ZX Spectrum games without a need for a keyboard. This is useful for games that don't support joysticks such as Chuckie Egg and for games that require keyboard input in addition to a joystick (e.g. Head Over Heels).

1. Launch a game you wish to map a joypad to a keyboard.
2. Launch the RGUI by pressing hotkey+X and navigate to `Quick menu` -> `Options`. In the menu, assign a key to joypad buttons `Joypad Left mapping`, `Joypad Right mapping` etc. as required. Below is an example for Chuckie Egg.

![RetroArch Options menu for Chuckie Egg](https://user-images.githubusercontent.com/8166945/51169479-e7405680-18a3-11e9-99ac-131838813999.png)

3. Exit the RGUI and test in-game if necessary.
4. To save, return to `Quick menu` -> `Options` in the RGUI and select `Game-options file`. This will save the mappings to a game specific options file.

