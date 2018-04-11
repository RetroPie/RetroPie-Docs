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