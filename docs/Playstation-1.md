***
![psx](https://cloud.githubusercontent.com/assets/10035308/12213692/20e2fe3a-b63a-11e5-9e49-c47c33bc659d.png)
***
_The PlayStation is a 5th generation video game console released by Sony in 1994._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-pcsx_rearmed](https://github.com/libretro/pcsx_rearmed) | psx  | .cue .cbn .chd .img .iso .m3u .mdf .pbp .toc .z .znx | psxonpsp660.bin scph101.bin scph7001.bin scph5501.bin scph1001.bin | /opt/retropie/configs/psx/retroarch.cfg |
| [PCSX-ReARMed](https://github.com/notaz/pcsx_rearmed) | psx  | .cue .cbn .img .iso .m3u .mdf .pbp .toc .z .znx | SCPH1001.BIN | /opt/retropie/configs/psx/pcsx.cfg |
| [lr-beetle-psx](https://github.com/libretro/beetle-psx-libretro) | psx  | .cue .ccd .chd .exe .iso .m3u .pbp .toc | scph5500.bin scph5501.bin scph5502.bin | /opt/retropie/configs/psx/retroarch.cfg |
| [lr-duckstation](https://github.com/stenzek/duckstation) | psx  | .exe .cue .bin .chd .psf .m3u .pbp | any valid BIOS dumps | /opt/retropie/configs/psx/duckstation.cfg |

## Emulators: [lr-pcsx_rearmed](https://github.com/libretro/pcsx_rearmed), [PCSX-ReARMed](https://github.com/notaz/pcsx_rearmed), [lr-beetle-psx](https://github.com/libretro/beetle-psx-libretro), [lr-duckstation](https://github.com/stenzek/duckstation).

### lr-pcsx_rearmed

Recommended for Raspberry Pi 2-4. The features of RetroArch combined with PCSX-ReARMed's excellent Dynamic Recompiler allow for an adequate PlayStation emulation experience, though expect some inaccurate emulation.

### PCSX-ReARMed

Recommended for Raspberry Pi 0/1 due to its lower system requirements, though expect some inaccurate emulation. Additionally, setting the resolution via [Runcommand](Runcommand) to a low 4:3 resolution is recommended for faster emulation and correct aspect ratio, though 480i (CEA-6) is the lowest recommended 4:3 CEA resolution due to CEA-2 causing visual issues and CEA-1 causing the system to lock up entirely.

### lr-beetle-psx

Recommended for more powerful x86 systems. It is accurate and includes several enhanced graphical features. Not available for ARM systems (like the Raspberry Pi) due to its poor performance on ARM.

### lr-duckstation

Experimental but promising fast, accurate emulation, including various graphial enhancements. Supported on all architectures aside from ARMv6 (Raspberyy Pi 0/1) and 32-bit x86.

## ROMS
Accepted File Extensions: **.cue .ccd .chd .exe .iso .m3u .pbp .toc**

Place your PlayStation ROMs in 
```
/home/pi/RetroPie/roms/psx
```

### `.bin` Only ROMs
  
If you only have a `.bin` ROM and no `.cue` file, generate it via:

-  [Online](http://nielsbuus.dk/pg/psx_cue_maker/) or [Offline](https://github.com/nielsbuus/psx_cue_maker)
-  [Individually](http://www.dslreports.com/r0/download/373724~1e45059000cfc371c157f544cc5aef07/MakeCue.zip)
-  [En Masse or Individually](https://github.com/thorst/CueMaker)

### ECM Compression

If your PSX game has an `.ecm` extension, it's a compressed file that needs to be extracted.

Directly on RetroPie, input to terminal:
```
sudo apt install ecm
ecm-uncompress game-file.bin.ecm
```

Alternatively, on Windows, use [ECM Decompressor](https://www.romhacking.net/utilities/1177/), or on Ubuntu 19.X+(or derivative), install ecm from the ubuntu archive with the following:
```
curl -sLO http://archive.ubuntu.com/ubuntu/pool/universe/c/cmdpack/ecm_1.03-1build1_amd64.deb && sudo dpkg -i ecm_1.03-1build1_amd64.deb && sudo rm ecm_1.03-1build1_amd64.deb
```

### CHD files

All supported PlayStation emulators have support for the CHD (V5) archive format. This is a lossless compression format which can be useful to tidy up multi-.bin ROMs into one file. See [Creating CHDs from CD-ROMS](CHD-files#creating-chds-from-cd-roms).

### Multi-Disc Games

.pbp format ROMs can package together multiple discs in one file. To change the disc through RetroArch, from the "Quick Menu", enter "Disk Control", use the "Disk Cycle Tray Status" to open the virtual disk tray, change the disk number to the correct one, then use the "Disk Cycle Tray Status" to close the virtual disk tray.

#### M3U playlists for .cue & .bins, or .chds

For multi-disc games on .cue & .bin ROM pairs or .chds, you can create a .m3u playlist file to enable you to change discs by the above method. Replace the `.cue` or `.chd` extension for each disc of the game with an appropriate `.CD1`, `.CD2`, etc so that EmulationStation will list only the `.m3u` and not the individual discs.
**NOTE:** **lr-duckstation** does not support extension renaming within .m3u playlists.

Example for Final Fantasy VII:

**Folder Structure:**
```
Final Fantasy VII (USA) (Disc 1).CD1 < This is the renamed .cue or .chd file.
Final Fantasy VII (USA) (Disc 2).CD2 < This is the renamed .cue or .chd file.
Final Fantasy VII (USA) (Disc 3).CD3 < This is the renamed .cue or .chd file.
Final Fantasy VII (USA).m3u
```

**Final Fantasy VII (USA).m3u's Text Contents:**
```
Final Fantasy VII (USA) (Disc 1).CD1
Final Fantasy VII (USA) (Disc 2).CD2
Final Fantasy VII (USA) (Disc 3).CD3
```

## BIOS

Place BIOS in
```
/home/pi/RetroPie/BIOS
```

While both **lr-pcsx_rearmed** and **PCSX-ReARMed** have an emulated BIOS to fall back on, it has limited compatibility so most games will have issues running with it (or not work at all), and all games that use memory card saves are prone to save corruption. It should be considered mandatory to manually install an official BIOS.

### lr-pcsx_rearmed

The following BIOS are supported: 

| Recognized Name | Redump Name | CRC32 | MD5 |
| :---: | :---: | :---: | :---: |
| psxonpsp660.bin |  | 5660F34F | C53CA5908936D412331790F4426C6C33
| scph101.bin | psone-45a.bin | 171BDCEC | 6E3735FF4C7DC899EE98981385F6F3D0
| scph7001.bin | ps-41a.bin | 502224B6 | 1E68C231D0896B7EADCAD1D7D8E76129
| scph5501.bin | ps-30a.bin | 8D8CB7E4 | 490F666E1AFB15B7362B406ED1CEA246
| scph1001.bin | ps-22a.bin | 37157331 | 924E392ED05558FFDB115408C263DCCF

If more than one of the BIOS above is provided, then the latest revision of the BIOS available is automatically chosen.
**Note**: psxonpsp660.bin is a BIOS dumped from the [PSP](PSP)'s PlayStation emulator. It is said to improve performance for certain PlayStation games as is a streamlined version of the BIOS, lacking irrelevant features like the built-in CD Player and Memory Card manager.

The recognized name can be all uppercase OR all lowercase.

### PCSX-ReARMed

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

### lr-duckstation

Any valid BIOS dump from real hardware is supported (too many to list). As such, any of the above BIOS dumps should be supported, when named appropriately with .bin extension.

The BIOS is automatically chosen based upon the region of the ROM.

## Controls

### lr-pcsx_rearmed, lr-beetle-psx & lr-duckstation Controls
lr-pcsx_rearmed and lr-beetle-psx utilize RetroArch configurations.

Add custom RetroArch controls to the retroarch.cfg file in
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

A common issue people using RetroPie have with PSX emulation is their analog sticks do not work. The reason for this is related to a default lr-pcsx_rearmed core setting, and there is a very good reason the setting is the way it is that we will get into later.

Open the **Quick Menu**, select **Controls** and for **Port 1 Controls** and **Port 2 Controls**, change the Device Type from **standard** to **dualshock**. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

On the **Controls** page, select **Save Core Remap File** to save this setting as a default for all games.

After a complete exit back to EmulationStation, all games that should work with the analog sticks will function correctly, however, we have just created a problem: roughly 1/3 of the PSX library will no longer accept any input whatsoever.

The reason for the problem is due to the PSX originally being released with a controller that didn't have analog sticks. The games released for the system prior to the analog sticks being added to the controller only account for the standard controller: these games are generally referred to as Digital-Only games.

Unfortunately, this is a problem that doesn't have an easy solution. The reason the emulator was set the way it was is because it was 100% compatible even if it removed all analog functionality. If you want all your games with analog support to work correctly, you will have to manually fix the Digital-Only games one by one.

The process of fixing a Digital-Only game is to set per-ROM Core Options, changing **Port 1 Device Type** and **Port 2 Device Type** back to **standard** and then do **Save Game Remap File**. See [Setting Core Options per-ROM](RetroArch-Core-Options#setting-core-options-per-rom).

(Optional) In **Port (#) Controls**, change all **Analog to Digital Type** settings from **None** to **Left Analog**, then do **Save Game Remap File**.

After a complete exit back to EmulationStation, the game you've manually fixed will function correctly plus you will be able to use the left analog stick for up to 8-way movement if you want to. Keep in mind the "Analog To Digital" step is completely optional and included for those that may want to still use an analog stick for movement in games that didn't support it originally.

For a decent list of which games are Digital-Only, check the spreadsheet and website found in the "Game Specific Control Information" section below.

The **negcon** setting found between pad type is for the [NeGcon](https://en.wikipedia.org/wiki/NeGcon).

While this section does focus on lr-pcsx_rearmed, what is done in this section could be done in PCSX-ReARMed's menu as well if not visually different.

### Game Specific Control Information

The main purpose of this section is for users to be able to identify Digital-Only games in their library and fix them as detailed above in the "The Controller Problem: Digital-Only & Analog"

If you have a limited input method such as an SNES-style controller or handheld, then the spreadsheet below will also help you figure out which games you will be able to play.

[PSX - General Game Info](https://docs.google.com/spreadsheets/d/1D4FKPOWCi11zhVvUcS8Bv4-IzyxH9MZRldugigTc59E/edit?usp=sharing)

>If you want to improve the spreadsheet, then request editing permission and you will be approved in a timely manner.

For a more complete resource, please check the [PlayStation DataCenter](http://psxdatacenter.com/).

### Multitap (3-5 Players)

lr-pcsx_rearmed has support for multitap, but not all games read input when a multitap is connected, so a per-ROM Core Options file should be created for multitap compatible games. Set the Core Options for **Pad 3 Type**, **Pad 4 Type** (and so on, depending on how many players are supported by the game) to the relevant Controller Type that the game supports. See [Setting Core Options per-ROM](RetroArch-Core-Options#setting-core-options-per-rom).

## Tweaks

### lr-pcsx_rearmed

#### Performance - PSX CPU Clock

The clock speed percentage of the emulated PSX hardware's CPU can be adjusted by the user. While the default setting of **57** is decent, it does cause some games to exceed their intended frame rate and the setting of **55** is recommended to reduce this from happening in more games. Some games, such as "Final Fantasy 7" and "Final Fantasy Tactics", may need even lower CPU speeds. See [Setting Core Options per-ROM](RetroArch-Core-Options#setting-core-options-per-rom).

#### Performance - Disable Vibration

Vibration is known to cause slowdown in some games. Disabling vibration in-game (if possible) is recommended if you notice this happen, or don't have a controller with vibration ability. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

Change Core Option **Enable Vibration** to **disabled**

Instances in-game where vibration occurs may still cause the slowdown even if vibration is disabled.

#### Video - Double Internal Resolution

lr-pcsx_rearmed has a Core Option **Enhance Resolution (Slow)** that improves graphical fidelity by doubling the normal resolution, producing a sharper 3D image, however all 2D bitmaps and texture maps retain their original resolution. It can present some (sometimes game-breaking) visual glitches. It should be used in tandem with the **Enhanced Resolution (Speed Hack)** for best performance, but this can increase the glitches. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

On a Pi 2 it can introduce performance issues, even with the speed hack, but on a Pi 3 and up it should be perform better, sometimes even without the speed hack. To disable these options for games which exhibit issues, or to only enable it for games that perform well, see [Setting Core Options per-ROM](RetroArch-Core-Options#setting-core-options-per-rom).

#### Video - Disable Dithering

The PSX had a dithering trick that blended colors together in an attempt to make games look more colorful. On modern TVs this effect can be less desirable. To disable, set the Core Option **Enable Dithering** to **disabled**. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

#### Audio - Switch Interpolation to Gaussian

Some games like "Spyro: Year of the Dragon" have audio corruption issues using the default Core Option **Sound: Interpolation** value of **simple**. The alternative **gaussian** setting fixes audio issue with minimal cost to performance. See [Setting Core Options](RetroArch-Core-Options#setting-core-options).

## Memory Card and Save State

### lr-pcsx_rearmed

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

On sites like [GameFAQs](http://gamefaqs.com/) you can find many save files for PlayStation games. Different emulators often use different save file formats, so you must convert such files to a suitable format.

One such tool is [Memory Card Manager 1.4 by Aldo Vargas](http://www.aldostools.org/memmanager.html). Download this and `MSVBVM50.DLL`, and run `MemManager.exe`:

![MemManager Screenshot](http://i.imgur.com/AqxfVpy.png)

Press the **New** button at the bottom and create a file the same name as your PSX ROM. For example, if you are using `Diablo.pbp` or `Diablo.cue` then call the new memory card file `Diablo.mcr`. Ensure you select the **Other - AdriPSX, FPSE, pcsx** format in the dropdown menu, then press **Save**.

Press the **><** at the bottom of the window which opens a second pane on the right. In the new pane, press the **...** at the top and open the save file you have downloaded. *Hopefully* you'll see valid memory card blocks, similar to what you'd see on an actual PSX. (some saves may not show expected/valid contents, in which case you're probably out of luck trying to use that save file, download a different one)

Click on the block in the right hand column you wish to import, and press the **<** arrow to copy it into your new memory card on the left-hand column. The screenshot above demonstrates the way to select the correct block and the correct button to press.

In your memory card on the left, click **Save As** and save over the blank card you just created.

Quit MemManager and rename your new memory card from `.mcr` to `.srm`. Following our example above, we'd now have a file called `Diablo.srm`. Copy this memory card file to your RetroPie `/psx/` ROMs directory.

The save file should now be available in your game.
