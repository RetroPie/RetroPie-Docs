***
![mame](https://cloud.githubusercontent.com/assets/10035308/12213821/0acf7328-b63d-11e5-8127-48c8c5d31fe3.png)
***
_MAME stands for Multiple Arcade Machine Emulator. MAME can emulate thousands of games that otherwise would have been lost in the ash-heaps of history._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [Mame4all-Pi](https://github.com/RetroPie/mame4all-pi) | arcade **or** mame-mame4all | .zip | neogeo.zip | /opt/retropie/configs/mame-mame4all/mame.cfg |
| [lr-imame4all](https://github.com/libretro/imame4all-libretro) | arcade **or** mame-mame4all | .zip | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/mame-mame4all/retroarch.cfg |
| [lr-mame2003](https://github.com/libretro/mame2003-libretro) | arcade **or** mame-libretro | .zip | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/mame-libretro/retroarch.cfg |
| [lr-mame2010](https://github.com/libretro/mame2010-libretro) | arcade **or** mame-libretro | .zip | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/mame-libretro/retroarch.cfg |
| [AdvanceMAME .94](http://advancemame.sourceforge.net/) | arcade **or** mame-advmame | .zip | neogeo.zip | /opt/retropie/configs/mame-advmame/advmame-0.94.0.rc |
| [AdvanceMAME](http://advancemame.sourceforge.net/) | arcade **or** mame-advmame | .zip | neogeo.zip | /opt/retropie/configs/mame-advmame/advmame-1.4.rc |

## Emulators: [AdvanceMAME](http://advancemame.sourceforge.net/), [Mame4all-Pi](https://github.com/RetroPie/mame4all-pi), [lr-imame4all](https://github.com/libretro/imame4all-libretro), [lr-mame2003](https://github.com/libretro/mame2003-libretro), [lr-mame2010](https://github.com/libretro/mame2010-libretro)

Mame4all-pi has the best performance of them all, but a limited romset. This is the best choice for the Raspberry Pi 1. lr-imame4all is the libretro equivalent, with possibly weaker performance, but features all the libretro benefits (RetroArch controller configurations, shader support, save states, etc). lr-mame2003 is a good choice for Raspberry Pi 2 and up, as it has a comprehensive romset, and good performance, as well as also being libretro. The AdvMames are popular as they have a huge romset, but they're non-libretro. All other MAME cores are experimental and should normally be avoided.

See Also: [FBA](https://github.com/petrockblog/RetroPie-Setup/wiki/FinalBurn-Alpha), [Neo Geo](https://github.com/petrockblog/RetroPie-Setup/wiki/GnGeo-Pi)

## ROMS

Because MAME emulates many different pieces of hardware and thousands of games it can be hard to keep track of everything. ROMs for MAME are probably the most confusing thing about RetroPie.

Accepted File Extensions: **.zip**

**For information on how to rebuild newer romsets to be compatible with these emulators see this post:**
**[Managing ROMs](https://github.com/petrockblog/RetroPie-Setup/wiki/Managing-ROMs)**

## **Arcade**

All arcade based romsets can be placed in the `arcade` rom folder but you will have to specify which emulator each rom will use from the [Runcommand Menu](runcommand)

[**All Arcade ROMS Compatibility List**](https://docs.google.com/spreadsheets/d/1antILt7D12EWOFzyJwTfB86NceghMJKXG7CdYumuHec/edit?usp=sharing) feel free to contribute to the list.

## **MAME4ALL-Pi**

Place your MAME4ALL-Pi ROMs in
```
/home/pi/RetroPie/roms/mame-mame4all
```

[Romset Used: **0.37b5**](https://archive.org/details/MAME0.37b5-MAME2000-ROMSet)

Total Games Emulated: [2270](http://code.google.com/p/imame4all/wiki/GameList) 

[**MAME4ALL-PI COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing)  feel free to contribute to the list.

## **lr-imame4all**

Place your lr-imame4all ROMs in
```
/home/pi/RetroPie/roms/mame-mame4all
```

[Romset Used: **0.37b5**](https://archive.org/details/MAME0.37b5-MAME2000-ROMSet)

Total Games Emulated: [2270](http://code.google.com/p/imame4all/wiki/GameList) 

[**lr-IMAME4ALL COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1Fmx2RPcgVgIIeKpaBKNEGWCDuu3DGfR-VkrnIVsIpeE/edit?usp=sharing)  feel free to contribute to the list.

## **AdvanceMAME**

Place your AdvanceMAME ROMs in
```
/home/pi/RetroPie/roms/mame-advmame
```

Romset Used: **.94** (AdvMame .94) or **.106** (AdvMame 1.4)

Total Games Emulated: **5563** (0.94.0) **6166** (1.4) (includes clones etc..)

[**AdvMame .94 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1AEQ94buG0rvbW0xdnYKeuEhHeCbuZlRfRJQCb1Dt8fw/edit?usp=sharing)  feel free to contribute to the list.

[**AdvMame 1.4 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1RapyxChe2BMOfbX-FsCup9SXGxvS1WmXAofwaTJtmxc/edit?usp=sharing)  feel free to contribute to the list.

## lr-Mame2003

**Please see [lr-mame2003](https://github.com/RetroPie/RetroPie-Setup/wiki/lr-mame2003) for information on how to configure specfic features of this emulator.**

Place your lr-Mame2003 ROMs in
```
/home/pi/RetroPie/roms/mame-libretro
```

[Romset Used: **.78**](https://archive.org/details/MAME0.78-MAME2003-ROMs-CHDs-Samples)

Total Games Emulated: 4705 (includes clones etc...)

[**lr-mame2003 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing)  feel free to contribute to the list.

## lr-Mame2010 (EXPERIMENTAL)

Place your lr-Mame2010 ROMs in
```
/home/pi/RetroPie/roms/mame-libretro
```

Romset Used: **.139**

Total Games Emulated: 8782 (includes clones etc...)

[**lr-mame2010 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1IRSmFrSDvIc6gAw0gn12TcQ3HDOwmrETTor8wvvb7VI/edit?usp=sharing) feel free to contribute to the list.

You will get errors loading some mame roms, not all roms are compatible or working. You will need to download ROMs that are confirmed working with your version of MAME

## BIOS
Some ROMs may need the **neogeo.zip** BIOS in order to run. Place the neogeo.zip BIOS file in the same folder as your ROMs
```shell
/home/pi/RetroPie/roms/mame-mame4all
```

These are the contents of a verified working neogeo.zip BIOS file *Note that each emulator requires different set of files so all the files may not be necessary.

**Please notice** that the file 000-lo.lo has two different versions:
* a 2 KB file, with CRC-32 of `E09E253C`
* a 3 KB file, with CRC-32 of `5A86CFF2`

Make sure you choose the suitable file for the emulator according to its specification found in the [.dat file](https://github.com/RetroPie/RetroPie-Setup/wiki/Managing-ROMs#step-3---acquire-dat-files).

```shell
000-lo.lo
asia-s3.rom
japan-j3.bin
neo-epo.bin
neo-geo.rom
neo-po.bin
neodebug.bin
neodebug.rom
neopen.sp1
ng-sfix.rom
ng-sm1.rom
sfix.sfix
sfix.sfx
sm1.sm1
sp-1v1_3db8c.bin
sp-45.sp1
sp-e.sp1
sp-j2.rom
sp-j2.sp1
sp-s.sp1
sp-s2.sp1
sp-u2.sp1
sp1.jipan.1024
uni-bios.22
uni-bios.rom
uni-bios_1_0.rom
uni-bios_1_1.rom
uni-bios_1_2.rom
uni-bios_1_2o.rom
uni-bios_1_3.rom
uni-bios_2_0.rom
uni-bios_2_1.rom
uni-bios_2_2.rom
uni-bios_2_3.rom
uni-bios_2_3o.rom
uni-bios_3_0.rom
uni-bios_3_1.rom
uni-bios_3_2.rom
usa_2slt.bin
v2.bin
vs-bios.rom
```
## Controls
AdvanceMAME and Mame4all-Pi have the same method in setting up controls, imame4all-libretro utilises RetroArch configurations

### AdvanceMAME and Mame4all-Pi

While in a game press Tab to open the menu to set up controls

### lr-imame4all

lr-imame4all utilises RetroArch configs.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/mame-mame4all/retroarch.cfg
```
### lr-mame2003, lr-mame2010

lr-mame2003 and lr-mame2010 utilise retroarch configs.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/mame-libretro/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)