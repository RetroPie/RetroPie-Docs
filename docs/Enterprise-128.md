# Enterprise - 64/128
***
![](https://upload.wikimedia.org/wikipedia/commons/5/5f/Enterprise128_01_%28edited%29.jpg)
***
_Enterprise is a home computer from the 80's, built with a Zilog Z80 processor. It was developed by British company Intelligent Software and marketed by Enterprise Computers, being sold starting with 1985._

_The Enterprise was made in the UK and it spread to other European countries, such as France, Spain and Germany. Perhaps the largest number of machines were to be found in Hungary. Hungarian developers wrote a lot of programs and created hardware extensions. Some machines reached ex-Soviet countries and even Egypt._
***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-ep128emu](https://github.com/libretro/ep128emu-core) | enterprise |  .img .dsk .cas .tap .dtf .wav .bas .com .trn .128 | optional | /opt/retropie/configs/enterprise/retroarch.cfg

## Emulator: [lr-ep128emu](https://github.com/libretro/ep128emu-core)

The Libretro _ep128emu_ core emulates the followig machines: Enterprise 64/128, Videoton TVC, Amstrad CPC and ZX Spectrum.

In RetroPie, the core is configured to emulate just the first 2 machines types, with the Amstrad and ZX Spectrum having a different system folders and emulators assigned.

## ROMS

Content that can be loaded by the _ep128emu_ core has the following file extensions:

- `.img` - Enterprise, CPC or TVC floppy disk image
- `.dsk` - Enterprise, CPC or TVC floppy disk image
- `.tap` - Enterprise or ZX Spectrum tape image
- `.dtf` - Enterprise compressed file
- `.cas` - Videoton TVC file format
- `.wav` - sound file interpreted as Enterprise tape
- `.bas`, `.com`, `.trn`, `.128` - common extensions for Enterprise executable files


Place your ROMs in

```
/home/pi/RetroPie/roms/enterprise
```

## BIOS

BIOS ROM files are optional, they should be copied to:

```
/home/pi/RetroPie/BIOS/ep128emu/rom
```

| Filename          | Description                     | md5sum                           |
|:-----------------:|:-------------------------------:|:--------------------------------:|
| `exos21.rom` | Enterprise 128 Expandible OS 2.1 <br> For EP128 | f36f24cbb87745fbd2714e4df881db09 |
| `basic21.rom` | Enterprise 128 BASIC Interpreter v2.1 <br> For EP128 | e972fe42b398c9ff1d93ff014786aec6 |
| `exdos13.rom` | Enterprise 128 Disk Controller v1.3 <br> For EP64/128 disk configs | ddff70c014d1958dc75378b6c9aab6f8 |
| `exos20.rom` | Enterprise 64 Expandible OS 2.0 <br> For EP64 | 5ad3baaad3b5156d6b60b34229a676fb |
| `basic20.rom` | Enterprise 64 BASIC Interpreter v2.0 <br> For EP64 | 8e18edce4a7acb2c33cc0ab18f988482 |
| `epfileio.rom` | Enterprise 128 Direct File I/O <br> For loading from host file (instead of disk or tape image) | a68ebcbc73a4d2178d755b7755bf18fe |
| `exos24uk.rom` | Enterprise 128 Expandible OS 2.4 <br> Only for enhanced functions (fast memory test) | 55af78f877a21ca45eb2df68a74fcc60 |
| `hun.rom` | Enterprise 128 Hungarian language extension | 22167938f142c222f40992839aa21a06 |
| `epdos16f.rom` | Enterprise 128 EP-DOS | 6593dff00ab32a4b1fc084674ededf2b |
| `exdos14isdos10uk.rom` | Enterprise 128 IS-DOS (CP/M) | f91c4a507cc6895bdd9c43df4f021df3 |
| `brd.rom` | Enterprise 128 German language extension | 6af0402906944fd134004b85097c8524 |
| `zt19uk.rom` | Enterprise 128 ZozoTools extension <br> For loading from DTF files | 228540b6be83ae2acd7569c8ff0f91d0 |
| `tvc22_sys.rom` | Videoton TVC system BIOS <br> For TVC emulation | 8c54285f541930cde766069942bad0f2 |
| `tvc22_ext.rom` | Videoton TVC extension BIOS <br> For TVC emulation | 5ce95a26ceed5bec73995d83568da9cf |
| `tvcfileio.rom` | Videoton TVC Direct File I/O <br> For loading from host file (instead of disk or tape image) | a2cf86ba8e7fc58b242137fe59036832 |
| `tvc_dos12d.rom` | Videoton TVC disk BIOS <br> For TVC disk configs | 88dc7876d584f90e4106f91444ab23b7 |

## Controls
_lr-ep128emu_ utilises Retroarch configurations. Add custom retroarch controls to the `retroarch.cfg` file in
```
/opt/retropie/configs/enterprise/retroarch.cfg
```

The following devices are configured automatically based on the emulated system:

| Emulated machine | User 1 default joypad | User 2 default joypad | User 3 default joypad |
|------------------|-----------------------|-----------------------|-----------------------|
| Enterprise | Internal | External 1 | External 2 |
| TVC | Internal | External 1 | External 2 |

See more details about the emulated joypad and keyboard at <https://docs.libretro.com/library/ep128emu/#joypad>.
