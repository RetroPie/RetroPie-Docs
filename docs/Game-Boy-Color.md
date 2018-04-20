***
![gbc](https://cloud.githubusercontent.com/assets/10035308/12191836/672b3014-b596-11e5-9bbe-bcafd30bb402.png)
***
_The Game Boy Color was an 8 bit handheld gaming console released by Nintendo in 1998. Pokemon Yellow anyone?_

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-gambatte](https://github.com/libretro/gambatte-libretro) | gbc  | .7z .gbc .zip | none | /opt/retropie/configs/gbc/retroarch.cfg |
| [lr-tgbdual](https://github.com/libretro/tgbdual-libretro) | gbc  | .7z .gbc .zip | none | /opt/retropie/configs/gb/retroarch.cfg |
| [lr-mgba](https://github.com/libretro/mgba) | gbc  | .7z .gb .zip | gbc_bios.bin | /opt/retropie/configs/gbc/retroarch.cfg |

## Emulators: [lr-gambatte](https://github.com/libretro/gambatte-libretro), [lr-tgbdual](https://github.com/libretro/tgbdual-libretro),  [lr-mgba](https://github.com/libretro/mgba)

lr-gambatte is the prefered single-player emulator, while lr-tgbdual runs two instances of the same game for either two-player link cable games or parallel play on the same system.
lr-mgba is an alternative emulator, supports local cable games, Game Boy BIOS and Super Game Boy.

## ROMS

Accepted File Extensions: **.7z .gbc .zip**

Place your Game Boy Color ROMs in
```
/home/pi/RetroPie/roms/gbc
```

## BIOS

`lr-mgba` can use the original Game Boy Color BIOS: **gbc_bios.bin**

`lr-mgba` can use the original Super Game Boy BIOS: **sgb_bios.bin**

Place the BIOS in
```
/home/pi/RetroPie/BIOS
```

The correct MD5 for **gbc_bios.bin** is `dbfce9db9deaa2567f6a84fde55f9680`

The correct MD5 for **sgb_bios.bin** is `d574d4f9c12f305074798f54c091a8b4`

## Controls

Both emulators utilise Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/gbc/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![gameboycolor](https://cloud.githubusercontent.com/assets/10035308/7334404/bd65e496-eb4e-11e4-82e6-78494534d305.png)