***
![segacd](https://cloud.githubusercontent.com/assets/10035308/12212918/3dc372e4-b62d-11e5-9318-f14163eae0cb.png)
***
The Sega CD was yet another add-on to the Sega Genesis. It was released in 1991.

***
## Emulators: [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX), [lr-picodrive](https://github.com/libretro/picodrive)
Genesis-Plus-GX is recommended for the Pi 2 as it has better accuracy and speed.

## ROMS
Accepted File Extensions: **.smd .bin .md .iso**

Place your Sega CD ROMS (.bin AND .cue) in
```
/home/pi/RetroPie/roms/segacd
```

If you don't have the corresponding .cue file in the same folder as your .bin file, your game may not have sound.

## BIOS

### lr-picodrive

The BIOS filename is: **us_scd1_9210.bin** 

Place this lr-Picodrive BIOS file in
```
/home/pi/RetroPie/BIOS
```
BIOS files that may also work are: eu_mcd1_9210.bin, jp_mcd1_9112.bin (Europe and Japan respectively)

### lr-Genesis-Plus-GX

The BIOS filename is: **bios_CD_U.bin** (can be renamed from the above BIOS)

Place this lr-Genesis-Plus-GX BIOS file in
```
/home/pi/RetroPie/roms/segacd
```
the alternate BIOS files above can be renamed: bios_CD_E.bin, bios_CD_J.bin (Europe and Japan respectively)

## Controls

lr-picodrive and lr-genesis-plus-gx utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/segacd/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

### 3 Button Genesis/MegaDrive Controller

![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)

### 6 Button Genesis/MegaDrive Controller

![genesis6btn](https://cloud.githubusercontent.com/assets/10035308/7336429/7e524110-ebbb-11e4-8777-05a824384d34.png)

### 6 Button Genesis/MegaDrive ArcadePad Controller

![megadrive6btnarcadepaddiagram](https://cloud.githubusercontent.com/assets/10035308/8268483/8b1b6dae-1744-11e5-9407-df58e2a81aad.png)