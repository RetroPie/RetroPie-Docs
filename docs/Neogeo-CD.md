***
_ The Neo Geo CD is the second home video game console of SNK Corporation's Neo Geo family, released on September 9, 1994, four years after its cartridge-based equivalent. It was discontinued in 1997 with sales of 570,000 systems._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-neocd](https://github.com/libretro/neocd_libretro) | neogeo  | .chd .cue .zip | uni-bioscd.rom | /opt/retropie/configs/neogeo/retroarch.cfg |

## Emulator: [lr-neocd](https://github.com/libretro/neocd_libretro) 

**lr-neocd**  is a complete rewrite of NeoCD from scratch in modern C++11. It is designed with accuracy and portability in mind rather than being all about speed like the the older versions.

## ROMS
Accepted File Extensions: **.cue** **.chd** **.zip**

Place your Neogeo CDROM images in
```
/home/pi/RetroPie/roms/neogeo
```
## BIOS
You will need a minimum of two BIOS files (eg. ng-lo.rom, uni-bioscd.rom) 

| Filename                  | Hash (MD5)                       |
| ------------------------- | -------------------------------- |
| neocd_f.rom    | a5f4a7a627b3083c979f6ebe1fabc5d2df6d083b |
| neocd_sf.rom   | 4a94719ee5d0e3f2b981498f70efc1b8f1cef325 |
| neocd_t.rom    | cc92b54a18a8bff6e595aabe8e5c360ba9e62eb5 |
| neocd_st.rom   | 19729b51bdab60c42aafef6e20ea9234c7eb8410 |
| neocd_z.rom    | b0f1c4fa8d4492a04431805f6537138b842b549f |
| neocd_sz.rom   | 6a947457031dd3a702a296862446d7485aa89dbb 
| front-sp1.bin  | 53bc1f283cdf00fa2efbb79f2e36d4c8038d743a |
| top-sp1.bin    | 235f4d1d74364415910f73c10ae5482d90b4274f |
| neocd.bin      | 7bb26d1e5d1e930515219cb18bcde5b7b23e2eda |
| uni-bioscd.rom | 5142f205912869b673a71480c5828b1eaed782a8 |

Place your BIOS files in:
```
/home/pi/RetroPie/BIOS
```

## Controls

lr-neocd utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/neogeo/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

