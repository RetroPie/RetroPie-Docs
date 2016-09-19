***
![psx](https://cloud.githubusercontent.com/assets/10035308/12213692/20e2fe3a-b63a-11e5-9e49-c47c33bc659d.png)
***
_The PlayStation 1 is a 5th generation video game console released by Sony in 1994._

***

| Emulator | Rom Folder | Extension | BIOS |  Controller Config |
| :---: | :---: | :---: | :---: | :---: |
| [lr-pcsx-rearmed](https://github.com/libretro/pcsx_rearmed) | psx  | .cue .cbn .img .iso .m3u .mdf .pbp .toc .z .znx | SCPH1001.BIN | /opt/retropie/configs/psx/retroarch.cfg |
| [pcsx-rearmed](https://github.com/notaz/pcsx_rearmed) | psx  | .cue .cbn .img .iso .m3u .mdf .pbp .toc .z .znx | SCPH1001.BIN | hardcoded |
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
* Manually:
http://www.shivaranjan.com/2007/01/03/how-to-create-cue-file-for-a-bin-file-in-5-steps/  
* Individually:
http://www.dslreports.com/r0/download/373724~1e45059000cfc371c157f544cc5aef07/MakeCue.zip
* En masse or individually: https://github.com/thorst/CueMaker
  
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

The BIOS file is named **SCPH1001.BIN** (both name and extension are case-sensitive so MUST be in capitals)

Place SCPH1001.BIN in
```
/home/pi/RetroPie/BIOS
```
See table at the bottom for alternative BIOS options that may or may not work.

## Controls

lr-pcsx-rearmed utilises Retroarch configurations

Add custom retroarch controls to the retroarch.cfg file in
```shell
/opt/retropie/configs/psx/retroarch.cfg
```
For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/petrockblog/RetroPie-Setup/wiki/RetroArch-Configuration)

![playstation3_diagram](https://cloud.githubusercontent.com/assets/10035308/16599634/7f353148-42c0-11e6-9023-dbaf074bc933.png)

### Video Guide  

<a href="https://www.youtube.com/watch?v=a7JtysTXaAU
" target="_blank"><img src="https://i.ytimg.com/vi_webp/a7JtysTXaAU/mqdefault.webp" 
alt="RetroPie Playstation 1 emulation" width="300" height="190" border="10" /></a>  

### Enhanced Graphics

lr-pcsx-rearmed has a core option to improve graphical fidelity by doubling the normal resolution. On a Pi 2 this introduces some slowdown and audio skipping, but on a Pi 3 it appears to work without issue. The 'speed hack' option is required for good results, but has some minor visual glitches.

To enable this, edit the `retroarch-core-options.cfg` file, found in:
```
/opt/retropie/configs/all/
```
The option is:
```
pcsx_rearmed_neon_enhancement_enable = "enabled"
pcsx_rearmed_neon_enhancement_no_main = "enabled"
```

### Multitap (3-8 player)

The latest version of lr-pcsx-rearmed has the ability to emulate up to two Multitaps, allowing 3-8 player support in games that permit it. It does this via core options. However, just as with the original hardware, many games do not support the multitap and will not recognise _any_ inputs with it turned on, so it is recommended to only enable multitaps for games that support it, via the 'Game Specific Options' retroarch functionality which allows you to create core options files for specific games. To enable this, use the [[Configuration Editor]] > **Advanced Configuration** > **Configure Libretro options** > **psx/retroarch.cfg** > Set **game_specific_options** to **true**.

Alternatively, you can manually edit `retroarch.cfg` in:
```
/opt/retropie/configs/psx/
```
The option is:
```
game_specific_options = "true"
```

Then, within a multiplayer game, load up the Retroarch menu via the menu hotkey combination (select & X/Triangle, by default), go to **Quick Menu** > **Options** > Find the **Multitap 1** and **Multitap 2** options and turn them on, as appropriate. Then scroll to the top, and choose **Create game options file**. Once this is completed, restart the game, and multiplayer options should become available.

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

### Multi-disc games or CD image not working

Note that all the emulators accept `.pbp` files, which are EBOOT-format PlayStation executables. These are also known as PSX2PSP files, used to play PlayStation 1 games on the PSP.

This is the easiest way to play multi-disc PlayStation games on RetroPie.

If a CD image such as `.iso` or `.bin/.cue` does not work, try the EBOOT version.

CD images can be converted to EBOOT `.pbp` files with the **PSX2PSP v1.4.2** application for Windows.

EBOOTs are also often smaller than CD images, so could be a good option if you're tight on space.

### Alternative BIOS files

Add different bios' that you've tested and tell the community if it works or not.

Name |Description| md5          |        CRC32       | Comment
-----|----------|--------------|--------------------|-----------|------
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