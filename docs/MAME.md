![MAME Logo](https://emillister.files.wordpress.com/2010/02/mame.png)

***
_MAME stands for Multiple Arcade Machine Emulator. MAME can emulate thousands of games that otherwise would have been lost in the ash-heaps of history._

***
## Emulators: [AdvanceMAME](http://advancemame.sourceforge.net/), [Mame4all-Pi](https://github.com/RetroPie/mame4all-pi), [imame4all-libretro](https://github.com/libretro/imame4all-libretro)
Mame4all-pi seems to have the best performance of them all but AdvanceMAME has support for more games. imame4all libretro can be compelling because it utilises RetroArch controller configurations.

See Also: [FBA](https://github.com/petrockblog/RetroPie-Setup/wiki/FinalBurn-Alpha), [Neo Geo](https://github.com/petrockblog/RetroPie-Setup/wiki/GnGeo-Pi)

## ROMS

Because MAME emulates many different pieces of hardware and thousands of games it can be hard to keep track of everything. ROMs for MAME are probably the most confusing thing about RetroPie.

Accepted File Extensions: **.zip**

**For information on how to rebuild newer romsets to be compatible with these emulators see this post:**
**[Managing ROMs](https://github.com/petrockblog/RetroPie-Setup/wiki/Managing-ROMs)**

### **MAME4ALL-Pi**

Romset Used: **0.37b5**

Total Games Emulated: [2270](http://code.google.com/p/imame4all/wiki/GameList) 

### [**MAME4ALL-PI COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing)  feel free to contribute to the list.


Place your MAME4ALL-Pi ROMs in
```
/home/pi/RetroPie/roms/mame-mame4all
```
### **imame4all-libretro**

Romset Used: **0.37b5**

Total Games Emulated: [2270](http://code.google.com/p/imame4all/wiki/GameList) 

### [**IMAME4ALL-Libretro COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1Fmx2RPcgVgIIeKpaBKNEGWCDuu3DGfR-VkrnIVsIpeE/edit?usp=sharing)  feel free to contribute to the list.

Place your imame4all-libretro ROMs in

For RetroPie 3.0:
```
/home/pi/RetroPie/roms/mame-mame4all
```

For RetroPie 2.6:
```
/home/pi/RetroPie/roms/mame-libretro
```
### **AdvanceMAME**

Romset Used: **.94** (AdvMame .94) or **.106** (AdvMame 1.2)

Total Games Emulated: **5563** (0.94.0) **6166** (1.2) (includes clones etc..)

Place your AdvanceMAME ROMs in
```
/home/pi/RetroPie/roms/mame-advmame
```

You will get errors loading some mame roms, not all roms are compatible or working. You will need to download ROMs that are confirmed working with your version of MAME

To find out which ROMs work for imame4all/mame4all-pi, have a look [Here](http://code.google.com/p/imame4all/wiki/GameList)

## BIOS
Some ROMs may need the **neogeo.zip** BIOS in order to run. Place the neogeo.zip BIOS file in the same folder as your ROMs
```shell
/home/pi/RetroPie/roms/mame-mame4all
or
(For RetroPie 2.6) /home/pi/RetroPie/roms/mame-libretro
or
/home/pi/RetroPie/roms/mame-advmame
```
These are the contents of a verified working neogeo.zip BIOS file * Note that all the files may not be necessary

```shell
000-lo.lo
asia-s3.rom
filelist.txt
japan-j3.bin
neo-geo.rom
ng-lo.rom
ng-sfix.rom
ng-sm1.rom
sfix.sfix
sm1.sm1
sp-1v1_3db8c.bin
sp-45.sp1
sp-e.sp1
sp-j2.sp1
sp-s.sp1
sp-s2.sp1
sp-u2.sp1
sp1.jipan.1024
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
vs-bios.rom
```
## Controls
AdvanceMAME and Mame4all-Pi have the same method in setting up controls, imame4all-libretro utilises RetroArch configurations

### AdvanceMAME and Mame4all-Pi

While in a game press Tab to open the menu to set up controls

### imame4all-libretro

imame4all-libretro utilises RetroArch configs.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/mame-mame4all/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)