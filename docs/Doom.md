![](http://1.bp.blogspot.com/-q1BVHMrTq7M/UT9Y6D_tCLI/AAAAAAAAD40/fM2ZUTzEIqE/s1600/risen3d+3d+models+doom+title.png)

***

_Doom was the game that popularized First Person Shooting as a genre. It was developed by Id Software in 1993._

***
## Ports: [lr-prboom](https://github.com/petrockblog/RetroPie-Setup/blob/master/scriptmodules/libretrocores/lr-prboom.sh), [LZDoom](https://github.com/rheit/zdoom), [GZDoom](https://zdoom.org/downloads), [DSDA-Doom](https://github.com/kraflab/dsda-doom/).

### lr-prboom

Port of PrBoom to Libretro. This port supports Doom, Doom 2, Final Doom and Freedoom alongside the simple mods that don't require other source port enhancements. Unlike other source ports that concentrate on offering many new game features or changes - such as ZDoom - PrBoom aims to act as a stable port of the more established or traditional engines.

### LZDoom

LZDoom is an enhanced source port of the Doom engine, based on GZDoom, for running on modern operating systems. It adds new features not found in the games originally published by id Software.

This port officially supports the following Doom engine games: Doom, Doom 2, Final Doom, Heretic, Hexen, Strife and Chex Quest. It also has official support for the following stand-alone mods: Action Doom 2: Urban Brawl, The Adventures of Square, Chex Quest 3, Hacx and Harmony. Additional stand-alone mods may work with this port, they just aren't officially supported.

### GZDoom

GZDoom is a 3D-accelerated Doom source port based on ZDoom. GZDoom features an OpenGL/GLES and Vulkan renderers and packs lots of new features, among them:

  * Sloped 3D floors
  * Light effects, including dynamic lights, brightmaps, and glowing flats.
  * Quake2-style skyboxes
  * True color support
  * Model support (MD3, OBJ and IQM)
  * Unicode fonts
  * ZScript

It has the broadest support for mods and the best support for total conversions. It is also a bit more performance demanding than the other DOOM source ports available, being suitable for PC installations or more powerfull SBC platforms.

### DSDA-Doom
This is a successor of PrBoom+ with many new features, including:

  * Heretic, Hexen, MBF21, Doom-in-Hexen, UDMF, and MAPINFO support
  * In-game console and scripting
  * Full controller support
  * Palette-based opengl renderer
  * Debugging features for testing
  * Strict mode for speedrunning
  * Various quality of life improvements
  * Advanced tools for TASing
  * Rewind
  * Support for MBF21 v1.4 and UMAPINFO v2.2

It has good support for mods/wads and it's recommended as a replacement for LZDoom as an all-platforms suited source port.

## Installation

### lr-prboom Installation

lr-prboom is found under Optional Packages in RetroPie Setup. After installation and a restart of EmulationStation, you will have the shareware version of Doom in the Ports section. 

Below you will find `.sh` and folder structure examples for Ultimate Doom, Doom 2, Final Doom, and Freedoom IWADs, and various Doom/Doom 2 PWADs that don't depend on the features more robust source ports provide. The reason for putting each game/mod in separate folders is so that each game has separate saves and settings, and allows you to install the additional high-quality MP3s detailed later without naming conflicts.

#### Full Games (IWADs)

##### Doom 2

Available on [GOG](https://www.gog.com/game/doom_ii) and [Steam](https://store.steampowered.com/app/2300/DOOM_II/)

Start script

``` sh title="Doom II.sh"
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/doom2/DOOM2.WAD"
```

Folder structure

``` sh
/home/pi/RetroPie/roms/ports/doom/doom2/
                                       DOOM2.WAD
                                       prboom.wad
```

##### Freedoom - Phase 1

Available for free [here](https://freedoom.github.io/download.html).

Start script 

``` sh title="Freedoom - Phase 1.sh"
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/freedoom/FREEDOOM1.WAD""
```

Folder structure
```
/home/pi/RetroPie/roms/ports/doom/freedoom/
                                          FREEDOOM1.WAD
                                          prboom.wad
```

##### Freedoom - Phase 2

Available for free [here](https://freedoom.github.io/download.html).

Start script

``` sh title="Freedoom - Phase 2.sh"
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/freedoom2/FREEDOOM2.WAD""
```

Folder structure
``` sh
/home/pi/RetroPie/roms/ports/doom/freedoom2/
                                           FREEDOOM2.WAD
                                           prboom.wad
```

#### Mods (PWADs)

These are used in conjunction with Doom/Freedoom - Phase 1 to play Doom mods and with Doom 2/Final Doom/Freedoom - Phase 2 to play Doom 2 mods. Ideally, you will want to have run the IWAD games before working on these so that you will be able to simply copy one of the appropriate game folders you made above that contains the IWAD you want/need to use, the `prboom.wad` and the respective `DOOM`/`DOOM2`/`PLUTONIA`/`TNT`/`FREEDOOM1`/`FREEDOOM2` folder containing the `prboom.cfg` to edit.

Due to the extensive number of PWADs out there, only these commercial PWADs are included in the documentation here, though they should give you a good idea of how to use other PWADs.

If you plan to use MP3 music over lr-prboom's MIDI, then it is advised that you follow the guide for that in the Enhancements section before copying any game folder for PWAD use to avoid additional work.

**It is advised that you also apply the fix for lr-prboom's current floor and ceiling bug found in the Issues section to all games before copying any game folder for PWAD use to avoid additional work.**

##### Doom - Sigil

A Doom mod made by John Romero for Doom's 35th anniversary. It is available for free [here](https://romero.com/sigil). It is currently unknown if the purchasable Buckethead soundtrack WAD can be played by lr-prboom and if the COMPAT version of the WADs is required instead of the regular WADs for a full playthrough. The regular Sigil WAD does load the first level of Sigil when selecting the fifth episode, though it also breaks all other episodes so that they load episode one when selected: the COMPAT version of the WAD replaces episode three without breaking the other episodes.

Start script

``` sh title="Doom - Sigil.sh"
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/sigil/DOOM.WAD"
```

Folder structure
```
/home/pi/RetroPie/roms/ports/doom/sigil/
                                       DOOM/
                                           prboom.cfg
                                       DOOM.WAD
                                       prboom.wad
                                       SIGIL_v1_21.wad
```


``` sh title="prboom.cfg section (##Files)"
## Files
wadfile_1                 "SIGIL_v1_21.wad"
#wadfile_2                 ""
#wadfile_3                 ""
#wadfile_4                 ""
#wadfile_5                 ""
#wadfile_6                 ""
#wadfile_7                 ""
#wadfile_8                 ""
#dehfile_1                 ""
#dehfile_2                 ""

```

##### Doom 2 - No Rest for the Living

[No Rest for the Living](https://doom.fandom.com/wiki/No_Rest_for_the_Living) was developed by Nerve Software for the release of Doom 2 on the XBLA. The episode consists of nine levels in all, eight standard levels and a single secret level, as a homage to the similarly structured nine-map episodes in the original Doom, particularly _Knee-Deep in the Dead_.

Start script

``` sh title="Doom 2 - No Rest for the Living.sh"
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/no-rest-for-the-living/DOOM2.WAD"
```

Folder structure
```
/home/pi/RetroPie/roms/ports/doom/no-rest-for-the-living/
                                                        DOOM2/
                                                             prboom.cfg
                                                        DOOM2.WAD
                                                        NERVE.WAD
                                                        prboom.wad
```

``` sh title="prboom.cfg section (##Files)"
## Files
wadfile_1                 "NERVE.WAD"
#wadfile_2                 ""
#wadfile_3                 ""
#wadfile_4                 ""
#wadfile_5                 ""
#wadfile_6                 ""
#wadfile_7                 ""
#wadfile_8                 ""
#dehfile_1                 ""
#dehfile_2                 ""
```

##### Lost Episodes of Doom

[The Lost Episodes of Doom](https://doom.fandom.com/wiki/The_Lost_Episodes_of_Doom) is a collection of three eight-level episodes for Doom by Christen Klie and Bob Carter. It takes place on the Jovian moons Callisto and Io, and on Jupiter itself. It was a commercial product.

Start script

``` sh title="Lost Episodes of Doom.sh"
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/lost-episodes-of-doom/DOOM.WAD"
```

Folder structure
```
/home/pi/RetroPie/roms/ports/doom/lost-episodes-of-doom/
                                                       DOOM/
                                                           prboom.cfg
                                                       DOOM.WAD
                                                       JPTR_V40.WAD
                                                       Jptr_fix.wad
                                                       prboom.wad
```

``` sh title="prboom.cfg section (##Files)"
## Files
wadfile_1                 "JPTR_V40.WAD"
wadfile_2                 "Jptr_fix.wad"
#wadfile_3                 ""
#wadfile_4                 ""
#wadfile_5                 ""
#wadfile_6                 ""
#wadfile_7                 ""
#wadfile_8                 ""
#dehfile_1                 ""
#dehfile_2                 ""
```

##### Hell to Pay

[Hell To Pay](https://doom.fandom.com/wiki/Hell_to_Pay) is a partial conversion for Doom II created by Wraith Corporation in 1996 and published by WizardWorks. In the plot of Hell To Pay, Earth is invaded by demonic aliens, and the player must journey to Planet Hell to activate the planet-killer bomb meant for Earth. Compared to Perdition's Gate, which has only new music and some new textures, this conversion has new graphics for textures, monsters, and weapons.

Start script
``` sh title="Hell to Pay.sh"
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/hell-to-pay/DOOM2.WAD"
```

Folder structure
```
/home/pi/RetroPie/roms/ports/doom/hell-to-pay/
                                             DOOM2/
                                                  prboom.cfg
                                             DOOM2.WAD
                                             HTP-RAW.WAD
                                             HTPDMO16.WAD
                                             HTPDMO17.WAD
                                             HTPDMO18.WAD
                                             HTPDMO19.WAD
                                             HTP-RAW.WAD
                                             prboom.wad
```

``` sh title="prboom.cfg section (##Files)"
## Files
wadfile_1                 "HTP-RAW.WAD"
wadfile_2                 "HTPDMO16.WAD"
wadfile_3                 "HTPDMO17.WAD"
wadfile_4                 "HTPDMO18.WAD"
wadfile_5                 "HTPDMO19.WAD"
#wadfile_6                 ""
#wadfile_7                 ""
#wadfile_8                 ""
#dehfile_1                 ""
#dehfile_2                 ""
```

##### Perdition's Gate

[Perdition's Gate](https://doom.fandom.com/wiki/Perdition%27s_Gate) is a 32-level commercial megawad for Doom II designed by Wraith Corporation and published by WizardWorks. Unlike its sister release, Hell to Pay, which is a partial conversion, Perdition's Gate only contains new graphics for various textures and new music besides its levels.

Start script

``` sh title="Perdition's Gate.sh"
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/perditions-gate/DOOM2.WAD"
```

Folder structure
```
/home/pi/RetroPie/roms/ports/doom/perditions-gate/
                                                 DOOM2/
                                                      prboom.cfg
                                                 DOOM2.WAD
                                                 PG-RAW-X.WAD
                                                 prboom.wad
```

``` sh title="prboom.cfg section (##Files)"
## Files
wadfile_1                 "PG-RAW-X.WAD"
#wadfile_2                 ""
#wadfile_3                 ""
#wadfile_4                 ""
#wadfile_5                 ""
#wadfile_6                 ""
#wadfile_7                 ""
#wadfile_8                 ""
#dehfile_1                 ""
#dehfile_2                 ""
```

### LZDoom Installation

#### To Launch Doom, Ultimate Doom, Doom 2, TNT, Plutonia, Final Doom (IWADS)

Use the same method for IWADS detailed above for lr-prboom, only set the default emulator for ROM to `lzdoom` at launch in the [runcommand launch menu](Runcommand#runcommand-launch-menu).

#### To Launch Doom Mods (PWADS)

Here, we'll use [Rex Claussen's, The Darkest Hour](http://doomnexus.drdteam.org/DH_Pix.html) as an example that can be used for any mod. Start by downloading [The Darkest Hour](ftp://ftp.fu-berlin.de/pc/msdos/games/idgames/levels/doom2/Ports/d-f/darkhour.zip). Next, you will either want to SSH into your Pi or drop out of EmulationStation using F4 on your keyboard. 

At the command line, type the following to create a directory for the `DarkHour.wad` file from the 'Darkest Hour' download.

``` sh
mkdir /home/pi/RetroPie/roms/ports/darkesthour
```

You may now transfer the `DarkHour.wad` file to this location via SFTP or Samba.

Next, you'll want to create a new script that we will use to launch The Darkest Hour from EmulationStation.

To do this, type:

``` sh
nano /home/pi/RetroPie/roms/ports/The\ Darkest\ Hour.sh
```

The Nano text editor will open, where you will now add the following to the text edit field.

``` sh
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ darkesthour
```

press `Ctrl+o` to save, `y` to confirm and `Ctrl+x` to exit out of the nano text editor.

Now we want to create a config folder by typing the following:

```
mkdir /opt/retropie/configs/ports/darkesthour
```

Once this is complete you will want to create a 'emulators.cfg' file for this new config folder by typing:

```
nano /opt/retropie/configs/ports/darkesthour/emulators.cfg
```

The Nano text editor will open, where you will now add the following to the text edit field:

``` sh
lzdoom = "/opt/retropie/ports/lzdoom/lzdoom +set fullscreen 1 -iwad /home/pi/RetroPie/roms/ports/doom/doom2.wad -file /home/pi/RetroPie/roms/ports/darkesthour/DarkHour.wad -config /home/pi/RetroPie/roms/ports/darkesthour/zdoom.ini -savedir /home/pi/RetroPie/roms/ports/darkesthour/"
default="lzdoom"
```

press `Ctrl+o` to save, `y` to confirm and `Ctrl+x` to exit out of the Nano text editor.

You'll notice that in the above example that LZDoom is making use of the 'Doom II' wad as a base for the 'Darkest Hour' modification.    This is common in most cases. However, some mods will need to make use of the _Ultimate Doom_ wad file entitled `doom.wad` instead. Both `doom.wad` and `doom2.wad` should be installed to `/home/pi/RetroPie/roms/ports/doom/` and the above example should be set accordingly. Also, you will notice the use of the commands "-config" and "-savedir", using these allow each game to have separate saves and settings. 

Having completed this step, you will now want to restart Emulation Station, navigate to 'Ports' and test your new menu entry.

## Controls

### lr-prboom Controls

lr-prboom utilises normal Retroarch control configurations found in the RetroArch menu by pressing _Hotkey Enable+X_ on your controller after the game software has launched. From the RetroArch Quick Menu, navigate to _Controls_.

For more information on custom RetroArch controls see: [RetroArch Configuration](RetroArch-Configuration)

### ZDoom Controls

LZDoom controls can be found in the Doom options menu by pressing any button or key after the game software has launched. Although the initial configuration may need to be started with a keyboard, full joystick autonomy is possible after being set.

Inside Options -> Joystick Options, under Configure Controllers, your controller should appear. Select it and you'll see assignments for Axes, which for a standard 2-stick style gamepad normally should be:
```
Axis 1: Strafing
Axis 2: Moving Forward
Axis 3: Turning
Axis 4: Looking Up/Down
```
The rest should be set to None

Depending on your type of controller, the axes assignment could vary.

If your character, or the menu cursor, move by themselves, in the same menu option you can add deadzone for each axis. Set it to something like 150-200 initially, and then decrease it if it's too much.

## Enhancements

### Alternative Music for lr-prboom

While lr-prboom does support playing MIDI music from the WADs, its quality leaves something to be desired.

To have higher quality music in your Doom games running in lr-prboom, you need to copy MP3s with specific names into the same folder your WAD for the game is located. You will also need to set PrBoom to use external music always within its internal menu options.

The easiest to use and highest quality authentic soundtrack you can get for games running in lr-prboom are the ones generated by a Roland SC-55 then digitized to MP3. Due to legal reasons, these soundtracks can't be linked here, but if this music is found, a leading `d_` will need to be removed from each MP3's filename, the `ream.mp3` will need to be renamed to `read_m.mp3`, and `mus_e2m5                  "e1m5.mp3"` needs to be changed to `mus_e2m5                  "e2m5.mp3"` in the `prboom.cfg` (if just copying and pasting the examples then this is fixed in them).

Keep in mind that the soundtracks for Doom 2, _Final Doom: TNT: Evilution_, and _Final Doom: The Plutonia Experiment_ are different even though their tracks are named identically. This means that the WADs/MP3s for those three games must be in separate folders to avoid filename conflicts between the MP3s.

An alternative ambient horror music option for your Doom games would be from [Aubrey Hodges](https://aubreyhodges.bandcamp.com/), who scored Doom/Doom 2 and _Final Doom: TNT: Evilution/The Plutonia Experiment_ on the PSX, and will require extensive renaming and copying: [this](https://doomwiki.org/wiki/PlayStation_Doom_music) chart should be useful in identifying which tracks play on each map.

Below you will find examples of the MP3s in the folders for Doom, Doom 2, Final Doom, and Sigil alongside `prboom.cfg` examples that allow you to copy just the required IWAD and respective folder containing the `prboom.cfg` for mods without needing to copy the MP3s.

#### Ultimate Doom

Folder structure 

```
/home/pi/RetroPie/roms/ports/doom/ultimate-doom/
                                               bunny.mp3
                                               DOOM/
                                                   prboom.cfg
                                               DOOM.WAD
                                               e1m1.mp3
                                               e1m2.mp3
                                               e1m3.mp3
                                               e1m4.mp3
                                               e1m5.mp3
                                               e1m6.mp3
                                               e1m7.mp3
                                               e1m8.mp3
                                               e1m9.mp3
                                               e2m1.mp3
                                               e2m2.mp3
                                               e2m3.mp3
                                               e2m4.mp3
                                               e2m5.mp3
                                               e2m6.mp3
                                               e2m7.mp3
                                               e2m8.mp3
                                               e2m9.mp3
                                               e3m1.mp3
                                               e3m2.mp3
                                               e3m3.mp3
                                               e3m4.mp3
                                               e3m5.mp3
                                               e3m6.mp3
                                               e3m7.mp3
                                               e3m8.mp3
                                               e3m9.mp3
                                               inter.mp3
                                               intro.mp3
                                               prboom.wad
                                               victor.mp3
```


``` sh title="prboom.cfg configuration section (## Music)"
## Music
mus_bunny                 "./ultimate-doom/bunny.mp3"
mus_e1m1                  "./ultimate-doom/e1m1.mp3"
mus_e1m2                  "./ultimate-doom/e1m2.mp3"
mus_e1m3                  "./ultimate-doom/e1m3.mp3"
mus_e1m4                  "./ultimate-doom/e1m4.mp3"
mus_e1m5                  "./ultimate-doom/e1m5.mp3"
mus_e1m6                  "./ultimate-doom/e1m6.mp3"
mus_e1m7                  "./ultimate-doom/e1m7.mp3"
mus_e1m8                  "./ultimate-doom/e1m8.mp3"
mus_e1m9                  "./ultimate-doom/e1m9.mp3"
mus_e2m1                  "./ultimate-doom/e2m1.mp3"
mus_e2m2                  "./ultimate-doom/e2m2.mp3"
mus_e2m3                  "./ultimate-doom/e2m3.mp3"
mus_e2m4                  "./ultimate-doom/e2m4.mp3"
mus_e2m5                  "./ultimate-doom/e2m5.mp3"
mus_e2m6                  "./ultimate-doom/e2m6.mp3"
mus_e2m7                  "./ultimate-doom/e2m7.mp3"
mus_e2m8                  "./ultimate-doom/e2m8.mp3"
mus_e2m9                  "./ultimate-doom/e2m9.mp3"
mus_e3m1                  "./ultimate-doom/e3m1.mp3"
mus_e3m2                  "./ultimate-doom/e3m2.mp3"
mus_e3m3                  "./ultimate-doom/e3m3.mp3"
mus_e3m4                  "./ultimate-doom/e3m4.mp3"
mus_e3m5                  "./ultimate-doom/e3m5.mp3"
mus_e3m6                  "./ultimate-doom/e3m6.mp3"
mus_e3m7                  "./ultimate-doom/e3m7.mp3"
mus_e3m8                  "./ultimate-doom/e3m8.mp3"
mus_e3m9                  "./ultimate-doom/e3m9.mp3"
mus_e4m1                  "./ultimate-doom/e3m4.mp3"
mus_e4m2                  "./ultimate-doom/e3m2.mp3"
mus_e4m3                  "./ultimate-doom/e3m3.mp3"
mus_e4m4                  "./ultimate-doom/e1m5.mp3"
mus_e4m5                  "./ultimate-doom/e2m7.mp3"
mus_e4m6                  "./ultimate-doom/e2m4.mp3"
mus_e4m7                  "./ultimate-doom/e2m6.mp3"
mus_e4m8                  "./ultimate-doom/e2m5.mp3"
mus_e4m9                  "./ultimate-doom/e1m9.mp3"
mus_e5m1                  "./sigil/e5m1.mp3"
mus_e5m2                  "./sigil/e5m2.mp3"
mus_e5m3                  "./sigil/e5m3.mp3"
mus_e5m4                  "./sigil/e5m4.mp3"
mus_e5m5                  "./sigil/e5m5.mp3"
mus_e5m6                  "./sigil/e5m6.mp3"
mus_e5m7                  "./sigil/e5m7.mp3"
mus_e5m8                  "./sigil/e5m8.mp3"
mus_e5m9                  "./sigil/e5m9.mp3"
mus_inter                 "./ultimate-doom/inter.mp3"
mus_introa                "./ultimate-doom/intro.mp3"
mus_intro                 "./ultimate-doom/intro.mp3"
mus_victor                "./ultimate-doom/victor.mp3"
mus_adrian                "./doom2/adrian.mp3"
mus_ampie                 "./doom2/ampie.mp3"
mus_betwee                "./doom2/betwee.mp3"
mus_count2                "./doom2/count2.mp3"
mus_countd                "./doom2/countd.mp3"
mus_ddtbl2                "./doom2/ddtbl2.mp3"
mus_ddtbl3                "./doom2/ddtbl3.mp3"
mus_ddtblu                "./doom2/ddtblu.mp3"
mus_dead2                 "./doom2/dead2.mp3"
mus_dead                  "./doom2/dead.mp3"
mus_dm2int                "./doom2/dm2int.mp3"
mus_dm2ttl                "./doom2/dm2ttl.mp3"
mus_doom2                 "./doom2/doom2.mp3"
mus_doom                  "./doom2/doom.mp3"
mus_evil                  "./doom2/evil.mp3"
mus_in_cit                "./doom2/in_cit.mp3"
mus_messag                "./doom2/messag.mp3"
mus_messg2                "./doom2/messg2.mp3"
mus_openin                "./doom2/openin.mp3"
mus_read_m                "./doom2/read_m.mp3"
mus_romer2                "./doom2/romer2.mp3"
mus_romero                "./doom2/romero.mp3"
mus_runni2                "./doom2/runni2.mp3"
mus_runnin                "./doom2/runnin.mp3"
mus_shawn2                "./doom2/shawn2.mp3"
mus_shawn3                "./doom2/shawn3.mp3"
mus_shawn                 "./doom2/shawn.mp3"
mus_stalks                "./doom2/stalks.mp3"
mus_stlks2                "./doom2/stlks2.mp3"
mus_stlks3                "./doom2/stlks3.mp3"
mus_tense                 "./doom2/tense.mp3"
mus_theda2                "./doom2/theda2.mp3"
mus_theda3                "./doom2/theda3.mp3"
mus_the_da                "./doom2/the_da.mp3"
mus_ultima                "./doom2/ultima.mp3"
```

</details>

#### Doom 2

Folder structure

```
/home/pi/RetroPie/roms/ports/doom/doom2/
                                               adrian.mp3
                                               ampie.mp3
                                               betwee.mp3
                                               count2.mp3
                                               countd.mp3
                                               ddtbl2.mp3
                                               ddtbl3.mp3
                                               ddtblu.mp3
                                               dead.mp3
                                               dead2.mp3
                                               dm2int.mp3
                                               dm2ttl.mp3
                                               doom.mp3
                                               DOOM2/
                                                    prboom.cfg
                                               doom2.mp3
                                               DOOM2.WAD
                                               evil.mp3
                                               in_cit.mp3
                                               messag.mp3
                                               messg2.mp3
                                               openin.mp3
                                               prboom.wad
                                               read_m.mp3
                                               romer2.mp3
                                               romero.mp3
                                               runni2.mp3
                                               runnin.mp3
                                               shawn.mp3
                                               shawn2.mp3
                                               shawn3.mp3
                                               stalks.mp3
                                               stlks2.mp3
                                               stlks3.mp3
                                               tense.mp3
                                               theda2.mp3
                                               theda3.mp3
                                               the_da.mp3
                                               ultima.mp3

``` sh title="prboom.cfg configuration section (## Music)"
## Music
mus_bunny                 "./ultimate-doom/bunny.mp3"
mus_e1m1                  "./ultimate-doom/e1m1.mp3"
mus_e1m2                  "./ultimate-doom/e1m2.mp3"
mus_e1m3                  "./ultimate-doom/e1m3.mp3"
mus_e1m4                  "./ultimate-doom/e1m4.mp3"
mus_e1m5                  "./ultimate-doom/e1m5.mp3"
mus_e1m6                  "./ultimate-doom/e1m6.mp3"
mus_e1m7                  "./ultimate-doom/e1m7.mp3"
mus_e1m8                  "./ultimate-doom/e1m8.mp3"
mus_e1m9                  "./ultimate-doom/e1m9.mp3"
mus_e2m1                  "./ultimate-doom/e2m1.mp3"
mus_e2m2                  "./ultimate-doom/e2m2.mp3"
mus_e2m3                  "./ultimate-doom/e2m3.mp3"
mus_e2m4                  "./ultimate-doom/e2m4.mp3"
mus_e2m5                  "./ultimate-doom/e2m5.mp3"
mus_e2m6                  "./ultimate-doom/e2m6.mp3"
mus_e2m7                  "./ultimate-doom/e2m7.mp3"
mus_e2m8                  "./ultimate-doom/e2m8.mp3"
mus_e2m9                  "./ultimate-doom/e2m9.mp3"
mus_e3m1                  "./ultimate-doom/e3m1.mp3"
mus_e3m2                  "./ultimate-doom/e3m2.mp3"
mus_e3m3                  "./ultimate-doom/e3m3.mp3"
mus_e3m4                  "./ultimate-doom/e3m4.mp3"
mus_e3m5                  "./ultimate-doom/e3m5.mp3"
mus_e3m6                  "./ultimate-doom/e3m6.mp3"
mus_e3m7                  "./ultimate-doom/e3m7.mp3"
mus_e3m8                  "./ultimate-doom/e3m8.mp3"
mus_e3m9                  "./ultimate-doom/e3m9.mp3"
mus_e4m1                  "./ultimate-doom/e3m4.mp3"
mus_e4m2                  "./ultimate-doom/e3m2.mp3"
mus_e4m3                  "./ultimate-doom/e3m3.mp3"
mus_e4m4                  "./ultimate-doom/e1m5.mp3"
mus_e4m5                  "./ultimate-doom/e2m7.mp3"
mus_e4m6                  "./ultimate-doom/e2m4.mp3"
mus_e4m7                  "./ultimate-doom/e2m6.mp3"
mus_e4m8                  "./ultimate-doom/e2m5.mp3"
mus_e4m9                  "./ultimate-doom/e1m9.mp3"
mus_e5m1                  "./sigil/e5m1.mp3"
mus_e5m2                  "./sigil/e5m2.mp3"
mus_e5m3                  "./sigil/e5m3.mp3"
mus_e5m4                  "./sigil/e5m4.mp3"
mus_e5m5                  "./sigil/e5m5.mp3"
mus_e5m6                  "./sigil/e5m6.mp3"
mus_e5m7                  "./sigil/e5m7.mp3"
mus_e5m8                  "./sigil/e5m8.mp3"
mus_e5m9                  "./sigil/e5m9.mp3"
mus_inter                 "./ultimate-doom/inter.mp3"
mus_introa                "./ultimate-doom/intro.mp3"
mus_intro                 "./ultimate-doom/intro.mp3"
mus_victor                "./ultimate-doom/victor.mp3"
mus_adrian                "./doom2/adrian.mp3"
mus_ampie                 "./doom2/ampie.mp3"
mus_betwee                "./doom2/betwee.mp3"
mus_count2                "./doom2/count2.mp3"
mus_countd                "./doom2/countd.mp3"
mus_ddtbl2                "./doom2/ddtbl2.mp3"
mus_ddtbl3                "./doom2/ddtbl3.mp3"
mus_ddtblu                "./doom2/ddtblu.mp3"
mus_dead2                 "./doom2/dead2.mp3"
mus_dead                  "./doom2/dead.mp3"
mus_dm2int                "./doom2/dm2int.mp3"
mus_dm2ttl                "./doom2/dm2ttl.mp3"
mus_doom2                 "./doom2/doom2.mp3"
mus_doom                  "./doom2/doom.mp3"
mus_evil                  "./doom2/evil.mp3"
mus_in_cit                "./doom2/in_cit.mp3"
mus_messag                "./doom2/messag.mp3"
mus_messg2                "./doom2/messg2.mp3"
mus_openin                "./doom2/openin.mp3"
mus_read_m                "./doom2/read_m.mp3"
mus_romer2                "./doom2/romer2.mp3"
mus_romero                "./doom2/romero.mp3"
mus_runni2                "./doom2/runni2.mp3"
mus_runnin                "./doom2/runnin.mp3"
mus_shawn2                "./doom2/shawn2.mp3"
mus_shawn3                "./doom2/shawn3.mp3"
mus_shawn                 "./doom2/shawn.mp3"
mus_stalks                "./doom2/stalks.mp3"
mus_stlks2                "./doom2/stlks2.mp3"
mus_stlks3                "./doom2/stlks3.mp3"
mus_tense                 "./doom2/tense.mp3"
mus_theda2                "./doom2/theda2.mp3"
mus_theda3                "./doom2/theda3.mp3"
mus_the_da                "./doom2/the_da.mp3"
mus_ultima                "./doom2/ultima.mp3"
```

</details>

#### Final Doom - Plutonia Experiment

Folder structure

```
/home/pi/RetroPie/roms/ports/doom/final-doom-plutonia-experiment/
                                                                adrian.mp3
                                                                ampie.mp3
                                                                betwee.mp3
                                                                count2.mp3
                                                                countd.mp3
                                                                ddtbl2.mp3
                                                                ddtbl3.mp3
                                                                ddtblu.mp3
                                                                dead.mp3
                                                                dead2.mp3
                                                                dm2int.mp3
                                                                dm2ttl.mp3
                                                                doom.mp3
                                                                doom2.mp3
                                                                evil.mp3
                                                                in_cit.mp3
                                                                messag.mp3
                                                                messg2.mp3
                                                                openin.mp3
                                                                PLUTONIA/
                                                                        prboom.cfg
                                                                PLUTONIA.WAD
                                                                prboom.wad
                                                                read_m.mp3
                                                                romer2.mp3
                                                                romero.mp3
                                                                runni2.mp3
                                                                runnin.mp3
                                                                shawn.mp3
                                                                shawn2.mp3
                                                                shawn3.mp3
                                                                stalks.mp3
                                                                stlks2.mp3
                                                                stlks3.mp3
                                                                tense.mp3
                                                                theda2.mp3
                                                                theda3.mp3
                                                                the_da.mp3
                                                                ultima.mp3
```

``` sh title="prboom.cfg configuration section (## Music)"
## Music
mus_bunny                 "./ultimate-doom/bunny.mp3"
mus_e1m1                  "./ultimate-doom/e1m1.mp3"
mus_e1m2                  "./ultimate-doom/e1m2.mp3"
mus_e1m3                  "./ultimate-doom/e1m3.mp3"
mus_e1m4                  "./ultimate-doom/e1m4.mp3"
mus_e1m5                  "./ultimate-doom/e1m5.mp3"
mus_e1m6                  "./ultimate-doom/e1m6.mp3"
mus_e1m7                  "./ultimate-doom/e1m7.mp3"
mus_e1m8                  "./ultimate-doom/e1m8.mp3"
mus_e1m9                  "./ultimate-doom/e1m9.mp3"
mus_e2m1                  "./ultimate-doom/e2m1.mp3"
mus_e2m2                  "./ultimate-doom/e2m2.mp3"
mus_e2m3                  "./ultimate-doom/e2m3.mp3"
mus_e2m4                  "./ultimate-doom/e2m4.mp3"
mus_e2m5                  "./ultimate-doom/e2m5.mp3"
mus_e2m6                  "./ultimate-doom/e2m6.mp3"
mus_e2m7                  "./ultimate-doom/e2m7.mp3"
mus_e2m8                  "./ultimate-doom/e2m8.mp3"
mus_e2m9                  "./ultimate-doom/e2m9.mp3"
mus_e3m1                  "./ultimate-doom/e3m1.mp3"
mus_e3m2                  "./ultimate-doom/e3m2.mp3"
mus_e3m3                  "./ultimate-doom/e3m3.mp3"
mus_e3m4                  "./ultimate-doom/e3m4.mp3"
mus_e3m5                  "./ultimate-doom/e3m5.mp3"
mus_e3m6                  "./ultimate-doom/e3m6.mp3"
mus_e3m7                  "./ultimate-doom/e3m7.mp3"
mus_e3m8                  "./ultimate-doom/e3m8.mp3"
mus_e3m9                  "./ultimate-doom/e3m9.mp3"
mus_e4m1                  "./ultimate-doom/e3m4.mp3"
mus_e4m2                  "./ultimate-doom/e3m2.mp3"
mus_e4m3                  "./ultimate-doom/e3m3.mp3"
mus_e4m4                  "./ultimate-doom/e1m5.mp3"
mus_e4m5                  "./ultimate-doom/e2m7.mp3"
mus_e4m6                  "./ultimate-doom/e2m4.mp3"
mus_e4m7                  "./ultimate-doom/e2m6.mp3"
mus_e4m8                  "./ultimate-doom/e2m5.mp3"
mus_e4m9                  "./ultimate-doom/e1m9.mp3"
mus_e5m1                  "./sigil/e5m1.mp3"
mus_e5m2                  "./sigil/e5m2.mp3"
mus_e5m3                  "./sigil/e5m3.mp3"
mus_e5m4                  "./sigil/e5m4.mp3"
mus_e5m5                  "./sigil/e5m5.mp3"
mus_e5m6                  "./sigil/e5m6.mp3"
mus_e5m7                  "./sigil/e5m7.mp3"
mus_e5m8                  "./sigil/e5m8.mp3"
mus_e5m9                  "./sigil/e5m9.mp3"
mus_inter                 "./ultimate-doom/inter.mp3"
mus_introa                "./ultimate-doom/intro.mp3"
mus_intro                 "./ultimate-doom/intro.mp3"
mus_victor                "./ultimate-doom/victor.mp3"
mus_adrian                "./final-doom-plutonia-experiment/adrian.mp3"
mus_ampie                 "./final-doom-plutonia-experiment/ampie.mp3"
mus_betwee                "./final-doom-plutonia-experiment/betwee.mp3"
mus_count2                "./final-doom-plutonia-experiment/count2.mp3"
mus_countd                "./final-doom-plutonia-experiment/countd.mp3"
mus_ddtbl2                "./final-doom-plutonia-experiment/ddtbl2.mp3"
mus_ddtbl3                "./final-doom-plutonia-experiment/ddtbl3.mp3"
mus_ddtblu                "./final-doom-plutonia-experiment/ddtblu.mp3"
mus_dead2                 "./final-doom-plutonia-experiment/dead2.mp3"
mus_dead                  "./final-doom-plutonia-experiment/dead.mp3"
mus_dm2int                "./final-doom-plutonia-experiment/dm2int.mp3"
mus_dm2ttl                "./final-doom-plutonia-experiment/dm2ttl.mp3"
mus_doom2                 "./final-doom-plutonia-experiment/doom2.mp3"
mus_doom                  "./final-doom-plutonia-experiment/doom.mp3"
mus_evil                  "./final-doom-plutonia-experiment/evil.mp3"
mus_in_cit                "./final-doom-plutonia-experiment/in_cit.mp3"
mus_messag                "./final-doom-plutonia-experiment/messag.mp3"
mus_messg2                "./final-doom-plutonia-experiment/messg2.mp3"
mus_openin                "./final-doom-plutonia-experiment/openin.mp3"
mus_read_m                "./final-doom-plutonia-experiment/read_m.mp3"
mus_romer2                "./final-doom-plutonia-experiment/romer2.mp3"
mus_romero                "./final-doom-plutonia-experiment/romero.mp3"
mus_runni2                "./final-doom-plutonia-experiment/runni2.mp3"
mus_runnin                "./final-doom-plutonia-experiment/runnin.mp3"
mus_shawn2                "./final-doom-plutonia-experiment/shawn2.mp3"
mus_shawn3                "./final-doom-plutonia-experiment/shawn3.mp3"
mus_shawn                 "./final-doom-plutonia-experiment/shawn.mp3"
mus_stalks                "./final-doom-plutonia-experiment/stalks.mp3"
mus_stlks2                "./final-doom-plutonia-experiment/stlks2.mp3"
mus_stlks3                "./final-doom-plutonia-experiment/stlks3.mp3"
mus_tense                 "./final-doom-plutonia-experiment/tense.mp3"
mus_theda2                "./final-doom-plutonia-experiment/theda2.mp3"
mus_theda3                "./final-doom-plutonia-experiment/theda3.mp3"
mus_the_da                "./final-doom-plutonia-experiment/the_da.mp3"
mus_ultima                "./final-doom-plutonia-experiment/ultima.mp3"
```

#### Final Doom - TNT Evilution

Folder structure

```
/home/pi/RetroPie/roms/ports/doom/final-doom-tnt-evilution/
                                                          adrian.mp3
                                                          ampie.mp3
                                                          betwee.mp3
                                                          count2.mp3
                                                          countd.mp3
                                                          ddtbl2.mp3
                                                          ddtbl3.mp3
                                                          ddtblu.mp3
                                                          dead.mp3
                                                          dead2.mp3
                                                          dm2int.mp3
                                                          dm2ttl.mp3
                                                          doom.mp3
                                                          doom2.mp3
                                                          evil.mp3
                                                          in_cit.mp3
                                                          messag.mp3
                                                          messg2.mp3
                                                          openin.mp3
                                                          prboom.wad
                                                          read_m.mp3
                                                          romer2.mp3
                                                          romero.mp3
                                                          runni2.mp3
                                                          runnin.mp3
                                                          shawn.mp3
                                                          shawn2.mp3
                                                          shawn3.mp3
                                                          stalks.mp3
                                                          stlks2.mp3
                                                          stlks3.mp3
                                                          tense.mp3
                                                          theda2.mp3
                                                          theda3.mp3
                                                          the_da.mp3
                                                          TNT/
                                                             prboom.cfg
                                                          TNT.WAD
                                                          ultima.mp3
```

``` sh title="prboom.cfg configuration section (## Music)"
## Music
mus_bunny                 "./ultimate-doom/bunny.mp3"
mus_e1m1                  "./ultimate-doom/e1m1.mp3"
mus_e1m2                  "./ultimate-doom/e1m2.mp3"
mus_e1m3                  "./ultimate-doom/e1m3.mp3"
mus_e1m4                  "./ultimate-doom/e1m4.mp3"
mus_e1m5                  "./ultimate-doom/e1m5.mp3"
mus_e1m6                  "./ultimate-doom/e1m6.mp3"
mus_e1m7                  "./ultimate-doom/e1m7.mp3"
mus_e1m8                  "./ultimate-doom/e1m8.mp3"
mus_e1m9                  "./ultimate-doom/e1m9.mp3"
mus_e2m1                  "./ultimate-doom/e2m1.mp3"
mus_e2m2                  "./ultimate-doom/e2m2.mp3"
mus_e2m3                  "./ultimate-doom/e2m3.mp3"
mus_e2m4                  "./ultimate-doom/e2m4.mp3"
mus_e2m5                  "./ultimate-doom/e2m5.mp3"
mus_e2m6                  "./ultimate-doom/e2m6.mp3"
mus_e2m7                  "./ultimate-doom/e2m7.mp3"
mus_e2m8                  "./ultimate-doom/e2m8.mp3"
mus_e2m9                  "./ultimate-doom/e2m9.mp3"
mus_e3m1                  "./ultimate-doom/e3m1.mp3"
mus_e3m2                  "./ultimate-doom/e3m2.mp3"
mus_e3m3                  "./ultimate-doom/e3m3.mp3"
mus_e3m4                  "./ultimate-doom/e3m4.mp3"
mus_e3m5                  "./ultimate-doom/e3m5.mp3"
mus_e3m6                  "./ultimate-doom/e3m6.mp3"
mus_e3m7                  "./ultimate-doom/e3m7.mp3"
mus_e3m8                  "./ultimate-doom/e3m8.mp3"
mus_e3m9                  "./ultimate-doom/e3m9.mp3"
mus_e4m1                  "./ultimate-doom/e3m4.mp3"
mus_e4m2                  "./ultimate-doom/e3m2.mp3"
mus_e4m3                  "./ultimate-doom/e3m3.mp3"
mus_e4m4                  "./ultimate-doom/e1m5.mp3"
mus_e4m5                  "./ultimate-doom/e2m7.mp3"
mus_e4m6                  "./ultimate-doom/e2m4.mp3"
mus_e4m7                  "./ultimate-doom/e2m6.mp3"
mus_e4m8                  "./ultimate-doom/e2m5.mp3"
mus_e4m9                  "./ultimate-doom/e1m9.mp3"
mus_e5m1                  "./sigil/e5m1.mp3"
mus_e5m2                  "./sigil/e5m2.mp3"
mus_e5m3                  "./sigil/e5m3.mp3"
mus_e5m4                  "./sigil/e5m4.mp3"
mus_e5m5                  "./sigil/e5m5.mp3"
mus_e5m6                  "./sigil/e5m6.mp3"
mus_e5m7                  "./sigil/e5m7.mp3"
mus_e5m8                  "./sigil/e5m8.mp3"
mus_e5m9                  "./sigil/e5m9.mp3"
mus_inter                 "./ultimate-doom/inter.mp3"
mus_introa                "./ultimate-doom/intro.mp3"
mus_intro                 "./ultimate-doom/intro.mp3"
mus_victor                "./ultimate-doom/victor.mp3"
mus_adrian                "./final-doom-tnt-evilution/adrian.mp3"
mus_ampie                 "./final-doom-tnt-evilution/ampie.mp3"
mus_betwee                "./final-doom-tnt-evilution/betwee.mp3"
mus_count2                "./final-doom-tnt-evilution/count2.mp3"
mus_countd                "./final-doom-tnt-evilution/countd.mp3"
mus_ddtbl2                "./final-doom-tnt-evilution/ddtbl2.mp3"
mus_ddtbl3                "./final-doom-tnt-evilution/ddtbl3.mp3"
mus_ddtblu                "./final-doom-tnt-evilution/ddtblu.mp3"
mus_dead2                 "./final-doom-tnt-evilution/dead2.mp3"
mus_dead                  "./final-doom-tnt-evilution/dead.mp3"
mus_dm2int                "./final-doom-tnt-evilution/dm2int.mp3"
mus_dm2ttl                "./final-doom-tnt-evilution/dm2ttl.mp3"
mus_doom2                 "./final-doom-tnt-evilution/doom2.mp3"
mus_doom                  "./final-doom-tnt-evilution/doom.mp3"
mus_evil                  "./final-doom-tnt-evilution/evil.mp3"
mus_in_cit                "./final-doom-tnt-evilution/in_cit.mp3"
mus_messag                "./final-doom-tnt-evilution/messag.mp3"
mus_messg2                "./final-doom-tnt-evilution/messg2.mp3"
mus_openin                "./final-doom-tnt-evilution/openin.mp3"
mus_read_m                "./final-doom-tnt-evilution/read_m.mp3"
mus_romer2                "./final-doom-tnt-evilution/romer2.mp3"
mus_romero                "./final-doom-tnt-evilution/romero.mp3"
mus_runni2                "./final-doom-tnt-evilution/runni2.mp3"
mus_runnin                "./final-doom-tnt-evilution/runnin.mp3"
mus_shawn2                "./final-doom-tnt-evilution/shawn2.mp3"
mus_shawn3                "./final-doom-tnt-evilution/shawn3.mp3"
mus_shawn                 "./final-doom-tnt-evilution/shawn.mp3"
mus_stalks                "./final-doom-tnt-evilution/stalks.mp3"
mus_stlks2                "./final-doom-tnt-evilution/stlks2.mp3"
mus_stlks3                "./final-doom-tnt-evilution/stlks3.mp3"
mus_tense                 "./final-doom-tnt-evilution/tense.mp3"
mus_theda2                "./final-doom-tnt-evilution/theda2.mp3"
mus_theda3                "./final-doom-tnt-evilution/theda3.mp3"
mus_the_da                "./final-doom-tnt-evilution/the_da.mp3"
mus_ultima                "./final-doom-tnt-evilution/ultima.mp3"
```

#### Doom - Sigil

A chart to assist with renaming the MP3 soundtrack can be found [here](https://doomwiki.org/wiki/SIGIL).

The soundtrack for the levels can be found [here](https://music.bucketheadpikes.com/album/sigil-soundtrack), the music for the title screen can be found [here](https://music.bucketheadpikes.com/track/eye-on-spiral-part-1), and the music for the intermission screen can be found [here](https://music.bucketheadpikes.com/track/triceratoptron).

Folder structure

```
/home/pi/RetroPie/roms/ports/doom/sigil/
                                       DOOM/
                                           prboom.cfg
                                       DOOM.WAD
                                       e5m1.mp3
                                       e5m2.mp3
                                       e5m3.mp3
                                       e5m4.mp3
                                       e5m5.mp3
                                       e5m6.mp3
                                       e5m7.mp3
                                       e5m8.mp3
                                       e5m9.mp3
                                       inter.mp3
                                       intro.mp3
                                       prboom.wad
                                       SIGIL_v1_21.wad
```

``` sh title="prboom.cfg configuration section (## Music)"
## Music
mus_bunny                 "./ultimate-doom/bunny.mp3"
mus_e1m1                  "./ultimate-doom/e1m1.mp3"
mus_e1m2                  "./ultimate-doom/e1m2.mp3"
mus_e1m3                  "./ultimate-doom/e1m3.mp3"
mus_e1m4                  "./ultimate-doom/e1m4.mp3"
mus_e1m5                  "./ultimate-doom/e1m5.mp3"
mus_e1m6                  "./ultimate-doom/e1m6.mp3"
mus_e1m7                  "./ultimate-doom/e1m7.mp3"
mus_e1m8                  "./ultimate-doom/e1m8.mp3"
mus_e1m9                  "./ultimate-doom/e1m9.mp3"
mus_e2m1                  "./ultimate-doom/e2m1.mp3"
mus_e2m2                  "./ultimate-doom/e2m2.mp3"
mus_e2m3                  "./ultimate-doom/e2m3.mp3"
mus_e2m4                  "./ultimate-doom/e2m4.mp3"
mus_e2m5                  "./ultimate-doom/e2m5.mp3"
mus_e2m6                  "./ultimate-doom/e2m6.mp3"
mus_e2m7                  "./ultimate-doom/e2m7.mp3"
mus_e2m8                  "./ultimate-doom/e2m8.mp3"
mus_e2m9                  "./ultimate-doom/e2m9.mp3"
mus_e3m1                  "./ultimate-doom/e3m1.mp3"
mus_e3m2                  "./ultimate-doom/e3m2.mp3"
mus_e3m3                  "./ultimate-doom/e3m3.mp3"
mus_e3m4                  "./ultimate-doom/e3m4.mp3"
mus_e3m5                  "./ultimate-doom/e3m5.mp3"
mus_e3m6                  "./ultimate-doom/e3m6.mp3"
mus_e3m7                  "./ultimate-doom/e3m7.mp3"
mus_e3m8                  "./ultimate-doom/e3m8.mp3"
mus_e3m9                  "./ultimate-doom/e3m9.mp3"
mus_e4m1                  "./ultimate-doom/e3m4.mp3"
mus_e4m2                  "./ultimate-doom/e3m2.mp3"
mus_e4m3                  "./ultimate-doom/e3m3.mp3"
mus_e4m4                  "./ultimate-doom/e1m5.mp3"
mus_e4m5                  "./ultimate-doom/e2m7.mp3"
mus_e4m6                  "./ultimate-doom/e2m4.mp3"
mus_e4m7                  "./ultimate-doom/e2m6.mp3"
mus_e4m8                  "./ultimate-doom/e2m5.mp3"
mus_e4m9                  "./ultimate-doom/e1m9.mp3"
mus_e5m1                  "./sigil/e5m1.mp3"
mus_e5m2                  "./sigil/e5m2.mp3"
mus_e5m3                  "./sigil/e5m3.mp3"
mus_e5m4                  "./sigil/e5m4.mp3"
mus_e5m5                  "./sigil/e5m5.mp3"
mus_e5m6                  "./sigil/e5m6.mp3"
mus_e5m7                  "./sigil/e5m7.mp3"
mus_e5m8                  "./sigil/e5m8.mp3"
mus_e5m9                  "./sigil/e5m9.mp3"
mus_inter                 "./sigil/inter.mp3"
mus_introa                "./sigil/intro.mp3"
mus_intro                 "./sigil/intro.mp3"
mus_victor                "./ultimate-doom/victor.mp3"
mus_adrian                "./doom2/adrian.mp3"
mus_ampie                 "./doom2/ampie.mp3"
mus_betwee                "./doom2/betwee.mp3"
mus_count2                "./doom2/count2.mp3"
mus_countd                "./doom2/countd.mp3"
mus_ddtbl2                "./doom2/ddtbl2.mp3"
mus_ddtbl3                "./doom2/ddtbl3.mp3"
mus_ddtblu                "./doom2/ddtblu.mp3"
mus_dead2                 "./doom2/dead2.mp3"
mus_dead                  "./doom2/dead.mp3"
mus_dm2int                "./doom2/dm2int.mp3"
mus_dm2ttl                "./doom2/dm2ttl.mp3"
mus_doom2                 "./doom2/doom2.mp3"
mus_doom                  "./doom2/doom.mp3"
mus_evil                  "./doom2/evil.mp3"
mus_in_cit                "./doom2/in_cit.mp3"
mus_messag                "./doom2/messag.mp3"
mus_messg2                "./doom2/messg2.mp3"
mus_openin                "./doom2/openin.mp3"
mus_read_m                "./doom2/read_m.mp3"
mus_romer2                "./doom2/romer2.mp3"
mus_romero                "./doom2/romero.mp3"
mus_runni2                "./doom2/runni2.mp3"
mus_runnin                "./doom2/runnin.mp3"
mus_shawn2                "./doom2/shawn2.mp3"
mus_shawn3                "./doom2/shawn3.mp3"
mus_shawn                 "./doom2/shawn.mp3"
mus_stalks                "./doom2/stalks.mp3"
mus_stlks2                "./doom2/stlks2.mp3"
mus_stlks3                "./doom2/stlks3.mp3"
mus_tense                 "./doom2/tense.mp3"
mus_theda2                "./doom2/theda2.mp3"
mus_theda3                "./doom2/theda3.mp3"
mus_the_da                "./doom2/the_da.mp3"
mus_ultima                "./doom2/ultima.mp3"
```


### Music for LZDoom/GZDoom/DSDA-Doom

LZDoom handles the MIDI music from the Doom games automatically. Options are provided in the in-game menu for various MIDI emulation devices, including OPL3, Timidity and FluidSynth.

Several fan-created MIDI music packs also exist, which can be loaded as PWAD / PK3 files using the methods outlined above.
