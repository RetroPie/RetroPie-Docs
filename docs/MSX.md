***
![msx2](https://cloud.githubusercontent.com/assets/10035308/12213189/80192ed2-b631-11e5-86b3-58d17dcc2432.png)
***
_The MSX was a 8bit personal computer standard developed by ASCII in 1983. Microsoft provided the BASIC interpreter and later MSX-DOS. Various electronics vendors made MSX systems such as Canon, Casio, Daewoo, Fujitsu, Goldstar (LG), Hitachi, JVC, Mitsubishi, Panasonic, Philips, Pioneer, Samsung, Sanyo, Sony, Toshiba, Yamaha and various others. The MSX was followed by the MSX2, after which manufacturers abandoned the market outside Japan due to limited success. In Japan a few manufacturers still held out and released the MSX2+ and finally the TurboR. MSX had its greatest success in Japan, and was able to establish some market share in countries like the Netherlands, Spain and Brazil._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-bluemsx](https://github.com/libretro/blueMSX-libretro) | msx  | .cas .rom .mx1 .mx2 .col .dsk .zip .m3u | see below  | /opt/retropie/configs/msx/retroarch.cfg |
| [lr-fmsx](https://github.com/libretro/fmsx-libretro) | msx  | .rom .mx1 .mx2 .dsk | see below | /opt/retropie/configs/msx/retroarch.cfg |
| [openMSX](http://openmsx.org/) | msx | .cas .rom .mx1 .mx2 .col .dsk | see below | see below |


## ROMS
Accepted File Extensions: **.cas .rom .mx1 .mx2 .col .dsk .zip .m3u**

Place your MSX ROMs in
```
/home/pi/RetroPie/roms/msx
```

## Controls

### Libretro cores 
lr-fmsx and lr-bluemsx utilise RetroArch configurations.

Add custom retroarch controls to the retroarch.cfg file in

```
/opt/retropie/configs/msx/retroarch.cfg
```

Keyboard support can also be enabled here by adding:

```
input_libretro_device_p2 = "3"
```

For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration).   
Many games will have varying keyboard controls.

### openMSX
By default, openMSX use the keyboard and automatically configures the 1st detected gamepad. MSX joysticks had 1 digital joystick and 2 buttons and openMSX auto-configures the D-Pad for the joystick Up/Down/Left/Right actions, the maps the even buttons as Button A, odd numbered buttons as Button B.

If you configure your gamepad in EmulationStation _after_ openMSX is installed, the gamepad is automatically configured by RetroPie as follows:

| Gamepad | openMSX action |
| :-: | :-: |
| A | A button |
| B | B button |
| D-Pad or Left Analog joystick | MSX Joystick |
| Y | <kbd>F1</kbd> |
| X | <kbd>F2</kbd> |
| Left Shoulder | <kbd>F3</kbd> |
| Right Shoulder | <kbd>F4</kbd> |
| Start | toggle openMSX menu |
| Select | openMSX OSD Keyboard |

**NOTE**: when using the openMSX menu, _B_ selects/execute the current menu action, while _A_ exits the current menu (back). You can use the D-Pad or Left Analog Joystick to navigate the menu.

#### Specific ROM controls

To make it easier to control openMSX just with a gamepad, there is an option to override the generated gamepad configuration for the ROM/game started

* open the `/opt/retropie/configs/msx/openmsx/share/joystick` folder (or via file shares: `\\configs\msx\openmsx\share\joystick`). The gamepad auto-configuration created by RetroPie should be in a file named after the controller's name and a `.tcl` extension
* copy an already existing controller `.tcl` configuration file to the `game` subfolder.
* edit the copied file and adjust the 'bind_default' commands configuration. See the openMSX documentation for how to use those commands:
  - http://openmsx.org/manual/commands.html#bind
  - https://openmsx.org/manual/commands.html#joystickN_config
  - http://map.grauw.nl/articles/keymatrix.php, the _The key matrix layouts_ section

* rename the new `.tcl` file to be similar to the disk/tape/rom name (i.e. _Metal Gear.zip_ looks for a file _Metal Gear.tcl_).
    
    If you are not sure which name to use, start the game, then press <kbd>F10</kbd> while in-game, and type `guess_title`, followed by <kbd>Enter</kbd>. openMSX will print the content name, which can be used as a filename for the override joystick configuration file.
    
    **NOTE**: special characters (_:?/\*_), are automatically stripped from the name so if your content file is _ABC?.dsk_,
   then the configuration file would be _ABC.tcl_.
   
## BIOS

### BlueMSX

Depending on the CORE option and machine you are running, it may require a different BIOS. Each machine folder has an ini file that explains which BIOS is needed, the following are some examples.

**BlueMSX BIOS List**

* COL - ColecoVision: coleco.rom
* MSX : MSX.ROM - PHILIPSDISK.ROM 
* MSX Brazilian : MSXBR.ROM - MICROSOLDISK.ROM 
* MSX German : MSXG.ROM - PHILIPSDISK.ROM 
* MSX Japanese : MSXJ.ROM - PANASONICDISK.ROM 
* MSX Korean : MSXKR.ROM - MSXHAN.ROM - NATIONALDISK.ROM 
* MSX Swedish : MSXSE.ROM - PHILIPSDISK.ROM 
* MSX2 : MSX2.ROM - MSX2EXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 
* MSX2 Arabic : MSX2AR.ROM - MSX2AREXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PANASONICDISK.ROM - KANJI.ROM - MSXKANJI.ROM - ARABIC.ROM - SWP.ROM - PAINT.ROM 
* MSX2 Brazilian : MSX2BR.ROM - MSX2BREXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - MICROSOLDISK.ROM 
* MSX2 French : MSX2FR.ROM - MSX2FREXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 
* MSX2 German : MSX2G.ROM - MSX2GEXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 
* MSX2 Japanese : MSX2J.ROM - MSX2JEXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PANASONICDISK.ROM - KANJI.ROM - MSXKANJI.ROM 
* MSX2 Korean : MSX2KR.ROM - MSX2KREXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - NATIONALDISK.ROM - HANGUL.ROM - MSX2HAN.ROM 
* MSX2 Only PSG : MSX2.ROM - MSX2EXT.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 
* MSX2 Russian : MSX2R.ROM - MSX2REXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - NATIONALDISK.ROM 
* MSX2 Spanish : MSX2SP.ROM - MSX2SPEXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PHILIPSDISK.ROM 
* MSX2+ : MSX2P.ROM - MSX2PEXT.ROM - MSX2PMUS.ROM - MOONSOUND.ROM - XBASIC2.ROM - PANASONICDISK.ROM - KANJI.ROM - MSXKANJI.ROM 
* Turbo-R : FSA1GT.ROM - KANJI.ROM - MOONSOUND.ROM - XBASIC2.ROM

If you're not sure about where to place your BIOS there is a Shared Roms folder you can also put them into (this only applies to ROMS that can be shared between different variants of MSX; Colecovision BIOS for example will not work if placed in the shared Roms folder.

```
/home/pi/RetroPie/BIOS/Machines/Shared Roms/
```

The following is a list of roms that can be added to the shared folder:


- ARAB1.ROM
- ARABIC.rom
- BEERIDE.ROM
- FMPAC.rom
- GCVMX80.ROM
- HANGUL.rom
- KANJI.rom
- MICROSOLDISK.ROM
- MOONSOUND.rom
- MSX2AREXT.ROM
- MSX2AR.ROM
- MSX2BREXT.rom
- MSX2BR.rom
- MSX2EXT.rom
- MSX2FREXT.rom
- MSX2FR.rom
- MSX2GEXT.rom
- MSX2G.rom
- MSX2HAN.rom
- MSX2JEXT.rom
- MSX2J.rom
- MSX2KREXT.rom
- MSX2KR.rom
- MSX2PEXT.rom
- MSX2PMUS.rom
- MSX2P.rom
- MSX2R2.ROM
- MSX2REXT.rom
- MSX2.rom
- MSX2R.rom
- MSX2SE.rom
- MSX2SPEXT.rom
- MSX2SP.rom
- MSXAR.ROM
- MSXBR.rom
- MSXDOS23.ROM
- MSXFR.rom
- MSXG.rom
- MSXHAN.rom
- MSXJ.rom
- MSXKANJI.rom
- MSXKR.rom
- MSXR2.rom
- MSX.rom
- MSXR.rom
- MSXSE.ROM
- MSXSP.rom
- MSXTREXT.ROM
- MSXTRMUS.ROM
- MSXTROPT.ROM
- MSXTR.ROM
- NATIONALDISK.rom
- NOVAXIS.rom
- PAINT.rom
- PANASONICDISK.rom
- PHILIPSDISK.rom
- RS232.ROM
- SUNRISEIDE.rom
- SWP.rom
- XBASIC2.rom

### openMSX
Copy the BIOS files to
````
/home/pi/RetroPie/BIOS/openmsx
````

openMSX supports a large number of MSX machines, each machine with it's own firmware and BIOS files. By default, openMSX includes the open source [C-BIOS](http://cbios.sourceforge.net) files, which enables the emulation of a MSX2+ machine, but it only supports cartridge based ROMs, without cassette/disk support.

The list of machines supported by openMSX is [here](https://github.com/openMSX/openMSX/tree/master/share/machines). Each machine has its own `.xml` file, where the ROMs needed are listed with their name and checksums. In order to emulate one of the machines, the necessary files listed in the `rom` tags should be copied in the openMSX BIOS folder.

For instance, the `Al Alamiah AX230` machine model needs the following ROMs:
```` xml
  <rom>
      <filename>IC125.BIN</filename>
      <sha1>0340707c5de2310dcf5e569b7db4c6a6a5590cb7</sha1>
  </rom>
````

**NOTE**: openMSX validates the BIOS files (_systemroms_) by their checksum, so file naming and folder structure is not important as long as the files' content is correct.

For the additional 3 systems that RetroPie configures, the BIOS files needed are listed below.

* MSX2 (based on the [BOOSTED_MSX2_EN](https://github.com/openMSX/openMSX/blob/master/share/machines/Boosted_MSX2_EN.txt) model)

    | File | SHA1 checksum |
    |:-|:-|
    | nms8250_disk.rom | DAB3E6F36843392665B71B04178AADD8762C6589 <br> C3EFEDDA7AB947A06D9345F7B8261076FA7CEEEF|
    | nms8250_basic-bios2.rom | 6103B39F1E38D1AA2D84B1C3219C44F1ABB5436E |
    | nms8250_msx2sub.rom | 5C1F9C7FB655E43D38E5DD1FCC6B942B2FF68B02 |
    | fmpac.rom | 9D789166E3CAF28E4742FE933D962E99618C633D |
    | phc-70fd2_basickun.rom | 22B3191D865010264001B9D896186A9818478A6B |
    | yrw801.rom | 32760893CE06DBE3930627755BA065CC3D8EC6CA |

* MSX2+ (based on the [BOOSTED_MSX+2_JP](https://github.com/openMSX/openMSX/blob/master/share/machines/Boosted_MSX2+_JP.txt) model)

    | File | SHA1 checksum |
    |:-|:-|
    | fs-a1wsx_kanjifont.rom | 5AFF2D9B6EFC723BC395B0F96F0ADFA83CC54A49 |
    | fs-a1wsx_basic-bios2p.rom | F4433752D3BF876BFEFB363C749D4D2E08A218B6 |
    | fs-a1wsx_fmbasic.rom | AAD42BA4289B33D8EED225D42CEA930B7FC5C228 |
    | fs-a1wsx_msx2psub.rom | FE0254CBFC11405B79E7C86C7769BD6322B04995 |
    | fs-a1wsx_kanjibasic.rom | DCC3A67732AA01C4F2EE8D1AD886444A4DBAFE06 |
    | fs-a1wsx_disk.rom | 7ED7C55E0359737AC5E68D38CB6903F9E5D7C2B6 |
    | fs-a1wsx_firmware.rom | 3330D9B6B76E3C4CCB7CF252496ED15D08B95D3F |
    | phc-70fd2_basickun.rom | 22B3191D865010264001B9D896186A9818478A6B |
    | yrw801.rom | 32760893CE06DBE3930627755BA065CC3D8EC6CA |

* MSX-TurboR (based on the [Panasonic_FS-A1GT](https://github.com/openMSX/openMSX/blob/master/share/machines/Panasonic_FS-A1GT.xml) model)

    | File | SHA1 checksum |
    |:-|:-|
    | fs-a1gt_firmware.rom | E779C338EB91A7DEA3FF75F3FDE76B8AF22C4A3A <br> 5FA3AA79AEBA2C0441F349E78E9A16D9D64422EA |
    | fs-a1gt_kanjifont.rom | 5AFF2D9B6EFC723BC395B0F96F0ADFA83CC54A49 |
 

## BlueMSX
### Changing the machine to be emulated

The machine model that is emulated can be configured through the [Core Options](RetroArch-Core-Options) menu. The following MSX models can be selected:

* MSX
* MSXTurboR
* MSX2
* MSX2+
* SVI - Spectravideo SVI-318
* SVI - Spectravideo SVI-328
* SVI - Spectravideo SVI-328 MK2

### Disc Swapping for multi-disc games

To change the disc in-game, open the RetroArch menu (_Hotkey + X_), open then _Disc Control_ menu and then choose _Load New Disc_ to add a new disc.

### M3U playlist for multi-disc Games

Multiple discs can be loaded simultaneously from Emulation Station into RetroArch by creating an M3U file (plain-text, `.m3u` extension). In its contents, enter the filenames of the DSK files one per line. In game you can then swap disks from the _Disc Control_ RetroArch menu, choosing one of the disks configured in the file from the _Current Disc Index_ selection.

## openMSX
openMSX will by default use a MSX C-BIOS rom image. C-BIOS is not a real BIOS rom and has certain restrictions, such as no support for anything other then cartridges (ROMs). So there is no support for disk or cassette for instance.   
In addition to that, RetroPie configures 3 other machines, which can be chosen from the [Runcommand launch menu](Runcommand#runcommand-launch-menu):

* MSX2 (launches the [BOOSTED_MSX2_EN](https://github.com/openMSX/openMSX/blob/master/share/machines/Boosted_MSX2_EN.txt) machine). It's a machine based on Philips NMS-8250 (most standard MSX2 in the Netherlands at least) with:
  - three external slots, slot B and C are in a sub slot (2-0 and 2-1)
  - 2048 kB memory mapper (in slot 3-2)
  - 2 disk drives
  - V9958 VDP with 192 kB VRAM
  - SCC+ in slot 2-3
  - FMPAC (slot 3-1)
  - MSX Audio
  - MoonSound with 640 kB sample RAM
  - GFX9000 with Video9000
  - 512 kB MegaRAM in slot 2-2
  - BASIC Compiler (MSX-BASIC Kun)

* MSX2+ (launches the [BOOSTED_MSX+2_JP](https://github.com/openMSX/openMSX/blob/master/share/machines/Boosted_MSX2+_JP.txt) machine). It's machine based on Panasonic FS-A1WSX (most complete MSX2+), which includes:
  - Kanji ROM
  - MSX-MUSIC
  - firmware
  - three external slots, slot B and C are in a sub slot (2-0 and 2-1)
  - 2048 kB memory mapper (in slot 3-0)
  - 2 disk drives
  - V9958 VDP with 192 kB VRAM
  - SCC+ in slot 2-3
  - MSX Audio
  - MoonSound with 640 kB sample RAM
  - GFX9000 with Video9000
  - 512 kB MegaRAM in slot 2-2
  - BASIC Compiler (MSX-BASIC Kun) 

* MSX-TurboR (launches the [Panasonic_FS-A1GT](https://github.com/openMSX/openMSX/blob/master/share/machines/Panasonic_FS-A1GT.xml) machine)


### Changing default machine to be emulated

By default openMSX will emulate a MSX2+ using the C-BIOS ROM. To change this, you need to start openMSX, either by starting a game or from the commandline by typing `/opt/retropie/emulators/openmsx/bin/openmsx`.   
When the emulator is running, press <kbd>F10</kbd> and you will get a overlay where you can type commands, here you need to type the following to change the default MSX to be emulated:

````
set default_emulator turbor
````

In the above example we change the default to the MSX TurboR, which was the last MSX machine produced. Other options could be `msx1`, `msx2` or `msx2plus`. There are many MSX machines that can potentially be emulated, for a list look in the directory `/opt/retropie/emulators/openmsx/share/machines` or online [here](https://github.com/openMSX/openMSX/tree/master/share/machines). If, for instance, you wanted to emulate a _Spectravideo SVI-728_, you will find in that directory a file `Spectravideo_SVI-728.xml`. Simply use the name of the file, excluding the .xml extension, as the machine name.

If your gamepad has been automatically configured by RetroPie, the machine type can be changed by opening the openMSX menu (pressing <kbd>Start</kbd> on your gamepad) and using the _Hardware_ sub-menu to choose another machine and make it default.

Machine types _msx1_, _msx2_, _msx2plus_ and _turbor_ are simply links to certain MSX machines :

- msx1 - European Toshiba HX10
- msx2 - European Philips NMS 8250
- msx2plus - Japanese Panasonic FS-A1WSX
- turbor - Japanese Panasonic FS-A1GT

The machine type selected will obviously have certain effects. For instance, the FS-A1GT model does not support cassettes, and so you cannot play cassette games on it. Starting some games (mainly Konami) on a Japanese machine may result in the in-game dialogue being in Japanese, while if you start the same game on a European machine the in-game dialogue may be in English.

Depending on the machine model chosen, additional BIOS files may be needed - see the [BIOS](#openmsx_1) section to find the necessary BIOS files.

### Exiting the emulator
By default the exit key in the emulator is `Alt-F4` on a keyboard. 

If the gamepad has been automatically configured by RetroPie, then you can also exit by pressing _Start_ (to open the openMSX menu) and choosing _Exit openMSX_

### Setting default screen on MSX2+ and TurboR machines
By default MSX2+ and TurboR machines will start with a screen type which is incompatible with lots of European software. Typically resulting in errors such as ``Syntax error in 10`` when starting disk or cassette based games. This is typically because the software is trying to change the width of the screen to something incompatible with the current screen type selected. The solution is to start the emulator to a MSX BIOS Ok prompt. This can be done when a game fails to start and gives you an Ok prompt, or you can start the emulator outside of RetroPie as shown above.

At the MSX BIOS Ok prompt (not the openMSX command prompt), type the following;

````
screen0
set screen
````

You have now changed your default screen to screen0 as was normal on European MSX machines, and saved the setting into virtual nvram.

**Note**: if you change your default machine type from say a TurboR to a MSX2+ you will have to redo this step as each MSX2 and later machine type has its own virtual nvram file.

### 50 or 60Hz?

European MSX machines ran at 50Hz, as that is the PAL video standard, while Japanese MSX machines ran at 60Hz as is standard on NTSC. How does this effect things? Well it means that lots of Japanese developed games run ~20% slower when run on a European MSX. This may mean more sluggish behaviour and slower sound if the programmers did not take this into account.

How does this effect emulation? The default C-BIOS based model uses 60Hz. A MSX2+ or TurboR will always be 60Hz since they where never officially sold in Europe. Of course the effect can also be the other way around - European MSX software that runs too fast on a Japanese machine type.

In openMSX, you can change the emulated frequency during runtime. Simply open the openMSX command prompt with `F10`, and type `toggle_freq`.