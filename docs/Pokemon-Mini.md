***
![pokemini](https://user-images.githubusercontent.com/22881403/45140090-634cc400-b177-11e8-8dae-1f9496366245.png)
***
_The Pokemon Mini is a handheld game console that was released by Nintendo in 2001.  All of the games released for it were themed around Nintendo's *Pokemon* franchise._
***

| Emulator | Rom Folder | Extension |
| :---: | :---: | :---: |
| [lr-pokemini](https://github.com/libretro/pokemini) | pokemini | .min .zip |

## Emulator: [lr-pokemini](https://github.com/libretro/pokemini)
This emulator can be installed from the experimental menu of the [RetroPie-Setup script.](https://github.com/RetroPie/RetroPie-Setup/wiki/Updating-RetroPie#using-the-retropie-setup-script)

A bug in the emulator causes two titles to not be able to save properly.  These two titles are "Pokemon Pinball Mini" and "Pokemon Race Mini".

## ROMS

Accepted File Extensions: **.min .zip** 

Place your Pokemon Mini ROMs in:
```
/home/pi/RetroPie/roms/pokemini
```
## BIOS

### lr-pokemini

lr-pokemini supports the **bios.min** BIOS file, but it isn't required.

Place the BIOS in
```
/home/pi/RetroPie/BIOS
```

| Recognized Name | No-Intro Name | md5sum | CRC32 |
| :--: | :--: | :--: | :--: |
| bios.min | [BIOS] Nintendo Pokemon Mini (World) | 1E4FB124A3A886865ACB574F388C803D | AED3C14D |

## Controls

lr-pokemini utilises Retroarch configurations.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/pokemini/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)