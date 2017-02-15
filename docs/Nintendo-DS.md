***
![nds](https://cloud.githubusercontent.com/assets/10035308/12213354/eab79344-b633-11e5-805b-7d1a93fa44dd.png)
***
The Nintendo DS is a handheld video game console that was released by Nintendo in 2004. The DS stands for Dual Screen.
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [DraStic](http://drastic-ds.com) | nds | .nds .zip | drastic_bios_arm7.bin, drastic_bios_arm9.bin | /opt/retropie/configs/nds/drastic/config/drastic.cfg |
| [lr-desmume](https://github.com/libretro/desmume) | nds | .nds .zip | none | /opt/retropie/configs/nds/retroarch.cfg |

Note that lr-desmume is very experimental and lags quite a bit even with an overclocked RPI 2/3. Now DraStic on the other hand, runs at about full speed on a RPI 2/3. Both can be installed through the experimental menu in the [RetroPie Setup Script](Updating RetroPie).

## Emulator: [DraStic](http://drastic-ds.com), [lr-desmume](https://github.com/libretro/desmume)

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

### DraStic Controls
DraStic controls and configurations are located in
```
/opt/retropie/configs/nds/drastic/config/drastic.cfg
```
