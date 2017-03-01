![](http://1.bp.blogspot.com/-q1BVHMrTq7M/UT9Y6D_tCLI/AAAAAAAAD40/fM2ZUTzEIqE/s1600/risen3d+3d+models+doom+title.png)

***
_Doom was the one game that popularised First Person Shooting as a genre. It was developed by Id Software in 1993._

***
## Emulator: [lr-prboom](https://github.com/petrockblog/RetroPie-Setup/blob/master/scriptmodules/libretrocores/lr-prboom.sh), [ZDOOM](https://github.com/rheit/zdoom)

## Controls

### Configuring controls for lr-prboom

lr-prboom utilises normal Retroarch control configurations found in the RetroArch menu by pressing 'select+x' on your controller after the game software has launched. From the RetroArch menu, navigate to 'Quick Menu' and then to 'Controls'.

For more information on custom RetroArch controls see: [RetroArch Configuration](https://github.com/retropie/retropie-setup/wiki/retroarch-configuration)

### Configuring controls for ZDoom

ZDoom controls can be found in the Doom options menu by pressing any button or key after the game software has launched. Although the initial configuration may need to be started with a keyboard, full joystick autonomy is possible after being set.

### How to Launch Doom IWADs and Mods (PWADs) from Emulationstation using lr-prboom

#### To Launch Doom, Ultimate Doom, Doom 2, TNT, Plutonia, Final Doom (IWADS)

Place your WADs in the doom rom folder, `/home/pi/RetroPie/roms/ports/doom`.

Create a shell script to launch your WAD. For example, for The Plutonia Expriment, 

```
nano /home/pi/RetroPie/roms/ports/The\ Plutonia\ Experiment.sh
```

The nano text editor will open, where you will now add the following to the text edit field.

```
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ "doom" "/home/pi/RetroPie/roms/ports/doom/plutonia.wad"
```

press 'ctrl+o' to save, 'y' to confirm and 'ctrl+x' to exit out of the nano text editor.

Set the proper file permissions for the script with:

```
chmod 0755 "/home/pi/RetroPie/roms/ports/The\ Plutonia\ Experiment.sh"
```

Set the default emulator for ROM to 'lr-prboom' at launch in the runcommand menu.

#### To Launch Doom Mods (PWADS)

In the doom rom folder, you will need prboom.wad and whichever Doom IWAD is required for the particular mod (`doom.wad` and/or `doom2.wad`).

Create a folder named for the intended mod and transfer the custom PWAD there. 

Using the 'Batman Doom' mod as an example, we'll create a folder called 'batman_doom' by typing:

```
mkdir /home/pi/RetroPie/roms/ports/batman_doom/
```

Create symlinks to prboom.wad and Doom2 WAD in the batman_doom folder with the following commands. If you have problems creating these links, you can also just copy these files.

```shell
ln -s /home/pi/RetroPie/roms/ports/doom/prboom.wad /home/pi/RetroPie/roms/ports/batman_doom/prboom.wad
```
```shell
ln -s /home/pi/RetroPie/roms/ports/doom/doom2.wad /home/pi/RetroPie/roms/ports/batman_doom/doom2.wad
```

Copy prboom.cfg from the Doom folder to the custom WAD folder. Add the name(s) of the custom WADs to #Files section (line 15/16).

Create a shell script named 'Batman Doom.sh' that will launch the custom WAD. 

```
nano /home/pi/RetroPie/roms/ports/Batman\ Doom.sh
```

The nano text editor will open, where you will now add the following to the text edit field. It's the same as Doom 2 script but it points to the Doom 2 IWAD in the batman folder instead.

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/doom/batman/doom2.wad" "lr-prboom"
```
press 'ctrl+o' to save, 'y' to confirm and 'ctrl+x' to exit out of the nano text editor.

Set the proper file permissions for the script with:

```
chmod 0755 "/home/pi/RetroPie/roms/ports/Batman\ Doom.sh"
```

Repeat for each mod (PWAD), creating a new folder for each one and a copy of the script above replacing the folder name as required.

### How to Launch Doom IWADs and Mods (PWADs) from Emulationstation using ZDOOM.

#### To Launch Doom, Ultimate Doom, Doom 2, TNT, Plutonia, Final Doom (IWADS)

Use the same method for IWADS detailed above for lr-prboom, only set the default emulator for ROM to 'zdoom' at launch in the runcommand menu.

#### To Launch Doom Mods (PWADS)

Here, we'll use [Rex Claussen's, The Darkest Hour](http://doomnexus.drdteam.org/DH_Pix.html) as an example that can be used for any mod. Start by downloading [The Darkest Hour](ftp://ftp.fu-berlin.de/pc/msdos/games/idgames/levels/doom2/Ports/d-f/darkhour.zip). Next you will either want to SSH into your Pi, or drop out of EmulationStation using F4 on your keyboard. 

At the command line, type the following to create a directory for the `DarkHour.wad` file from the 'Darkest Hour' download.

```
mkdir /home/pi/RetroPie/roms/ports/darkesthour
```

You may now transfer the `DarkHour.wad` file to this location via SFTP or Samba.

Next you'll want to create a new script that we will use to launch The Darkest Hour from EmulationStation.

To do this, type:

```
nano /home/pi/RetroPie/roms/ports/The\ Darkest\ Hour.sh
```

The nano text editor will open, where you will now add the following to the text edit field.

```shell
#!/bin/bash
"/opt/retropie/supplementary/runcommand/runcommand.sh" 0 _PORT_ darkesthour
```

press 'ctrl+o' to save, 'y' to confirm and 'ctrl+x' to exit out of the nano text editor.

Set the proper file permissions for the script with:

```
chmod 0755 "/home/pi/RetroPie/roms/ports/The\ Darkest\ Hour.sh"
```

Now we want to create a config folder by typing the following:

```
mkdir /opt/retropie/configs/ports/darkesthour
```

Once this is complete you will want to create a 'emulators.cfg' file for this new config folder by typing:

```
nano /opt/retropie/configs/ports/darkesthour/emulators.cfg
```

The nano text editor will open, where you will now add the following to the text edit field.

```
zdoom = "/opt/retropie/ports/zdoom/zdoom +set fullscreen 1 -iwad /home/pi/RetroPie/roms/ports/doom/doom2.wad -file /home/pi/RetroPie/roms/ports/darkesthour/DarkHour.wad"`
default="zdoom"
```

press 'ctrl+o' to save, 'y' to confirm and 'ctrl+x' to exit out of the nano text editor.

You'll notice that in the above example that ZDoom is making use of the 'Doom II' wad as a base for the 'Darkest Hour' modification. This is common in most cases. However, some mods will need to make use of the 'Ultimate Doom' wad file entitled `doom.wad` instead. Both `doom.wad` and `doom2.wad` should be installed to `/home/pi/RetroPie/roms/ports/doom/` and the above example should be set accordingly.

Having completed this step, you will now want to restart Emulation Station, navigate to 'Ports' and test your new menu entry.

### How to setup Freedoom

[Freedoom](https://freedoom.github.io/index.html) is a collection of reusable assets (textures, sound effects and music tracks) that will completely replace the original Doom assets and are liberally licensed under the [BSD license](https://en.wikipedia.org/wiki/BSD_licenses).

Why is this important to me?

[id Software](http://www.idsoftware.com/) released the source code for Doom's engine under the [GNU General Public License](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html) but not the assets so to legally use this, you would either need the [shareware version](ftp://ftp.idsoftware.com/idstuff/doom/) or you would need to own the original game (which you can still purchase online on [Steam](http://store.steampowered.com/sub/18397/), [GOG.com](https://www.gog.com/game/the_ultimate_doom) and other places like eBay).

Freedoom aims to be compatible with many of the thousands of Doom levels and other “mods” already released for the original game making them playable without the need to use non-free software.  This project has been a work-in-progress for many years now and has already replaced a considerable amount of the game's content but still haven't reached the targeted version 1.0.

Freedoom is divided into three [IWADs](https://zdoom.org/wiki/IWAD).

* Phase 1, which is a replacement for the original Doom and The Ultimate Doom containing 4 chapters with 9 levels each.

* Phase 2, which replaces Doom II and Final Doom and contains a massive 32-level chapter.

* Last FreeDM, which also replaces Doom II and Final Doom and is designed to be a fast-paced competitive deathmatch only campaign containing no monsters.

First you need to download Freedoom: [https://freedoom.github.io/download.html](https://freedoom.github.io/download.html)

As of this writing, the newest version of Freedoom is 0.11 so you can use wget to download the 2 files needed:
```
cd
wget https://github.com/freedoom/freedoom/releases/download/v0.11/freedoom-0.11.zip && wget https://github.com/freedoom/freedoom/releases/download/v0.11/freedm-0.11.zip
```

Next extract both files:

`unzip freedoom-0.11.zip && unzip freedm-0.11.zip`

The files will be extracted to folders named `freedoom-0.11` and `freedm-0.11` respectively and I like to keep all the Doom WADs in the same folder so why not put them with the shareware doom1.wad.

`mv freedoom-0.11/freedoom*.wad freedm-0.11/freedm.wad /home/pi/RetroPie/roms/ports/doom/`

Now we need to make scripts so we can launch Freedoom from EmulationStation using lr-prboom. We want to place these scripts in the Ports directory.

`nano /home/pi/RetroPie/roms/ports/Freedoom\ Phase\ 1.sh`

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/ports/doom/freedoom1.wad" "lr-prboom"
```

`nano /home/pi/RetroPie/roms/ports/Freedoom\ Phase\ 2.sh`

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/ports/doom/freedoom2.wad" "lr-prboom"
```

`nano /home/pi/RetroPie/roms/ports/FreeDM.sh`

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/emulators/retroarch/bin/retroarch -L /opt/retropie/libretrocores/lr-prboom/prboom_libretro.so --config /opt/retropie/configs/ports/doom/retroarch.cfg /home/pi/RetroPie/roms/ports/doom/freedm.wad" "lr-prboom"
```

If you would rather use [ZDoom](https://zdoom.org/News) use this with the correct WAD filename:

```shell
#!/bin/bash
/opt/retropie/supplementary/runcommand/runcommand.sh 0 "/opt/retropie/ports/zdoom/zdoom -iwad /home/pi/RetroPie/roms/ports/doom/freedoom1.wad" "zdoom"
```

After all the scripts have been made, you will need to set them to be executable.

`chmod +x /home/pi/RetroPie/roms/ports/Freedoom\ Phase\ 1.sh /home/pi/RetroPie/roms/ports/Freedoom\ Phase\ 2.sh /home/pi/RetroPie/roms/ports/FreeDM.sh`

Last step is to reboot EmulationStation and navigate to the Ports.  You should now see these 3 Freedoom games on the list.

To delete the left over extracted folders and downloaded files:
```
cd
rm -rf freedoom-0.11/ freedm-0.11/ freedoom-0.11.zip freedm-0.11.zip
```

### Music

The most ideal and authentic way to listen to the the original Doom (1&2) tracks is to google 'doom 1 and 2 midis' and download them. You can then convert the midi files into MP3s.

To enable music in your Doom game(s) you need to copy MP3s with specific names into the same folder as your ROMs are located. You can find a list of names [here](https://github.com/libretro/libretro-prboom/blob/master/src/m_misc.c#L605): They follow the scheme e1m1.mp3, e1m2.mp3, ..., e2m1.mp, e2m2.mp3, ... . There are freely available tracks available - find them by searching for "PSX Doom Music".

If you are having trouble with the audio not playing after you have renamed all the MP3s, try clearing all the ID3 tag information for each of the MP3s.

Below are the corresponding tracks if the MP3s are named:

File Name | mp3 
 --- | ---
* mus_e1m1       |           "level 01 (hangar).mp3" 
* mus_e1m2        |          "level 02 (plant).mp3" 
* mus_e1m3         |         "level 03 (toxin refinery).mp3" 
* mus_e1m4          |        "level 04 (command control).mp3" 
* mus_e1m5           |       "level 05 (phobos lab).mp3" 
* mus_e1m6            |      "level 06 (central processing).mp3" 
* mus_e1m7            |      "level 07 (computer station).mp3" 
* mus_e1m8          |        "level 08 (phobos anomaly).mp3" 
* mus_e1m9           |       "level 06 (fistula).mp3" 
* mus_e2m1          |        "level 09 (deimos anomaly).mp3" 
* mus_e2m2          |        "level 10 (containment area).mp3" 
* mus_e2m3          |        "level 11 (refinery).mp3" 
* mus_e2m4          |        "level 12 (deimos lab).mp3" 
* mus_e2m5          |        "level 13 (command center).mp3" 
* mus_e2m6          |        "level 02 (plant).mp3" 
* mus_e2m7          |        "level 01 (hangar).mp3" 
* mus_e2m8          |        "level 03 (toxin refinery).mp3" 
* mus_e2m9          |        "level 02 (virgil).mp3" 
* mus_e3m1          |        "level 17 (hell keep).mp3" 
* mus_e3m2          |        "level 03 (canyon).mp3" 
* mus_e3m3          |        "level 18 (pandemonium).mp3" 
* mus_e3m4          |        "level 06 (central processing).mp3" 
* mus_e3m5          |        "level 20 (unholy cathedral).mp3" 
* mus_e3m6          |        "level 21 (mt erebus).mp3" 
* mus_e3m7          |        "level 22 (limbo).mp3" 
* mus_e3m8          |        "level 09 (nessus).mp3" 
* mus_e3m9          |        "level 10 (paradox).mp3" 
* mus_inter         |        "e2m3.mp3" 
* mus_intro         |        "track 02 title screen.mp3" 
* mus_bunny         |        "track 03 main menu.mp3" 
* mus_victor        |        "track 09 endgame.mp3" 
* mus_introa        |        "track 02 title screen.mp3" 
* mus_runnin        |        "level 01 (hangar).mp3" 
* mus_stalks        |        "level 10 (containment area).mp3" 
* mus_countd        |        "level 22 (limbo).mp3" 
* mus_betwee        |        "level 16 (hell gate).mp3" 
* mus_doom          |        "level 08 (phobos anomaly).mp3" 
* mus_the_da        |        "level 21 (mt erebus).mp3" 
* mus_shawn         |        "level 20 (unholy cathedral).mp3" 
* mus_ddtblu        |        "level 24 (hell beneath).mp3" 
* mus_in_cit        |        "level 11 (refinery).mp3" 
* mus_dead          |        "level 13 (command center).mp3" 
* mus_stlks2           |     "level 09 (deimos anomaly).mp3" 
* mus_theda2           |     "level 17 (hell keep).mp3" 
* mus_doom2            |     "level 08 (minos).mp3" 
* mus_ddtbl2            |    "level 16 (hell gate).mp3" 
* mus_runni2           |     "level 04 (combine).mp3" 
* mus_dead2            |     "level 18 (pandemonium).mp3" 
* mus_stlks3          |      "level 06 (central processing).mp3" 
* mus_romero          |      "level 05 (phobos lab).mp3" 
* mus_shawn2          |      "level 10 (containment area).mp3" 
* mus_messag          |      "level 01 (attack).mp3" 
* mus_count2          |      "level 02 (plant).mp3" 
* mus_ddtbl3         |       "level 03 (toxin refinery).mp3" 
* mus_ampie          |       "level 01 (hangar).mp3" 
* mus_theda3         |       "level 06 (fistula).mp3" 
* mus_adrian           |     "level 07 (computer station).mp3" 
* mus_messg2          |      "level 08 (phobos anomaly).mp3" 
* mus_romer2          |      "level 11 (refinery).mp3" 
* mus_tense           |      "level 07 (geryon).mp3" 
* mus_shawn3          |      "level 05 (catwalk).mp3" 
* mus_openin          |      "level 04 (command control).mp3" 
* mus_evil            |      "level 16 (hell gate).mp3" 
* mus_ultima          |      "level 03 (toxin refinery).mp3" 
* mus_read_m          |      "track 03 main menu.mp3" 
* mus_dm2ttl          |      "track 02 title screen.mp3" 
* mus_dm2int         |       "track 05 stats screen.mp3"