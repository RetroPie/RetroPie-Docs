***
![ngpc](https://cloud.githubusercontent.com/assets/10035308/12213463/93536f40-b635-11e5-81ef-e30de2236d00.png)
***
The Neo Geo Pocket Color was a handheld video game system released by SNK in 1999.

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-beetle-ngp](https://github.com/libretro/beetle-ngp-libretro.git) | ngpc  | .7z .ngc .zip | none | /opt/retropie/configs/ngpc/retroarch.cfg |
| [lr-fbneo](https://github.com/libretro/fbneo.git) | ngp  | .7z .ngp .zip | ngp.zip | /opt/retropie/configs/ngp/retroarch.cfg |

## Emulators: [lr-beetle-ngp](https://github.com/libretro/beetle-ngp-libretro.git), [lr-fbneo](https://github.com/libretro/fbneo.git)

## ROMS
Accept File Extensions: **.7z .ngc .zip**

Place your Neo Geo Pocket Color ROMs in
```
/home/pi/RetroPie/roms/ngpc
```

NOTE: **lr-fbneo** expects the game roms to be in .zip/.7z archives named in a similar fashion to arcade romsets, so the filenames of the roms is important. Use a romset validation/building program like Clrmamepro or RomCenter to have the correct filenames, using the [FBNeo NeoGeo Pocket DAT](https://github.com/libretro/FBNeo/blob/master/dats/FinalBurn%20Neo%20(ClrMame%20Pro%20XML%2C%20NeoGeo%20Pocket%20Games%20only).dat) file and a No-Intro Neo Geo Pocket Color ROM collection.

## BIOS
**lr-fbneo** needs a BIOS ROM (`ngp.zip`) in order to run Neo Geo Pocket ROMs. The file needs to contain the `SNK Neo-Geo Pocket Color BIOS (1999)(SNK)(en-ja).bin` ROM. Place the `ngp.zip` file in `/home/pi/RetroPie/BIOS/fbneo`.

| Filename | No-Intro name | MD5 | CRC32 | 
| :--: | :--: | :--: | :--: |
| ngp.zip | [BIOS] SNK Neo Geo Pocket Color (World) (En,Ja).ngp | 3655AACEBB43A963607D4CF821FC1301 | 6EEB6F40 |

## Controls

Both emulators use Retroarch input configurations.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/ngpc/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![neogeopocketdiagram](https://cloud.githubusercontent.com/assets/10035308/8244887/0e06c54a-15e4-11e5-8f8f-28758d16c446.png)