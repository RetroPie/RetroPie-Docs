***
![msx2](https://cloud.githubusercontent.com/assets/10035308/12213189/80192ed2-b631-11e5-86b3-58d17dcc2432.png)
***
_The MSX was a personal computer released by Microsoft in 1983._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-bluemsx](https://github.com/libretro/blueMSX-libretro) | msx  | .rom .mx1 .mx2 .col .dsk | see below  | /opt/retropie/configs/msx/retroarch.cfg |
| [lr-fmsx](https://github.com/libretro/fmsx-libretro) | msx  | .rom .mx1 .mx2 .col .dsk | see below | /opt/retropie/configs/msx/retroarch.cfg |
| [OpenMSX](http://openmsx.org/) | msx | .rom .mx1 .mx2 .col .dsk | see below | hardcoded |

## Emulator: [lr-fmsx](https://github.com/libretro/fmsx-libretro), [lr-bluemsx](https://github.com/libretro/blueMSX-libretro), [OpenMSX](http://openmsx.org/)

## ROMS
Accepted File Extensions: **.rom .mx1 .mx2 .col .dsk**

Place your MSX ROMs in
```
/home/pi/RetroPie/roms/msx
```

## Controls
 
lr-fmsx and lr-bluemsx utilise RetroArch configurations. openMSX has its own configuration, and will ignore control definitions made in RetroArch.

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/msx/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

Many games will have varying keyboard controls.

## BIOS List

MSX : MSX.ROM - PHILIPSDISK.ROM 

MSX Brazilian : MSXBR.ROM - MICROSOLDISK.ROM 

MSX German : MSXG.ROM - PHILIPSDISK.ROM 

MSX Japanese : MSXJ.ROM - PANASONICDISK.ROM 

MSX Korean : MSXKR.ROM - MSXHAN.ROM - NATIONALDISK.ROM 

MSX Swedish : MSXSE.ROM - PHILIPSDISK.ROM 

MSX2 : MSX2.ROM - MSX2EXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 

MSX2 Arabic : MSX2AR.ROM - MSX2AREXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PANASONICDISK.ROM - KANJI.ROM - MSXKANJI.ROM - ARABIC.ROM - SWP.ROM - PAINT.ROM 

MSX2 Brazilian : MSX2BR.ROM - MSX2BREXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - MICROSOLDISK.ROM 

MSX2 French : MSX2FR.ROM - MSX2FREXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 

MSX2 German : MSX2G.ROM - MSX2GEXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 

MSX2 Japanese : MSX2J.ROM - MSX2JEXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PANASONICDISK.ROM - KANJI.ROM - MSXKANJI.ROM 

MSX2 Korean : MSX2KR.ROM - MSX2KREXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - NATIONALDISK.ROM - HANGUL.ROM - MSX2HAN.ROM 

MSX2 Only PSG : MSX2.ROM - MSX2EXT.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 

MSX2 Russian : MSX2R.ROM - MSX2REXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - NATIONALDISK.ROM 

MSX2 Spanish : MSX2SP.ROM - MSX2SPEXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 

MSX2+ : MSX2P.ROM - MSX2PEXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PANASONICDISK.ROM - KANJI.ROM - MSXKANJI.ROM 

Turbo-R : FSA1GT.ROM - KANJI.ROM - MOONSOUND.ROM - XBASIC2.ROM

## openMSX
openMSX will by default use a MSX2+ c-bios rom image. c-bios is not a real BIOS rom and has certain restrictions, such as no support for anything other then cartridges (ROMs). So there is no support for disk or cassette for instance.

You can change this by adding dumps of real MSX system roms into the ``/opt/retropie/emulators/openmsx/share/systemroms`` or the ``~/.openMSX/share/systemroms`` directory.

To locate real MSX system ROMs, try google.

### Changing default machine to be emulated
By default openMSX will emulate a MSX2+ using the c-bios ROMs. To change this, you need to start openMSX, either by starting a game or from the commandline by typing ``/opt/retropie/emulators/openmsx/bin/openmsx``

When the emulator is running, press `F10` and you will get a overlay where you can type commands, here you need to type the following to change the default MSX to be emulated;

``set default_emulator turbor``

In the above example we change the default to the MSX TurboR, which was the last MSX machine produced. Other options could be ``msx1``, ``msx2`` or ``msx2plus``. There are many MSX machines that can potentially be emulated, for a list look in the directory ``/opt/retropie/emulators/openmsx/share/machines``. If for instance you wanted to emulate a Spectravideo SVI-728 you will find in that directory a file ``Spectravideo_SVI-728.xml``, simply use the name of the file, excluding the .xml extension as the machine name.

Machine type msx1, msx2, msx2plus and turbor are simply links to certain MSX machines as follows;
- msx1 = European Toshiba HX10
- msx2 = European Philips NMS 8250
- msx2plus = Japanese Panasonic FS-A1WSX
- turbor = Japanese Panasonic FS-A1GT

The machine type selected will obviously have certain effects. For instance the FS-A1GT does not support cassettes, and so you cannot play cassette games on it. Also starting some games (mainly Konami) on a Japanese machine may result in the in-game dialogue being in Japanese, while if you start the same game on a European machine the in-game dialogue may be in English.

Note: If you do not have the ROMs for the default machine type requested in the correct location, openMSX will still start, but with the c-bios ROMs.

### Exiting the emulator
The key definitions defined in retropie will not work in openMSX. openMSX does however allow you to redefine your controls. For more information, look at the openMSX website for 'bind'.

By default the exit key in the emulator is ``Alt-F4``

### Setting default screen on MSX2+ and TurboR machines
By default MSX2+ and TurboR machines will start with a screen type which is incompatible with lots of European software. Typically resulting in errors such as ``Syntax error in 10`` when starting disk or cassette based games. This is typically because the software is trying to change the width of the screen to something incompatible with the current screen type selected. The solution is to start the emulator to a MSX BIOS Ok prompt. This can be done when a game fails to start and gives you an Ok prompt, or you can start the emulator outside of RetroPie as shown above.

At the MSX BIOS Ok prompt (not the openMSX command prompt), type the following;

``screen0``

``set screen``

You have now changed your default screen to screen0 as was normal on European MSX machines, and saved the setting into virtual nvram.

Note: if you change your default machine type from say a TurboR to a MSX2+ you will have to redo this step as each MSX2 and later machine type has its own virtual nvram file.

### 50 or 60Hz?
European MSX machines ran at 50Hz, as that is the PAL video standard. Japanese MSX machines however ran at 60Hz as is standard on NTSC. How does this effect things? Well it means that lots of Japanese developed games run ~20% slower when run on a European MSX. This may mean more sluggish behaviour and slower sound if the programmers did not take this into account.

How does this effect emulation? The default c-bios roms use 60Hz. If you use real MSX system roms, then it depends on which machine your emulating. A MSX2+ or TurboR will always be 60Hz since they where never officially sold in Europe.

Of course the effect can also be the other way around. European MSX software that runs too fast on a Japanese machine type.

In openMSX, you can change the emulated frequency during runtime. Simply open the openMSX command prompt with `F10`, and type `toggle_freq`.