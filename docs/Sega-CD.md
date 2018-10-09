***
![segacd](https://cloud.githubusercontent.com/assets/10035308/12214194/e316cbd2-b647-11e5-87a0-fd8f03b75edd.png)
***
The Sega CD was an add-on to the Sega Genesis. It was released in 1991.

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX) | segacd | .bin .chd .cue .iso | bios_CD_U.bin, bios_CD_E.bin, bios_CD_J.bin | /opt/retropie/configs/segacd/retroarch.cfg |
| [lr-picodrive](https://github.com/libretro/picodrive) | segacd | .bin .cue .iso | us_scd1_9210.bin, eu_mcd1_9210.bin, jp_mcd1_9112.bin | /opt/retropie/configs/segacd/retroarch.cfg |

## Emulators: [lr-genesis-plus-gx](https://github.com/libretro/Genesis-Plus-GX), [lr-picodrive](https://github.com/libretro/picodrive)
**lr-genesis-plus-gx** is recommended for the Pi 2/3 as it has better accuracy. **lr-picodrive** is required for multidisc games due to lr-genesis-plus-gx's lack of support for disc swapping.

## ROMS
Accepted File Extensions: **.bin .chd .cue .iso**  
Note: .bin files wont be displayed within Emulation Station, they will be referenced via the .cue.


Place your Sega CD ROMS (.chd .iso OR .bin AND .cue) in
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

### Configuring a 6 button controller

First you need to tell retroarch to use 6 buttons, because the default is to use 3.

#### lr-picodrive

Launch a Sega CD game and go to the Retroarch menu (default mapping: `select + x`). Go to `Quick Menu -> Core Options` and set the two input devices to `6 button pad`. Then exit the Retroarch menu. Once you quit the game, the configuration will be saved within the `retroarch-core-options.cfg` file under `/opt/retropie/configs/all`. You do not need to edit this file. These core options will also take affect on any other system which you may use lr-picodrive for (eg. Sega 32X, Sega Megadrive).

#### lr-genesis-plus-gx

There are two ways to achieve this:

##### Option 1
You can edit the file `/opt/retropie/configs/segacd/retroarch.cfg` and add in the following:

    input_libretro_device_p1 = "513"
    input_libretro_device_p2 = "513"

This will set the controller type to a 6 button pad, and will reload this configuration every time the emulator is launched.

##### Option 2
You can save a Core Remap File which reloads every time the emulator is launched:

Go to the Retroarch menu (default mapping: `select + x`). Go to `Quick Menu -> Core Input Options` and set the User 1 and User 2 Device Type to be MD Joypad 6 Button.

Scroll down on the same page and select Save Core Remap File. This will save a core remap file (.rmp) to a folder called "Genesis Plus GX" in the `/opt/retropie/configs/segacd` folder. By default this remap file will load every time the emulator is launched.

### 3 Button Genesis/MegaDrive Controller

![genesis](https://cloud.githubusercontent.com/assets/10035308/7336303/aec335e0-ebb4-11e4-93b3-26037dd26ffb.png)

### 6 Button Genesis/MegaDrive Wireless Controller

![sega_megadrive_6button_diagram](https://cloud.githubusercontent.com/assets/10035308/16599642/7f43e53a-42c0-11e6-9152-c33099878ccc.png)

### 6 Button Genesis/MegaDrive ArcadePad Controller

![sega_megadrive_6button_arcadepad_diagram](https://cloud.githubusercontent.com/assets/10035308/16599641/7f43ae62-42c0-11e6-924a-50ca4e44f401.png)