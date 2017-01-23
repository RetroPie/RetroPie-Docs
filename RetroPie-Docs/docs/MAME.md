***
![mame](https://cloud.githubusercontent.com/assets/10035308/12213821/0acf7328-b63d-11e5-8127-48c8c5d31fe3.png)
***
_MAME stands for Multiple Arcade Machine Emulator. MAME can emulate thousands of games that otherwise would have been lost in the ash-heaps of history._

See Also: [[FB Alpha|FinalBurn-Alpha]], [[Neo Geo]]

***

There are a variety of arcade emulator versions available in RetroPie. There are significant differences in performance, compatibility, and configuration between them. If you're getting started with an arcade emulation project, begin by reading [Managing Arcade ROMs](https://github.com/RetroPie/RetroPie-Setup/wiki/Managing-ROMs).

This page is a resource for additional details on RetroPie's MAME emulators including configuration paths, controls, and the ROM sets which each emulator requires.

[**All Arcade ROMS Compatibility List**](https://docs.google.com/spreadsheets/d/1antILt7D12EWOFzyJwTfB86NceghMJKXG7CdYumuHec/edit?usp=sharing) feel free to contribute to the list.

| Emulator | ROM Folder | Required ROM Set Version | Controller Configuration |
| :---: | :---: | :---: | :---: | :---: | :---: |
| [mame4all-pi](https://github.com/RetroPie/mame4all-pi) | arcade **or** mame-mame4all | MAME 0.37b5 | /opt/retropie/configs/mame-mame4all/cfg/default.cfg |
| [lr-imame4all](https://github.com/libretro/imame4all-libretro) | arcade **or** mame-mame4all | MAME 0.37b5 | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/mame-mame4all/retroarch.cfg |
| [lr-mame2003](https://github.com/libretro/mame2003-libretro) | arcade **or** mame-libretro | MAME 0.78 | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/mame-libretro/retroarch.cfg |
| [lr-mame2010](https://github.com/libretro/mame2010-libretro) | arcade **or** mame-libretro | MAME 0.139 | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/mame-libretro/retroarch.cfg |
| [AdvanceMAME 0.94](http://advancemame.sourceforge.net/) | arcade **or** mame-advmame | MAME 0.94 | /opt/retropie/configs/mame-advmame/advmame-0.94.0.rc |
| [AdvanceMAME 1.4](http://advancemame.sourceforge.net/) | arcade **or** mame-advmame | MAME 0.106 | /opt/retropie/configs/mame-advmame/advmame-1.4.rc |

## Arcade ROM paths

In RetroPie 3.0.0 some emulators share directories, so you need to choose which FBA, NeoGeo and mame4all version you want. So you can have one zipped ROMset for each of these (mame4all, FBA, NeoGeo, advmame) To avoid having several EmulationStation menus for different arcade emulators, all arcade-based ROMs can be placed in the `arcade` ROM folder, but you will have to specify which emulator each will use from the [Runcommand Menu](runcommand)

## Emulators

Note: These details are as per the default installed binaries on the RetroPie 3.0.0 image.

---
### [mame4all-pi on sourceforge](http://sourceforge.net/projects/mame4allpi/)

```shell
Roms Dir: /home/pi/RetroPie/roms/mame-mame4all
Binary Dir: /opt/retropie/emulators/mame4all
Config Dir: /opt/retropie/configs/mame-mame4all
```
**MAME Version**: 0.37b5 (July 2000)

**Active Sets: 2241**
* BIOS: 1
* CHDs: 0
* Samples: 35

**MAME 0.37b5 DAT File**: [mame4all-037b5-RetroPie-260.zip](https://drive.google.com/file/d/0B2TMeZ6iEFvHVUNfWHpUZk82bkk/view?usp=sharing)

**MAME 0.37b5 DAT File**: [mame4all-no-clones-no-neogeo](https://drive.google.com/file/d/0B2TMeZ6iEFvHNm5OYndFUHM3djg/view?usp=sharing) (no clones, no neogeo)

**[MAME4ALL-PI Compatibility List](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing)** feel free to contribute to the list.

**Controls**

While in a game press Tab to open the menu to set up controls. The MAME4ALL tab menu configuration is stored in:
```shell 
/opt/retropie/configs/mame-mame4all/cfg/default.cfg
```
Other files in this cfg directory are ROM specific configs.

Note: Should your input configuration or other aspect of the configuration need resetting to defaults, remove the default.cfg or ROM specific .cfg file, and it will be re-created with default values next time you start MAME4ALL or modify the ROM configuration.

---
### [lr-imame4all on github](https://github.com/libretro/imame4all-libretro)
```shell
Roms Dir: /home/pi/RetroPie/roms/mame-mame4all
Binary Dir: /opt/retropie/libretrocores/lr-imame4all
Config Dir: /opt/retropie/configs/mame-mame4all/retroarch.cfg
```
**MAME Version**: 0.37b5 (July 2000)

**Active Sets: 2241**
* BIOS: 1
* CHDs: 0
* Samples: 35

**MAME 0.37b5 DAT File**: [mame4all-037b5-RetroPie-260.zip](https://drive.google.com/file/d/0B2TMeZ6iEFvHVUNfWHpUZk82bkk/view?usp=sharing)

**MAME 0.37b5 'Lite' DAT File (no clones, no neogeo)**: [mame4all-no-clones-no-neogeo](https://drive.google.com/file/d/0B2TMeZ6iEFvHNm5OYndFUHM3djg/view?usp=sharing)

**[lr-IMAME4ALL Compatibility List](https://docs.google.com/spreadsheets/d/1Fmx2RPcgVgIIeKpaBKNEGWCDuu3DGfR-VkrnIVsIpeE/edit?usp=sharing)** feel free to contribute to the list.

**Controls**

lr-imame4all utilises [RetroArch control configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration). Add custom retroarch controls to the retroarch.cfg file in:
```shell
/opt/retropie/configs/mame-mame4all/retroarch.cfg
```

---
### [lr-mame2003 on github](https://github.com/libretro/mame2003-libretro)

**Please see [lr-mame2003 on RetroPie](lr-mame2003) for information on how to configure specific features of this emulator.**

```shell
Roms Dir: /home/pi/RetroPie/roms/mame-libretro
Samples Dir: /home/pi/RetroPie/BIOS/mame2003/samples/
Binary Dir: /opt/retropie/libretrocores/lr-mame2003
Config Dir: /opt/retropie/configs/mame-libretro/retroarch.cfg
```
**MAME Version**: 0.78 (December 2003)

**Active Sets: 4705**
* BIOS: 15
* CHDs: 30
* Samples: 56

**MAME 0.78 DAT File**: [MAME 0.78.dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHTkc2TXZOOFhCRzQ/view?usp=sharing)

**MAME 0.78u5 DAT File**: [mame2003-lr-working-no-clones](https://drive.google.com/file/d/0B2TMeZ6iEFvHV21wRVh6TF9uQ1U/view?usp=sharing) (working only, no clones)

**MAME 0.78u5 'Lite' DAT File**: [mame2003-lr-lite](https://drive.google.com/file/d/0B2TMeZ6iEFvHY1VzcXYyT09iRGs/view?usp=sharing) (working, no clones, neogeo, PlayChoice/NES multiplay, no rotary/dial/trackball/lightgun controls, no casino/multiplay/quiz/mahjong/fruit_machines/rhythm/mature)

**[lr-mame2003 Compatibility List](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing)** feel free to contribute to the list.

**Controls**

lr-mame2003 utilises [RetroArch control configurations](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration). Add custom retroarch controls to the retroarch.cfg file in:
```shell
/opt/retropie/configs/mame-libretro/retroarch.cfg
```

---
### [lr-mame2010 on github](https://github.com/libretro/mame2010-libretro)
**Note: This emulator is considered experimental in RetroPie and has limited functionality. For example, only 2 players are supported.**

```shell
Roms Dir: /home/pi/RetroPie/roms/mame-libretro
Binary Dir: /opt/retropie/libretrocores/lr-mame2010
Config Dir: /opt/retropie/configs/mame-libretro/retroarch.cfg
```
**MAME Version**: 0.139 (August 2010)

**Active Sets: 8782**
* BIOS: ?
* CHDs: 406
* Samples: 70 (4 more samples are not in circulation)

**MAME 0.139 DAT File**: [MAME 0.139.dat](https://drive.google.com/file/d/0B2TMeZ6iEFvHUFdCc04zZ3o4dnM/view?usp=sharing) 

**[lr-mame2010 Compatibility List](https://docs.google.com/spreadsheets/d/1IRSmFrSDvIc6gAw0gn12TcQ3HDOwmrETTor8wvvb7VI/edit?usp=sharing)** feel free to contribute to the list.

**Controls**

lr-mame2010 utilises [RetroArch control configurations](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration). Add custom retroarch controls to the retroarch.cfg file in:
```shell
/opt/retropie/configs/mame-libretro/retroarch.cfg
```

---

### [AdvanceMAME 0.94 on sourceforge](http://sourceforge.net/projects/advancemame/)
```shell
Roms Dir: /home/pi/RetroPie/roms/mame-advmame
Binary Dir: /opt/retropie/emulators/advmame/bin
Config Dir: /opt/retropie/configs/mame-advmame
```
**MAME Version**: MAME 0.94 (March 2005)

**Active Sets: 5563**
* BIOS: 25
* CHDs: ?
* Samples: ?

**AdvanceMAME 0.94 DAT File**: [advmame-0.94-RetroPie-260.7z](https://drive.google.com/file/d/0B2TMeZ6iEFvHa2E5Rzl4ZEdMdjQ/view?usp=sharing)

**[AdvanceMAME 0.94 Compatibility List](https://docs.google.com/spreadsheets/d/1AEQ94buG0rvbW0xdnYKeuEhHeCbuZlRfRJQCb1Dt8fw/edit?usp=sharing)** feel free to contribute to the list.

**Controls**

While in a game press Tab to open the menu to set up controls. advmame tab menu configuration is stored in:
```shell 
/opt/retropie/configs/advmame/cfg/default.cfg
```
Other files in this cfg directory are ROM specific configs.

Note: Should your input configuration or other aspect of the configuration need resetting to defaults, remove the default.cfg or ROM specific .cfg file, and it will be re-created with default values next time you start AdvanceMAME or modify the ROM configuration.

---

### [AdvanceMAME 1.4 on sourceforge](http://sourceforge.net/projects/advancemame/)
```shell
Roms Dir: /home/pi/RetroPie/roms/mame-advmame
Binary Dir: /opt/retropie/emulators/advmame/bin
Config Dir: /opt/retropie/configs/mame-advmame
```
**MAME Version**: MAME 0.106 (May 2006)

**Active Sets: 6166**
* BIOS: 26
* CHDs: 86
* Samples: 64 (3 more samples are not in circulation)

**AdvanceMAME 1.4 DAT File**: [advmame12-106.7z](https://drive.google.com/file/d/0B2TMeZ6iEFvHMEZnb1RxQWNmdHM/view?usp=sharing)

**[AdvanceMAME 1.4 Compatibility List](https://docs.google.com/spreadsheets/d/1RapyxChe2BMOfbX-FsCup9SXGxvS1WmXAofwaTJtmxc/edit?usp=sharing)** feel free to contribute to the list.

**Controls**

While in a game press Tab to open the menu to set up controls. advmame tab menu configuration is stored in:
```shell 
/opt/retropie/configs/advmame/cfg/default.cfg
```
Other files in this cfg directory are ROM specific configs.

Note: Should your input configuration or other aspect of the configuration need resetting to defaults, remove the default.cfg or ROM specific .cfg file, and it will be re-created with default values next time you start AdvanceMAME or modify the ROM configuration.