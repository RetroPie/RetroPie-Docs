***
![psx](https://cloud.githubusercontent.com/assets/10035308/12213692/20e2fe3a-b63a-11e5-9e49-c47c33bc659d.png)
***
_The PlayStation is a 5th generation video game console released by Sony in 1994._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-pcsx-rearmed](https://github.com/libretro/pcsx_rearmed) | psx  | .cue .cbn .chd .img .iso .m3u .mdf .pbp .toc .z .znx | scph101.bin scph7001.bin scph5501.bin scph1001.bin | /opt/retropie/configs/psx/retroarch.cfg |
| [PCSX-ReARMed](https://github.com/notaz/pcsx_rearmed) | psx  | .cue .cbn .img .iso .m3u .mdf .pbp .toc .z .znx | SCPH1001.BIN | /opt/retropie/configs/psx/pcsx.cfg |
| [lr-beetle-psx](https://github.com/libretro/beetle-psx-libretro) | psx  | .cue .cbn .chd .img .iso .m3u .mdf .pbp .toc .z .znx | scph5500.bin scph5501.bin scph5502.bin | /opt/retropie/configs/psx/retroarch.cfg |

## Emulators: [lr-pcsx-rearmed](https://github.com/libretro/pcsx_rearmed), [PCSX-ReARMed](https://github.com/notaz/pcsx_rearmed), [lr-beetle-psx](https://github.com/libretro/beetle-psx-libretro).

### lr-pcsx-rearmed

The prefered PSX emulator for those on a Raspberry Pi 2/3. The features of RetroArch combined with PCSX-ReARMed's excellent Dynamic Recompiler allow for an adequate PSX emulation experience on the Raspberry Pi, though expect some inaccurate emulation.

Raspberry Pi 0/1 users that choose to use this unrecommended emulator should be made aware that RetroArch's **Bilinear Filtering** will cause abnormal behavior in some games and should be disabled whenever emulation issues are encountered.

### PCSX-ReARMed

This emulator is advised for those on a Raspberry Pi 0/1 due to the lower system requirements, though expect some inaccurate emulation.

Setting the Runcommand's resolution setting for this emulator to a low 4:3 resolution on the RPi0 or RPi1 is recommended for faster emulation and correct aspect ratio, though 480i (CEA-6) is the lowest recommended 4:3 CEA resolution due to CEA-2 causing visual issues and CEA-1 causing the system to lock up entirely.

### lr-beetle-psx

This emulator is supplied for people who are running RetroPie on more powerful x86 CPU systems. It is accurate and the best you could ask for when it comes to a PSX core for RetroArch.

lr-beetle-psx is not available for systems with ARM CPUs (like the Raspberry Pi) due to its poor performance on ARM CPUs.

## ROMS
Accepted File Extensions: **.cue .cbn .chd .img .iso .m3u .mdf .pbp .toc .z .znx**

Place your PlayStation ROMs in 
```
/home/pi/RetroPie/roms/psx
```

### `.bin` Only ROMs
  
If you only have a `.bin` ROM and no `.cue` file, you can generate it:

-  [Online](http://nielsbuus.dk/pg/psx_cue_maker/) or [Offline](https://github.com/nielsbuus/psx_cue_maker)
-  [Manually](http://www.shivaranjan.com/2007/01/03/how-to-create-cue-file-for-a-bin-file-in-5-steps/)
-  [Individually](http://www.dslreports.com/r0/download/373724~1e45059000cfc371c157f544cc5aef07/MakeCue.zip)
-  [En Masse or Individually](https://github.com/thorst/CueMaker)

### ECM Compression

If your PSX game has an `.ecm` extension, it's a compressed file that needs to be extracted.

If on Windows, then the following program will do the job. - [ECM Decompressor](https://www.romhacking.net/utilities/1177/)

If familiar with the Terminal on the Raspberry Pi, then all you have to do is

```
sudo apt-get install ecm
ecm-uncompress game-file.bin.ecm
```

### CHD Archive Usage

lr-pcsx-rearmed has support for the CHD (V5) archive format, though a source update of the emulator may be required for said support.

This format will save space and allow you to keep your PSX ROM folder tidy without much work at all, and is the most efficient way to play multi-disc games.

The following archive contains a MAME 0.205 version of CHDMAN and Windows batch files that can be used to quickly convert your PSX games to CHD (V5): [Download](https://drive.google.com/file/d/0B-ElaPpvBHs5aUd0QUM3c05kY2c/view?usp=sharing)

All you have to do is run the appropriate batch file in the same folder as the ROM(s) you wish to compress, though keep in mind the program will search subfolders for `.cue` files to compress as well so you'll want to isolate it unless you want it to do that. If you don't get a `.chd` after running the appropriate batch, then something is wrong with the ROM(s) `.cue`.

### M3U playlist for Multi-Disc Games

Multiple discs can be loaded simultaneously from EmulationStation into RetroArch by creating a `.m3u` file (plain text with `.m3u` extension).

While `.m3u` playlists can be used with a `.cue` and a single `.bin` format ROM, any multi-disc game that has multiple `.bin` files will not work with `.m3u`. Due to this, converting your multi-disc games to `.chd` is the easiest and most efficient method of setting up multi-disc games to be playable with RetroPie.

Replace the `.chd` extension for each disc of the game with an appropriate `.CD1`, `.CD2`, etc so that EmulationStation won't list the individual discs.

Example for Final Fantasy VII:

**Folder Structure:**
```
Final Fantasy VII (USA) (Disc 1).CD1 < This is the renamed .chd file.
Final Fantasy VII (USA) (Disc 2).CD2 < This is the renamed .chd file.
Final Fantasy VII (USA) (Disc 3).CD3 < This is the renamed .chd file.
Final Fantasy VII (USA).m3u
```

**Final Fantasy VII (USA).m3u's Text Contents:**
```
Final Fantasy VII (USA) (Disc 1).CD1
Final Fantasy VII (USA) (Disc 2).CD2
Final Fantasy VII (USA) (Disc 3).CD3
```

To change the disc through RetroArch, from the "Quick Menu", enter "Disk Control", use the "Disk Cycle Tray Status" to open the virtual disk tray, change the disk number to the correct one, then use the "Disk Cycle Tray Status" to close the virtual disk tray.

Alternatively, you could add the following hotkeys to your controller's config file in `/opt/retropie/configs/all/retroarch/autoconfig` so that you can change the disc using hotkeys.

```
input_disk_eject_toggle_btn = "11"
input_disk_next_btn = "12"
```

## BIOS

### lr-pcsx-rearmed

While lr-pcsx-rearmed has an emulated BIOS to fall back on, this has limited compatibility meaning most games will have issues running with it, others will not work at all, and all games that use memory card saves are prone to save corruption. It should be considered mandatory to manually install an official BIOS.

The following BIOS are supported: 

| Recognized Name | Redump Name | CRC32 | MD5 |
| :---: | :---: | :---: | :---: |
| scph101.bin | psone-45a.bin | 171BDCEC | 6E3735FF4C7DC899EE98981385F6F3D0
| scph7001.bin | ps-41a.bin | 502224B6 | 1E68C231D0896B7EADCAD1D7D8E76129
| scph5501.bin | ps-30a.bin | 8D8CB7E4 | 490F666E1AFB15B7362B406ED1CEA246
| scph1001.bin | ps-22a.bin | 37157331 | 924E392ED05558FFDB115408C263DCCF

Place BIOS in
```
/home/pi/RetroPie/BIOS
```
If more than one of the BIOS above is provided, then the latest revision of the BIOS available is automatically chosen.

The recognized name can be all uppercase or all lowercase so if saving space and using **PCSX-ReARMed** is a concern, then you may want to consider renaming **scph1001.bin** to **SCPH1001.BIN** instead of having two copies of the same BIOS.

### PCSX-ReARMed

Whilst PCSX-ReARMed has an emulated BIOS to fall back on, this has limited compatibility meaning most games will have issues running with it, others will not work at all, and all games that use memory card saves are prone to save corruption. It should be considered mandatory to manually install an official BIOS.

The following BIOS is supported:

| Recognized Name | Redump Name | CRC32 | MD5 |
| :---: | :---: | :---: | :---: |
| SCPH1001.BIN | ps-22a.bin | 37157331 | 924E392ED05558FFDB115408C263DCCF

Place BIOS in
```
/home/pi/RetroPie/BIOS
```
The recognized BIOS filename is case-sensitive (must be in all uppercase).

### lr-beetle-psx

The following BIOS are supported: 

| Recognized Name | Redump Name | CRC32 | MD5 |
| :---: | :---: | :---: | :---: |
scph5500.bin | ps-30j | FF3EEB8C | 8DD7D5296A650FAC7319BCE665A6A53C
scph5501.bin | ps-30a | 8D8CB7E4 | 490F666E1AFB15B7362B406ED1CEA246
scph5502.bin | ps-30e | D786F0B9 | 32736F17079D0B2B7024407C39BD3050

The BIOS is automatically chosen based upon the region of the ROM.

The recognized BIOS filename is case-sensitive (must be in all lowercase).

## Controls

### lr-pcsx-rearmed & lr-beetle-psx Controls
lr-pcsx-rearmed and lr-beetle-psx utilize Retroarch configurations.

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/psx/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![playstation3_diagram](https://cloud.githubusercontent.com/assets/10035308/16599634/7f353148-42c0-11e6-9023-dbaf074bc933.png)

### PCSX-ReARMed Controls
PCSX-ReARMed controls and configurations are located in
```
/opt/retropie/configs/psx/pcsx.cfg
```
You will need a keyboard to press Escape on to access the emulator's menu so that you can then configure your controller: a controller with a Home/Guide button that can be a dedicated Open Menu button is required to use this emulator with just a controller.

### The Controller Problem: Digital-Only & Analog

A common issue people using RetroPie have with PSX emulation is their analog sticks do not work. The reason for this is related to a default lr-pcsx-rearmed core setting, and there is a very good reason the setting is the way it is that we will get into later.

Using a controller while a PSX game is running, navigate to RetroArch's Quick Menu (Hotkey Enable + Top Face Button by default), then enter the Options section. In Options, you will want to change "Pad 1 Type" and "Pad 2 Type" from "standard" to "dualshock". 

After the previous two settings have been changed, back out to the Quick Menu so that you can enter the Controls section. In Controls, you need to change all controllers from "RetroPad" to "RetroPad w/ Analog", then use the "Save Core Remap File" function to save this setting as a default for all games.

After a complete exit back to EmulationStation, all games that should work with the analog sticks will function correctly, however, we have just created a problem: roughly 1/3 of the PSX library will no longer accept any input whatsoever.

The reason for the problem is due to the PSX originally being released with a controller that didn't have analog sticks so the games released for the system before the analog sticks were added to the controller only accounted for the standard controller: these games are generally referred to as Digital-Only games.

Unfortunately, this is a problem that doesn't have an easy solution. The reason the emulator was set the way is was is because that was 100% compatible even if it removed all analog functionality. If you want all your games with analog support to work correctly, you will have to manually fix the Digital-Only games one by one.

The process of fixing a Digital-Only game manually is mostly reverting the changes you made, but with a couple extra steps. From RetroArch's Quick Menu, go into Options, use the "Create game-options file" function at the top, then change "Pad 1 Type" and "Pad 2 Type" back to "standard".

With those three things done, now we need to go back to the Quick Menu and go into the Controls section. In Controls, change all "RetroPad w/ Analog" back to ""RetroPad", change all "Analog To Digital" settings for each controller from "None" to "Left Analog", then use the "Save Game Remap File".

After a complete exit back to EmulationStation, the game you've manually fixed will function correctly plus you will be able to use the left analog stick for upto 8-way movement if you want to. Keep in mind the "Analog To Digital" step is completely optional and included for those that may want to still use an analog stick for movement in games that didn't support it originally.

For a decent list of which games are Digital-Only, check the spreadsheet and website found in the "Game Specific Control Information" section below.

The "analog" setting found between "standard" and "dualshock" in the Quick Menu's Options for lr-pcsx-rearmed is for the [NeGcon](https://en.wikipedia.org/wiki/NeGcon).

While this section does focus on lr-pcsx-rearmed, what is done in this section could be done in PCSX-ReARMed's menu as well if not visually different.

### Game Specific Control Information

The main purpose of this section is for users to be able to identify Digital-Only games in their library and fix them as detailed above in the "The Controller Problem: Digital-Only & Analog"

If you have a limited input method such as an SNES-style controller or handheld, then the spreadsheet below will also help you figure out which games you will be able to play.

[PSX - General Game Info](https://docs.google.com/spreadsheets/d/1D4FKPOWCi11zhVvUcS8Bv4-IzyxH9MZRldugigTc59E/edit?usp=sharing)

>If you want to improve the spreadsheet, then request editing permission and you will be approved in a timely manner.

For a more complete resource, please check the [PlayStation DataCenter](http://psxdatacenter.com/).

### Multitap (3-5 Players)

lr-pcsx-rearmed has support for multitap, though due to RetroArch limitations you can only go up to five players.

All you have to do is go into RetroArch's Quick Menu's Options while playing a PSX game that supports the multitap, use the "Create game-options file" function at the top, then set (depending on the number of players "Pad 3 Type", "Pad 4 Type", "Pad 5 Type" to the proper controller type as detailed in the "The Controller Problem: Digital-Only and Analog" section found above and do any relevant changes over in the Quick Menu's Controls as well alongside using the "Save Game Remap File" in there.

After a complete exit back to EmulationStation, multitap should function correctly.

## Tweaks

### lr-pcsx-rearmed

#### Performance - PSX CPU Clock

The clock speed percentage of the emulated PSX hardware's CPU can be adjusted by the user. While the default setting of "57" is decent, it does cause some games to exceed their intended framerate and the setting of "55" is recommended to reduce this from happening in more games.

Using a controller while a PSX game is running, navigate to RetroArch's Quick Menu (Hotkey Enable + Top Face Button by default), then enter the Options section. In Options, you will want to change "PSX cpu clock (default 57)" from "57" to "55".

If you encounter slowdown in games, then increasing the "PSX cpu clock (default 57)" from "55" to something higher may fix that issue if the slowdown is CPU speed related.

While 55 is considered a safe number, it will still cause games like "Final Fantasy 7" and "Final Fantasy Tactics" to exceed their framerate. In Options, you should use the "Create game-options file" function at the top, then change "PSX cpu clock (default 57)" from "55" to "54" for games like that. As for why "54" isn't recommended due to this happening, that is due to the possibility of more games requiring even less and these being two well known exceptions to the recommended setting of "55".

#### Performance - Disable Vibration

Vibration is known to cause slowdown in some games. Disabling vibration in-game (if possible) is recommended if you notice this happen, and you may want to disable it in lr-pcsx-rearmed as well if your controller doesn't have vibration or doesn't work.

Using a controller while a PSX game is running, navigate to RetroArch's Quick Menu (Hotkey Enable + Top Face Button by default), then enter the Options section. In Options, you will want to change "Enable Vibration" to "disabled".

Keep in mind that disabling vibration in-game is what is known to reduce the slowdown it causes, and may still cause the slowdown even if vibration is disabled in lr-pcsx-rearmed.

#### Video - Double Internal Resolution

lr-pcsx-rearmed has a core option to improve graphical fidelity by doubling the normal resolution, producing a sharper 3D image, however all 2D bitmaps and texture maps retain the original resolution.  On a Pi 2 this introduces some slowdown and audio skipping, but on a Pi 3 it appears to work without issue. The 'speed hack' option is required for good results, but has some (sometimes game-breaking) visual glitches.

Using a controller while a PSX game is running, navigate to RetroArch's Quick Menu (Hotkey Enable + Top Face Button by default), then enter the Options section. In Options, you will want to change "Enhanced resolution (slow)" to "enabled" and "Enhanced resolution speed hack" to "enabled".

If you encounter issues using the above settings, then there are two things you can do. In Options, you should use the "Create game-options file" function at the top, then try changing "Enhanced resolution speed hack" to "disabled", exit back to EmulationStation, and see if the problem is corrected without gameplay slowdown. If problems persist, then change "Enhanced resolution (slow)" to "disabled".

#### Video - Disable Dithering

The PSX had a dithering trick that blended colors together in an attempt to make games look more colorful. On modern TVs, this makes the graphics look dirty to some people.

Using a controller while a PSX game is running, navigate to RetroArch's Quick Menu (Hotkey Enable + Top Face Button by default), then enter the Options section. In Options, you will want to change "Enable Dithering" to "disabled".

#### Audio - Switch Interpolation to Gaussian

Some games like "Spyro: Year of the Dragon" have audio corruption issues using the default "simple" setting. The alternative "gaussian" setting fixes audio issue with minimal cost to performance.

Using a controller while a PSX game is running, navigate to RetroArch's Quick Menu (Hotkey Enable + Top Face Button by default), then enter the Options section. In Options, you will want to change "Sound: Interpolation" to "gaussian".

Users following the "Video - Double Internal Resolution" tweak should keep in mind that setting "Sound: Interpolation" to "gaussian" may affect performance to a more noticeable degree.

## Memory Card and Save State

### lr-pcsx-rearmed

Memory Card saves have the `.srm` extension and are located in
```
/home/pi/RetroPie/roms/psx/
```
A new memory card `.srm` file with the same name as the ROM is created for each game as needed.

### PCSX-ReARMed

Memory Card saves are located in
```
/opt/retropie/configs/psx/pcsx/memcards/
```
Their naming convention is cardX.mcd where 'X' is a number between 0 and 9.  Numbers 0 and 1 represent the first 2 Memory Card slots respectively.

Save States are located in
```
/opt/retropie/configs/psx/pcsx/sstates/
```

### Importing Save Files

On sites like [GameFAQs](http://gamefaqs.com/) you can find many save files for PlayStation games, these are either disk images of peoples' memory cards or hacked memory cards with a save file that gets you to a certain point in the game or gives you a character with many levels/gold/items, however the game works.

All the different PlayStation emulators (ePSXe, PCSX, Bleem, PSEmu, etc) and memory card dumper hardware (DexDrive, MadCatz Data Deck) use a different memory card save format, so you often can't just copy these downloaded save files right onto the Pi.

First you must use a memory card manager utility to convert from one format to the format suitable for RetroPie's PCSX-based emulators. One such tool is [Memory Card Manager 1.4 by Aldo Vargas](http://www.aldostools.org/memmanager.html). Download this and `MSVBVM50.DLL`, and run `MemManager.exe`. It looks like this:

![MemManager Screenshot](http://i.imgur.com/AqxfVpy.png)

Press the **New** button at the bottom and create a file the same name as your PSX ROM. For example, if you are using `Diablo.pbp` or `Diablo.cue` then call the new memory card file `Diablo.mcr`. Ensure you select the **Other - AdriPSX, FPSE, pcsx** format in the dropdown menu, then press **Save**.

Press the **><** at the bottom of the window which opens a second pane on the right. In the new pane, press the **...** at the top and open the save file you have downloaded. *Hopefully* you'll see valid memory card blocks, similar to what you'd see on an actual PSX. (some saves may not show expected/valid contents, in which case you're probably out of luck trying to use that save file, download a different one)

Click on the block in the right hand column you wish to import, and press the **<** arrow to copy it into your new memory card on the left hand column. The screenshot above demonstrates the way to select the correct block and the correct button to press.

In your memory card on the left, click **Save As** and save over the blank card you just created.

Quit MemManager and rename your new memory card from `.mcr` to `.srm`. Following our example above, we'd now have a file called `Diablo.srm`. Copy this memory card file to your RetroPie ROMs directory.

Now go to RetroPie and run your game in the PSX emulator. You should be able to see the contents of the memory card and load the saved game which you downloaded.