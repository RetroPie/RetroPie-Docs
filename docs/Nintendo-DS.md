***
![nds](https://cloud.githubusercontent.com/assets/10035308/12213354/eab79344-b633-11e5-805b-7d1a93fa44dd.png)
***
The Nintendo DS is a handheld video game console that was released by Nintendo in 2004. The DS stands for Dual Screen.
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [DraStic](http://drastic-ds.com/) | nds | .nds .zip | nds_bios_arm7.bin (Optional), nds_bios_arm9.bin (Optional), nds_firmware.bin (Optional) | /opt/retropie/configs/nds/drastic/config/drastic.cfg |
| [lr-desmume](https://github.com/libretro/desmume) | nds | .nds .zip | none | /opt/retropie/configs/nds/retroarch.cfg |

## Emulator: [DraStic](http://drastic-ds.com/)

Note that while DraStic may run very well, it is currently experimental beta software. Currently, all games that require the microphone at any point will crash.

## BIOS

The default installation of DraStic includes simulated BIOS files that will work in most cases. Actual BIOS files (listed above) can be added to
```
/opt/retropie/configs/nds/drastic/system
```

## ROMS
Accepted File Extensions: **.nds .zip**

Place your DS ROMs in 
```
/home/pi/RetroPie/roms/nds
```

## Controls

### lr-desmume Controls

Add custom controls using the DraStic GUI (by pressing RIGHT ANALOG RIGHT), or by editing
```
/opt/retropie/configs/nds/drastic/config/drastic.cfg
```

## Emulator: [lr-desmume](https://github.com/libretro/desmume)

Note that lr-desmume is very experimental and lags quite a bit even with an overclocked RPI 2/3.

## BIOS

Not needed

## ROMS
Accepted File Extensions: **.nds .zip**

Place your DS ROMs in 
```
/home/pi/RetroPie/roms/nds
```

## Controls

### lr-desmume Controls
lr-desmume utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/nds/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![nintendo_ds_diagram](https://cloud.githubusercontent.com/assets/10035308/16599645/7f549f56-42c0-11e6-88a8-3acda5287da3.png)