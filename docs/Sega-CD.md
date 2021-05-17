***
![segacd](https://cloud.githubusercontent.com/assets/10035308/12214194/e316cbd2-b647-11e5-87a0-fd8f03b75edd.png)
***
The Sega CD was an add-on to the Sega Mega Drive/Genesis. It was released in 1991.

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX) | segacd | .bin .chd .cue .iso .m3u | bios_CD_U.bin, bios_CD_E.bin, bios_CD_J.bin | /opt/retropie/configs/segacd/retroarch.cfg |
| [lr-picodrive](https://github.com/libretro/picodrive) | segacd | .bin .cue .iso .m3u | us_scd1_9210.bin, eu_mcd1_9210.bin, jp_mcd1_9112.bin | /opt/retropie/configs/segacd/retroarch.cfg |

## Emulators: [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX), [lr-picodrive](https://github.com/libretro/picodrive)
**lr-genesis-plus-gx** is recommended for the Pi 2/3 as it has better accuracy. 

## ROMS
Accepted File Extensions: **.bin .chd .cue .iso**, **.m3u** for multi-disc games.    
Note: .bin files won't be displayed within Emulation Station, they will be referenced via the .cue.

Place your Sega CD ROMS (.chd .iso OR .bin AND .cue) in
```
/home/pi/RetroPie/roms/segacd
```
If you don't have the corresponding .cue file in the same folder as your .bin file, your game may not have sound.
### Multi-Disc games
For multi-disc games using `.cue` or `.chd` format, you can create a `.m3u` playlist to be able to easily change discs from the RetroArch's _Disk Control_ menu. 

To change the disc through RetroArch, from the "Quick Menu", enter "Disk Control", use the "Disk Cycle Tray Status" to open the virtual disk tray, change the disk number to the correct one, then use the "Disk Cycle Tray Status" to close the virtual disk tray.

Example playlist for _Fahrenheit_:

Folder Structure:

* Fahrenheit (Disc 1).cue
* Fahrenheit (Disc 1).bin
* Fahrenheit (Disc 2).cue
* Fahrenheit (Disc 2 - track1).bin
* Fahrenheit (Disc 2 - track2).bin

Contents of the `.m3u` playlist

````
Fahrenheit (Disc 1).cue
Fahrenheit (Disc 2).cue
````

## CHD Files

lr-genesis-plus-gx has support for the CHD (V1-V5) archive format. This format will save space and allow you to keep your Mega CD/Sega CD ROM folder tidy. See [Creating CHDs from CD-ROMS](CHD-files.md#creating-chds-from-cd-roms).

* Corpse Killer 32x version only (1 disc)
* Dracula Unleashed (2 discs)
* Fahrenheit (2 discs)
* Ground Zero Texas (2 discs)
* Night Trap (2 discs)
* Penn & Teller - Smoke and Mirrors (2 disc)
* Sherlock Holmes - Consulting Detective Volume II (2 discs)
* Prize Fighter (2 discs) (can be played as individual discs in chd file format with lr-genesis-plus-gx)
* Slam City with Scottie Pippen (4 discs) (non-32X version can be played as individual discs in chd file format with lr-genesis-plus-gx)
* Supreme Warrior (2 discs, 32x version only)
* Surgical Strike (1 disc, 32x version only)

## BIOS

### lr-picodrive

The BIOS filename is: **us_scd1_9210.bin** 

Place this lr-picodrive BIOS file in
```
/home/pi/RetroPie/BIOS
```
BIOS files that may also work are: eu_mcd1_9210.bin, jp_mcd1_9112.bin (Europe and Japan respectively)

### lr-genesis-plus-gx

The BIOS filename is: **bios_CD_U.bin** (can be renamed from the above BIOS)

Place this lr-genesis-plus-gx BIOS file in
```
/home/pi/RetroPie/BIOS
```
the alternate BIOS files above can be renamed: bios_CD_E.bin, bios_CD_J.bin (Europe and Japan respectively)  
  
Video Guide using lr-genesis-plus-gx: https://www.youtube.com/watch?v=PkktRuK8uWU

### Checksums

| lr-picodrive filename | lr-Genesis-Plus-GX filename | No-Intro filename | md5sum |
| :---: | :---: | :---: | :---: |
| us_scd1_9210.bin | bios_CD_U.bin | [BIOS] Sega CD (USA) (v1.10).md | 2efd74e3232ff260e371b99f84024f7f |
| eu_mcd1_9210.bin | bios_CD_E.bin | [BIOS] Mega-CD (Europe) (v1.00).md | e66fa1dc5820d254611fdcdba0662372 |
| jp_mcd1_9112.bin | bios_CD_J.bin | [BIOS] Mega-CD (Asia) (v1.00S).md | bdeb4c47da613946d422d97d98b21cda |

## Controls

lr-picodrive and lr-genesis-plus-gx utilise RetroArch configurations

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/segacd/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

### 6 button controller

See [6 button controller](Mega-Drive-Genesis#6-button-controller)

### 3 Button Genesis/Mega Drive Controller

![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)

### 6 Button Genesis/Mega Drive Wireless Controller

![sega_megadrive_6button_diagram](https://cloud.githubusercontent.com/assets/10035308/16599642/7f43e53a-42c0-11e6-9152-c33099878ccc.png)

### 6 Button Genesis/Mega Drive ArcadePad Controller

![sega_megadrive_6button_arcadepad_diagram](https://cloud.githubusercontent.com/assets/10035308/16599641/7f43ae62-42c0-11e6-924a-50ca4e44f401.png)
