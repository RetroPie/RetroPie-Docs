***
![mame](https://cloud.githubusercontent.com/assets/10035308/12213821/0acf7328-b63d-11e5-8127-48c8c5d31fe3.png)
***
_MAME stands for Multiple Arcade Machine Emulator. MAME can emulate thousands of games that otherwise would have been lost in the ash-heaps of history._

***

| Emulator | Rom Folder | Romset | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: | :---: |
| [Mame4all-Pi](https://github.com/RetroPie/mame4all-pi) | arcade **or** mame-mame4all | 0.37b5 | neogeo.zip | /opt/retropie/configs/mame-mame4all/cfg/default.cfg |
| [lr-imame4all](https://github.com/libretro/imame4all-libretro) | arcade **or** mame-mame4all | 0.37b5 | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/mame-mame4all/retroarch.cfg |
| [lr-mame2003](https://github.com/libretro/mame2003-libretro) | arcade **or** mame-libretro | .78 | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/mame-libretro/retroarch.cfg |
| [lr-mame2010](https://github.com/libretro/mame2010-libretro) | arcade **or** mame-libretro | .139 | neogeo.zip | /opt/retropie/configs/arcade/retroarch.cfg, **or** /opt/retropie/configs/mame-libretro/retroarch.cfg |
| [AdvanceMAME .94](http://advancemame.sourceforge.net/) | arcade **or** mame-advmame | .94 | neogeo.zip | /opt/retropie/configs/mame-advmame/advmame-0.94.0.rc |
| [AdvanceMAME](http://advancemame.sourceforge.net/) | arcade **or** mame-advmame | .94 | neogeo.zip | /opt/retropie/configs/mame-advmame/advmame-1.4.rc |

## Emulators: [AdvanceMAME](http://advancemame.sourceforge.net/), [mame4all-pi](https://github.com/RetroPie/mame4all-pi), [lr-imame4all](https://github.com/libretro/imame4all-libretro), [lr-mame2003](https://github.com/libretro/mame2003-libretro), [lr-mame2010](https://github.com/libretro/mame2010-libretro)

mame4all-pi has the best performance of them all, but a limited romset. This is the best choice for the Raspberry Pi 1/0. lr-imame4all is the libretro equivalent, with possibly weaker performance, but features all the libretro benefits (RetroArch controller configurations, shader support, save states, etc). lr-mame2003 is a good choice for Raspberry Pi 2 and up, as it has a comprehensive romset, and good performance, as well as also being libretro. The AdvMames are popular as they have a huge romset, but they're non-libretro. All other MAME cores are experimental and should normally be avoided.

See Also: [[FinalBurn-Alpha]], [[Neo Geo]]

## ROMS

Because MAME emulates many different pieces of hardware and thousands of games it can be hard to keep track of everything. ROMs for MAME are probably the most confusing thing about RetroPie. 

Accepted File Extensions: **.zip**

When working with these ROMs *you will need to know which romset it belongs to, then use a compatible emulator to run it*. There are many ways to figure this out, so some resources are linked below. For example, let's say you have a ROM file such as **anAwesomeGame.zip** and you learn that it belongs to romset 0.37b5. Then place **anAwesomeGame.zip** file (without extracting it) into the *arcade or mame-mame4all* ROM directories (as mentioned in the above table). Then, make sure you have the corresponding BIOS file, **neogeo.zip**, *in that same directory*. That's it. Be sure that in the game's run configuration that the correct emulator is used and you are good to go.

**For information on how to rebuild newer romsets to be compatible with these emulators see this post:**
**[Managing ROMs](https://github.com/petrockblog/RetroPie-Setup/wiki/Managing-ROMs)**

## **Arcade**

To avoid having several EmulationStation menus for different arcade emulators, all arcade-based ROMs can be placed in the `arcade` ROM folder, but you will have to specify which emulator each will use from the [Runcommand Menu](runcommand)

[**All Arcade ROMS Compatibility List**](https://docs.google.com/spreadsheets/d/1antILt7D12EWOFzyJwTfB86NceghMJKXG7CdYumuHec/edit?usp=sharing) feel free to contribute to the list.

## **Emulators**

### **MAME4ALL-Pi**

Place your MAME4ALL-Pi ROMs in
```
/home/pi/RetroPie/roms/mame-mame4all
```

Romset Used: **0.37b5**

Total Games Emulated: [2270](http://code.google.com/p/imame4all/wiki/GameList) 

[**MAME4ALL-PI COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1gpuoZx78kDDdnf_yADicsSZHMfpOxNySSov7UdCDAik/edit?usp=sharing)  feel free to contribute to the list.

### **lr-imame4all**

Place your lr-imame4all ROMs in
```
/home/pi/RetroPie/roms/mame-mame4all
```

Romset Used: **0.37b5**

Total Games Emulated: [2270](http://code.google.com/p/imame4all/wiki/GameList) 

[**lr-IMAME4ALL COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1Fmx2RPcgVgIIeKpaBKNEGWCDuu3DGfR-VkrnIVsIpeE/edit?usp=sharing)  feel free to contribute to the list.

### **AdvanceMAME**

Place your AdvanceMAME ROMs in
```
/home/pi/RetroPie/roms/mame-advmame
```

Romset Used: **.94** (AdvMame .94) or **0.106** (AdvMame 1.4)

Total Games Emulated: **5563** (0.94.0) **6166** (1.4) (includes clones etc..)

[**AdvMame .94 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1AEQ94buG0rvbW0xdnYKeuEhHeCbuZlRfRJQCb1Dt8fw/edit?usp=sharing)  feel free to contribute to the list.

[**AdvMame 1.4 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1RapyxChe2BMOfbX-FsCup9SXGxvS1WmXAofwaTJtmxc/edit?usp=sharing)  feel free to contribute to the list.

### lr-Mame2003

**Please see [[lr-mame2003]] for information on how to configure specific features of this emulator.**

Place your lr-mame2003 ROMs in
```
/home/pi/RetroPie/roms/mame-libretro
```

Place your samples in
```
/home/pi/RetroPie/BIOS/mame2003/samples/
```

Romset Used: **.78**

Total Games Emulated: 4705 (includes clones etc...)

[**lr-mame2003 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1LP1MELCvcxu7TfiowF_0ZuvRVEMqlfQyTVetnOJvuJc/edit?usp=sharing)  feel free to contribute to the list.

### lr-mame2010 (EXPERIMENTAL)

Place your lr-Mame2010 ROMs in
```
/home/pi/RetroPie/roms/mame-libretro
```

Romset Used: **.139**

Total Games Emulated: 8782 (includes clones etc...)

[**lr-mame2010 COMPATIBILITY LIST**](https://docs.google.com/spreadsheets/d/1IRSmFrSDvIc6gAw0gn12TcQ3HDOwmrETTor8wvvb7VI/edit?usp=sharing) feel free to contribute to the list.

This emulator has limited functionality. For example, only 2 players are supported.

## BIOS
Some ROMs may need the **neogeo.zip** BIOS in order to run. Place the neogeo.zip BIOS file in the same folder as your MAME ROMs. For example:
```shell
/home/pi/RetroPie/roms/mame-mame4all
```

Each MAME version requires a different neogeo.zip, so make sure you choose the suitable file for the emulator according to its specification found in the [.dat file](https://github.com/RetroPie/RetroPie-Setup/wiki/Managing-ROMs#step-3---acquire-dat-files). The correct neogeo.zip will normally be found within complete romsets for the MAME version.

## Controls
AdvanceMAME and Mame4all-Pi have the same method in setting up controls, imame4all-libretro utilises RetroArch configurations

### AdvanceMAME and Mame4all-Pi

While in a game press Tab to open the menu to set up controls

Mame4all Menu Tab menu configuration is stored in
```shell 
/opt/retropie/configs/mame-mame4all/cfg/default.cfg
```
Other files in this cfg directory are ROM specific configs.

Note: Should your input configuration or other aspect of the configuration need resetting to defaults, remove the default.cfg or ROM specific .cfg file, and it will be re-created with default values next time you start Mame4all or modify the ROM configuration.

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

## Edge Case Games

### Joust (various)

Joust will not start (usually) until the 'Service Button' is pushed.  It will appear to hang on 'FACTORY SETTINGS RESTORED'.  If you are using keyboard controls, push F2. If you are using a controller push the RESET hotkey (default SELECT+X). That will reset the game with the new NVRAM settings, and you will be able to continue.