***
![psx](https://cloud.githubusercontent.com/assets/10035308/12213692/20e2fe3a-b63a-11e5-9e49-c47c33bc659d.png)
***
_The PlayStation 1 is a 5th generation video game console released by Sony in 1994._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-pcsx-rearmed](https://github.com/libretro/pcsx_rearmed) | psx  | .cue .cbn .img .iso .m3u .mdf .pbp .toc .z .znx | SCPH1001.BIN | /opt/retropie/configs/psx/retroarch.cfg |
| [pcsx-rearmed](https://github.com/notaz/pcsx_rearmed) | psx  | .cue .cbn .img .iso .m3u .mdf .pbp .toc .z .znx | SCPH1001.BIN | /opt/retropie/configs/psx/pcsx.cfg |
| [lr-beetle-psx](https://github.com/libretro/beetle-psx-libretro) | psx  | .cue .cbn .img .iso .m3u .mdf .pbp .toc .z .znx | scph5500.bin scph5501.bin scph5502.bin | /opt/retropie/configs/psx/retroarch.cfg |

## Emulators: [lr-pcsx-rearmed](https://github.com/libretro/pcsx_rearmed), [pcsx-rearmed](https://github.com/notaz/pcsx_rearmed), 

## ROMS
Accepted File Extensions: **.cue .cbn .img .iso .m3u .mdf .pbp .toc .z .znx**

Place your PlayStation ROMs in 
```
/home/pi/RetroPie/roms/psx
```

### Why arent my .bin files showing in Emulation Station?
  
Since June 16th 2016 the RetroPie script has configured Emulation Station to no longer show .bin files in the UI.
This means that a .cue file is required to start the game.  
  
A .cue file is basically a plain text file that tells the emulator where in the .bin file the (data and/or audio) track(s) are. This is often important in the case where multiple audio files are in the single .bin file. These are often called "mixed mode" discs. [Wikipedia .cue files](https://en.wikipedia.org/wiki/Cue_sheet_(computing))
  
If you only have a .bin file and no .cue file, you can generate it:
-  [Manually](http://www.shivaranjan.com/2007/01/03/how-to-create-cue-file-for-a-bin-file-in-5-steps/)  
-  [Individually](http://www.dslreports.com/r0/download/373724~1e45059000cfc371c157f544cc5aef07/MakeCue.zip)
-  [En masse or individually](https://github.com/thorst/CueMaker)  

### Cue files
You can also find cue files for many games here, obviously you will need to make sure the .bin filename is correct when you use it.  
[Link to .cue files](http://s000.tinyupload.com/index.php?file_id=08258966889995234828)

### Why .bin was removed
- It is very common for PSX games to be in 2 parts, a .bin and .cue, this means that Emulation Station will show duplicates for each game which no-one really wants. This is because it used to show extensions .bin and .cue
- A PSX game will only ever need one .cue file, so by hiding a .bin it prevents duplicates showing (as it could have multiple .bin files)
- By hiding .bin files it will make the user think a little bit more about how the emulator loads files rather than blindly throwing files at it until it works.
- Any PSX game that has multi tracks will work better (usually audio tracks) if it has a .cue to point to the audio.  
https://retropie.org.uk/forum/topic/735/psx-please-remove-bin-from-the-file-types

if your psx game is a .ecm extension, its a compressed file that needs to be extracted with ecmtools.

### Where is lr-beetle-psx?

The Beetle/Mednafen PSX core is not available for systems with ARM CPUs (like the Raspberry Pi) because it does not perform well enough. This emulator is supplied for people who are running RetroPie on more powerful x86 systems.

* [RetroPie commit - Add Beetle PSX emulator](https://github.com/RetroPie/RetroPie-Setup/commit/6f0ce53857bd9eab2d78ad1dd6eefc112cf61e6d)

~~~shell
$ grep flags scriptmodules/libretrocores/lr-beetle-psx.sh
rp_module_flags="!arm"
~~~

## BIOS

The BIOS file is named **SCPH1001.BIN**

Place SCPH1001.BIN in
```
/home/pi/RetroPie/BIOS
```
See table at the bottom for alternative BIOS options that may or may not work.

## Controls

### lr-pcsx-rearmed Controls
lr-pcsx-rearmed utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/psx/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

![playstation3_diagram](https://cloud.githubusercontent.com/assets/10035308/16599634/7f353148-42c0-11e6-9023-dbaf074bc933.png)

### pcsx-rearmed Controls
pcsx-rearmed controls and configurations are located in
```
/opt/retropie/configs/psx/pcsx.cfg
```
An example mapping for pcsx-rearmed using an Xbox 360 controller is below for reference:

**Xbox 360 Controller**
```
binddev = sdl:Xbox 360 Wireless Receiver (XBOX)
bind backspace = Fast Forward
bind \xA0 = player1 CROSS
bind \xA1 = player1 SQUARE
bind \xA2 = player1 CIRCLE
bind \xA3 = player1 TRIANGLE
bind \xA4 = player1 L1
bind \xA5 = player1 R1
bind \xA6 = player1 L2
bind \xA7 = player1 R2
bind \xA8 = player1 SELECT
bind \xA9 = player1 START
bind \xAA = Enter Menu
bind \xAB = player1 L3
bind \xAC = player1 R3
bind \xAD = player1 LEFT
bind \xAE = player1 RIGHT
bind \xAF = player1 UP
bind \xB0 = player1 DOWN
bind up = player1 UP
bind down = player1 DOWN
bind right = player1 RIGHT
bind left = player1 LEFT
bind f1 = Save State
bind f2 = Load State
bind f3 = Prev Save Slot
bind f4 = Next Save Slot
bind f5 = Toggle Frameskip
bind f7 = Show/Hide FPS
bind f8 = Switch Renderer
bind f11 = Toggle fullscreen
bind f12 = Take Screenshot
```

### Video Guide  

<a href="https://www.youtube.com/watch?v=a7JtysTXaAU
" target="_blank"><img src="https://i.ytimg.com/vi_webp/a7JtysTXaAU/mqdefault.webp" 
alt="RetroPie Playstation 1 emulation" width="300" height="190" border="10" /></a>  

### Enhanced Graphics

lr-pcsx-rearmed has a core option to improve graphical fidelity by doubling the normal resolution. This increases the resolution of the 3D polygons, producing a far sharper image, however all 2D bitmaps and texture maps retain the original resolution.  On a Pi 2 this introduces some slowdown and audio skipping, but on a Pi 3 it appears to work without issue. The 'speed hack' option is required for good results, but has some minor visual glitches.

To enable this, edit the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
pcsx_rearmed_neon_enhancement_enable = "enabled" # Double resolution
pcsx_rearmed_neon_enhancement_no_main = "enabled" # Speed hack
```

#### Bilinear Smoothing

To further refine the graphics, enable bilinear smoothing.

To enable this, edit the `retroarch.cfg` file, found in:
```
/opt/retropie/configs/psx/
```
The option is:
```
video_smooth = "true"
```

### Multitap (3-8 player)

The latest version of lr-pcsx-rearmed has the ability to emulate up to two Multitaps, allowing 3-8 player support in games that permit it. It does this via core options. However, just as with the original hardware, many games do not support the multitap and will not recognise _any_ inputs with it turned on, so it is recommended to only enable multitaps for games that support it, via the 'Game Specific Options' retroarch functionality which allows you to create core options files for specific games. To enable this, use the [Configuration Editor](Configuration-Editor) > **Advanced Configuration** > **Configure Libretro options** > **psx/retroarch.cfg** > Set **game_specific_options** to **true**.

Alternatively, you can manually edit `retroarch.cfg` in:
```
/opt/retropie/configs/psx/
```
The option is:
```
game_specific_options = "true"
```

Then, within a multiplayer game, load up the Retroarch menu via the menu hotkey combination (select & X/Triangle, by default), go to **Quick Menu** > **Options** > Find the **Multitap 1** and **Multitap 2** options and turn them on, as appropriate. Then scroll to the top, and choose **Create game options file**. Once this is completed, restart the game, and multiplayer options should become available.

**Create game options file** will create a game specific core options file located at:
```
/opt/retropie/configs/all/retroarch/config/PCSX-ReARMed/GAME_TITLE.opt
```

### Analog Controller Type

lr-pcsc-rearmed controller type can be changed in-game and in a configuration file to support games that require the analog/dualshock controller type.<br>
**NOTE:** Games that do not support analog controls will be unresponsive in this mode.
* Use the Retroarch GUI hotkey(default select+X) in-game
* Navigate to Quick Menu -> Core Options
* Change Pad # Type from standard to analog
* `retroarch-core-options.cfg` will be updated automatically when a game is exited, so there is no need to set save on exit

Retroarch Core options can be located in `/opt/retropie/configs/all/retroarch-core-options.cfg` for changing manually outside of a game.
```
pcsx_rearmed_pad1type = "analog"
pcsx_rearmed_pad2type = "standard"
```

The standalone pcsx-rearmed controller type can be changed in the in-game menu.
* Enter the in-game menu using ESC on a keyboard
* Navigate to the controls menu
* Change Port # device from Standard to Analog

### Disc Swapping for Multi-disc Games in RetroArch 

To change disks in-game, go to Core Disk Options > Disk Image Append.

Some games like Metal Gear Solid require the disk tray to be opened before changing disks. To do this, change 'Disk Index' to 'No Disk' first. 

### M3U playlist for Multi-disc Games

Multiple discs can be loaded simultaneously from Emulation Station into RetroArch by creating an M3U file (plain-text, ".m3u" extension). In it's contents, enter the filenames of the CUE/TOC/CCD files one per line. In game you can then swap disks from the core disk options menu (under Options). Make sure to cycle tray status before attempting to change disks.

To have the M3U file be the only item listed in Emulation Station to reduced menu clutter:

Remove the .cue extension on the multi-disc files so that es_systems.cfg won't list them.
Remove the .cue extension you reference them in the M3U.

An M3U for Chrono Cross looks like this for example:

```
Chrono Cross CD1
Chrono Cross CD2
```

This will function the same as EBOOT-format without altering the files.

### EBOOT-format (.pbp) for Multi-disc games

All current emulators accept `.pbp` files, which are EBOOT-format PlayStation executables. These are traditionally used to play PlayStation 1 games on the PSP.

This is a streamlined, single file alternative for playing multi-disc PlayStation games on RetroPie.

CD images can be converted to EBOOT `.pbp` files with the **PSX2PSP v1.4.2** application for Windows, or **iPoPS** for Mac OSX.

EBOOTs are also often smaller than CD images, so this is a good option if you're tight on space. It should be noted that this compression comes at a minor cost to load speed, but the difference is mostly negligible.

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

### Alternative BIOS files

Add different bios' that you've tested and tell the community if it works or not.

Name |Description| md5          |        CRC32       | Comment
-----|----------|--------------|--------------------|-----------|
ps-10j|SCPH-1000/DTL-H1000 (Version 1.0 J)|239665b1a3dade1b5a52c06338011044|3b601fc8||
ps-11j|SCPH-3000/DTL-H1000H (Version 1.1 01/22/95)|849515939161e62f6b866f6853006780|3539def6||
ps-20a|DTL-H1001 (Version 2.0 05/07/95 A)|dc2b9bf8da62ec93e868cfd29f0d067d|55847d8c||
ps-20e|DTL-H1002/SCPH-1002 (Version 2.0 05/10/95 E)|54847e693405ffeb0359c6287434cbef|9bb87c4b||
ps-21j|SCPH-3500 (Version 2.1 07/17/95 J)|cba733ceeff5aef5c32254f1d617fa62|bc190209||
ps-21a|DTL-H1101 (Version 2.1 07/17/95 A)|da27e8b6dab242d8f91a9b25d80c63b8|aff00f2f||
ps-21e|SCPH-1002/DTL-H1102 (Version 2.1 07/17/95 E)|417b34706319da7cf001e76e40136c23|86c30531||
ps-22j|SCPH-5000/DTL-H1200/DTL-H3000 (Version 2.2 12/04/95 J)|57a06303dfa9cf9351222dfcbb4a29d9|24fc7e17||
ps-22a|SCPH-1001/DTL-H1201/DTL-H3001 (Version 2.2 12/04/95 A)|924e392ed05558ffdb115408c263dccf|37157331||
ps-22e|SCPH-1002/DTL-H1202/DTL-H3002 (Version 2.2 12/04/95 E)|e2110b8a2b97a8e0b857a45d32f7e187|1e26792f||
ps-22d|DTL-H1100 (Version 2.2 03/06/96 D)|ca5cfc321f916756e3f0effbfaeba13b|decb22f5||
ps-30j|SCPH-5500 (Version 3.0 09/09/96 J)|8dd7d5296a650fac7319bce665a6a53c|ff3eeb8c||
ps-30a|SCPH-5501/SCPH-5503/SCPH-7003 (Version 3.0 11/18/96 A)|490f666e1afb15b7362b406ed1cea246|8d8cb7e4||
ps-30e|SCPH-5502/SCPH-5552 (Version 3.0 01/06/97 E)|32736f17079d0b2b7024407c39bd3050|d786f0b9||
ps-40j|SCPH-7000/SCPH-7500/SCPH-9000 (Version 4.0 08/18/97 J)|8e4c14f567745eff2f0408c8129f72a6|ec541cd0||
ps-41a|SCPH-7001/SCPH-7501/SCPH-7503/SCPH-9001/SCPH-9003/SCPH-9903 (Version 4.1 12/16/97 A)|1e68c231d0896b7eadcad1d7d8e76129|502224b6||
ps-41e|SCPH-7002/SCPH-7502/SCPH-9002 (Version 4.1 12/16/97 E)|b9d9a0286c33dc6b7237bb13cd46fdee|318178bf||
psone-43j|SCPH-100 (Version 4.3 03/11/00 J)|8abc1b549a4a80954addc48ef02c4521|f2af798b||
psone-44e|SCPH-102 (Version 4.4 03/24/00 E)|b10f5e0e3d9eb60e5159690680b1e774|0bad7ea9||
psone-45a|SCPH-101 (Version 4.5 05/25/00 A)|6e3735ff4c7dc899ee98981385f6f3d0|171bdcec||
psone-45e|SCPH-102 (Version 4.5 05/25/00 E)|de93caec13d1a141a40a79f5c86168d6|76b880e5||